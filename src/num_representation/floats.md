# Floats

Floats in Rust follow the 2008 revision of the IEEE-754 standard on 
[single-precision floating-points](https://en.wikipedia.org/wiki/Single-precision_floating-point_format)(e.g. `f32`, `float`, `binary32`)
and [double-precision floating-points](https://en.wikipedia.org/wiki/Double-precision_floating-point_format)(e.g. `f64`, `double`, `binary64`) representations of floating-points.

> Don't use floats for financial operations

```
 1/2, 1/4, 1/8, 1/16, 1/32
```

Better precision -> smaller range

larger range -> worse precision

Mantissa vs exponent

//TODO: Insert photos of float binary representations

23 binary digits of precision for f32

56 binary digits of precision for f64

