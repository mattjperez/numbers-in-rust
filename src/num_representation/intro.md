# Number Representation

In computer science, everything (at the moment) is represented by `1`'s and `0`'s, stored in groupings such as `bytes` (8 `bits`).  
Each bit represents a **power of 2**, so a group of **8 bits** representing the number `130` may look like this.

|       Bits        |       1       |       0       |       0       |       0       |       0       |       0       |       1       |       0       |
| :---------------: | :-----------: | :-----------: | :-----------: | :-----------: | :-----------: | :-----------: | :-----------: | :-----------: |
| Base 10 (Decimal) |      128      |      64       |      32       |      16       |       8       |       4       |       2       |       1       |
|  Base 2 (Binary)  | 2<sup>7</sup> | 2<sup>6</sup> | 2<sup>5</sup> | 2<sup>4</sup> | 2<sup>3</sup> | 2<sup>2</sup> | 2<sup>1</sup> | 2<sup>0</sup> |

`128 + 0 + 0 + 0 + 0 + 0 + 2 + 0 == 130`
The above representation is that of an `unsigned` integer with `8-bits`, i.e. Rust's `u8`.  

>For simplicity, we'll only be looking at the `8-bit` variants of integers in this major section. You can apply these topics to the larger variants by extending the number of bits towards the left-hand side, i.e. 256, 512, etc.

