How do rust macros work?
<!--question-->

There are two ways to define new macros:

- Macros by Example define new syntax in a higher-level, declarative way.
- Procedural Macros can be used to implement custom derive.

## Macro Invocation

A macro invocation executes a macro at compile time and replaces the invocation with the result of the macro. Macros may be invoked in the following situations:

- Expressions and statements
- Patterns
- Types
- Items including associated items
- macro_rules transcribers
- External blocks

When used as an item or a statement, the MacroInvocationSemi form is used where a semicolon is required at the end when not using curly braces. Visibility qualifiers are never allowed before a macro invocation or macro_rules definition.

```rust
// Used as an expression.
let x = vec![1,2,3];

// Used as a statement.
println!("Hello!");

// Used in a pattern.
macro_rules! pat {
    ($i:ident) => (Some($i))
}

if let pat!(x) = Some(1) {
    assert_eq!(x, 1);
}

// Used in a type.
macro_rules! Tuple {
    { $A:ty, $B:ty } => { ($A, $B) };
}

type N2 = Tuple!(i32, i32);

// Used as an item.
thread_local!(static FOO: RefCell<u32> = RefCell::new(1));

// Used as an associated item.
macro_rules! const_maker {
    ($t:ty, $v:tt) => { const CONST: $t = $v; };
}
trait T {
    const_maker!{i32, 7}
}

// Macro calls within macros.
macro_rules! example {
    () => { println!("Macro call in a macro!") };
}
// Outer macro `example` is expanded, then inner macro `println` is expanded.
example!();
```

Source: https://doc.rust-lang.org/reference/macros.html
