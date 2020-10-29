# C3P0

C3P0 contains protocol definitions. 

Centralizing these definitions, it is hoped that libraries and applications will make use of them to make data more portable between components of a system.

## Installation

If [available in Hex](https://hex.pm/docs/publish), the package can be installed
by adding `c3p0` to your list of dependencies in `mix.exs`:

```elixir
def deps do
  [
    {:c3p0, "~> 0.3.0"}
  ]
end
```

## Protocols

### ID

`C3P0.ID` is a protocol to standardize finding an ID for a peice of data.

There are two functions in this protocol:

1. `C3P0.ID.id(data)` 
2. `C3P0.ID.guid(data)`

By default the guid will fall back to the id.

This will work on all structs and maps which have fields `id` (and optionally `guid`)

To customize for your struct if there are different fields, derive the `C3P0.ID` protocol.

```elixir
defmodule MyStruct do
  @derive {C3P0.ID, id_field: :local_id, guid_field: :global_id}
  defstruct [:local_id, :global_id]
end
```

### GenerateGuid

`C3P0.GenerateGuid` is a protocol to generate a map containing an `id` and `guid` given a resource.


### Humanize

`C3P0.Humanize` is a protocol to display as a string the data provided.

Falls back to a simple `to_string`

### Blank

`C3P0.Blank` is a protocol to handle blankness.

Empty strings, bbinaries, lists, maps and tuples are considered `blank?` along with `nil`.

The protocol defines 3 functions:

* `blank?(data)` - true/false
* `present?(data)` - true/false
* `presence(data)` - returns the value if it is not blank. nil if it is blank

### Metadata

`C3P0.Metadata` is a protocol to provide a map of metadata about a struct.

## Contributing

We love contributions and they're welcome here!

C3P0 is aiming to be a central collection of useful protocols and we'd love more protocols that folks find useful. 

Please raise an issue or submit a PR. Protocols can be really powerful especially if everyone uses the same ones.


Documentation can be generated with [ExDoc](https://github.com/elixir-lang/ex_doc)
and published on [HexDocs](https://hexdocs.pm). Once published, the docs can
be found at [https://hexdocs.pm/c3p0](https://hexdocs.pm/c3p0).

