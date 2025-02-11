---
category: "[[Technology]]"
---
# Overview
---
Bit Manipulation is the process of applying logical operations on a sequence of bits. Bit is the smallest element of data and all electronic devices support it. Bit operations have constant time complexity. Bit manipulation requires knowledge on **binary and binary conversion**.
# Usage
---
1. Low-level device control
2. Error detection
3. Encryption
4. Data compression
5. Optimization
# Bit Operation
---
In bit operation takes one or more binary sequence and operates on them per bit. There are advantages of bit operations over arithmetic operation. Bit operations are:
1. Fast and simple actions
2. Directly supported by the processors.
3. Manipulate values for comparison and calculation.
# Bitwise Operators
---
1. AND `&`
2. OR `|`
3. NOT `~`
4. XOR `^`
5. Left Shift `<<`
6. Arithmetic/Signed Right Shift `>>` (Keeps the MSB value)
7. Logical/unsigned Right Shift `>>>` (Replaces the MSB value with 0)
# Bit Tricks
---
- Set or flip or clear a bit
	- `1 << x` -> Only x-th bit is set, changed from 0 to 1
	- `~ ( 1 << x )` -> Every bit except x-th is set, changed from 0 to 1)
	- `n | ( 1 << x )` -> Sets the x-th bit in the number n
	- `n ^ ( 1 << x )` -> Flips the x-th bit in the number n
	- `n & ~ ( 1 << x )` -> Clears the x-th bit in the number n
- Check if a bit is set
	- `(number >> x) & 1`
- 
- Check if the number is even
	- `(x & 1) == 0`
- Convert characters to Uppercase or Lowercase
	- `ch ^= 32`

# Bit Problems
---
- Count set bits (count of 1 in bit representation)

```java
private static int countBits(int n) {
        int count = 0;
        while (n > 0) {
            n &= (n - 1);
            count++;
        }
        return count;
    }
```

- 