# Endianness

Won't go into too much detail here, but it wouldn't feel write to have something with this much about data representation and not mention endianness.
Endianness is basically the ordering of bytes. 

In all the examples I've displayed, you'll notice the Most Significant Byte (MSB) is on the left-hand side
with the Least-Significant-Bit (LSB) on the right-hand side. If we were to expand this from `8-bit` to `16-bit` it would look like this
```rust
//TODO: add rust-examples of how to see these representations
```
```

  |---------------------------------------------------------unsigned 32-bit integer------------------------------------------------- -|
S |-------------------------------2 bytes---------------------------|-------------------------------2 bytes---------------------------| E
T |---------------8-bits -----------------| -----------8-bits-------|---------------8-bits------------------| -----------8-bits-------|
A |-------nibble--------|------nibble-----|----nibble---|---nibble--|-------nibble--------|------nibble-----|----nibble---|---nibble--| N
R |32768 16384 8192 4096|2048 1024 512 256|128 64 32  16| 8  4  2  1| 32768 16384 8192 4096|2048 1024 512 256|128 64 32 16| 8  4  2  1|  
T |  1     0     1    0 |  1    0   1   0 | 1   0  1   1| 1  0  1  1|  1     1     0    0 |  1    1   0   0 | 1   1  0   1| 1  1  0  1| D
  |---------------------|-----------------|-------------|-----------|---------------------|-----------------|-------------|-----------| 
0x|           A         |         A       |       B           B     |           C         |        C        |     D       |    D      |
```
This is referred to as Big-Endian or Network Byte Order (as it's the ordering used for network traffic).

The opposite ordering is called Little-Endian, and looks like this.
```
  |---------------------------------------------------------unsigned 32-bit integer------------------------------------------------- -|
S |-------------------------------2 bytes---------------------------|-------------------------------2 bytes---------------------------| E
T |---------------8-bits -----------------| -----------8-bits-------|---------------8-bits------------------| -----------8-bits-------|
A |-------nibble--------|------nibble-----|----nibble---|---nibble--|-------nibble--------|------nibble-----|----nibble---|---nibble--| N
R |32768 16384 8192 4096|2048 1024 512 256|128 64 32  16| 8  4  2  1| 32768 16384 8192 4096|2048 1024 512 256|128 64 32 16| 8  4  2  1|  
T |  1     1     0    1 |  1    1   0   1 | 1   1  0   0| 1  1  0  0|  1     0     1    1 |  1    0   1   1 | 1   0  1   0| 1  0  1  0| D
  |---------------------|-----------------|-------------|-----------|---------------------|-----------------|-------------|-----------| 
0x|          D          |        D        |      C      |    C      |           B         |         B       |       A     |     A     |
```
However, many of the most popular architectures and operating systems are Little-Endian, where the LSB would be on the left-hand side and MSB on the right-hand side. 
This means that little-endian architectures need to convert the byte ordering of network traffic in order to use it.

This is a bit of a black-hole of a subject so we won't go much further into it.
Just know that this is an annoying thing to be aware of if you're ever implementing things where byte ordering is a thing.

The Rust standard library has numerical methods to identify, enforce, and referse byte orderings.
Just look for methods with letters like `le` (little-endian), `be` (big-endian), and `ne` (native endian).

[Example of endianness and compatibility](https://jira.mongodb.org/browse/SERVER-1625)
[Endianness, alignment, and char signage incompatibility](https://dflund.se/~pi/mongo_big_endian.html)

