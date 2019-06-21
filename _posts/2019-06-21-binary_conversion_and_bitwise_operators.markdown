---
layout: post
title:      "Binary Conversion and Bitwise Operators"
date:       2019-06-21 00:48:11 -0400
permalink:  binary_conversion_and_bitwise_operators
---


Bitwise operators and binary conversion is a topic that may come up in CS algorithms and problem solving. 

The binary number system represents each number with 2 symbols (0 and 1) where the decimal system represents them with 10 symbols (0-9). Binary numbers are also referred to as base-2 or with a radix of 2, where decimal numbers have a base or radix of 10.

In javascript, you can use the following functions to convert binary numbers to decimal and decimal numbers to binary

`parseInt(‘10001’, 2)` -> 10001 to decimal, second argument reads number or string in that radix (2)

`Number(8).toString(2)` -> 8 to binary, returns string, 8 can be as string or integer

However, these methods will not work for unsigned binary numbers representing negative values.

To further understand how the conversions are made, the following will explain each number is derived.

To convert a number from decimal to binary:
* Divide number by 2 -> result is quotient, and remainder (0 or 1)
* Continue dividing quotient by 2 until reaching 0 quotient
* Concatenate all remainders from most significant(last remainder) to least significant(first remainder)

Ex. 13 to binary
```
13/2 = 6 remainder 1 (first, least significant)
 -> 6/2 = 3 remainder 0 
   -> 3/2 = 1 remainder 1 
      -> 1/2 = 0 remainder 1 (last, most significant)
13 (base10) = 1101 (base2)
```

To convert a number from binary to decimal:
* For each bit bi (0 or 1), sum (bi x 2^i) 
* start from least significant (last) bit  as i=0

Ex. 1101 to decimal
```
i=0 ->   b0=1, 2^0=1   ->   1*1 = 1
i=1 ->   b1=0, 2^1=2    ->   0*2 = 0
i=2 ->   b2=1, 2^2=4    ->   1*4 = 4
i=3 ->   b3=1, 2^3=8    ->   1*8 = 5

Sum terms -> 1 + 0 + 4 + 8 = 13 
1101(base2) = 13 (base10)
``` 

Bitwise logical operators work slightly similarly to boolean operators to combine binary numbers. They compare numbers bit by bit, and builds the result from each comparison.

* Bitwise and (`&`)
All pairs result in 0, except 1 and 1 -> `101 & 100` = 100
* Bitwise or ( `| `)
All pairs result in 1, except 0 and 0 -> `0101 | 0110` = 0111
* Bitwise xor (`^`)
Pairs that are different result in 1. 0 with 0 and 1 with 1 result in 0 -> 0101 ^ 0110 = 0011
* Bitwise not (`~`)
Inverts value -> ~101 = 010
