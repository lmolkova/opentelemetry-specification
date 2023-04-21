# Attribute Registry

**Status**: [Experimental](../document-status.md)

This document contains a registry of defined OpenTelemetry attributes which may be referenced by individual semantic conventions.
These attributes can also be used by instrumentations and user applications on any signals if they don't conflict with other attributes and semantic conventions
applied on such telemetry item.

<details>
<summary>Table of Contents</summary>

<!-- toc -->
<!-- tocstop -->

</details>

## Resource attributes

TODO: should we allow populating resource attributes on spans (as opt-in), but not the other way around?

TODO: pick a format

### Service

Format1:
- all attributes are fully defined in their corresponding convention files. 
- registry is generated table with link to original definitions and a brief description
 

| Attribute  | Type | Description  | Examples  | Status |
|---|---|---|---|---|
| [`service.name`](/specification/resource/semantic_conventions/README.md#servicename) | string | Logical name of the service | `shoppingcart` | Stable |
| [`service.namespace`](/specification/resource/semantic_conventions/README.md#servicenamespace) | string | A namespace for `service.name`. | `Shop` | Experimental |
| [`service.instance.id`](/specification/resource/semantic_conventions/README.md#serviceinstanceid) | string | The string ID of the service instance. | `my-k8s-pod-deployment-1`; `627cc493-f310-47de-96bd-71410b7dec09` | Experimental |
| [`service.version`](/specification/resource/semantic_conventions/README.md#serviceversion) | string | The version string of the service API or implementation. | `2.0.0` | Experimental |

## Other attributes 

### Server

Format 2: 
- individual attributes are described fully in the registry
- have proper anchors 
- everything else references registry

Pros: single place for basic, not signal-specific, not convention-specific information about attribute

#### [`server.address`](/specification/common/attribute-registry.md#serveraddress)

Logical server hostname, matches server FQDN if available, and IP or socket address if FQDN is not known. 

**Type**: string
**Examples**: `example.com`
**Status**: experimental

#### `server.port`

Server port number 

**Type**: int
**Examples**: `80`; `8080`; `443`
**Status**: experimental

#### `server.socket.domain`

The domain name of an immediate peer.
Usually represents a proxy or intermediary domain name.

**Type**: string
**Examples**: `proxy.example.com`
**Status**: experimental

#### `server.socket.address`

Physical server IP address or Unix socket domain name. Should usually be set only when it's different than [`server.address`](/specification/common/attribute-registry.md#serveraddress)

**Type**: string
**Examples**: `10.5.3.2`
**Status**: experimental

#### `server.socket.port`

Physical server port.

**Type**: int
**Examples**:  `16456`
**Status**: experimental
