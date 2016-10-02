---
title: Knuth–Morris–Pratt Algorithm
tags: [KMP, Algorithms]
---

# General Idea #
The KMP Algorithm is first to build a "partial match" table `T` by KMP Table Building Algorithm, which indicates where we need to look for the start of a new match when the the current one ends in a mismatch. Then, we shall use the KMP Search Algorithm to find the the substring `W` in `S`.
# Table Building Algorithm #
First, we set `T[0] = -1`. Then we shall discover a proper suffix of `W[0..m-1]` which is also a prefix of `W`, the length of which is the value in the table `T`. In other words, `W[0..i] == W[m-i-1..m-1]` when the index equals to `m` and `m != i + 1`. In this case, `T[m] = i + 1`, if `i` does not exists, then `T[m] = 0`.
# Search Algorithm #
When `S[m + i]` is not equal to `W[i]`, we move the index `m` of `S` forward to `m + i - T[i]`, which is the next possible match according to the "partial match" table `T`. If all characters are match, then `W` is a substring of `S`, and there may be several substrings `W` in `S`.
