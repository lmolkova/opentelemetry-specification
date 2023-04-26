# OpenTelemetry attributes registry

<!-- TOC -->

- [OpenTelemetry attributes registry](#opentelemetry-attributes-registry)
    - [action](#action)
    - [aws](#aws)
        - [aws.dynamodb](#awsdynamodb)
        - [aws.ecs](#awsecs)
        - [aws.ecs.cluster](#awsecscluster)
        - [aws.ecs.container](#awsecscontainer)
        - [aws.ecs.task](#awsecstask)
        - [aws.eks.cluster](#awsekscluster)
        - [aws.lambda](#awslambda)
        - [aws.log.group](#awsloggroup)
        - [aws.log.stream](#awslogstream)
        - [aws.s3](#awss3)
    - [browser](#browser)
    - [client](#client)
        - [client.socket](#clientsocket)
    - [cloud](#cloud)
        - [cloud.account](#cloudaccount)
    - [cloudevents](#cloudevents)
    - [code](#code)
    - [container](#container)
        - [container.image](#containerimage)
    - [daemon](#daemon)
    - [db](#db)
        - [db.cassandra](#dbcassandra)
        - [db.cassandra.coordinator](#dbcassandracoordinator)
        - [db.cosmosdb](#dbcosmosdb)
        - [db.jdbc](#dbjdbc)
        - [db.mongodb](#dbmongodb)
        - [db.mssql](#dbmssql)
        - [db.redis](#dbredis)
        - [db.sql](#dbsql)
    - [deployment](#deployment)
    - [destination](#destination)
    - [device](#device)
        - [device.model](#devicemodel)
    - [enduser](#enduser)
    - [event](#event)
    - [exception](#exception)
    - [faas](#faas)
        - [faas.document](#faasdocument)
    - [feature_flag](#feature_flag)
    - [gc](#gc)
    - [graphql](#graphql)
        - [graphql.operation](#graphqloperation)
    - [heroku](#heroku)
        - [heroku.app](#herokuapp)
        - [heroku.release](#herokurelease)
    - [host](#host)
        - [host.image](#hostimage)
    - [http](#http)
    - [k8s](#k8s)
        - [k8s.cluster](#k8scluster)
        - [k8s.container](#k8scontainer)
        - [k8s.cronjob](#k8scronjob)
        - [k8s.daemonset](#k8sdaemonset)
        - [k8s.deployment](#k8sdeployment)
        - [k8s.job](#k8sjob)
        - [k8s.namespace](#k8snamespace)
        - [k8s.node](#k8snode)
        - [k8s.pod](#k8spod)
        - [k8s.replicaset](#k8sreplicaset)
        - [k8s.statefulset](#k8sstatefulset)
    - [log](#log)
        - [log.record](#logrecord)
    - [message](#message)
    - [messaging](#messaging)
        - [messaging.batch](#messagingbatch)
        - [messaging.destination](#messagingdestination)
        - [messaging.kafka.consumer](#messagingkafkaconsumer)
        - [messaging.kafka.destination](#messagingkafkadestination)
        - [messaging.kafka.message](#messagingkafkamessage)
        - [messaging.kafka.source](#messagingkafkasource)
        - [messaging.message](#messagingmessage)
        - [messaging.rabbitmq.destination](#messagingrabbitmqdestination)
        - [messaging.rocketmq](#messagingrocketmq)
        - [messaging.rocketmq.message](#messagingrocketmqmessage)
        - [messaging.source](#messagingsource)
    - [net](#net)
        - [net.host](#nethost)
        - [net.host.carrier](#nethostcarrier)
        - [net.host.connection](#nethostconnection)
        - [net.peer](#netpeer)
        - [net.protocol](#netprotocol)
        - [net.sock](#netsock)
        - [net.sock.host](#netsockhost)
        - [net.sock.peer](#netsockpeer)
    - [opentracing](#opentracing)
    - [os](#os)
    - [otel](#otel)
        - [otel.library](#otellibrary)
        - [otel.scope](#otelscope)
    - [peer](#peer)
    - [pool](#pool)
    - [process](#process)
        - [process.executable](#processexecutable)
        - [process.runtime](#processruntime)
    - [rpc](#rpc)
        - [rpc.connect_rpc](#rpcconnect_rpc)
        - [rpc.grpc](#rpcgrpc)
        - [rpc.jsonrpc](#rpcjsonrpc)
    - [server](#server)
        - [server.socket](#serversocket)
    - [service](#service)
        - [service.instance](#serviceinstance)
    - [source](#source)
    - [telemetry](#telemetry)
        - [telemetry.auto](#telemetryauto)
        - [telemetry.sdk](#telemetrysdk)
    - [thread](#thread)
    - [type](#type)
    - [user_agent](#user_agent)
    - [webengine](#webengine)

<!-- /TOC -->
## action

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="action">`action`</a> | string | Name of the garbage collector action. [1] | `end of minor GC`; `end of major GC` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** Garbage collector action is generally obtained via [GarbageCollectionNotificationInfo#getGcAction()](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.management/com/sun/management/GarbageCollectionNotificationInfo.html#getGcAction()).

## aws

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="aws.request_id">`aws.request_id`</a> | string | The AWS request ID as returned in the response headers `x-amz-request-id` or `x-amz-requestid`. | `79b9da39-b7ae-508a-a6bc-864b2829c622`; `C9ER4AJX75574TDJ` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### aws.dynamodb

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="aws.dynamodb.attribute_definitions">`aws.dynamodb.attribute_definitions`</a> | string[] | The JSON-serialized value of each item in the `AttributeDefinitions` request field. | `[{ "AttributeName": "string", "AttributeType": "string" }]` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.dynamodb.attributes_to_get">`aws.dynamodb.attributes_to_get`</a> | string[] | The value of the `AttributesToGet` request parameter. | `[lives, id]` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.dynamodb.consistent_read">`aws.dynamodb.consistent_read`</a> | boolean | The value of the `ConsistentRead` request parameter. |  | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.dynamodb.consumed_capacity">`aws.dynamodb.consumed_capacity`</a> | string[] | The JSON-serialized value of each item in the `ConsumedCapacity` response field. | `[{ "CapacityUnits": number, "GlobalSecondaryIndexes": { "string" : { "CapacityUnits": number, "ReadCapacityUnits": number, "WriteCapacityUnits": number } }, "LocalSecondaryIndexes": { "string" : { "CapacityUnits": number, "ReadCapacityUnits": number, "WriteCapacityUnits": number } }, "ReadCapacityUnits": number, "Table": { "CapacityUnits": number, "ReadCapacityUnits": number, "WriteCapacityUnits": number }, "TableName": "string", "WriteCapacityUnits": number }]` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.dynamodb.count">`aws.dynamodb.count`</a> | int | The value of the `Count` response parameter. | `10` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.dynamodb.exclusive_start_table">`aws.dynamodb.exclusive_start_table`</a> | string | The value of the `ExclusiveStartTableName` request parameter. | `Users`; `CatsTable` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.dynamodb.global_secondary_index_updates">`aws.dynamodb.global_secondary_index_updates`</a> | string[] | The JSON-serialized value of each item in the the `GlobalSecondaryIndexUpdates` request field. | `[{ "Create": { "IndexName": "string", "KeySchema": [ { "AttributeName": "string", "KeyType": "string" } ], "Projection": { "NonKeyAttributes": [ "string" ], "ProjectionType": "string" }, "ProvisionedThroughput": { "ReadCapacityUnits": number, "WriteCapacityUnits": number } }]` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.dynamodb.global_secondary_indexes">`aws.dynamodb.global_secondary_indexes`</a> | string[] | The JSON-serialized value of each item of the `GlobalSecondaryIndexes` request field | `[{ "IndexName": "string", "KeySchema": [ { "AttributeName": "string", "KeyType": "string" } ], "Projection": { "NonKeyAttributes": [ "string" ], "ProjectionType": "string" }, "ProvisionedThroughput": { "ReadCapacityUnits": number, "WriteCapacityUnits": number } }]` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.dynamodb.index_name">`aws.dynamodb.index_name`</a> | string | The value of the `IndexName` request parameter. | `name_to_group` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.dynamodb.item_collection_metrics">`aws.dynamodb.item_collection_metrics`</a> | string | The JSON-serialized value of the `ItemCollectionMetrics` response field. | `{ "string" : [ { "ItemCollectionKey": { "string" : { "B": blob, "BOOL": boolean, "BS": [ blob ], "L": [ "AttributeValue" ], "M": { "string" : "AttributeValue" }, "N": "string", "NS": [ "string" ], "NULL": boolean, "S": "string", "SS": [ "string" ] } }, "SizeEstimateRangeGB": [ number ] } ] }` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.dynamodb.limit">`aws.dynamodb.limit`</a> | int | The value of the `Limit` request parameter. | `10` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.dynamodb.local_secondary_indexes">`aws.dynamodb.local_secondary_indexes`</a> | string[] | The JSON-serialized value of each item of the `LocalSecondaryIndexes` request field. | `[{ "IndexArn": "string", "IndexName": "string", "IndexSizeBytes": number, "ItemCount": number, "KeySchema": [ { "AttributeName": "string", "KeyType": "string" } ], "Projection": { "NonKeyAttributes": [ "string" ], "ProjectionType": "string" } }]` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.dynamodb.projection">`aws.dynamodb.projection`</a> | string | The value of the `ProjectionExpression` request parameter. | `Title`; `Title, Price, Color`; `Title, Description, RelatedItems, ProductReviews` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.dynamodb.provisioned_read_capacity">`aws.dynamodb.provisioned_read_capacity`</a> | double | The value of the `ProvisionedThroughput.ReadCapacityUnits` request parameter. | `1.0`; `2.0` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.dynamodb.provisioned_write_capacity">`aws.dynamodb.provisioned_write_capacity`</a> | double | The value of the `ProvisionedThroughput.WriteCapacityUnits` request parameter. | `1.0`; `2.0` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.dynamodb.scan_forward">`aws.dynamodb.scan_forward`</a> | boolean | The value of the `ScanIndexForward` request parameter. |  | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.dynamodb.scanned_count">`aws.dynamodb.scanned_count`</a> | int | The value of the `ScannedCount` response parameter. | `50` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.dynamodb.segment">`aws.dynamodb.segment`</a> | int | The value of the `Segment` request parameter. | `10` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.dynamodb.select">`aws.dynamodb.select`</a> | string | The value of the `Select` request parameter. | `ALL_ATTRIBUTES`; `COUNT` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.dynamodb.table_count">`aws.dynamodb.table_count`</a> | int | The the number of items in the `TableNames` response parameter. | `20` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.dynamodb.table_names">`aws.dynamodb.table_names`</a> | string[] | The keys in the `RequestItems` object field. | `[Users, Cats]` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.dynamodb.total_segments">`aws.dynamodb.total_segments`</a> | int | The value of the `TotalSegments` request parameter. | `100` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### aws.ecs

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="aws.ecs.launchtype">`aws.ecs.launchtype`</a> | string | The [launch type](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/launch_types.html) for an ECS task. | `ec2` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
`aws.ecs.launchtype` MUST be one of the following:

| Value  | Description |
|---|---|
| `ec2` | ec2 |
| `fargate` | fargate |


### aws.ecs.cluster

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="aws.ecs.cluster.arn">`aws.ecs.cluster.arn`</a> | string | The ARN of an [ECS cluster](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/clusters.html). | `arn:aws:ecs:us-west-2:123456789123:cluster/my-cluster` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### aws.ecs.container

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="aws.ecs.container.arn">`aws.ecs.container.arn`</a> | string | The Amazon Resource Name (ARN) of an [ECS container instance](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_instances.html). | `arn:aws:ecs:us-west-1:123456789123:container/32624152-9086-4f0e-acae-1a75b14fe4d9` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### aws.ecs.task

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="aws.ecs.task.arn">`aws.ecs.task.arn`</a> | string | The ARN of an [ECS task definition](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definitions.html). | `arn:aws:ecs:us-west-1:123456789123:task/10838bed-421f-43ef-870a-f43feacbbb5b` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.ecs.task.family">`aws.ecs.task.family`</a> | string | The task definition family this task definition is a member of. | `opentelemetry-family` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.ecs.task.revision">`aws.ecs.task.revision`</a> | string | The revision for this task definition. | `8`; `26` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### aws.eks.cluster

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="aws.eks.cluster.arn">`aws.eks.cluster.arn`</a> | string | The ARN of an EKS cluster. | `arn:aws:ecs:us-west-2:123456789123:cluster/my-cluster` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### aws.lambda

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="aws.lambda.invoked_arn">`aws.lambda.invoked_arn`</a> | string | The full invoked ARN as provided on the `Context` passed to the function (`Lambda-Runtime-Invoked-Function-Arn` header on the `/runtime/invocation/next` applicable). [1] | `arn:aws:lambda:us-east-1:123456:function:myfunction:myalias` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** This may be different from `cloud.resource_id` if an alias is involved.

### aws.log.group

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="aws.log.group.arns">`aws.log.group.arns`</a> | string[] | The Amazon Resource Name(s) (ARN) of the AWS log group(s). [1] | `[arn:aws:logs:us-west-1:123456789012:log-group:/aws/my/group:*]` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.log.group.names">`aws.log.group.names`</a> | string[] | The name(s) of the AWS log group(s) an application is writing to. [2] | `[/aws/lambda/my-function, opentelemetry-service]` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** See the [log group ARN format documentation](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/iam-access-control-overview-cwl.html#CWL_ARN_Format).

**[2]:** Multiple log groups must be supported for cases like multi-container applications, where a single application has sidecar containers, and each write to their own log group.

### aws.log.stream

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="aws.log.stream.arns">`aws.log.stream.arns`</a> | string[] | The ARN(s) of the AWS log stream(s). [1] | `[arn:aws:logs:us-west-1:123456789012:log-group:/aws/my/group:log-stream:logs/main/10838bed-421f-43ef-870a-f43feacbbb5b]` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.log.stream.names">`aws.log.stream.names`</a> | string[] | The name(s) of the AWS log stream(s) an application is writing to. | `[logs/main/10838bed-421f-43ef-870a-f43feacbbb5b]` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** See the [log stream ARN format documentation](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/iam-access-control-overview-cwl.html#CWL_ARN_Format). One log group can contain several log streams, so these ARNs necessarily identify both a log group and a log stream.

### aws.s3

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="aws.s3.bucket">`aws.s3.bucket`</a> | string | The S3 bucket name the request refers to. Corresponds to the `--bucket` parameter of the [S3 API](https://docs.aws.amazon.com/cli/latest/reference/s3api/index.html) operations. [1] | `some-bucket-name` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.s3.copy_source">`aws.s3.copy_source`</a> | string | The source object (in the form `bucket`/`key`) for the copy operation. [2] | `someFile.yml` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.s3.delete">`aws.s3.delete`</a> | string | The delete request container that specifies the objects to be deleted. [3] | `Objects=[{Key=string,VersionId=string},{Key=string,VersionId=string}],Quiet=boolean` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.s3.key">`aws.s3.key`</a> | string | The S3 object key the request refers to. Corresponds to the `--key` parameter of the [S3 API](https://docs.aws.amazon.com/cli/latest/reference/s3api/index.html) operations. [4] | `someFile.yml` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.s3.part_number">`aws.s3.part_number`</a> | int | The part number of the part being uploaded in a multipart-upload operation. This is a positive integer between 1 and 10,000. [5] | `3456` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="aws.s3.upload_id">`aws.s3.upload_id`</a> | string | Upload ID that identifies the multipart upload. [6] | `dfRtDYWFbkRONycy.Yxwh66Yjlx.cph0gtNBtJ` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** The `bucket` attribute is applicable to all S3 operations that reference a bucket, i.e. that require the bucket name as a mandatory parameter.
This applies to almost all S3 operations except `list-buckets`.

**[2]:** The `copy_source` attribute applies to S3 copy operations and corresponds to the `--copy-source` parameter
of the [copy-object operation within the S3 API](https://docs.aws.amazon.com/cli/latest/reference/s3api/copy-object.html).
This applies in particular to the following operations:

- [copy-object](https://docs.aws.amazon.com/cli/latest/reference/s3api/copy-object.html)
- [upload-part-copy](https://docs.aws.amazon.com/cli/latest/reference/s3api/upload-part-copy.html)

**[3]:** The `delete` attribute is only applicable to the [delete-object](https://docs.aws.amazon.com/cli/latest/reference/s3api/delete-object.html) operation.
The `delete` attribute corresponds to the `--delete` parameter of the
[delete-objects operation within the S3 API](https://docs.aws.amazon.com/cli/latest/reference/s3api/delete-objects.html).

**[4]:** The `key` attribute is applicable to all object-related S3 operations, i.e. that require the object key as a mandatory parameter.
This applies in particular to the following operations:

- [copy-object](https://docs.aws.amazon.com/cli/latest/reference/s3api/copy-object.html)
- [delete-object](https://docs.aws.amazon.com/cli/latest/reference/s3api/delete-object.html)
- [get-object](https://docs.aws.amazon.com/cli/latest/reference/s3api/get-object.html)
- [head-object](https://docs.aws.amazon.com/cli/latest/reference/s3api/head-object.html)
- [put-object](https://docs.aws.amazon.com/cli/latest/reference/s3api/put-object.html)
- [restore-object](https://docs.aws.amazon.com/cli/latest/reference/s3api/restore-object.html)
- [select-object-content](https://docs.aws.amazon.com/cli/latest/reference/s3api/select-object-content.html)
- [abort-multipart-upload](https://docs.aws.amazon.com/cli/latest/reference/s3api/abort-multipart-upload.html)
- [complete-multipart-upload](https://docs.aws.amazon.com/cli/latest/reference/s3api/complete-multipart-upload.html)
- [create-multipart-upload](https://docs.aws.amazon.com/cli/latest/reference/s3api/create-multipart-upload.html)
- [list-parts](https://docs.aws.amazon.com/cli/latest/reference/s3api/list-parts.html)
- [upload-part](https://docs.aws.amazon.com/cli/latest/reference/s3api/upload-part.html)
- [upload-part-copy](https://docs.aws.amazon.com/cli/latest/reference/s3api/upload-part-copy.html)

**[5]:** The `part_number` attribute is only applicable to the [upload-part](https://docs.aws.amazon.com/cli/latest/reference/s3api/upload-part.html)
and [upload-part-copy](https://docs.aws.amazon.com/cli/latest/reference/s3api/upload-part-copy.html) operations.
The `part_number` attribute corresponds to the `--part-number` parameter of the
[upload-part operation within the S3 API](https://docs.aws.amazon.com/cli/latest/reference/s3api/upload-part.html).

**[6]:** The `upload_id` attribute applies to S3 multipart-upload operations and corresponds to the `--upload-id` parameter
of the [S3 API](https://docs.aws.amazon.com/cli/latest/reference/s3api/index.html) multipart operations.
This applies in particular to the following operations:

- [abort-multipart-upload](https://docs.aws.amazon.com/cli/latest/reference/s3api/abort-multipart-upload.html)
- [complete-multipart-upload](https://docs.aws.amazon.com/cli/latest/reference/s3api/complete-multipart-upload.html)
- [list-parts](https://docs.aws.amazon.com/cli/latest/reference/s3api/list-parts.html)
- [upload-part](https://docs.aws.amazon.com/cli/latest/reference/s3api/upload-part.html)
- [upload-part-copy](https://docs.aws.amazon.com/cli/latest/reference/s3api/upload-part-copy.html)

## browser

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="browser.brands">`browser.brands`</a> | string[] | Array of brand name and version separated by a space [1] | `[ Not A;Brand 99, Chromium 99, Chrome 99]` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="browser.language">`browser.language`</a> | string | Preferred language of the user using the browser [2] | `en`; `en-US`; `fr`; `fr-FR` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="browser.mobile">`browser.mobile`</a> | boolean | A boolean that is true if the browser is running on a mobile device [3] |  | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="browser.platform">`browser.platform`</a> | string | The platform on which the browser is running [4] | `Windows`; `macOS`; `Android` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** This value is intended to be taken from the [UA client hints API](https://wicg.github.io/ua-client-hints/#interface) (`navigator.userAgentData.brands`).

**[2]:** This value is intended to be taken from the Navigator API `navigator.language`.

**[3]:** This value is intended to be taken from the [UA client hints API](https://wicg.github.io/ua-client-hints/#interface) (`navigator.userAgentData.mobile`). If unavailable, this attribute SHOULD be left unset.

**[4]:** This value is intended to be taken from the [UA client hints API](https://wicg.github.io/ua-client-hints/#interface) (`navigator.userAgentData.platform`). If unavailable, the legacy `navigator.platform` API SHOULD NOT be used instead and this attribute SHOULD be left unset in order for the values to be consistent.
The list of possible values is defined in the [W3C User-Agent Client Hints specification](https://wicg.github.io/ua-client-hints/#sec-ch-ua-platform). Note that some (but not all) of these values can overlap with values in the [`os.type` and `os.name` attributes](./os.md). However, for consistency, the values in the `browser.platform` attribute should capture the exact value that the user agent provides.

## client

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="client.address">`client.address`</a> | string | Client address - unix domain socket name, IPv4 or IPv6 address. [1] | `/tmp/my.sock`; `10.1.2.80` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="client.port">`client.port`</a> | int | Client port number [2] | `65123` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** When observed from the server side, and when communicating through an intermediary, `client.address` SHOULD represent client address behind any intermediaries (e.g. proxies) if it's available.

**[2]:** When observed from the server side, and when communicating through an intermediary, `client.port` SHOULD represent client port behind any intermediaries (e.g. proxies) if it's available.

### client.socket

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="client.socket.address">`client.socket.address`</a> | string | Immediate client peer address - unix domain socket name, IPv4 or IPv6 address. | `/tmp/my.sock`; `127.0.0.1` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="client.socket.port">`client.socket.port`</a> | int | Immediate client peer port number | `35555` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

## cloud

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="cloud.availability_zone">`cloud.availability_zone`</a> | string | Cloud regions often have multiple, isolated locations known as zones to increase availability. Availability zone represents the zone where the resource is running. [1] | `us-east-1c` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="cloud.platform">`cloud.platform`</a> | string | The cloud platform in use. [2] | `alibaba_cloud_ecs` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="cloud.provider">`cloud.provider`</a> | string | Name of the cloud provider. | `alibaba_cloud` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="cloud.region">`cloud.region`</a> | string | The geographical region the resource is running. [3] | `us-central1`; `us-east-1` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="cloud.resource_id">`cloud.resource_id`</a> | string | Cloud provider-specific native identifier of the monitored cloud resource (e.g. an [ARN](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) on AWS, a [fully qualified resource ID](https://learn.microsoft.com/en-us/rest/api/resources/resources/get-by-id) on Azure, a [full resource name](https://cloud.google.com/apis/design/resource_names#full_resource_name) on GCP) [4] | `arn:aws:lambda:REGION:ACCOUNT_ID:function:my-function`; `//run.googleapis.com/projects/PROJECT_ID/locations/LOCATION_ID/services/SERVICE_ID`; `/subscriptions/<SUBSCIPTION_GUID>/resourceGroups/<RG>/providers/Microsoft.Web/sites/<FUNCAPP>/functions/<FUNC>` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** Availability zones are called "zones" on Alibaba Cloud and Google Cloud.

**[2]:** The prefix of the service SHOULD match the one specified in `cloud.provider`.

**[3]:** Refer to your provider's docs to see the available regions, for example [Alibaba Cloud regions](https://www.alibabacloud.com/help/doc-detail/40654.htm), [AWS regions](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/), [Azure regions](https://azure.microsoft.com/en-us/global-infrastructure/geographies/), [Google Cloud regions](https://cloud.google.com/about/locations), or [Tencent Cloud regions](https://www.tencentcloud.com/document/product/213/6091).

**[4]:** On some cloud providers, it may not be possible to determine the full ID at startup,
so it may be necessary to set `cloud.resource_id` as a span attribute instead.

The exact value to use for `cloud.resource_id` depends on the cloud provider.
The following well-known definitions MUST be used if you set this attribute and they apply:

* **AWS Lambda:** The function [ARN](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html).
  Take care not to use the "invoked ARN" directly but replace any
  [alias suffix](https://docs.aws.amazon.com/lambda/latest/dg/configuration-aliases.html)
  with the resolved function version, as the same runtime instance may be invokable with
  multiple different aliases.
* **GCP:** The [URI of the resource](https://cloud.google.com/iam/docs/full-resource-names)
* **Azure:** The [Fully Qualified Resource ID](https://docs.microsoft.com/en-us/rest/api/resources/resources/get-by-id) of the invoked function,
  *not* the function app, having the form
  `/subscriptions/<SUBSCIPTION_GUID>/resourceGroups/<RG>/providers/Microsoft.Web/sites/<FUNCAPP>/functions/<FUNC>`.
  This means that a span attribute MUST be used, as an Azure function app can host multiple functions that would usually share
  a TracerProvider.
`cloud.platform` has the following list of well-known values. If one of them applies, then the respective value MUST be used, otherwise a custom value MAY be used.

| Value  | Description |
|---|---|
| `alibaba_cloud_ecs` | Alibaba Cloud Elastic Compute Service |
| `alibaba_cloud_fc` | Alibaba Cloud Function Compute |
| `alibaba_cloud_openshift` | Red Hat OpenShift on Alibaba Cloud |
| `aws_ec2` | AWS Elastic Compute Cloud |
| `aws_ecs` | AWS Elastic Container Service |
| `aws_eks` | AWS Elastic Kubernetes Service |
| `aws_lambda` | AWS Lambda |
| `aws_elastic_beanstalk` | AWS Elastic Beanstalk |
| `aws_app_runner` | AWS App Runner |
| `aws_openshift` | Red Hat OpenShift on AWS (ROSA) |
| `azure_vm` | Azure Virtual Machines |
| `azure_container_instances` | Azure Container Instances |
| `azure_aks` | Azure Kubernetes Service |
| `azure_functions` | Azure Functions |
| `azure_app_service` | Azure App Service |
| `azure_openshift` | Azure Red Hat OpenShift |
| `gcp_compute_engine` | Google Cloud Compute Engine (GCE) |
| `gcp_cloud_run` | Google Cloud Run |
| `gcp_kubernetes_engine` | Google Cloud Kubernetes Engine (GKE) |
| `gcp_cloud_functions` | Google Cloud Functions (GCF) |
| `gcp_app_engine` | Google Cloud App Engine (GAE) |
| `gcp_openshift` | Red Hat OpenShift on Google Cloud |
| `ibm_cloud_openshift` | Red Hat OpenShift on IBM Cloud |
| `tencent_cloud_cvm` | Tencent Cloud Cloud Virtual Machine (CVM) |
| `tencent_cloud_eks` | Tencent Cloud Elastic Kubernetes Service (EKS) |
| `tencent_cloud_scf` | Tencent Cloud Serverless Cloud Function (SCF) |

`cloud.provider` has the following list of well-known values. If one of them applies, then the respective value MUST be used, otherwise a custom value MAY be used.

| Value  | Description |
|---|---|
| `alibaba_cloud` | Alibaba Cloud |
| `aws` | Amazon Web Services |
| `azure` | Microsoft Azure |
| `gcp` | Google Cloud Platform |
| `heroku` | Heroku Platform as a Service |
| `ibm_cloud` | IBM Cloud |
| `tencent_cloud` | Tencent Cloud |


### cloud.account

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="cloud.account.id">`cloud.account.id`</a> | string | The cloud account ID the resource is assigned to. | `111111111111`; `opentelemetry` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

## cloudevents

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="cloudevents.event_id">`cloudevents.event_id`</a> | string | The [event_id](https://github.com/cloudevents/spec/blob/v1.0.2/cloudevents/spec.md#id) uniquely identifies the event. | `123e4567-e89b-12d3-a456-426614174000`; `0001` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="cloudevents.event_source">`cloudevents.event_source`</a> | string | The [source](https://github.com/cloudevents/spec/blob/v1.0.2/cloudevents/spec.md#source-1) identifies the context in which an event happened. | `https://github.com/cloudevents`; `/cloudevents/spec/pull/123`; `my-service` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="cloudevents.event_spec_version">`cloudevents.event_spec_version`</a> | string | The [version of the CloudEvents specification](https://github.com/cloudevents/spec/blob/v1.0.2/cloudevents/spec.md#specversion) which the event uses. | `1.0` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="cloudevents.event_subject">`cloudevents.event_subject`</a> | string | The [subject](https://github.com/cloudevents/spec/blob/v1.0.2/cloudevents/spec.md#subject) of the event in the context of the event producer (identified by source). | `mynewfile.jpg` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="cloudevents.event_type">`cloudevents.event_type`</a> | string | The [event_type](https://github.com/cloudevents/spec/blob/v1.0.2/cloudevents/spec.md#type) contains a value describing the type of event related to the originating occurrence. | `com.github.pull_request.opened`; `com.example.object.deleted.v2` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

## code

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="code.column">`code.column`</a> | int | The column number in `code.filepath` best representing the operation. It SHOULD point within the code unit named in `code.function`. | `16` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="code.filepath">`code.filepath`</a> | string | The source code file name that identifies the code unit as uniquely as possible (preferably an absolute file path). | `/usr/local/MyApplication/content_root/app/index.php` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="code.function">`code.function`</a> | string | The method or function name, or equivalent (usually rightmost part of the code unit's name). | `serveRequest` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="code.lineno">`code.lineno`</a> | int | The line number in `code.filepath` best representing the operation. It SHOULD point within the code unit named in `code.function`. | `42` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="code.namespace">`code.namespace`</a> | string | The "namespace" within which `code.function` is defined. Usually the qualified class or module name, such that `code.namespace` + some separator + `code.function` form a unique identifier for the code unit. | `com.example.MyHttpService` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

## container

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="container.id">`container.id`</a> | string | Container ID. Usually a UUID, as for example used to [identify Docker containers](https://docs.docker.com/engine/reference/run/#container-identification). The UUID might be abbreviated. | `a3bf90e006b2` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="container.name">`container.name`</a> | string | Container name used by container runtime. | `opentelemetry-autoconf` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="container.runtime">`container.runtime`</a> | string | The container runtime managing this container. | `docker`; `containerd`; `rkt` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### container.image

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="container.image.name">`container.image.name`</a> | string | Name of the image the container was built on. | `gcr.io/opentelemetry/operator` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="container.image.tag">`container.image.tag`</a> | string | Container image tag. | `0.1` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

## daemon

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="daemon">`daemon`</a> | boolean | Whether the thread is daemon or not. |  | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

## db

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="db.connection_string">`db.connection_string`</a> | string | The connection string used to connect to the database. It is recommended to remove embedded credentials. | `Server=(localdb)\v11.0;Integrated Security=true;` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="db.name">`db.name`</a> | string | This attribute is used to report the name of the database being accessed. For commands that switch the database, this should be set to the target database (even if the command fails). [1] | `customers`; `main` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="db.operation">`db.operation`</a> | string | The name of the operation being executed, e.g. the [MongoDB command name](https://docs.mongodb.com/manual/reference/command/#database-operations) such as `findAndModify`, or the SQL keyword. [2] | `findAndModify`; `HMSET`; `SELECT` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="db.statement">`db.statement`</a> | string | The database statement being executed. | `SELECT * FROM wuser_table`; `SET mykey "WuValue"` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="db.system">`db.system`</a> | string | An identifier for the database management system (DBMS) product being used. See below for a list of well-known identifiers. | `other_sql` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="db.user">`db.user`</a> | string | Username for accessing the database. | `readonly_user`; `reporting_user` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** In some SQL databases, the database name to be used is called "schema name". In case there are multiple layers that could be considered for database name (e.g. Oracle instance name and schema name), the database name to be used is the more specific layer (e.g. Oracle schema name).

**[2]:** When setting this to an SQL keyword, it is not recommended to attempt any client-side parsing of `db.statement` just to get this property, but it should be set if the operation name is provided by the library being instrumented. If the SQL statement has an ambiguous operation, or performs more than one operation, this value may be omitted.
`db.system` has the following list of well-known values. If one of them applies, then the respective value MUST be used, otherwise a custom value MAY be used.

| Value  | Description |
|---|---|
| `other_sql` | Some other SQL database. Fallback only. See notes. |
| `mssql` | Microsoft SQL Server |
| `mssqlcompact` | Microsoft SQL Server Compact |
| `mysql` | MySQL |
| `oracle` | Oracle Database |
| `db2` | IBM Db2 |
| `postgresql` | PostgreSQL |
| `redshift` | Amazon Redshift |
| `hive` | Apache Hive |
| `cloudscape` | Cloudscape |
| `hsqldb` | HyperSQL DataBase |
| `progress` | Progress Database |
| `maxdb` | SAP MaxDB |
| `hanadb` | SAP HANA |
| `ingres` | Ingres |
| `firstsql` | FirstSQL |
| `edb` | EnterpriseDB |
| `cache` | InterSystems Caché |
| `adabas` | Adabas (Adaptable Database System) |
| `firebird` | Firebird |
| `derby` | Apache Derby |
| `filemaker` | FileMaker |
| `informix` | Informix |
| `instantdb` | InstantDB |
| `interbase` | InterBase |
| `mariadb` | MariaDB |
| `netezza` | Netezza |
| `pervasive` | Pervasive PSQL |
| `pointbase` | PointBase |
| `sqlite` | SQLite |
| `sybase` | Sybase |
| `teradata` | Teradata |
| `vertica` | Vertica |
| `h2` | H2 |
| `coldfusion` | ColdFusion IMQ |
| `cassandra` | Apache Cassandra |
| `hbase` | Apache HBase |
| `mongodb` | MongoDB |
| `redis` | Redis |
| `couchbase` | Couchbase |
| `couchdb` | CouchDB |
| `cosmosdb` | Microsoft Azure Cosmos DB |
| `dynamodb` | Amazon DynamoDB |
| `neo4j` | Neo4j |
| `geode` | Apache Geode |
| `elasticsearch` | Elasticsearch |
| `memcached` | Memcached |
| `cockroachdb` | CockroachDB |
| `opensearch` | OpenSearch |
| `clickhouse` | ClickHouse |
| `spanner` | Cloud Spanner |
| `trino` | Trino |


### db.cassandra

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="db.cassandra.consistency_level">`db.cassandra.consistency_level`</a> | string | The consistency level of the query. Based on consistency values from [CQL](https://docs.datastax.com/en/cassandra-oss/3.0/cassandra/dml/dmlConfigConsistency.html). | `all` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="db.cassandra.idempotence">`db.cassandra.idempotence`</a> | boolean | Whether or not the query is idempotent. |  | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="db.cassandra.page_size">`db.cassandra.page_size`</a> | int | The fetch size used for paging, i.e. how many rows will be returned at once. | `5000` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="db.cassandra.speculative_execution_count">`db.cassandra.speculative_execution_count`</a> | int | The number of times a query was speculatively executed. Not set or `0` if the query was not executed speculatively. | `0`; `2` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="db.cassandra.table">`db.cassandra.table`</a> | string | The name of the primary table that the operation is acting upon, including the keyspace name (if applicable). [1] | `mytable` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** This mirrors the db.sql.table attribute but references cassandra rather than sql. It is not recommended to attempt any client-side parsing of `db.statement` just to get this property, but it should be set if it is provided by the library being instrumented. If the operation is acting upon an anonymous table, or more than one table, this value MUST NOT be set.
`db.cassandra.consistency_level` MUST be one of the following:

| Value  | Description |
|---|---|
| `all` | all |
| `each_quorum` | each_quorum |
| `quorum` | quorum |
| `local_quorum` | local_quorum |
| `one` | one |
| `two` | two |
| `three` | three |
| `local_one` | local_one |
| `any` | any |
| `serial` | serial |
| `local_serial` | local_serial |


### db.cassandra.coordinator

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="db.cassandra.coordinator.dc">`db.cassandra.coordinator.dc`</a> | string | The data center of the coordinating node for a query. | `us-west-2` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="db.cassandra.coordinator.id">`db.cassandra.coordinator.id`</a> | string | The ID of the coordinating node for a query. | `be13faa2-8574-4d71-926d-27f16cf8a7af` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### db.cosmosdb

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="db.cosmosdb.client_id">`db.cosmosdb.client_id`</a> | string | Unique Cosmos client instance id. | `3ba4827d-4422-483f-b59f-85b74211c11d` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="db.cosmosdb.connection_mode">`db.cosmosdb.connection_mode`</a> | string | Cosmos client connection mode. | `gateway` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="db.cosmosdb.container">`db.cosmosdb.container`</a> | string | Cosmos DB container name. | `anystring` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="db.cosmosdb.operation_type">`db.cosmosdb.operation_type`</a> | string | CosmosDB Operation Type. | `Invalid` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="db.cosmosdb.request_charge">`db.cosmosdb.request_charge`</a> | double | RU consumed for that operation | `46.18`; `1.0` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="db.cosmosdb.request_content_length">`db.cosmosdb.request_content_length`</a> | int | Request payload size in bytes |  | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="db.cosmosdb.status_code">`db.cosmosdb.status_code`</a> | int | Cosmos DB status code. | `200`; `201` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="db.cosmosdb.sub_status_code">`db.cosmosdb.sub_status_code`</a> | int | Cosmos DB sub status code. | `1000`; `1002` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
`db.cosmosdb.connection_mode` MUST be one of the following:

| Value  | Description |
|---|---|
| `gateway` | Gateway (HTTP) connections mode |
| `direct` | Direct connection. |

`db.cosmosdb.operation_type` has the following list of well-known values. If one of them applies, then the respective value MUST be used, otherwise a custom value MAY be used.

| Value  | Description |
|---|---|
| `Invalid` | invalid |
| `Create` | create |
| `Patch` | patch |
| `Read` | read |
| `ReadFeed` | read_feed |
| `Delete` | delete |
| `Replace` | replace |
| `Execute` | execute |
| `Query` | query |
| `Head` | head |
| `HeadFeed` | head_feed |
| `Upsert` | upsert |
| `Batch` | batch |
| `QueryPlan` | query_plan |
| `ExecuteJavaScript` | execute_javascript |


### db.jdbc

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="db.jdbc.driver_classname">`db.jdbc.driver_classname`</a> | string | The fully-qualified class name of the [Java Database Connectivity (JDBC)](https://docs.oracle.com/javase/8/docs/technotes/guides/jdbc/) driver used to connect. | `org.postgresql.Driver`; `com.microsoft.sqlserver.jdbc.SQLServerDriver` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### db.mongodb

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="db.mongodb.collection">`db.mongodb.collection`</a> | string | The collection being accessed within the database stated in `db.name`. | `customers`; `products` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### db.mssql

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="db.mssql.instance_name">`db.mssql.instance_name`</a> | string | The Microsoft SQL Server [instance name](https://docs.microsoft.com/en-us/sql/connect/jdbc/building-the-connection-url?view=sql-server-ver15) connecting to. This name is used to determine the port of a named instance. [1] | `MSSQLSERVER` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** If setting a `db.mssql.instance_name`, `server.port` is no longer required (but still recommended if non-standard).

### db.redis

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="db.redis.database_index">`db.redis.database_index`</a> | int | The index of the database being accessed as used in the [`SELECT` command](https://redis.io/commands/select), provided as an integer. To be used instead of the generic `db.name` attribute. | `0`; `1`; `15` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### db.sql

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="db.sql.table">`db.sql.table`</a> | string | The name of the primary table that the operation is acting upon, including the database name (if applicable). [1] | `public.users`; `customers` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** It is not recommended to attempt any client-side parsing of `db.statement` just to get this property, but it should be set if it is provided by the library being instrumented. If the operation is acting upon an anonymous table, or more than one table, this value MUST NOT be set.

## deployment

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="deployment.environment">`deployment.environment`</a> | string | Name of the [deployment environment](https://en.wikipedia.org/wiki/Deployment_environment) (aka deployment tier). | `staging`; `production` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

## destination

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="destination.address">`destination.address`</a> | string | Peer address, for example IP address or UNIX socket name. | `10.5.3.2` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="destination.domain">`destination.domain`</a> | string | The domain name of the destination system. [1] | `foo.example.com` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="destination.port">`destination.port`</a> | int | Peer port number | `3389`; `2888` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** This value may be a host name, a fully qualified domain name, or another host naming format.

## device

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="device.id">`device.id`</a> | string | A unique identifier representing the device [1] | `2ab2916d-a51f-4ac8-80ee-45ac31a28092` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="device.manufacturer">`device.manufacturer`</a> | string | The name of the device manufacturer [2] | `Apple`; `Samsung` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** The device identifier MUST only be defined using the values outlined below. This value is not an advertising identifier and MUST NOT be used as such. On iOS (Swift or Objective-C), this value MUST be equal to the [vendor identifier](https://developer.apple.com/documentation/uikit/uidevice/1620059-identifierforvendor). On Android (Java or Kotlin), this value MUST be equal to the Firebase Installation ID or a globally unique UUID which is persisted across sessions in your application. More information can be found [here](https://developer.android.com/training/articles/user-data-ids) on best practices and exact implementation details. Caution should be taken when storing personal data or anything which can identify a user. GDPR and data protection laws may apply, ensure you do your own due diligence.

**[2]:** The Android OS provides this field via [Build](https://developer.android.com/reference/android/os/Build#MANUFACTURER). iOS apps SHOULD hardcode the value `Apple`.

### device.model

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="device.model.identifier">`device.model.identifier`</a> | string | The model identifier for the device [1] | `iPhone3,4`; `SM-G920F` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="device.model.name">`device.model.name`</a> | string | The marketing name for the device model [2] | `iPhone 6s Plus`; `Samsung Galaxy S6` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** It's recommended this value represents a machine readable version of the model identifier rather than the market or consumer-friendly name of the device.

**[2]:** It's recommended this value represents a human readable version of the device model rather than a machine readable alternative.

## enduser

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="enduser.id">`enduser.id`</a> | string | Username or client_id extracted from the access token or [Authorization](https://tools.ietf.org/html/rfc7235#section-4.2) header in the inbound request from outside the system. | `username` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="enduser.role">`enduser.role`</a> | string | Actual/assumed role the client is making the request under extracted from token or application security context. | `admin` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="enduser.scope">`enduser.scope`</a> | string | Scopes or granted authorities the client currently possesses extracted from token or application security context. The value would come from the scope associated with an [OAuth 2.0 Access Token](https://tools.ietf.org/html/rfc6749#section-3.3) or an attribute value in a [SAML 2.0 Assertion](http://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0.html). | `read:message, write:files` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

## event

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="event.domain">`event.domain`</a> | string | The domain identifies the business context for the events. [1] | `browser` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="event.name">`event.name`</a> | string | The name identifies the event. | `click`; `exception` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** Events across different domains may have same `event.name`, yet be
unrelated events.
`event.domain` has the following list of well-known values. If one of them applies, then the respective value MUST be used, otherwise a custom value MAY be used.

| Value  | Description |
|---|---|
| `browser` | Events from browser apps |
| `device` | Events from mobile apps |
| `k8s` | Events from Kubernetes |


## exception

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="exception.escaped">`exception.escaped`</a> | boolean | SHOULD be set to true if the exception event is recorded at a point where it is known that the exception is escaping the scope of the span. [1] |  | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="exception.message">`exception.message`</a> | string | The exception message. | `Division by zero`; `Can't convert 'int' object to str implicitly` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="exception.stacktrace">`exception.stacktrace`</a> | string | A stacktrace as a string in the natural representation for the language runtime. The representation is to be determined and documented by each language SIG. | `Exception in thread "main" java.lang.RuntimeException: Test exception\n at com.example.GenerateTrace.methodB(GenerateTrace.java:13)\n at com.example.GenerateTrace.methodA(GenerateTrace.java:9)\n at com.example.GenerateTrace.main(GenerateTrace.java:5)` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="exception.type">`exception.type`</a> | string | The type of the exception (its fully-qualified class name, if applicable). The dynamic type of the exception should be preferred over the static type in languages that support it. | `java.net.ConnectException`; `OSError` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** An exception is considered to have escaped (or left) the scope of a span,
if that span is ended while the exception is still logically "in flight".
This may be actually "in flight" in some languages (e.g. if the exception
is passed to a Context manager's `__exit__` method in Python) but will
usually be caught at the point of recording the exception in most languages.

It is usually not possible to determine at the point where an exception is thrown
whether it will escape the scope of a span.
However, it is trivial to know that an exception
will escape, if one checks for an active exception just before ending the span,
as done in the [example above](#recording-an-exception).

It follows that an exception may still escape the scope of the span
even if the `exception.escaped` attribute was not set or set to false,
since the event might have been recorded at a time where it was not
clear whether the exception will escape.

## faas

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="faas.coldstart">`faas.coldstart`</a> | boolean | A boolean that is true if the serverless function is executed for the first time (aka cold-start). |  | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="faas.cron">`faas.cron`</a> | string | A string containing the schedule period as [Cron Expression](https://docs.oracle.com/cd/E12058_01/doc/doc.1014/e12030/cron_expressions.htm). | `0/5 * * * ? *` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="faas.instance">`faas.instance`</a> | string | The execution environment ID as a string, that will be potentially reused for other invocations to the same function/function version. [1] | `2021/06/28/[$LATEST]2f399eb14537447da05ab2a2e39309de` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="faas.invocation_id">`faas.invocation_id`</a> | string | The invocation ID of the current function invocation. | `af9d5aa4-a685-4c5f-a22b-444f80b3cc28` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="faas.invoked_name">`faas.invoked_name`</a> | string | The name of the invoked function. [2] | `my-function` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="faas.invoked_provider">`faas.invoked_provider`</a> | string | The cloud provider of the invoked function. [3] | `alibaba_cloud` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="faas.invoked_region">`faas.invoked_region`</a> | string | The cloud region of the invoked function. [4] | `eu-central-1` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="faas.max_memory">`faas.max_memory`</a> | int | The amount of memory available to the serverless function converted to Bytes. [5] | `134217728` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="faas.name">`faas.name`</a> | string | The name of the single function that this runtime instance executes. [6] | `my-function`; `myazurefunctionapp/some-function-name` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="faas.time">`faas.time`</a> | string | A string containing the function invocation time in the [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) format expressed in [UTC](https://www.w3.org/TR/NOTE-datetime). | `2020-01-23T13:47:06Z` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="faas.trigger">`faas.trigger`</a> | string | Type of the trigger which caused this function invocation. [7] | `datasource` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="faas.version">`faas.version`</a> | string | The immutable version of the function being executed. [8] | `26`; `pinkfroid-00002` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** * **AWS Lambda:** Use the (full) log stream name.

**[2]:** SHOULD be equal to the `faas.name` resource attribute of the invoked function.

**[3]:** SHOULD be equal to the `cloud.provider` resource attribute of the invoked function.

**[4]:** SHOULD be equal to the `cloud.region` resource attribute of the invoked function.

**[5]:** It's recommended to set this attribute since e.g. too little memory can easily stop a Java AWS Lambda function from working correctly. On AWS Lambda, the environment variable `AWS_LAMBDA_FUNCTION_MEMORY_SIZE` provides this information (which must be multiplied by 1,048,576).

**[6]:** This is the name of the function as configured/deployed on the FaaS
platform and is usually different from the name of the callback
function (which may be stored in the
[`code.namespace`/`code.function`](../../trace/semantic_conventions/span-general.md#source-code-attributes)
span attributes).

For some cloud providers, the above definition is ambiguous. The following
definition of function name MUST be used for this attribute
(and consequently the span name) for the listed cloud providers/products:

* **Azure:**  The full name `<FUNCAPP>/<FUNC>`, i.e., function app name
  followed by a forward slash followed by the function name (this form
  can also be seen in the resource JSON for the function).
  This means that a span attribute MUST be used, as an Azure function
  app can host multiple functions that would usually share
  a TracerProvider (see also the `cloud.resource_id` attribute).

**[7]:** For the server/consumer span on the incoming side,
`faas.trigger` MUST be set.

Clients invoking FaaS instances usually cannot set `faas.trigger`,
since they would typically need to look in the payload to determine
the event type. If clients set it, it should be the same as the
trigger that corresponding incoming would have (i.e., this has
nothing to do with the underlying transport used to make the API
call to invoke the lambda, which is often HTTP).

**[8]:** Depending on the cloud provider and platform, use:

* **AWS Lambda:** The [function version](https://docs.aws.amazon.com/lambda/latest/dg/configuration-versions.html)
  (an integer represented as a decimal string).
* **Google Cloud Run:** The [revision](https://cloud.google.com/run/docs/managing/revisions)
  (i.e., the function name plus the revision suffix).
* **Google Cloud Functions:** The value of the
  [`K_REVISION` environment variable](https://cloud.google.com/functions/docs/env-var#runtime_environment_variables_set_automatically).
* **Azure Functions:** Not applicable. Do not set this attribute.
`faas.invoked_provider` has the following list of well-known values. If one of them applies, then the respective value MUST be used, otherwise a custom value MAY be used.

| Value  | Description |
|---|---|
| `alibaba_cloud` | Alibaba Cloud |
| `aws` | Amazon Web Services |
| `azure` | Microsoft Azure |
| `gcp` | Google Cloud Platform |
| `tencent_cloud` | Tencent Cloud |

`faas.trigger` MUST be one of the following:

| Value  | Description |
|---|---|
| `datasource` | A response to some data source operation such as a database or filesystem read/write. |
| `http` | To provide an answer to an inbound HTTP request |
| `pubsub` | A function is set to be executed when messages are sent to a messaging system. |
| `timer` | A function is scheduled to be executed regularly. |
| `other` | If none of the others apply |


### faas.document

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="faas.document.collection">`faas.document.collection`</a> | string | The name of the source on which the triggering operation was performed. For example, in Cloud Storage or S3 corresponds to the bucket name, and in Cosmos DB to the database name. | `myBucketName`; `myDbName` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="faas.document.name">`faas.document.name`</a> | string | The document name/table subjected to the operation. For example, in Cloud Storage or S3 is the name of the file, and in Cosmos DB the table name. | `myFile.txt`; `myTableName` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="faas.document.operation">`faas.document.operation`</a> | string | Describes the type of the operation that was performed on the data. | `insert` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="faas.document.time">`faas.document.time`</a> | string | A string containing the time when the data was accessed in the [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) format expressed in [UTC](https://www.w3.org/TR/NOTE-datetime). | `2020-01-23T13:47:06Z` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
`faas.document.operation` has the following list of well-known values. If one of them applies, then the respective value MUST be used, otherwise a custom value MAY be used.

| Value  | Description |
|---|---|
| `insert` | When a new object is created. |
| `edit` | When an object is modified. |
| `delete` | When an object is deleted. |


## feature_flag

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="feature_flag.key">`feature_flag.key`</a> | string | The unique identifier of the feature flag. | `logo-color` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="feature_flag.provider_name">`feature_flag.provider_name`</a> | string | The name of the service provider that performs the flag evaluation. | `Flag Manager` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="feature_flag.variant">`feature_flag.variant`</a> | string | SHOULD be a semantic identifier for a value. If one is unavailable, a stringified version of the value can be used. [1] | `red`; `true`; `on` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** A semantic identifier, commonly referred to as a variant, provides a means
for referring to a value without including the value itself. This can
provide additional context for understanding the meaning behind a value.
For example, the variant `red` maybe be used for the value `#c05543`.

A stringified version of the value can be used in situations where a
semantic identifier is unavailable. String representation of the value
should be determined by the implementer.

## gc

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="gc">`gc`</a> | string | Name of the garbage collector. [1] | `G1 Young Generation`; `G1 Old Generation` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** Garbage collector name is generally obtained via [GarbageCollectionNotificationInfo#getGcName()](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.management/com/sun/management/GarbageCollectionNotificationInfo.html#getGcName()).

## graphql

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="graphql.document">`graphql.document`</a> | string | The GraphQL document being executed. [1] | `query findBookById { bookById(id: ?) { name } }` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** The value may be sanitized to exclude sensitive information.

### graphql.operation

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="graphql.operation.name">`graphql.operation.name`</a> | string | The name of the operation being executed. | `findBookById` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="graphql.operation.type">`graphql.operation.type`</a> | string | The type of the operation being executed. | `query`; `mutation`; `subscription` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
`graphql.operation.type` MUST be one of the following:

| Value  | Description |
|---|---|
| `query` | GraphQL query |
| `mutation` | GraphQL mutation |
| `subscription` | GraphQL subscription |


## heroku

### heroku.app

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="heroku.app.id">`heroku.app.id`</a> | string | Unique identifier for the application | `2daa2797-e42b-4624-9322-ec3f968df4da` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### heroku.release

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="heroku.release.commit">`heroku.release.commit`</a> | string | Commit hash for the current release | `e6134959463efd8966b20e75b913cafe3f5ec` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="heroku.release.creation_timestamp">`heroku.release.creation_timestamp`</a> | string | Time and date the release was created | `2022-10-23T18:00:42Z` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

## host

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="host.arch">`host.arch`</a> | string | The CPU architecture the host system is running on. | `amd64` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="host.id">`host.id`</a> | string | Unique host ID. For Cloud, this must be the instance_id assigned by the cloud provider. For non-containerized systems, this should be the `machine-id`. See the table below for the sources to use to determine the `machine-id` based on operating system. | `fdbf79e8af94cb7f9e8df36789187052` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="host.name">`host.name`</a> | string | Name of the host. On Unix systems, it may contain what the hostname command returns, or the fully qualified hostname, or another name specified by the user. | `opentelemetry-test` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="host.type">`host.type`</a> | string | Type of host. For Cloud, this must be the machine type. | `n1-standard-1` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
`host.arch` has the following list of well-known values. If one of them applies, then the respective value MUST be used, otherwise a custom value MAY be used.

| Value  | Description |
|---|---|
| `amd64` | AMD64 |
| `arm32` | ARM32 |
| `arm64` | ARM64 |
| `ia64` | Itanium |
| `ppc32` | 32-bit PowerPC |
| `ppc64` | 64-bit PowerPC |
| `s390x` | IBM z/Architecture |
| `x86` | 32-bit x86 |


### host.image

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="host.image.id">`host.image.id`</a> | string | VM image ID or host OS image ID. For Cloud, this value is from the provider. | `ami-07b06b442921831e5` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="host.image.name">`host.image.name`</a> | string | Name of the VM image or OS install the host was instantiated from. | `infra-ami-eks-worker-node-7d4ec78312`; `CentOS-8-x86_64-1905` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="host.image.version">`host.image.version`</a> | string | The version string of the VM image or host OS as defined in [Version Attributes](README.md#version-attributes). | `0.1` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

## http

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="http.method">`http.method`</a> | string | HTTP request method. | `GET`; `POST`; `HEAD` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="http.request_content_length">`http.request_content_length`</a> | int | The size of the request payload body in bytes. This is the number of bytes transferred excluding headers and is often, but not always, present as the [Content-Length](https://www.rfc-editor.org/rfc/rfc9110.html#field.content-length) header. For requests using transport encoding, this should be the compressed size. | `3495` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="http.resend_count">`http.resend_count`</a> | int | The ordinal number of request resending attempt (for any reason, including redirects). [1] | `3` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="http.response_content_length">`http.response_content_length`</a> | int | The size of the response payload body in bytes. This is the number of bytes transferred excluding headers and is often, but not always, present as the [Content-Length](https://www.rfc-editor.org/rfc/rfc9110.html#field.content-length) header. For requests using transport encoding, this should be the compressed size. | `3495` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="http.route">`http.route`</a> | string | The matched route (path template in the format used by the respective server framework). See note below [2] | `/users/:userID?`; `{controller}/{action}/{id?}` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="http.scheme">`http.scheme`</a> | string | The URI scheme identifying the used protocol. | `http`; `https` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="http.status_code">`http.status_code`</a> | int | [HTTP response status code](https://tools.ietf.org/html/rfc7231#section-6). | `200` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="http.target">`http.target`</a> | string | The full request target as passed in a HTTP request line or equivalent. | `/users/12314/?q=ddds` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="http.url">`http.url`</a> | string | Full HTTP request URL in the form `scheme://host[:port]/path?query[#fragment]`. Usually the fragment is not transmitted over HTTP, but if it is known, it should be included nevertheless. [3] | `https://www.foo.bar/search?q=OpenTelemetry#SemConv` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** The resend count SHOULD be updated each time an HTTP request gets resent by the client, regardless of what was the cause of the resending (e.g. redirection, authorization failure, 503 Server Unavailable, network issues, or any other).

**[2]:** MUST NOT be populated when this is not supported by the HTTP server framework as the route attribute should have low-cardinality and the URI path can NOT substitute it.
SHOULD include the [application root](/specification/trace/semantic_conventions/http.md#http-server-definitions) if there is one.

**[3]:** `http.url` MUST NOT contain credentials passed via URL in form of `https://username:password@www.example.com/`. In such case the attribute's value should be `https://www.example.com/`.

## k8s

### k8s.cluster

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="k8s.cluster.name">`k8s.cluster.name`</a> | string | The name of the cluster. | `opentelemetry-cluster` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="k8s.cluster.uid">`k8s.cluster.uid`</a> | string | A pseudo-ID for the cluster, set to the UID of the `kube-system` namespace. [1] | `218fc5a9-a5f1-4b54-aa05-46717d0ab26d` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** K8s does not have support for obtaining a cluster ID. If this is ever
added, we will recommend collecting the `k8s.cluster.uid` through the
official APIs. In the meantime, we are able to use the `uid` of the
`kube-system` namespace as a proxy for cluster ID. Read on for the
rationale.

Every object created in a K8s cluster is assigned a distinct UID. The
`kube-system` namespace is used by Kubernetes itself and will exist
for the lifetime of the cluster. Using the `uid` of the `kube-system`
namespace is a reasonable proxy for the K8s ClusterID as it will only
change if the cluster is rebuilt. Furthermore, Kubernetes UIDs are
UUIDs as standardized by
[ISO/IEC 9834-8 and ITU-T X.667](https://www.itu.int/ITU-T/studygroups/com17/oid.html).
Which states:

> If generated according to one of the mechanisms defined in Rec.
  ITU-T X.667 | ISO/IEC 9834-8, a UUID is either guaranteed to be
  different from all other UUIDs generated before 3603 A.D., or is
  extremely likely to be different (depending on the mechanism chosen).

Therefore, UIDs between clusters should be extremely unlikely to
conflict.

### k8s.container

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="k8s.container.name">`k8s.container.name`</a> | string | The name of the Container from Pod specification, must be unique within a Pod. Container runtime usually uses different globally unique name (`container.name`). | `redis` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="k8s.container.restart_count">`k8s.container.restart_count`</a> | int | Number of times the container was restarted. This attribute can be used to identify a particular container (running or stopped) within a container spec. | `0`; `2` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### k8s.cronjob

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="k8s.cronjob.name">`k8s.cronjob.name`</a> | string | The name of the CronJob. | `opentelemetry` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="k8s.cronjob.uid">`k8s.cronjob.uid`</a> | string | The UID of the CronJob. | `275ecb36-5aa8-4c2a-9c47-d8bb681b9aff` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### k8s.daemonset

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="k8s.daemonset.name">`k8s.daemonset.name`</a> | string | The name of the DaemonSet. | `opentelemetry` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="k8s.daemonset.uid">`k8s.daemonset.uid`</a> | string | The UID of the DaemonSet. | `275ecb36-5aa8-4c2a-9c47-d8bb681b9aff` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### k8s.deployment

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="k8s.deployment.name">`k8s.deployment.name`</a> | string | The name of the Deployment. | `opentelemetry` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="k8s.deployment.uid">`k8s.deployment.uid`</a> | string | The UID of the Deployment. | `275ecb36-5aa8-4c2a-9c47-d8bb681b9aff` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### k8s.job

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="k8s.job.name">`k8s.job.name`</a> | string | The name of the Job. | `opentelemetry` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="k8s.job.uid">`k8s.job.uid`</a> | string | The UID of the Job. | `275ecb36-5aa8-4c2a-9c47-d8bb681b9aff` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### k8s.namespace

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="k8s.namespace.name">`k8s.namespace.name`</a> | string | The name of the namespace that the pod is running in. | `default` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### k8s.node

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="k8s.node.name">`k8s.node.name`</a> | string | The name of the Node. | `node-1` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="k8s.node.uid">`k8s.node.uid`</a> | string | The UID of the Node. | `1eb3a0c6-0477-4080-a9cb-0cb7db65c6a2` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### k8s.pod

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="k8s.pod.name">`k8s.pod.name`</a> | string | The name of the Pod. | `opentelemetry-pod-autoconf` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="k8s.pod.uid">`k8s.pod.uid`</a> | string | The UID of the Pod. | `275ecb36-5aa8-4c2a-9c47-d8bb681b9aff` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### k8s.replicaset

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="k8s.replicaset.name">`k8s.replicaset.name`</a> | string | The name of the ReplicaSet. | `opentelemetry` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="k8s.replicaset.uid">`k8s.replicaset.uid`</a> | string | The UID of the ReplicaSet. | `275ecb36-5aa8-4c2a-9c47-d8bb681b9aff` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### k8s.statefulset

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="k8s.statefulset.name">`k8s.statefulset.name`</a> | string | The name of the StatefulSet. | `opentelemetry` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="k8s.statefulset.uid">`k8s.statefulset.uid`</a> | string | The UID of the StatefulSet. | `275ecb36-5aa8-4c2a-9c47-d8bb681b9aff` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

## log

### log.record

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="log.record.uid">`log.record.uid`</a> | string | A unique identifier for the Log Record. [1] | `01ARZ3NDEKTSV4RRFFQ69G5FAV` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** If an id is provided, other log records with the same id will be considered duplicates and can be removed safely. This means, that two distinguishable log records MUST have different values.
The id MAY be an [Universally Unique Lexicographically Sortable Identifier (ULID)](https://github.com/ulid/spec), but other identifiers (e.g. UUID) may be used as needed.

## message

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="message.compressed_size">`message.compressed_size`</a> | int | Compressed size of the message in bytes. |  | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="message.id">`message.id`</a> | int | MUST be calculated as two different counters starting from `1` one for sent messages and one for received message. [1] |  | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="message.type">`message.type`</a> | string | Whether this is a received or sent message. | `SENT` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="message.uncompressed_size">`message.uncompressed_size`</a> | int | Uncompressed size of the message in bytes. |  | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** This way we guarantee that the values will be consistent between different implementations.
`message.type` MUST be one of the following:

| Value  | Description |
|---|---|
| `SENT` | sent |
| `RECEIVED` | received |


## messaging

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="messaging.client_id">`messaging.client_id`</a> | string | A unique identifier for the client that consumes or produces a message. | `client-5`; `myhost@8742@s8083jm` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="messaging.operation">`messaging.operation`</a> | string | A string identifying the kind of messaging operation as defined in the [Operation names](#operation-names) section above. [1] | `publish` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="messaging.system">`messaging.system`</a> | string | A string identifying the messaging system. | `kafka`; `rabbitmq`; `rocketmq`; `activemq`; `AmazonSQS` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** If a custom value is used, it MUST be of low cardinality.
`messaging.operation` has the following list of well-known values. If one of them applies, then the respective value MUST be used, otherwise a custom value MAY be used.

| Value  | Description |
|---|---|
| `publish` | publish |
| `receive` | receive |
| `process` | process |


### messaging.batch

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="messaging.batch.message_count">`messaging.batch.message_count`</a> | int | The number of messages sent, received, or processed in the scope of the batching operation. [1] | `0`; `1`; `2` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** Instrumentations SHOULD NOT set `messaging.batch.message_count` on spans that operate with a single message. When a messaging client library supports both batch and single-message API for the same operation, instrumentations SHOULD use `messaging.batch.message_count` for batching APIs and SHOULD NOT use it for single-message APIs.

### messaging.destination

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="messaging.destination.anonymous">`messaging.destination.anonymous`</a> | boolean | A boolean that is true if the message destination is anonymous (could be unnamed or have auto-generated name). |  | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="messaging.destination.name">`messaging.destination.name`</a> | string | The message destination name [1] | `MyQueue`; `MyTopic` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="messaging.destination.template">`messaging.destination.template`</a> | string | Low cardinality representation of the messaging destination name [2] | `/customers/{customerId}` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="messaging.destination.temporary">`messaging.destination.temporary`</a> | boolean | A boolean that is true if the message destination is temporary and might not exist anymore after messages are processed. |  | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** Destination name SHOULD uniquely identify a specific queue, topic or other entity within the broker. If
the broker does not have such notion, the destination name SHOULD uniquely identify the broker.

**[2]:** Destination names could be constructed from templates. An example would be a destination name involving a user name or product id. Although the destination name in this case is of high cardinality, the underlying template is of low cardinality and can be effectively used for grouping and aggregation.

### messaging.kafka.consumer

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="messaging.kafka.consumer.group">`messaging.kafka.consumer.group`</a> | string | Name of the Kafka Consumer Group that is handling the message. Only applies to consumers, not producers. | `my-group` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### messaging.kafka.destination

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="messaging.kafka.destination.partition">`messaging.kafka.destination.partition`</a> | int | Partition the message is sent to. | `2` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### messaging.kafka.message

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="messaging.kafka.message.key">`messaging.kafka.message.key`</a> | string | Message keys in Kafka are used for grouping alike messages to ensure they're processed on the same partition. They differ from `messaging.message.id` in that they're not unique. If the key is `null`, the attribute MUST NOT be set. [1] | `myKey` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="messaging.kafka.message.offset">`messaging.kafka.message.offset`</a> | int | The offset of a record in the corresponding Kafka partition. | `42` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="messaging.kafka.message.tombstone">`messaging.kafka.message.tombstone`</a> | boolean | A boolean that is true if the message is a tombstone. |  | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** If the key type is not string, it's string representation has to be supplied for the attribute. If the key has no unambiguous, canonical string form, don't include its value.

### messaging.kafka.source

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="messaging.kafka.source.partition">`messaging.kafka.source.partition`</a> | int | Partition the message is received from. | `2` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### messaging.message

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="messaging.message.conversation_id">`messaging.message.conversation_id`</a> | string | The [conversation ID](#conversations) identifying the conversation to which the message belongs, represented as a string. Sometimes called "Correlation ID". | `MyConversationId` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="messaging.message.id">`messaging.message.id`</a> | string | A value used by the messaging system as an identifier for the message, represented as a string. | `452a7c7c7c7048c2f887f61572b18fc2` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="messaging.message.payload_compressed_size_bytes">`messaging.message.payload_compressed_size_bytes`</a> | int | The compressed size of the message payload in bytes. | `2048` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="messaging.message.payload_size_bytes">`messaging.message.payload_size_bytes`</a> | int | The (uncompressed) size of the message payload in bytes. Also use this attribute if it is unknown whether the compressed or uncompressed payload size is reported. | `2738` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### messaging.rabbitmq.destination

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="messaging.rabbitmq.destination.routing_key">`messaging.rabbitmq.destination.routing_key`</a> | string | RabbitMQ message routing key. | `myKey` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### messaging.rocketmq

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="messaging.rocketmq.client_group">`messaging.rocketmq.client_group`</a> | string | Name of the RocketMQ producer/consumer group that is handling the message. The client type is identified by the SpanKind. | `myConsumerGroup` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="messaging.rocketmq.consumption_model">`messaging.rocketmq.consumption_model`</a> | string | Model of message consumption. This only applies to consumer spans. | `clustering` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="messaging.rocketmq.namespace">`messaging.rocketmq.namespace`</a> | string | Namespace of RocketMQ resources, resources in different namespaces are individual. | `myNamespace` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
`messaging.rocketmq.consumption_model` MUST be one of the following:

| Value  | Description |
|---|---|
| `clustering` | Clustering consumption model |
| `broadcasting` | Broadcasting consumption model |


### messaging.rocketmq.message

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="messaging.rocketmq.message.delay_time_level">`messaging.rocketmq.message.delay_time_level`</a> | int | The delay time level for delay message, which determines the message delay time. | `3` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="messaging.rocketmq.message.delivery_timestamp">`messaging.rocketmq.message.delivery_timestamp`</a> | int | The timestamp in milliseconds that the delay message is expected to be delivered to consumer. | `1665987217045` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="messaging.rocketmq.message.group">`messaging.rocketmq.message.group`</a> | string | It is essential for FIFO message. Messages that belong to the same message group are always processed one by one within the same consumer group. | `myMessageGroup` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="messaging.rocketmq.message.keys">`messaging.rocketmq.message.keys`</a> | string[] | Key(s) of message, another way to mark message besides message id. | `[keyA, keyB]` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="messaging.rocketmq.message.tag">`messaging.rocketmq.message.tag`</a> | string | The secondary classifier of message besides topic. | `tagA` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="messaging.rocketmq.message.type">`messaging.rocketmq.message.type`</a> | string | Type of message. | `normal` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
`messaging.rocketmq.message.type` MUST be one of the following:

| Value  | Description |
|---|---|
| `normal` | Normal message |
| `fifo` | FIFO message |
| `delay` | Delay message |
| `transaction` | Transaction message |


### messaging.source

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="messaging.source.anonymous">`messaging.source.anonymous`</a> | boolean | A boolean that is true if the message source is anonymous (could be unnamed or have auto-generated name). |  | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="messaging.source.name">`messaging.source.name`</a> | string | The message source name [1] | `MyQueue`; `MyTopic` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="messaging.source.template">`messaging.source.template`</a> | string | Low cardinality representation of the messaging source name [2] | `/customers/{customerId}` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="messaging.source.temporary">`messaging.source.temporary`</a> | boolean | A boolean that is true if the message source is temporary and might not exist anymore after messages are processed. |  | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** Source name SHOULD uniquely identify a specific queue, topic, or other entity within the broker. If
the broker does not have such notion, the source name SHOULD uniquely identify the broker.

**[2]:** Source names could be constructed from templates. An example would be a source name involving a user name or product id. Although the source name in this case is of high cardinality, the underlying template is of low cardinality and can be effectively used for grouping and aggregation.

## net

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="net.transport">`net.transport`</a> | string | Transport protocol used. See note below. | `ip_tcp` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
`net.transport` has the following list of well-known values. If one of them applies, then the respective value MUST be used, otherwise a custom value MAY be used.

| Value  | Description |
|---|---|
| `ip_tcp` | ip_tcp |
| `ip_udp` | ip_udp |
| `pipe` | Named or anonymous pipe. See note below. |
| `inproc` | In-process communication. [1] |
| `other` | Something else (non IP-based). |

**[1]:** Signals that there is only in-process communication not using a "real" network protocol in cases where network attributes would normally be expected. Usually all other network attributes can be left out in that case.


### net.host

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="net.host.name">`net.host.name`</a> | string | Deprecated, use `server.address`. | `example.com` | ![Deprecated](https://img.shields.io/badge/-deprecated-red)<br> |
| <a name="net.host.port">`net.host.port`</a> | int | Deprecated, use `server.port`. | `8080` | ![Deprecated](https://img.shields.io/badge/-deprecated-red)<br> |

### net.host.carrier

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="net.host.carrier.icc">`net.host.carrier.icc`</a> | string | The ISO 3166-1 alpha-2 2-character country code associated with the mobile carrier network. | `DE` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="net.host.carrier.mcc">`net.host.carrier.mcc`</a> | string | The mobile carrier country code. | `310` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="net.host.carrier.mnc">`net.host.carrier.mnc`</a> | string | The mobile carrier network code. | `001` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="net.host.carrier.name">`net.host.carrier.name`</a> | string | The name of the mobile carrier. | `sprint` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### net.host.connection

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="net.host.connection.subtype">`net.host.connection.subtype`</a> | string | This describes more details regarding the connection.type. It may be the type of cell technology connection, but it could be used for describing details about a wifi connection. | `LTE` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="net.host.connection.type">`net.host.connection.type`</a> | string | The internet connection type currently being used by the host. | `wifi` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
`net.host.connection.subtype` has the following list of well-known values. If one of them applies, then the respective value MUST be used, otherwise a custom value MAY be used.

| Value  | Description |
|---|---|
| `gprs` | GPRS |
| `edge` | EDGE |
| `umts` | UMTS |
| `cdma` | CDMA |
| `evdo_0` | EVDO Rel. 0 |
| `evdo_a` | EVDO Rev. A |
| `cdma2000_1xrtt` | CDMA2000 1XRTT |
| `hsdpa` | HSDPA |
| `hsupa` | HSUPA |
| `hspa` | HSPA |
| `iden` | IDEN |
| `evdo_b` | EVDO Rev. B |
| `lte` | LTE |
| `ehrpd` | EHRPD |
| `hspap` | HSPAP |
| `gsm` | GSM |
| `td_scdma` | TD-SCDMA |
| `iwlan` | IWLAN |
| `nr` | 5G NR (New Radio) |
| `nrnsa` | 5G NRNSA (New Radio Non-Standalone) |
| `lte_ca` | LTE CA |

`net.host.connection.type` has the following list of well-known values. If one of them applies, then the respective value MUST be used, otherwise a custom value MAY be used.

| Value  | Description |
|---|---|
| `wifi` | wifi |
| `wired` | wired |
| `cell` | cell |
| `unavailable` | unavailable |
| `unknown` | unknown |


### net.peer

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="net.peer.name">`net.peer.name`</a> | string | Deprecated, use `server.address`. | `example.com` | ![Deprecated](https://img.shields.io/badge/-deprecated-red)<br> |
| <a name="net.peer.port">`net.peer.port`</a> | int | Deprecated, use `server.port`. | `8080` | ![Deprecated](https://img.shields.io/badge/-deprecated-red)<br> |

### net.protocol

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="net.protocol.name">`net.protocol.name`</a> | string | Application layer protocol used. The value SHOULD be normalized to lowercase. | `amqp`; `http`; `mqtt` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="net.protocol.version">`net.protocol.version`</a> | string | Version of the application layer protocol used. See note below. [1] | `3.1.1` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** `net.protocol.version` refers to the version of the protocol used and might be different from the protocol client's version. If the HTTP client used has a version of `0.27.2`, but sends HTTP version `1.1`, this attribute should be set to `1.1`.

### net.sock

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="net.sock.family">`net.sock.family`</a> | string | Protocol [address family](https://man7.org/linux/man-pages/man7/address_families.7.html) which is used for communication. | `inet6`; `bluetooth` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
`net.sock.family` has the following list of well-known values. If one of them applies, then the respective value MUST be used, otherwise a custom value MAY be used.

| Value  | Description |
|---|---|
| `inet` | IPv4 address |
| `inet6` | IPv6 address |
| `unix` | Unix domain socket path |


### net.sock.host

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="net.sock.host.addr">`net.sock.host.addr`</a> | string | Deprecated, use `server.socket.address`. | `/var/my.sock` | ![Deprecated](https://img.shields.io/badge/-deprecated-red)<br> |
| <a name="net.sock.host.port">`net.sock.host.port`</a> | int | Deprecated, use `server.socket.port`. | `8080` | ![Deprecated](https://img.shields.io/badge/-deprecated-red)<br> |

### net.sock.peer

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="net.sock.peer.addr">`net.sock.peer.addr`</a> | string | Deprecated. On client spans use `server.socket.address`, on server spans use `client.socket.address` | `192.168.0.1` | ![Deprecated](https://img.shields.io/badge/-deprecated-red)<br> |
| <a name="net.sock.peer.name">`net.sock.peer.name`</a> | string | Deprecated, use `server.socket.domain` on client spans. | `/var/my.sock` | ![Deprecated](https://img.shields.io/badge/-deprecated-red)<br> |
| <a name="net.sock.peer.port">`net.sock.peer.port`</a> | int | Deprecated, use `server.socket.port` on client spans and `client.socket.port` on server spans. | `65531` | ![Deprecated](https://img.shields.io/badge/-deprecated-red)<br> |

## opentracing

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="opentracing.ref_type">`opentracing.ref_type`</a> | string | Parent-child Reference type [1] | `child_of` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** The causal relationship between a child Span and a parent Span.
`opentracing.ref_type` MUST be one of the following:

| Value  | Description |
|---|---|
| `child_of` | The parent Span depends on the child Span in some capacity |
| `follows_from` | The parent Span does not depend in any way on the result of the child Span |


## os

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="os.description">`os.description`</a> | string | Human readable (not intended to be parsed) OS version information, like e.g. reported by `ver` or `lsb_release -a` commands. | `Microsoft Windows [Version 10.0.18363.778]`; `Ubuntu 18.04.1 LTS` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="os.name">`os.name`</a> | string | Human readable operating system name. | `iOS`; `Android`; `Ubuntu` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="os.type">`os.type`</a> | string | The operating system type. | `windows` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="os.version">`os.version`</a> | string | The version string of the operating system as defined in [Version Attributes](../../resource/semantic_conventions/README.md#version-attributes). | `14.2.1`; `18.04.1` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
`os.type` has the following list of well-known values. If one of them applies, then the respective value MUST be used, otherwise a custom value MAY be used.

| Value  | Description |
|---|---|
| `windows` | Microsoft Windows |
| `linux` | Linux |
| `darwin` | Apple Darwin |
| `freebsd` | FreeBSD |
| `netbsd` | NetBSD |
| `openbsd` | OpenBSD |
| `dragonflybsd` | DragonFly BSD |
| `hpux` | HP-UX (Hewlett Packard Unix) |
| `aix` | AIX (Advanced Interactive eXecutive) |
| `solaris` | SunOS, Oracle Solaris |
| `z_os` | IBM z/OS |


## otel

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="otel.status_code">`otel.status_code`</a> | string | Name of the code, either "OK" or "ERROR". MUST NOT be set if the status code is UNSET. | `OK` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="otel.status_description">`otel.status_description`</a> | string | Description of the Status if it has a value, otherwise not set. | `resource not found` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
`otel.status_code` MUST be one of the following:

| Value  | Description |
|---|---|
| `OK` | The operation has been validated by an Application developer or Operator to have completed successfully. |
| `ERROR` | The operation contains an error. |


### otel.library

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="otel.library.name">`otel.library.name`</a> | string | Deprecated, use the `otel.scope.name` attribute. | `io.opentelemetry.contrib.mongodb` | ![Deprecated](https://img.shields.io/badge/-deprecated-red)<br> |
| <a name="otel.library.version">`otel.library.version`</a> | string | Deprecated, use the `otel.scope.version` attribute. | `1.0.0` | ![Deprecated](https://img.shields.io/badge/-deprecated-red)<br> |

### otel.scope

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="otel.scope.name">`otel.scope.name`</a> | string | The name of the instrumentation scope - (`InstrumentationScope.Name` in OTLP). | `io.opentelemetry.contrib.mongodb` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="otel.scope.version">`otel.scope.version`</a> | string | The version of the instrumentation scope - (`InstrumentationScope.Version` in OTLP). | `1.0.0` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

## peer

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="peer.service">`peer.service`</a> | string | The [`service.name`](../../resource/semantic_conventions/README.md#service) of the remote service. SHOULD be equal to the actual `service.name` resource attribute of the remote service if any. | `AuthTokenCache` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

## pool

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="pool">`pool`</a> | string | Name of the memory pool. [1] | `G1 Old Gen`; `G1 Eden space`; `G1 Survivor Space` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** Pool names are generally obtained via [MemoryPoolMXBean#getName()](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/java/lang/management/MemoryPoolMXBean.html#getName()).

## process

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="process.command">`process.command`</a> | string | The command used to launch the process (i.e. the command name). On Linux based systems, can be set to the zeroth string in `proc/[pid]/cmdline`. On Windows, can be set to the first parameter extracted from `GetCommandLineW`. | `cmd/otelcol` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="process.command_args">`process.command_args`</a> | string[] | All the command arguments (including the command/executable itself) as received by the process. On Linux-based systems (and some other Unixoid systems supporting procfs), can be set according to the list of null-delimited strings extracted from `proc/[pid]/cmdline`. For libc-based executables, this would be the full argv vector passed to `main`. | `[cmd/otecol, --config=config.yaml]` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="process.command_line">`process.command_line`</a> | string | The full command used to launch the process as a single string representing the full command. On Windows, can be set to the result of `GetCommandLineW`. Do not set this if you have to assemble it just for monitoring; use `process.command_args` instead. | `C:\cmd\otecol --config="my directory\config.yaml"` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="process.owner">`process.owner`</a> | string | The username of the user that owns the process. | `root` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="process.parent_pid">`process.parent_pid`</a> | int | Parent Process identifier (PID). | `111` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="process.pid">`process.pid`</a> | int | Process identifier (PID). | `1234` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### process.executable

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="process.executable.name">`process.executable.name`</a> | string | The name of the process executable. On Linux based systems, can be set to the `Name` in `proc/[pid]/status`. On Windows, can be set to the base name of `GetProcessImageFileNameW`. | `otelcol` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="process.executable.path">`process.executable.path`</a> | string | The full path to the process executable. On Linux based systems, can be set to the target of `proc/[pid]/exe`. On Windows, can be set to the result of `GetProcessImageFileNameW`. | `/usr/bin/cmd/otelcol` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### process.runtime

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="process.runtime.description">`process.runtime.description`</a> | string | An additional description about the runtime of the process, for example a specific vendor customization of the runtime environment. | `Eclipse OpenJ9 Eclipse OpenJ9 VM openj9-0.21.0` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="process.runtime.name">`process.runtime.name`</a> | string | The name of the runtime of this process. For compiled native binaries, this SHOULD be the name of the compiler. | `OpenJDK Runtime Environment` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="process.runtime.version">`process.runtime.version`</a> | string | The version of the runtime of this process, as returned by the runtime without modification. | `14.0.2` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

## rpc

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="rpc.method">`rpc.method`</a> | string | The name of the (logical) method being called, must be equal to the $method part in the span name. [1] | `exampleMethod` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="rpc.service">`rpc.service`</a> | string | The full (logical) name of the service being called, including its package name, if applicable. [2] | `myservice.EchoService` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="rpc.system">`rpc.system`</a> | string | A string identifying the remoting system. See below for a list of well-known identifiers. | `grpc` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** This is the logical name of the method from the RPC interface perspective, which can be different from the name of any implementing method/function. The `code.function` attribute may be used to store the latter (e.g., method actually executing the call on the server side, RPC client stub method on the client side).

**[2]:** This is the logical name of the service from the RPC interface perspective, which can be different from the name of any implementing class. The `code.namespace` attribute may be used to store the latter (despite the attribute name, it may include a class name; e.g., class with method actually executing the call on the server side, RPC client stub class on the client side).
`rpc.system` has the following list of well-known values. If one of them applies, then the respective value MUST be used, otherwise a custom value MAY be used.

| Value  | Description |
|---|---|
| `grpc` | gRPC |
| `java_rmi` | Java RMI |
| `dotnet_wcf` | .NET WCF |
| `apache_dubbo` | Apache Dubbo |
| `connect_rpc` | Connect RPC |


### rpc.connect_rpc

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="rpc.connect_rpc.error_code">`rpc.connect_rpc.error_code`</a> | string | The [error codes](https://connect.build/docs/protocol/#error-codes) of the Connect request. Error codes are always string values. | `cancelled` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
`rpc.connect_rpc.error_code` MUST be one of the following:

| Value  | Description |
|---|---|
| `cancelled` | cancelled |
| `unknown` | unknown |
| `invalid_argument` | invalid_argument |
| `deadline_exceeded` | deadline_exceeded |
| `not_found` | not_found |
| `already_exists` | already_exists |
| `permission_denied` | permission_denied |
| `resource_exhausted` | resource_exhausted |
| `failed_precondition` | failed_precondition |
| `aborted` | aborted |
| `out_of_range` | out_of_range |
| `unimplemented` | unimplemented |
| `internal` | internal |
| `unavailable` | unavailable |
| `data_loss` | data_loss |
| `unauthenticated` | unauthenticated |


### rpc.grpc

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="rpc.grpc.status_code">`rpc.grpc.status_code`</a> | int | The [numeric status code](https://github.com/grpc/grpc/blob/v1.33.2/doc/statuscodes.md) of the gRPC request. | `0` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
`rpc.grpc.status_code` MUST be one of the following:

| Value  | Description |
|---|---|
| `0` | OK |
| `1` | CANCELLED |
| `2` | UNKNOWN |
| `3` | INVALID_ARGUMENT |
| `4` | DEADLINE_EXCEEDED |
| `5` | NOT_FOUND |
| `6` | ALREADY_EXISTS |
| `7` | PERMISSION_DENIED |
| `8` | RESOURCE_EXHAUSTED |
| `9` | FAILED_PRECONDITION |
| `10` | ABORTED |
| `11` | OUT_OF_RANGE |
| `12` | UNIMPLEMENTED |
| `13` | INTERNAL |
| `14` | UNAVAILABLE |
| `15` | DATA_LOSS |
| `16` | UNAUTHENTICATED |


### rpc.jsonrpc

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="rpc.jsonrpc.error_code">`rpc.jsonrpc.error_code`</a> | int | `error.code` property of response if it is an error response. | `-32700`; `100` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="rpc.jsonrpc.error_message">`rpc.jsonrpc.error_message`</a> | string | `error.message` property of response if it is an error response. | `Parse error`; `User already exists` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="rpc.jsonrpc.request_id">`rpc.jsonrpc.request_id`</a> | string | `id` property of request or response. Since protocol allows id to be int, string, `null` or missing (for notifications), value is expected to be cast to string for simplicity. Use empty string in case of `null` value. Omit entirely if this is a notification. | `10`; `request-7`; `` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="rpc.jsonrpc.version">`rpc.jsonrpc.version`</a> | string | Protocol version as in `jsonrpc` property of request/response. Since JSON-RPC 1.0 does not specify this, the value can be omitted. | `2.0`; `1.0` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

## server

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="server.address">`server.address`</a> | string | Logical server hostname, matches server FQDN if available, and IP or socket address if FQDN is not known. | `example.com` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="server.port">`server.port`</a> | int | Logical server port number | `80`; `8080`; `443` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### server.socket

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="server.socket.address">`server.socket.address`</a> | string | Physical server IP address or Unix socket address. | `10.5.3.2` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="server.socket.domain">`server.socket.domain`</a> | string | The domain name of an immediate peer. [1] | `proxy.example.com` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="server.socket.port">`server.socket.port`</a> | int | Physical server port. | `16456` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** Typically observed from the client side, and represents a proxy or other intermediary domain name.

## service

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="service.name">`service.name`</a> | string | Logical name of the service. [1] | `shoppingcart` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="service.namespace">`service.namespace`</a> | string | A namespace for `service.name`. [2] | `Shop` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="service.version">`service.version`</a> | string | The version string of the service API or implementation. | `2.0.0` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** MUST be the same for all instances of horizontally scaled services. If the value was not specified, SDKs MUST fallback to `unknown_service:` concatenated with [`process.executable.name`](process.md#process), e.g. `unknown_service:bash`. If `process.executable.name` is not available, the value MUST be set to `unknown_service`.

**[2]:** A string value having a meaning that helps to distinguish a group of services, for example the team name that owns a group of services. `service.name` is expected to be unique within the same namespace. If `service.namespace` is not specified in the Resource then `service.name` is expected to be unique for all services that have no explicit namespace defined (so the empty/unspecified namespace is simply one more valid namespace). Zero-length namespace string is assumed equal to unspecified namespace.

### service.instance

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="service.instance.id">`service.instance.id`</a> | string | The string ID of the service instance. [1] | `my-k8s-pod-deployment-1`; `627cc493-f310-47de-96bd-71410b7dec09` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** MUST be unique for each instance of the same `service.namespace,service.name` pair (in other words `service.namespace,service.name,service.instance.id` triplet MUST be globally unique). The ID helps to distinguish instances of the same service that exist at the same time (e.g. instances of a horizontally scaled service). It is preferable for the ID to be persistent and stay the same for the lifetime of the service instance, however it is acceptable that the ID is ephemeral and changes during important lifetime events for the service (e.g. service restarts). If the service has no inherent unique ID that can be used as the value of this attribute it is recommended to generate a random Version 1 or Version 4 RFC 4122 UUID (services aiming for reproducible UUIDs may also use Version 5, see RFC 4122 for more recommendations).

## source

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="source.address">`source.address`</a> | string | Source address, for example IP address or UNIX socket name. | `10.5.3.2` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="source.domain">`source.domain`</a> | string | The domain name of the source system. [1] | `foo.example.com` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="source.port">`source.port`</a> | int | Source port number | `3389`; `2888` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** This value may be a host name, a fully qualified domain name, or another host naming format.

## telemetry

### telemetry.auto

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="telemetry.auto.version">`telemetry.auto.version`</a> | string | The version string of the auto instrumentation agent, if used. | `1.2.3` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

### telemetry.sdk

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="telemetry.sdk.language">`telemetry.sdk.language`</a> | string | The language of the telemetry SDK. | `cpp` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="telemetry.sdk.name">`telemetry.sdk.name`</a> | string | The name of the telemetry SDK as defined above. [1] | `opentelemetry` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="telemetry.sdk.version">`telemetry.sdk.version`</a> | string | The version string of the telemetry SDK. | `1.2.3` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

**[1]:** The OpenTelemetry SDK MUST set the `telemetry.sdk.name` attribute to `opentelemetry`.
If another SDK, like a fork or a vendor-provided implementation, is used, this SDK MUST set the
`telemetry.sdk.name` attribute to the fully-qualified class or module name of this SDK's main entry point
or another suitable identifier depending on the language.
The identifier `opentelemetry` is reserved and MUST NOT be used in this case.
All custom identifiers SHOULD be stable across different versions of an implementation.
`telemetry.sdk.language` has the following list of well-known values. If one of them applies, then the respective value MUST be used, otherwise a custom value MAY be used.

| Value  | Description |
|---|---|
| `cpp` | cpp |
| `dotnet` | dotnet |
| `erlang` | erlang |
| `go` | go |
| `java` | java |
| `nodejs` | nodejs |
| `php` | php |
| `python` | python |
| `ruby` | ruby |
| `webjs` | webjs |
| `swift` | swift |


## thread

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="thread.id">`thread.id`</a> | int | Current "managed" thread ID (as opposed to OS thread ID). | `42` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="thread.name">`thread.name`</a> | string | Current thread name. | `main` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

## type

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="type">`type`</a> | string | The type of memory. | `heap`; `non_heap` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
`type` MUST be one of the following:

| Value  | Description |
|---|---|
| `heap` | Heap memory. |
| `non_heap` | Non-heap memory |


## user_agent

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="user_agent.original">`user_agent.original`</a> | string | Value of the [HTTP User-Agent](https://www.rfc-editor.org/rfc/rfc9110.html#field.user-agent) header sent by the client. | `CERN-LineMode/2.15 libwww/2.17b3` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

## webengine

| Attribute  | Type | Description  | Examples  | Stability |
|---|---|---|---|---|
| <a name="webengine.description">`webengine.description`</a> | string | Additional description of the web engine (e.g. detailed version and edition information). | `WildFly Full 21.0.0.Final (WildFly Core 13.0.1.Final) - 2.2.2.Final` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="webengine.name">`webengine.name`</a> | string | The name of the web engine. | `WildFly` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |
| <a name="webengine.version">`webengine.version`</a> | string | The version of the web engine. | `21.0.0` | ![Experimental](https://img.shields.io/badge/-experimental-blue)<br> |

