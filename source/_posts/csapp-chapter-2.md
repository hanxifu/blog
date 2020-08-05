---
title: csapp-chapter-2
date: 2020-08-01 21:19:28
tags: [CSAPP]
---

# Chapter 2

<!-- TOC -->

- [Chapter 2](#chapter-2)
  - [Concepts](#concepts)
  - [Excercises](#excercises)
    - [2.1](#21)
    - [2.2](#22)
    - [2.3](#23)
    - [2.4](#24)
    - [2.5](#25)
    - [2.6](#26)
    - [2.7](#27)
    - [2.8](#28)
    - [2.9](#29)
    - [2.10](#210)
    - [2.11](#211)
    - [2.12](#212)
    - [2.13](#213)
    - [2.14](#214)
    - [2.15](#215)
    - [2.16](#216)

<!-- /TOC -->

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

To Be Continued...