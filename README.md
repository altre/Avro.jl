# Avro

This is a clone of https://github.com/JuliaData/Avro.jl with the added functionality of writing record by record and reading on partition at a time. The relevant PR is: https://github.com/JuliaData/Avro.jl/pull/16 Should this be merged, we should revert to the official Avro package and delete this everywhere.


This is a pure Julia implementation of the [Apache Avro](http://avro.apache.org/docs/current/index.html) data standard. It provides convenient APIs for reading/writing data directly in the avro format, or as schema-included object container files.

## Installation

The package can be installed by typing in the following in a Julia REPL:

```julia
julia> using Pkg; Pkg.add("Avro")
```

### Implementation status

It currently supports:

  * All primitive types
  * All nested/complex types
  * Logical types listed in the spec (Decimal, UUID, Date, Time, Timestamps, Duration)
  * Binary encoding/decoding
  * Reading/writing object container files via the Tables.jl interface
  * Supports the xz, zstd, deflate, and bzip2 compression codecs for object container files

Currently not supported are:

  * JSON encoding/decoding of objects
  * Single object encoding or schema fingerprints
  * Schema resolution
  * Protocol messages, calls, handshakes
  * Snappy compression

### Package motivation

Why use the avro format vs. other data formats? Some benefits include:
  * Very concise binary encoding, especially object container files with compression
  * Very fast reading/writing
  * Objects/data must have well-defined schema
  * One of the few "row-oriented" binary data formats
