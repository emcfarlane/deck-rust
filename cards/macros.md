Rust macros?
<!--question-->
`macro_rules` allows users to define syntax extension in a declarative way. We call such extensions "macros by example" or simply "macros".

## Transcribing

When a macro is invoked, the macro expander looks up macro invocations by name, and tries each macro rule in turn. It transcribes the first successful match; if this results in an error, then future matches are not tried. When matching, no lookahead is performed; if the compiler cannot unambiguously determine how to parse the macro invocation one token at a time, then it is an error. In the following example, the compiler does not look ahead past the identifier to see if the following token is a ), even though that would allow it to parse the invocation unambiguously:

```rust
macro_rules! ambiguity {
    ($($i:ident)* $j:ident) => { };
}

ambiguity!(error); // Error: local ambiguity
```


