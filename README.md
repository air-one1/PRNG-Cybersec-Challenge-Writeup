# PRNG-Cybersec-Challenge-Writeup
Writeup for a Pseudo Random Number Generator (PRNG) cybersecurity challenge. Demonstrates file encryption using a pseudo-random key and XOR operation. Explore PRNG security vulnerabilities.

## Challenge Objective

The objective of this challenge is to explore and analyze the security implications of using PRNGs for cryptographic purposes.
We have a C program for buffer encryption.

## Key Generation

The program utilizes a Linear Congruential Generator (LCG) to generate a sequence of PRNs. It defined by:

$X_{n+1} := a \cdot X_n + c \mod m$

$X_n$  is the current state of the generator, $X_{n+1}$ the next one.
$a$ , $c$ , and  $m$  are constants. Initial value,  $X_0$ , is set based on  $time(NULL)$  value.

## Buffer Encryption

$\forall  E_i$  in a sequence and its corresponding element  $K_i$  in the key sequence, the XOR operation is performed:

$C_i = E_i \oplus K_i$

If the end of the key sequence is reached, it starts again from the beginning.

## File Encryption

The program reads the file in blocks. Each block is encrypted using the XOR operation with the corresponding elements from the key sequence. Mathematically, if $B$ represents a block from the file and  $K$  is the encryption key, then the encrypted block  $C$  is calculated as:

$C = B \oplus K$

This operation is repeated for each block of the file.

## Important Note

All operations (LCG and XOR) are performed on integers, typically 8-bit bytes. The result of an XOR operation between two elements is also an element of the same size.
