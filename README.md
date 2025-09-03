# StreamingFast Fork of protoreflect

This is a fork of [jhump/protoreflect](https://github.com/jhump/protoreflect) with modifications to ensure bytes representation settings are respected in nested `anypb.Any` fields.

## Changes

The main change is in the `anyResolver.Resolve` method in `dynamic/json.go`. The modification ensures that when a message contains an `anypb.Any` field, the inner JSON object rendered will respect the same bytes encoding configuration that is set for the top-level message, providing consistent output.

This is particularly important for applications like the StreamingFast Substreams CLI that render Protobuf to JSON and need consistent bytes encoding throughout the entire JSON output.

