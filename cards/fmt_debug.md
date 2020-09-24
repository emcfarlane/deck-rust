Rust debug formatting?
<!--question-->
All types which want to use std::fmt formatting traits require an implementation to be printable. Automatic implementations are only provided for types such as in the std library. All others must be manually implemented somehow.

The fmt::Debug trait makes this very straightforward. All types can derive (automatically create) the fmt::Debug implementation. This is not true for fmt::Display which must be manually implemented.

```
// This structure cannot be printed either with `fmt::Display` or
// with `fmt::Debug`.
struct UnPrintable(i32);

// The `derive` attribute automatically creates the implementation
// required to make this `struct` printable with `fmt::Debug`.
#[derive(Debug)]
struct DebugPrintable(i32);
```
