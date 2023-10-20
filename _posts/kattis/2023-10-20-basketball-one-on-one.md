---
title: 'Kattis: Basketball One-on-One'
categories:
  - kattis
tags:
  - kattis 
toc: true
toc_sticky: true
use_math: true
# datatable: true
---

# Basketball One-on-One

## Problem

Alice and Barbara played some friendly games of one-on-one basketball after work, and we agreed to help them keep score.

1. Each successful shot by a player earns them either one or two points;
2. The first player to eleven points wins, with one exception;
3. If the score is tied $10-10$, the previous rule is replaced by a “win by 2” rule: the first player to lead the other by at least two points wins.[^1]

## Input
The input consists of a single line with no more than characters: the record of one game. The record consists of single letters (either A or B) alternating with single numbers (either 1 or 2).

An example output could be 

### Sample Input 1
```bash
A2B1A2B2A1A2A2A2
```

### Sample Output 1
```bash
A
```

### Sample Input 2
```bash
A2B2A1B2A2B1A2B2A1B2A1A1B1A1A2
```

### Sample Output 2
```bash
A
```


## Footnotes
[^1]: Rules taken from https://open.kattis.com/problems/basketballoneonone