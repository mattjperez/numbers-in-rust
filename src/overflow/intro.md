# Overflow
[Rust Reference on Overflow](https://doc.rust-lang.org/1.49.0/reference/expressions/operator-expr.html#overflow)

> Integer operators will panic when they overflow when compiled in debug mode. The -C debug-assertions and -C overflow-checks compiler flags can be used to control this more directly. The following things are considered to be overflow:
> - When +, * or - create a value greater than the maximum value, or less than the minimum value that can be stored. This includes unary - on the smallest value of any signed integer type.
> - Using / or %, where the left-hand argument is the smallest integer of a signed integer type and the right-hand argument is -1.
> - Using << or >> where the right-hand argument is greater than or equal to the number of bits in the type of the left-hand argument, or is negative.

> The following is a paraphrasing from [Myths and Legends about Integer Overflow in Rust](http://huonw.github.io/blog/2016/04/myths-and-legends-about-integer-overflow-in-rust/)

Rust's standard library provides four additional methods to handle bit overflows.
These explicit implementations give you precise control over your numerical operations to ensure a defined behavior.

- `wrapping_<add/sub/mul/div/etc...>`
- `saturating_<add/sub/mul/div/etc...>`
- `overflowing_<add/sub/mul/div/etc...>`
- `checked_<add/sub/mul/div/etc...>`
- `unchecked_<add/sub/mul/div/etc...>` // nightly-only (unchecked_math)

These methods will prevent panicking when overflow occurs and let you overflow purposefully if that's your intention (like in hashing algorithms and ring buffers).

```rust
//TODO: Elaborate on these further, especially in regard to signed integers`
```
- `wrapping_..` returns the straight two's complement result
- `saturating_..` returns the largest/smallest value (as appropriate) of the type when overflow occurs
- `overflowing_..` returns the two's complement result along with a boolean indicating if overflow occured
- `checked_..` returns an `Option` that's `None` if overflowing occurs
- `unchecked_..` assumes overflow cannot occur. Results in undefined behavior when `result > <int>::MAX || result < <int>::MIN`



```rust
//TODO: examples
```


#### Rust vs C/C++ on overflows
[Reddit: Why are i32s the Fastest?](https://www.reddit.com/r/rust/comments/931leq/why_are_i32s_the_fastest/e3a3eop?utm_source=share&utm_medium=web2x&context=3)

