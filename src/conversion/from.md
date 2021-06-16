# Converting with `From`
For numeric types, `From` is only implemented for *lossless* conversions. 
```rust
let ten_as_i64 = i64::from(10_i32) // Ok!
let ten_as_i32 = i32::from(10_i64) // Panics!
```

