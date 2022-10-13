# Messaging semantic conventions vNext

## Single messages

### Span name

The span name should be descriptive and make it clear, what operation a span
describes. In the context of messaging systems, this means that a span should
at the very least make clear that it refers to a messaging system, in addition
it needs to make clear what particular [messaging operation](#operation-name)
it refers to.

Ideally, the span name also contains the destination name of the messages it
refers to. However, a destination name should only be added to the span name
when it is of low cardinality. This is usually the case when the destination
name is a meaningful and manually configured name (like a manually configure
queue or topic name), it is usually not the case if the destination name is an
auto-generated identifier (like a conversation id or an auto-generated name for
an anonymous destination).

> The span name SHOULD consist of the name of the messaging system followed by
> an [operation name](#operation-name). The destination name MAY be appended if
> it is of low cardinality.

#### Examples

* `kafka publish shop.orders`
* `rabbitmq receive print_jobs`
* `AmazonSQS deliver`
* `activemq settle`

### Operation name

The following operations related to messages are covered by these semantic
conventions:

| Operation name | Description |
|----------------|-------------|
| `publish`      | One ore more messages are provided for publishing to an intermediary. |
| `create`       | A message is created. |
| `receive`      | One or more messages are requested by a consumer. |
| `deliver`      | One or more message are passed to a consumer. |
| `settle`       | One or more message are settled. |

For further details about each of those operations refer, to the [section about trace structure](#trace-structure).

### Span kind

[Span kinds](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/trace/api.md#spankind)
SHOULD be set according to the following table, based on the operation a span describes.

| Operation name | Span kind|
|----------------|-------------|
| `publish`      | `PRODUCER`, if no `create` spans are present. `INTERNAL` otherwise. |
| `create`       | `PRODUCER` |
| `receive`      | `CONSUMER` |
| `deliver`      | `CONSUMER` |
| `settle`       | `INTERNAL` |

Setting span kinds according to this table ensures, that span links between
consumer and producers always go from a `PRODUCER` span on the producer side to
a `CONSUMER` span on the consumer side. This allows analysis tools to interpret
linked traces without the need of additional semantic hints.

### Attributes

#### Common

<!-- semconv messaging_vnext.common -->
| Attribute  | Type | Description  | Examples  | Requirement Level |
|---|---|---|---|---|
| `messaging_vnext.batch.size` | int | The number of messages sent, received, or processed in the scope of the batching operation. [1] | `0`; `1` | Conditionally Required: [2] |
| `messaging_vnext.operation` | string | This attribute should be set to one of the [pre-defined operation names](#operation-names). | `publish` | Required |
| `messaging_vnext.system` | string | A string identifying the messaging system. [3] | `kafka`; `rabbitmq`; `rocketmq`; `activemq`; `AmazonSQS` | Required |
| [`net.app.protocol.name`](span-general.md) | string | Application layer protocol used. The value SHOULD be normalized to lowercase. | `amqp`; `http`; `mqtt` | Recommended |
| [`net.app.protocol.version`](span-general.md) | string | Version of the application layer protocol used. See note below. [4] | `3.1.1` | Recommended |
| [`net.peer.name`](span-general.md) | string | Logical remote hostname, see note below. [5] | `example.com` | Conditionally Required: If available |
| [`net.peer.port`](span-general.md) | int | Logical remote port number [6] | `80`; `8080`; `443` | Conditionally Required: [7] |
| [`net.sock.family`](span-general.md) | string | Protocol [address family](https://man7.org/linux/man-pages/man7/address_families.7.html) which is used for communication. | `inet6`; `bluetooth` | Conditionally Required: [8] |
| [`net.sock.peer.addr`](span-general.md) | string | Remote socket peer address: IPv4 or IPv6 for internet protocols, path for local communication, [etc](https://man7.org/linux/man-pages/man7/address_families.7.html). | `127.0.0.1`; `/tmp/mysql.sock` | Recommended |
| [`net.sock.peer.name`](span-general.md) | string | Remote socket peer name. | `proxy.example.com` | Recommended: [9] |
| [`net.sock.peer.port`](span-general.md) | int | Remote socket peer port. | `16456` | Recommended: [10] |

**[1]:** Instrumentation SHOULD always set it on batch `receive` operations regardless of the actual number of received messages (e.g. 0, 1, or more).

**[2]:** If available within the messaging system, and only if the span describes operations that operate with message batches.

**[3]:** A string identifying the messaging broker or intermediary, e. g. `kafka`,
`rabbitmq`, `rocketmq`, `AzureEventHubs`, or `AmazonSQS`.

If the messaging broker or intermediary are not known, this should be set to a
value that best identifies the usage scenario. This could be the messaging
library used (e. g. `jms`), or the protocol used (e. g. `amqp`).

A list of recommended values will be provided independently of the messaging
semantic conventions document.

**[4]:** `net.app.protocol.version` refers to the version of the protocol used and might be different from the protocol client's version. If the HTTP client used has a version of `0.27.2`, but sends HTTP version `1.1`, this attribute should be set to `1.1`.

**[5]:** This should be the hostname of the broker this specific operation is performed against.

**[6]:** This should be the port of the broker this specific operation is performed for.

**[7]:** If available and if not default for the network protocol used

**[8]:** If different than `inet` and if any of `net.sock.peer.addr` or `net.sock.host.addr` are set. Consumers of telemetry SHOULD accept both IPv4 and IPv6 formats for the address in `net.sock.peer.addr` if `net.sock.family` is not set. This is to support instrumentations that follow previous versions of this document.

**[9]:** If different than `net.peer.name` and if `net.sock.peer.addr` is set.

**[10]:** If defined for the address family and if different than `net.peer.port` and if `net.sock.peer.addr` is set.
<!-- endsemconv -->

##### Producer

When publishing single message, instrumentations SHOULD create one span to track sending and inject it into the message.
If message already has context, instrumentation MUST create a link from publish span to message context and MUST not modify message context.
Instrumentation SHOULD put per-message attributes on the publish span.

<!-- semconv messaging_vnext.publish_and_create -->
| Attribute  | Type | Description  | Examples  | Requirement Level |
|---|---|---|---|---|
| `messaging_vnext.destination.name` | string | A string identifying queue, topic, or other entity name within a broker or globally. [1] | `MyQueue`; `MyTopic` | Conditionally Required: [2] |
| `messaging_vnext.destination.kind` | string | The kind of message destination [3] | `queue` | Conditionally Required: [4] |
| `messaging_vnext.destination.template` | string | Low cardinality field representing messaging destination [5] | `/customers/{customerId}` | Conditionally Required: when available |
| `messaging_vnext.destination.temporary` | boolean | denotes that the destination is a temporary destination and might not exist anymore after messages are processed |  | Recommended: [6] |
| `messaging_vnext.destination.anonymous` | boolean | denotes that the destination is an anonymous destination (could be unnamed or have auto-generated name) [7] |  | Recommended: [8] |
| `messaging_vnext.message.correlation_id` | string | A value used by application to correlate request and responses, represented as a string. | `1452a7c7c7c7048c2f887f61572b18fc` | Recommended |
| `messaging_vnext.message.id` | string | A value used by the messaging system as an identifier for the message, represented as a string. | `452a7c7c7c7048c2f887f61572b18fc2` | Recommended |
| `messaging_vnext.message.timestamp` | int | Message timestamp that matches either creation time or enqueued time. The earliest time available should be used. MUST be absolute Unix epoch time. | `1661407697` | Recommended |

**[1]:** If messages in a batch have different `messaging_vnext.destination.name` it MUST
be populated on each corresponding link to message context. Otherwise it MUST be populated on 
publish span.

**[2]:** If available and only if different for multiple messages sent in a single batch.

**[3]:** Different brokers have different concepts of message destinations, the most
popular being queues and topics. One of the most important differences in
destination kinds is how messages are settled: messages are settled
individually in queues, whereas messages are settled based on checkpoints in
topics. Individual brokers might specify additional destination kinds.

**[4]:** If the message destination is either a `queue` or `topic`.

**[5]:** In some instances, message destination names are constructed from templates. An
example would be a destination name involving a user name or product id.
Although the destination name in this case is of high cardinality, the
underlying template is of low cardinality and can be effectively used for
grouping and searching spans.

This attribute is optional, but recommended if the destination name is created
based on such a template.

**[6]:** when supported by messaging system and only if the destination is temporary. If missing, assumed to be false.

**[7]:** If set to `true`, this flag denotes that the destination is a temporary
destination and might not exist anymore after messages are processed.

**[8]:** when supported by messaging system and only if the destination is anonymous. If missing, assumed to be false.

`messaging_vnext.destination.kind` has the following list of well-known values. If one of them applies, then the respective value MUST be used, otherwise a custom value MAY be used.

| Value  | Description |
|---|---|
| `queue` | A message sent to a queue |
| `topic` | A message sent to a topic |
<!-- endsemconv -->

##### Consumer

Push and pull-based consumers have different tracing semantics (`receive` operation for pull and `deliver` for push).

If message is pulled by consumer, instrumentation MUST add a link to the message being received on the `receive` span. 

Since the context is not known until pull request completes and it's not possible to add links after span start,
instrumentations SHOULD record the start time when receive call starts, but postpone span creation until messages are received. 
Instrumentations SHOULD use recorded time to set start time on the span being created.
When recording a link to  received message, per-message attributes SHOULD be set on `receive` span.

If message is pushed to consumer, instrumentations SHOULD use trace-context from received message as a remote parent to `deliver` 
span and populate message-specific attributes on `deliver span`.

<!-- semconv messaging_vnext.consumer -->
| Attribute  | Type | Description  | Examples  | Requirement Level |
|---|---|---|---|---|
| `messaging_vnext.source.name` | string | A string identifying queue, topic, or other entity name within broker or globally [1] | `MyQueue`; `MyTopic` | Conditionally Required: [2] |
| `messaging_vnext.source.kind` | string | The kind of message destination | `queue` | Conditionally Required: [3] |
| `messaging_vnext.source.template` | string | Low cardinality field representing messaging destination | `/customers/{customerId}` | Conditionally Required: when available |
| `messaging_vnext.source.temporary` | boolean | denotes that the source is a temporary source and might not exist anymore after messages are processed |  | Recommended: [4] |
| `messaging_vnext.source.anonymous` | boolean | denotes that the source is an anonymous source (could be unnamed or have auto-generated name) |  | Recommended: [5] |
| `messaging_vnext.message.correlation_id` | string | A value used by application to correlate request and responses, represented as a string. | `1452a7c7c7c7048c2f887f61572b18fc` | Recommended |
| `messaging_vnext.message.id` | string | A value used by the messaging system as an identifier for the message, represented as a string. | `452a7c7c7c7048c2f887f61572b18fc2` | Recommended |
| `messaging_vnext.message.redelivered` | boolean | Indicates if message was already delivered to a consumer. | `True` | Recommended |
| `messaging_vnext.message.timestamp` | int | Message timestamp that matches either creation time or enqueued time. The earliest time available should be used. MUST be absolute Unix epoch time. | `1661407697` | Recommended |

**[1]:** The source name defines the name of the source of a message, as
specified by the consumer. There are different kinds of sources, varying
between message brokers, e. g. queues in RabbitMQ or topics in
Kafka.

This attributes is required for consumer spans modelling `deliver`, `receive`,
or `settle` operations. The name of the source a message is received from can
be different from the name of the destination a message was sent to.    

If messages in a batch have different `messaging_vnext.source.name`, it MUST
be populated on each corresponding link to message context. Otherwise it MUST be populated on 
consumer span.

**[2]:** When available and the same for all messages being sent.

**[3]:** If the message destination is either a `queue` or `topic`.

**[4]:** when supported by messaging system and only if the source is temporary. If missing, assumed to be false.

**[5]:** when supported by messaging system and only if the destination is anonymous. If missing, assumed to be false.

`messaging_vnext.source.kind` has the following list of well-known values. If one of them applies, then the respective value MUST be used, otherwise a custom value MAY be used.

| Value  | Description |
|---|---|
| `queue` | A message sent to a queue |
| `topic` | A message sent to a topic |
<!-- endsemconv -->

**Settle message**

If messaging system settles individual messages, instrumentation MUST add link from settlement span to the 
message being settled, but SHOULD populate message-specific attributes on settlement span.
Following attributes apply:

<!-- semconv messaging_vnext.consumer.settle.message -->
| Attribute  | Type | Description  | Examples  | Requirement Level |
|---|---|---|---|---|
| `messaging_vnext.settlement_type_todo` | string | Settlement operation | `complete`; `abandon`; `defer` | Recommended |
| `messaging_vnext.message.correlation_id` | string | A value used by application to correlate request and responses, represented as a string. | `1452a7c7c7c7048c2f887f61572b18fc` | Recommended |
| `messaging_vnext.message.id` | string | A value used by the messaging system as an identifier for the message, represented as a string. | `452a7c7c7c7048c2f887f61572b18fc2` | Recommended |
| `messaging_vnext.message.redelivered` | boolean | Indicates if message was already delivered to a consumer. | `True` | Recommended |
| `messaging_vnext.message.timestamp` | int | Message timestamp that matches either creation time or enqueued time. The earliest time available should be used. MUST be absolute Unix epoch time. | `1661407697` | Recommended |
<!-- endsemconv -->

**Settle offset**

If messaging system settles message offset or sequence number, following attributes apply:

<!-- semconv messaging_vnext.consumer.settle.offset -->
| Attribute  | Type | Description  | Examples  | Requirement Level |
|---|---|---|---|---|
| `messaging_vnext.offset_todo` | int | Offset |  | Required |
<!-- endsemconv -->

### Examples

#### Single message producer, single message push-based consumer

```
  PRODUCER                                   CONSUMER

  +------------+         (link)              +------------+
  | Publish m1 | . . . . . . . . . . . . . . | Deliver m1 |
  +------------+                             +------------+
```

#### Single message producer, single message push-based consumer with manual settlement

```
  PRODUCER                                   CONSUMER

  +------------+                             +------------------+
  | Publish m1 | . . . . . . . . . . . . . . | Deliver m1       |
  +------------+                             +-----+-----------++
                                                   | Settle m1 |
                                                   +-----------+
```

#### Single message producer, single message push-based consumer with auto-settlement

TODO: where would ambient context come from in push cases?

```
  PRODUCER                                   CONSUMER

                                           +--------------------------+
                                           | Ambient                  |
  +------------+                           +-+------------+-----------+
  | Publish m1 | . . . . . . . . . . . . . . | Deliver m1 |
  +------------+                             +------------+-----------+
                                                          | Settle m1 |
                                                          +-----------+
```
