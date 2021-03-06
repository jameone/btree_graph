# Binary Tree Graph (btree_graph)

## Branch Status

| build                 | test               | main               |
| :-------------------: | :----------------: | :----------------: |
| ![CodeBuild(build)]   | ![CodeBuild(test)] | ![CodeBuild(main)] |

![CodeBuild(main)]
[![Version badge]][crates.io]
[![Docs badge]][docs.rs]

[CodeBuild(main)]: https://codebuild.us-east-1.amazonaws.com/badges?uuid=eyJlbmNyeXB0ZWREYXRhIjoieHhXM3oweUNEUEhLQmNvaytuRmZWRHV2UVEzMUk0akhyU0NyMi9hblhXcTBiVWp6bjQzNXlLRGJubGcwQUxFOHZNV01HcERNUnNZbm5NSG5yYWJia2pzPSIsIml2UGFyYW1ldGVyU3BlYyI6Iis2T2l2LzVjZGV6Mk1oVWIiLCJtYXRlcmlhbFNldFNlcmlhbCI6MX0%3D&branch=main
[CodeBuild(test)]: https://codebuild.us-east-1.amazonaws.com/badges?uuid=eyJlbmNyeXB0ZWREYXRhIjoieHhXM3oweUNEUEhLQmNvaytuRmZWRHV2UVEzMUk0akhyU0NyMi9hblhXcTBiVWp6bjQzNXlLRGJubGcwQUxFOHZNV01HcERNUnNZbm5NSG5yYWJia2pzPSIsIml2UGFyYW1ldGVyU3BlYyI6Iis2T2l2LzVjZGV6Mk1oVWIiLCJtYXRlcmlhbFNldFNlcmlhbCI6MX0%3D&branch=main
[CodeBuild(build)]: https://codebuild.us-east-1.amazonaws.com/badges?uuid=eyJlbmNyeXB0ZWREYXRhIjoieHhXM3oweUNEUEhLQmNvaytuRmZWRHV2UVEzMUk0akhyU0NyMi9hblhXcTBiVWp6bjQzNXlLRGJubGcwQUxFOHZNV01HcERNUnNZbm5NSG5yYWJia2pzPSIsIml2UGFyYW1ldGVyU3BlYyI6Iis2T2l2LzVjZGV6Mk1oVWIiLCJtYXRlcmlhbFNldFNlcmlhbCI6MX0%3D&branch=main
[Version badge]: https://img.shields.io/crates/v/btree_graph
[crates.io]: https://crates.io/crates/btree_graph
[Docs badge]: https://img.shields.io/badge/docs.rs-rustdoc-blue
[docs.rs]: https://docs.rs/btree_graph/

This library is a minimal implementation of a graph
(abstract data structure) by way of two binary tree maps
(`BTreeMap`). This implementation is often referred to as
an adjacency list.

The primary goals of this implementation are to be
minimal and idiomatic to the Rust language. The `alloc`
crate is the only dependency when compiled with default
features and is not optional. As one might assume, `alloc`
is required for reason the implementation relies on `BTreeMap`
(and the `BTreeSet` wrapper).

## Example
```rust
use btree_graph::BTreeGraph;

fn main() {
    let mut graph: BTreeGraph<String, String> = BTreeGraph::new();
    // Add nodes.
    graph.add_vertex(String::from("Tarzan"));
    graph.add_vertex(String::from("Jane"));
    // Add a relationship.
    graph.add_edge(String::from("Tarzan"), String::from("Jane"), String::from("Loves"));

    // Assert relationship now exists.
    assert!(graph.adjacdent(String::from("Tarzan"), String::from("Jane")));
}
```

## Usage

Add the following to your `Cargo.toml` file:
```toml
[dependencies]
btree_graph = "0.2.2"
```

## API

Please see the [API](src/graph/api.rs) for a full list of
available methods.

## License

This work is dually licensed under MIT OR Apache-2.0.