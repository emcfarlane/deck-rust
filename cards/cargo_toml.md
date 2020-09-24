What are the command cargo commands?
<!--question-->

Creating:
```
$ cargo new hello_cargo
$ cd hello_cargo
```

Building:
```
$ cargo build
   Compiling hello_cargo v0.1.0 (file:///projects/hello_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 2.85 secs
```

Check code:
```
$ cargo check
   Checking hello_cargo v0.1.0 (file:///projects/hello_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 0.32 secs
```

Building for release:
```
$ cargo build --release
```
Creates an executable `target/release` instead of `target/debug`.


