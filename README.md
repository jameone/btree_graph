# Binary Tree Graph (btree_graph)

[![Build Status](https://travis-ci.com/jameone/btree_graph.svg?branch=main)](https://travis-ci.com/jameone/btree_graph)
[![Code Version](https://img.shields.io/crates/v/btree_graph)](https://img.shields.io/crates/v/btree_graph)
[![Docs badge]][docs.rs]

[Docs badge]: https://img.shields.io/badge/docs.rs-rustdoc-green
[docs.rs]: https://docs.rs/btree_graph/

This library is a minimal implementation of a graph 
(abstract data structure) by way of two binary tree maps
(`BTreeMap`). This implementation is often referred to as
an adjacency list.

The primary goals of this implementation are to be 
minimal and idiomatic to the Rust language. The `alloc`
crate is the only dependency when compiled with default
features. As one might assume, `alloc` is required for 
reason the implementation relies on `BTreeMap` (and the
`BTreeSet` wrapper).

Secondary concerns include serialization,
deserialization, and encoding. For these the `serde`,
`serde_json`, `serde_yaml`, and `serde_cbor` crates
are included and available under the feature flags:
`serde`, `json`, `yaml`, and `cbor`. Please see the 
encoding module's [API](./src/encoding/api.rs) for
the optional trait definitions. *Note: using `json`,
`yaml`, or `cbor` features will automatically require
a `serde` dependency.*

## Example
```rust
use btree_graph::BTreeGraph;

fn main() {
    let mut graph: BTreeGraph<String, String> = BTreeGraph::new();
    // Add nodes.
    graph.add_vertex(String::from("Jim"));
    graph.add_vertex(String::from("Jane"));
    // Add a relationship.
    graph.add_edge(String::from("Jim"), String::from("Jane"), String::from("Loves"));
    
    // Assert relationship now exists.
    assert!(graph.adjacdent(String::from("Jim"), String::from("Jane")));
}
```

## Usage

Add the following to your `Cargo.toml` file:
```toml
[dependencies]
btree_graph = "0.1.2"
```

## API

Please see the [API](./src/graph/api.rs) for a full list of
available methods.

## License

This work is dually licensed under MIT OR Apache-2.0.