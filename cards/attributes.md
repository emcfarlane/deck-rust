What is an attribute?
<!--question-->
An attribute is a general, free-form metadatum that is interpreted according to name, convention, language, and compiler version. Attributes are modeled on Attributes in ECMA-335, with the syntax coming from ECMA-334 (C#).

Inner attributes, written with a bang (!) after the hash (#), apply to the item that the attribute is declared within. Outer attributes, written without the bang after the hash, apply to the thing that follows the attribute.

The attribute consists of a path to the attribute, followed by an optional delimited token tree whose interpretation is defined by the attribute. Attributes other than macro attributes also allow the input to be an equals sign (=) followed by a literal expression. See the meta item syntax below for more details.

Attributes can be classified into the following kinds:

Built-in attributes
Macro attributes
Derive macro helper attributes
Tool attributes
Attributes may be applied to many things in the language:

All item declarations accept outer attributes while external blocks, functions, implementations, and modules accept inner attributes.
Most statements accept outer attributes (see Expression Attributes for limitations on expression statements).
Block expressions accept outer and inner attributes, but only when they are the outer expression of an expression statement or the final expression of another block expression.
Enum variants and struct and union fields accept outer attributes.
Match expression arms accept outer attributes.
Generic lifetime or type parameter accept outer attributes.
Expressions accept outer attributes in limited situations, see Expression Attributes for details.
Function, closure and function pointer parameters accept outer attributes. This includes attributes on variadic parameters denoted with ... in function pointers and external blocks.
Some examples of attributes:

```
// General metadata applied to the enclosing module or crate.
#![crate_type = "lib"]

// A function marked as a unit test
#[test]
fn test_foo() {
    /* ... */
}

// A conditionally-compiled module
#[cfg(target_os = "linux")]
mod bar {
    /* ... */
}

// A lint attribute used to suppress a warning/error
#[allow(non_camel_case_types)]
type int8_t = i8;

// Inner attribute applies to the entire function.
fn some_unused_variables() {
  #![allow(unused_variables)]

  let x = ();
  let y = ();
  let z = ();
}
```
