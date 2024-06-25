# Building Wasmtime

## Prerequisites

### Git Submodules
The Wasmtime repository contains a number of git submodules. To build Wasmtime and most other crates in the repository, ensure that these are initialized with the following command:
```sh
git submodule update --init
```

### The Rust Toolchain
Install the Rust toolchain, which includes `rustup`, `cargo`, `rustc`, etc. You can find the installation instructions [here](https://www.rust-lang.org/).

### libclang (Optional)
The `wasmtime-fuzzing` crate transitively depends on `bindgen`, which requires `libclang` to be installed on your system. If you want to work on Wasmtime's fuzzing infrastructure, you'll need `libclang`. Details on how to get `libclang` and make it available for `bindgen` are [here](https://rust-lang.github.io/rust-bindgen/requirements.html).

## Building the Wasmtime CLI
To make an unoptimized, debug build of the Wasmtime CLI tool, go to the root of the repository and run:
```sh
cargo build
```
The built executable will be located at `target/debug/wasmtime`.

To make an optimized build, run the following command in the root of the repository:
```sh
cargo build --release
```
The built executable will be located at `target/release/wasmtime`.

You can also build and run a local Wasmtime CLI by replacing `cargo build` with `cargo run`.

## Building the Wasmtime C API
To build the C API of Wasmtime, run:
```sh
cargo build --release -p wasmtime-c-api
```
This will place the shared library inside `target/release`. On Linux, it will be called `libwasmtime.{a,so}`. On macOS, it will be called `libwasmtime.{a,dylib}`. On Windows, it will be called `wasmtime.{lib,dll,dll.lib}`.

## Building Other Wasmtime Crates
You can build any of the Wasmtime crates by appending `-p wasmtime-whatever` to the `cargo build` invocation. For example, to build the `wasmtime-environ` crate, execute:
```sh
cargo build -p wasmtime-environ
```
Alternatively, you can `cd` into the crate's directory and run `cargo build` there, without needing to supply the `-p` flag:
```sh
cd crates/environ/
cargo build
```