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
<!-- endsemconv -->

##### Producer

**Create**
<!-- semconv messaging_vnext.create -->
<!-- endsemconv -->

(no attributes)

**Publish**

<!-- semconv messaging_vnext.publish_and_create -->
<!-- endsemconv -->

##### Consumer

**Receive or deliver**

<!-- semconv messaging_vnext.consumer -->
<!-- endsemconv -->

When receiving messages using pull API, `receive` span MUST have links to each message being received.
`Delivery` span (push scenario) SHOULD use remove message context as a parent. 

TODO: event -> link (tooling)

<!-- semconv messaging_vnext.link.consume -->
<!-- endsemconv -->

**Settle messages**

<!-- semconv messaging_vnext.consumer.settle.messages -->
<!-- endsemconv -->

TODO: event -> link (tooling)
When settling messages in batches, SHOULD have links to each message being settled:

<!-- semconv messaging_vnext.link.consume -->
<!-- endsemconv -->

**Settle offset**

<!-- semconv messaging_vnext.consumer.settle.offset -->
| Attribute  | Type | Description  | Examples  | Requirement Level |
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
