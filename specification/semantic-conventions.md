# Semantic Conventions

**Status**: [Development](document-status.md)

The **Semantic Conventions** define the keys and values which describe commonly observed concepts, protocols, and operations used by applications.

OpenTelemetry defines its core semantic conventions in the
[semantic-conventions](https://github.com/open-telemetry/semantic-conventions)
repository.

## Federated Semantic Conventions

**Status**: [Development](document-status.md)

Federated semantic conventions are owned by OpenTelemetry SIGs and maintained
in repositories separate from the core semantic conventions. They SHOULD depend
on and extend the core semantic conventions, reusing core definitions instead
of redefining them. Each federated registry has its own
[schema URL and version](schemas/README.md#semantic-conventions-schema-urls).

Federated semantic conventions (the list is not exhaustive and will grow over
time):

- [semantic-conventions-genai](https://github.com/open-telemetry/semantic-conventions-genai):
  generative AI model clients and agents.
- [semantic-conventions-client-side](https://github.com/open-telemetry/semantic-conventions-client-side):
  browser, mobile, and desktop applications.
- [semantic-conventions-mainframe](https://github.com/open-telemetry/semantic-conventions-mainframe):
  IBM Z and LinuxONE.

Core and federated semantic conventions SHOULD be defined using the
[semantic conventions definition syntax](https://github.com/open-telemetry/weaver/blob/main/schemas/semconv-syntax.v2.md).
See [OTEP 4815](../oteps/4815-semantic-conventions-schema-v2.md) for background
and design details.

## Reserved Attributes

Semantic conventions MUST provide the following attributes:

- [`error.type`](https://github.com/open-telemetry/semantic-conventions/blob/main/docs/registry/attributes/error.md#error-type)
- [`exception.message`](https://github.com/open-telemetry/semantic-conventions/blob/main/docs/registry/attributes/exception.md#exception-message)
- [`exception.stacktrace`](https://github.com/open-telemetry/semantic-conventions/blob/main/docs/registry/attributes/exception.md#exception-stacktrace)
- [`exception.type`](https://github.com/open-telemetry/semantic-conventions/blob/main/docs/registry/attributes/exception.md#exception-type)
- [`server.address`](https://github.com/open-telemetry/semantic-conventions/blob/main/docs/registry/attributes/server.md#server-address)
- [`server.port`](https://github.com/open-telemetry/semantic-conventions/blob/main/docs/registry/attributes/server.md#server-port)
- [`service.name`](https://github.com/open-telemetry/semantic-conventions/blob/main/docs/registry/attributes/service.md#service-name)
- [`telemetry.sdk.language`](https://github.com/open-telemetry/semantic-conventions/blob/main/docs/registry/attributes/telemetry.md#telemetry-sdk-language)
- [`telemetry.sdk.name`](https://github.com/open-telemetry/semantic-conventions/blob/main/docs/registry/attributes/telemetry.md#telemetry-sdk-name)
- [`telemetry.sdk.version`](https://github.com/open-telemetry/semantic-conventions/blob/main/docs/registry/attributes/telemetry.md#telemetry-sdk-version)
- [`url.scheme`](https://github.com/open-telemetry/semantic-conventions/blob/main/docs/registry/attributes/url.md#url-scheme)

Semantic conventions MUST provide the following events:

- [`exception`](https://github.com/open-telemetry/semantic-conventions/blob/main/docs/exceptions/exceptions-spans.md)

## In-development Reserved Attributes

Semantic conventions MUST provide the following attributes:

- [`service.instance.id`](https://github.com/open-telemetry/semantic-conventions/blob/main/docs/registry/attributes/service.md#service-instance-id)

## Reserved Namespace

The `otel.*` namespace is reserved for defining compatibility with
non-OpenTelemetry technologies.
