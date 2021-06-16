# Unsigned Integers

In computer science, everything (at the moment) is represented by `1`'s and `0`'s, stored in groupings such as `bytes` (8 `bits`).  
Each bit represents a **power of 2**, so a group of **8 bits** representing the number `130` may look like this.

|       Bits        |       1       |       0       |       0       |       0       |       0       |       0       |       1       |       0       |
| :---------------: | :-----------: | :-----------: | :-----------: | :-----------: | :-----------: | :-----------: | :-----------: | :-----------: |
| Base 10 (Decimal) |      128      |      64       |      32       |      16       |       8       |       4       |       2       |       1       |
|  Base 2 (Binary)  | 2<sup>7</sup> | 2<sup>6</sup> | 2<sup>5</sup> | 2<sup>4</sup> | 2<sup>3</sup> | 2<sup>2</sup> | 2<sup>1</sup> | 2<sup>0</sup> |

`128 + 0 + 0 + 0 + 0 + 0 + 2 + 0 == 130`
The above representation is that of an `unsigned` integer with `8-bits`, i.e. Rust's `u8`.  

>For simplicity, we'll only be looking at the `8-bit` variants of integers in this major section. You can apply these topics to the larger variants by extending the number of bits towards the left-hand side, i.e. 256, 512, etc.

Rust makes viewing these representations fairly straightforward using one of its convenient formatting 

```rust
println!("{:b}", 128);
// 10000000


println!("{:08b}", 1); // packed with 0's, up to 8 places
// 00000001
```
The largest number representable by `u8` (all bits set to `1`) is `255`, and the lowest number (all bits set to `0`) is `0`.  If we tried to represent something larger, say `256`, this would happen.

```rust
let num: u8 = 256;
println!("{}", num);

// 
 --> src/main.rs:2:19
  |
2 |     let num: u8 = 256;
  |                   ^^^
  |
  = note: `#[deny(overflowing_literals)]` on by default
  = note: the literal `256` does not fit into the type `u8` whose range is `0..=255`
// rustc's error messages are really thoughtful, thanks compiler team!

```
The two notes above are especially helpful because they 

a.  try to provide as much detail as possible to the context of the error, possibly helping you fix the issue immediately, and 

b. give you keywords to search for more in-depth information (`overflowing_literals`). 

These numbers are `unsigned` because they do not contain a `sign bit`, a bit used to indicate whether a number is positive or negative. 
Therefore **unsigned integers can only represent positive values**.
This makes them perfect for modeling situations where negative values don't exist, like a shopping cart; you can't have `-1 headphones` in your cart, right? 
As you'll see in the section on `signed integers`, the maximum number you can represent in a `u8` is larger than that of an `i8`.
This is true for `unsigned` type to their `signed` counterpart. 



