# Operators

Operators are made available to different types and structures via certain traits (`Add`, `Sub`, `Rem`, etc).
However, these traits (and therefore operators) have different implementations depending on the type.
These implementations may have general norms and exceptions depending on the type and the operation. 
This section will help you determine if you can use a regular operator for an operation or if you should use an overflow-specific method.


https://github.com/rust-lang/rfcs/pull/560
