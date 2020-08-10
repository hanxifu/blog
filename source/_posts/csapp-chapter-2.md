---
title: csapp-chapter-2
date: 2020-08-01 21:19:28
tags: [CSAPP]
---

# Chapter 2

## Concepts

TBD

## Excercises

### 2.1

A

```text
0x39A7F8
0011 1001 1010 0111 1111 1000
```

B

```text
1100 1001 0111 1011
   C    9    7    B
0xC97B
```

C

```text
0xD5E4C
1101 0101 1110 0100 1100
```

D

```text
10 0110 1110 0111 1011 0101
 2    6    E    7    B    5
0x26E7B5
```

### 2.2

| n   | $2^n$ (dec) | $2^n$ (hex) |
| --- | ----------- | ----------- |
| 9   | 512         | 0x200       |
| 19  | 524288      | 0x80000     |
| 14  | 16384       | 0x4000      |
| 16  | 65536       | 0x10000     |
| 17  | 131072      | 0x20000     |
| 5   | 32          | 0x20        |
| 7   | 128         | 0x80        |

### 2.3

| dec | bin       | hex  |
| --- | --------- | ---- |
| 0   | 0000 0000 | 0x00 |
| 167 | 1010 0111 | 0xA7 |
| 62  | 0011 1110 | 0x3E |
| 188 | 1011 1100 | 0xBC |
| 55  | 0011 0111 | 0x37 |
| 136 | 1000 1000 | 0x88 |
| 243 | 1111 0011 | 0xF3 |
| 82  | 0101 0010 | 0x52 |
| 172 | 1010 1100 | 0xAC |
| 231 | 1110 0111 | 0xE7 |

### 2.4

A

$$
0x503C + 0x8 = 0x5044
$$

B

$$
0x503C - 0x40 = 0x4FFC
$$

C

$$
\begin{aligned}
    0x503C + 64 \\
    = 0x503C + 0x40 \\
    = 0x507C
\end{aligned}
$$

D

$$
0x50EA - 0x503C = 0xAE
$$

### 2.5

