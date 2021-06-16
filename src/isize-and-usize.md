# `isize` and `usize`
According to [The Rust Reference](https://doc.rust-lang.org/reference/types/numeric.html#machine-dependent-integer-types), these integer types are machine-dependent and use the same number of bits as that of a pointer in the machine. This makes `usize` and `isize` proportional to the size of the machine's address space, and this is determined by its architecture (x86-64, etc). These types can be 16-bit, 32-bit, or 64-bit depending on the machine. However, due to many pieces of Rust code assuming sizes of 32-bit or 64-bit (common pointer sizes in modern architectures), 16-bit support is limited.
The primary concerns around machine-dependent types are that of portability and security. 
By using `isize` or `usize` at inappropriate points in your code, you're introducing variation in how your code *could* operate. These could manifest as overflows on machines with 16-bit pointers due to the lack of support as mentioned at the beginning of this section or something less obvious (which is arguably worse). 

So when should I use them? 
After some a few posts on the [Rust User Forum](https://users.rust-lang.org), reddit, and stackoverflow, 
their usage tends to gravitate around two things:

- indexing into an array
- offsets

Even when it comes to the above, `usize` appears to be the dominant type used in these cases, with few general use-cases for `isize`.
> If you have any opinions on this or any major use-cases you think would be useful for others, please feel free to open an issue/pull-request/discussion!

You could argue that this narrow scope actually leads to further introspection when it comes to what you're writing.
It forces you to think more deeply about the bounds of the operations you'll be performing, and in doing so, make it easier to select the most appropriate type for the situation. 
From a holistic view, this makes your logic more robust and better aligned with the *spirit* of Rust.

Basically, stick to explicit integer types as much as possible and be wary when using machine-dependent integers outside of the narrow scope above.

Originally called `int/uint`, but was one of the early RFCs.
https://github.com/rust-lang/rfcs/blob/master/text/0544-rename-int-uint.md
