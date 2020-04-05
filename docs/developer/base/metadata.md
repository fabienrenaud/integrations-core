# Metadata

-----

Often, you will want to collect mostly unstructured data that doesn't map well to tags, like fine-grained
product version inforation.

The base class provides [a method](api.md#datadog_checks.base.checks.base.AgentCheck.set_metadata) that handles such
cases. The collected data is captured by [flares](https://docs.datadoghq.com/agent/troubleshooting/send_a_flare/),
displayed on the Agent's [status page](https://docs.datadoghq.com/agent/guide/agent-status-page/), and will
eventually be queryable in-app.

## Interface

This adds a method `set_metadata` to the `AgentCheck` base class that updates cached metadata values, which are then sent by the Agent at regular intervals.

It requires 2 arguments:

1. `name` - the name of the metadata
2. `value` - the value for the metadata. if `name` has no transformer defined then the raw `value` will be submitted and therefore it must be a `str`

The method also accepts arbitrary keyword arguments that are forwarded to any defined transformers.
