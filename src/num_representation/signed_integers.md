# Signed Integers

There are different ways to represent signed integers, Rust uses a method called [two's complement](https://en.wikipedia.org/wiki/Two%27s_complement). 
Ben Eater has a [video on two's complement](https://www.youtube.com/watch?v=4qH4unVtJkE&t=29s) where he does an amazing job of explaining things. The next few sub-sections are merely a recap of his video so feel free to skip it if you're familiar with the concept. I'm including this as a convenient reference when looking at how Rust handles integer overflow.

#### Unsigned Operations

To add two `unsigned` integers, convert them to their binary representations and add them as you would with pen and paper, by carrying the bit to the next .

```
128 = 10000000
+ 2 = 00000010
---------------
130 = 10000010
```

#### Introducing a Sign Bit, Signed Magnitude

A simple way to represent positive and negative numbers is by adding a `sign bit`. In this case, `0` represents positive integers while `1` represents negative integers.

```
64 with sign bit
0 1 0 0 0 0 0 0

-64 with sign bit
1 1 0 0 0 0 0 0
```

You'll notice we've lost an entire power of 2 by introducing a sign bit. The range we can represent with 8 bits has gone from `0..=255` to `-127..=127`.

While that's the cost to represent negatives, we've also lost the ability to add/subtract bits how we did previously, at least when negative numbers are involved.

```
8 + (-8)
  0 0 0 0 1 0 0 0
+ 1 0 0 0 1 0 0 0
-----------------
  1 0 0 1 0 0 0 0  == -16 ???
```

#### One's Complement

Sign bit and mirrored bits

```
24 in 8-bit ones-complement
 +/-  64 32  16  8  4  2  1
  0   0   0   1  1  0  0  0

-24 in 8-bit ones-complement
 +/-  64  32  16  8  4  2  1
  1   1   1   0  0  1  1  1

```
Almost, but not quite there. The following scenarios still happen.
```
There are two distinct possibilities for 0.
 +/-  64 32  16  8  4  2  1
  0   0   0   0  0  0  0  0  =  0
  1   0   0   0  0  0  0  0  = -0

!!!!!!!!Fix the next example

Operations with two negative numbers are off-by-one
(-8) + (-10)  
  1 1 1 1 0 1 1 1  // -8
+ 1 1 1 1 0 1 0 1  // -10
-----------------
  1 1 1 1 1 1 0 0  == -1


```


#### Two's Complement

One's complement, but with `-0` removed, has the effect of converting the *largest bit* to a negative.

```
24 as u8
 128  64 32  16  8  4  2  1
  0   0   0   1  1  0  0  0

24 as i8
-128  64  32  16  8  4  2  1
  0    0   0   1  1  0  0  0
  
Bit Addition/Subtraction is restored!
You also now know why the min and max values representable with twos-complement are off-by-one!
```



#### Flipping Signs with Two's Complement

1. Invert the bits
2. Add 1
```
24 as u8
 128  64 32  16  8  4  2  1
  0   0   0   1  1  0  0  0
  
1) Invert the bits
  1   1   1   0  0  1  1  1
2) Add 1 (carry bits forward)
  1   1   1   0  1  0  0  0
  
-24 as i8
-128  64  32  16  8  4  2  1
  1   1   1   0  1  0  0  0

-128 + 64 + 32 + 8 
-128 + 104
-24
  
```

There you have it, this is how signed integers are represented in Rust.

