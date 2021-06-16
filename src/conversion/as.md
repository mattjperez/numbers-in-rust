# Casting with As

`as` works for **both** *lossless* and *lossy* conversions.

When casting from one integer type to another integer type, with the same number of bits, it is a [no-op](https://en.wikipedia.org/wiki/NOP_(code)), as in nothing happens.
The underlying bits have not changed, merely the *lens* which these bytes are interpreted changes from that of a `u128` to an `i128`.
Unlike `From`, the true value of the integer is not maintained and the bits are merely interpreted as the destination type's encoding.
```rust
println!("128_u8 `as` i8 becomes {}", 128_u8 as i8);
// 128_u8 `as` i8 becomes -128
```

[Rust Reference on Type Casting](https://doc.rust-lang.org/1.49.0/reference/expressions/operator-expr.html#type-cast-expressions)

[Rust Reference on Casting Semantics](https://doc.rust-lang.org/1.49.0/reference/expressions/operator-expr.html#semantics)

https://doc.rust-lang.org/stable/rust-by-example/types/cast.html

