
# Constants
As great as it is to know what happens under the hood, it would be nice to have convenient ways to... 
- check what is the difference in precision for Pi as an `f32` vs an `f64`
- see what the minimum or maximum value for a given type is, like `i128` or `u128`.
- represent `infinity` or `negative infinity` or `NaN`

That's where constants come in. 

> fun fact: in the source code, `NAN` is represented as `0.0_f32 / 0.0_f32`, `INFINITY` as `1.0_f32 / 0.0_f32`, and `NEG_INFINITY` as `-1.0_f32 / 0.0_f32`.
> Dividing by zero appears to have its uses :) 
```rust

//TODO: Add examples
```

Check a given type's documentation to see what kind of constants they have available. 
For example, [`std::i128`](https://doc.rust-lang.org/std/i128/index.html) and [`std::f32`](https://doc.rust-lang.org/std/f32/consts/index.html)