[related code](https://github.com/hanxifu/my-csapp/blob/master/chapter2/show_bytes.c)

0x 87 65 43 21

|     | little endian | big endian |
| --- | ------------- | ---------- |
| A   | 21            | 87         |
| B   | 21 43         | 87 65      |
| C   | 21 43 65      | 87 65 43   |

### 2.6

[related code](https://github.com/hanxifu/my-csapp/blob/master/chapter2/show_bytes.c)

```C
int    3510593   -> 0x00359141
float  3510593.0 -> 0x4A564504
```

A

1. 0000 0000 0011 0101 1001 0001 0100 0001
2. 0100 1010 0101 0110 0100 0101 0000 0100

B

```text
       1101011001000101000001
1001010010101100100010100000100
```

C

despite of the first signed bit, all bits are included in float

### 2.7

[related code](https://github.com/hanxifu/my-csapp/blob/master/chapter2/show_bytes.c)

61 62 63 64 65 66 (`strlen` does not contain 0x00 length)

### 2.8

| op     | result    |
| ------ | --------- |
| a      | 0110 1001 |
| b      | 0101 0101 |
| ~a     | 1001 0110 |
| ~b     | 1010 1010 |
| a & b  | 0100 0001 |
| a \| b | 0111 1101 |
| a ^ b  | 0011 1100 |

### 2.9

A

| color      | R   | G   | B   | ~RGB           |
| ---------- | --- | --- | --- | -------------- |
| black      | 0   | 0   | 0   | 111 white      |
| blue       | 0   | 0   | 1   | 110 yellow     |
| green      | 0   | 1   | 0   | 101 red-purple |
| blue-green | 0   | 1   | 1   | 100 red        |
| red        | 1   | 0   | 0   | 011 blue-green |
| red-purple | 1   | 0   | 1   | 010 green      |
| yellow     | 1   | 1   | 0   | 001 blue       |
| white      | 1   | 1   | 1   | 000 black      |

B

blue | green = 001 | 010 = 011

yellow & green = 110 & 010 = 010

red ^ red-purple = 100 ^ 101 = 001

### 2.10

| step | *x  | *y    |
| ---- | --- | ----- |
| init | a   | b     |
| 1    | a   | a ^ b |
| 2    | b   | a ^ b |
| 3    | b   | a     |

### 2.11

[related code](https://github.com/hanxifu/my-csapp/blob/master/chapter2/reverse_array_inplace.c)

A

k, k

B

mid = mid ^ mid = 0

C

change <= to <

### 2.12 
 
A

x & 0xFF

B

x ^ ~0xFF

C

x | 0xFF

### 2.13

bis -> |

bic -> &~

x ^ y = (x & ~y) | (~x & y)

```c
int bool_or(int x, int y) {
    int result = bis(x, y);
    return result;
}

int bool_xor(int x, int y) {
    int result = bis(bic(x, y), bic(y, x));
    return result;
}
```

### 2.14

x = 0x66 = 0110 0110

y = 0x39 = 0011 1001

| exp        | val       | hex  |
| ---------- | --------- | ---- |
| x & y      | 0010 0000 | 0x20 |
| x \| y     | 0111 1111 | 0x7F |
| ~x \| ~y   | 1101 1111 | 0xDF |
| x & !y     | 0000 0000 | 0x00 |
| x && y     | 0000 0001 | 0x01 |
| x \|\| y   | 0000 0001 | 0x01 |
| !x \|\| !y | 0000 0000 | 0x00 |
| x && ~y    | 0000 0001 | 0x01 |

### 2.15

```c
return !(x ^ y);
```

### 2.16

| x                | x << 3           | x >> 2 (logical) | x >> 2 (Arithmetic) |
| ---------------- | ---------------- | ---------------- | ------------------- |
| 0xC3 (1100 0011) | (0001 1000) 0x18 | (0011 0000) 0x30 | (1111 0000) 0xF0    |
| 0x75 (0111 0101) | (1010 1000) 0xA8 | (0001 1101) 0x1D | (0001 1101) 0x1D    |
| 0x87 (1000 0111) | (0011 1000) 0x38 | (0010 0001) 0x21 | (1110 0001) 0xE1    |
| 0x66 (0110 0110) | (0011 0000) 0x30 | (0001 1001) 0x19 | (0001 1001) 0x19    |

### 2.17

| hex | bin  | $B2U_4$            | $B2T_4$             |
| --- | ---- | ------------------ | ------------------- |
| 0xE | 1110 | 8 + 4 + 2 = 14     | -8 + 4 + 2 = -2     |
| 0x0 | 0000 | 0                  | 0                   |
| 0x5 | 0101 | 4 + 1 = 5          | 4 + 1 = 5           |
| 0x8 | 1000 | 8                  | -8                  |
| 0xD | 1101 | 8 + 4 + 1 = 13     | -8 + 4 + 1 = -3     |
| 0xF | 1111 | 8 + 4 + 2 + 1 = 15 | -8 + 4 + 2 + 1 = -1 |

### 2.18

|     | hex   | dec                                       |
| --- | ----- | ----------------------------------------- |
| A   | 0x2e0 | $2^9 + 2^7 + 2^6 + 2^5 = 736$             |
| B   | -0x58 | $-(2^6 + 2^4 + 2^3) = -88$                |
| C   | 0x28  | $2^5 + 2^3 = 40$                          |
| D   | -0x30 | $-(2^5 + 2^4) = -48$                      |
| E   | 0x78  | $2^6 + 2^5 + 2^4 + 2^3 = 120$             |
| F   | 0x88  | $2^7 + 2^3 = 136$                         |
| G   | 0x1f8 | $2^8 + 2^7 + 2^6 + 2^5 + 2^4 + 2^3 = 504$ |
| H   | 0xc0  | $2^7 + 2^6 = 192$                         |
| I   | -0x48 | $-(2^6 + 2^3) = -72$                      |

### 2.19

| x   | $T2U_4(x)$ |
| --- | ---------- |
| -8  | 8          |
| -3  | 13         |
| -2  | 14         |
| -1  | 15         |
| 0   | 0          |
| 5   | 5          |

### 2.20

| x   | $T2U_4(x)$ | steps           |
| --- | ---------- | --------------- |
| -8  | 8          | $-8 + 2^4 = 8$  |
| -2  | 14         | $-2 + 2^4 = 14$ |
| -1  | 15         | $-1 + 2^4 = 15$ |
| 0   | 0          | 0               |
| 5   | 5          | 5               |

### 2.21

| exp                            | type     | val | steps                                                             |
| ------------------------------ | -------- | --- | ----------------------------------------------------------------- |
| -2147483647 - 1 == 2147483648U | unsigned | 1   | $T2U_{32}(-2^{31}) = 2^{31}$                                      |
| -2147483647 - 1 < 2147483647   | signed   | 1   | will not overflow                                                 |
| -2147483647 - 1U < 2147483647  | unsigned | 0   | $T2U_{32}(-2^{31}) = 2^{31}$ > $2^{31} -1$                        |
| -2147483647 - 1 < -2147483647  | signed   | 1   | will not overflow                                                 |
| -2147483647 - 1U < -2147483647 | unsigned | 1   | $T2U_{32}(-2^{31}) = 2^{31}$ $T2U_{32}(-2^{31} + 1) = 2^{31} + 1$ |

### 2.22

| bin    | $B2T_w$                           |
| ------ | --------------------------------- |
| 1011   | -2^3 + 2^1 + 2^0 = -5             |
| 11011  | -2^4 + 2^3 + 2^1 + 2^0 = -5       |
| 111011 | -2^5 + 2^4 + 2^3 + 2^1 + 2^0 = -5 |

### 2.23

| w          | $fun1(w)$  | $fun2(w)$  |
| ---------- | ---------- | ---------- |
| 0x00000076 | 0x00000076 | 0x00000076 |
| 0x87654321 | 0x00000021 | 0x00000021 |
| 0x000000C9 | 0x000000C9 | 0xFFFFFFC9 |
| 0xEDCBA987 | 0x00000087 | 0xFFFFFF87 |

### 2.24

| origin(hex) | cutoff(hex) | origin(unsigned) | cutoff(unsigned) | T   | cutoff(T)                  |
| ----------- | ----------- | ---------------- | ---------------- | --- | -------------------------- |
| 0           | 0           | 0                | 0                | 0   | 0 < $TMax_3$ 0             |
| 2           | 2           | 2                | 2                | 2   | 2 < $TMax_3$ 2             |
| 9           | 1           | 9                | 1                | -7  | -7 < $TMin_3$ -7 + 2^3 = 1 |
| B           | 3           | 11               | 3                | -5  | -5 < $TMin_3$ -5 + 2^3 = 3 |
| F           | 7           | 15               | 7                | -1  | -1 < $TMax_3$ -1           |

### 2.25

[related code](https://github.com/hanxifu/my-csapp/blob/master/chapter2/length.c)

1. (unsigned)0 - 1 = 4294967295
2. (unsigned)i <= 4294967295 (always true)
3. access a[...]

### 2.26

[related code](https://github.com/hanxifu/my-csapp/blob/master/chapter2/strlonger.c)

A. when strlen(s) < strlen(t), the result will be mistaken.

B. (unsigned)0 - (unsigned)1 = 4294967295 > 0, so it will always return 1.

C. Change to `return strlen(s) > strlen(t);`

### 2.27

[related code](https://github.com/hanxifu/my-csapp/blob/master/chapter2/uadd_ok.c)

### 2.28

| x(hex) | x(dec) | $-{^u_4}x$(hex) | $-{^u_4}x$(dec) |
| ------ | ------ | --------------- | --------------- |
| 0      | 0      | 0               | 0               |
| 5      | 5      | B               | 11              |
| 8      | 8      | 8               | 8               |
| D      | 13     | 3               | 3               |
| F      | 15     | 1               | 1               |

### 2.29

| x     | y     | x+y    | $x+{^t_5}(y)$ | cond         |
| ----- | ----- | ------ | ------------- | ------------ |
| 10100 | 10001 | 100101 | 00101         | neg overflow |
| 11000 | 11000 | 110000 | 10000         | neg overflow |
| 10111 | 01000 | 11111  | 11111         | neg normal   |
| 00010 | 00101 | 00111  | 00111         | pos normal   |
| 01100 | 00100 | 010000 | 10000         | pos overflow |

### 2.30

[related code](https://github.com/hanxifu/my-csapp/blob/master/chapter2/tadd_ok.c)

### 2.31

[related code](https://github.com/hanxifu/my-csapp/blob/master/chapter2/tadd_ok.c)

### 2.32

[related code](https://github.com/hanxifu/my-csapp/blob/master/chapter2/tadd_ok.c)

TO BE CONTINUED...
