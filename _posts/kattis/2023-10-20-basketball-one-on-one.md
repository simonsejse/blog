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

# Problem Description

Alice and Barbara played some friendly games of one-on-one basketball after work, and we agreed to help them keep score.

1. Each successful shot by a player earns them either one or two points;
2. The first player to eleven points wins, with one exception;
3. If the score is tied $10-10$, the previous rule is replaced by a “win by 2” rule: the first player to lead the other by at least two points wins.[^1]

# Input Specification
The input consists of a single line with no more than characters: the record of one game. The record consists of single letters (either A or B) alternating with single numbers (either 1 or 2).


{: .text-center}
| Sample Input 1                          | Sample Output 1 |
|:---------------------------------------:|:---------------:|
| `A2B1A2B2A1A2A2A2`                        |        `A`        |
| `A2B2A1B2A2B1A2B2A1B2A1A1B1A1A2`          |        `A`        |

# Solution
A simple iterative approach where we just check each letter and see if it's A or B and increment the corresponding number.

## Complexity

### Runtime Complexity
Reading line from the standard input, `io::stdin().read_line(&mut input)`, requires $\mathbb{O}(n)$ time, furthermore, we iterative over each character in the input string `input` which also takes $\mathbb{O}(n)$ time, and last but not least, we have one comparison each loop which takes constant time, i.e., $\mathbb{O}(1)$ time.
- $\mathbb{O}(n) + \mathbb{O}(n) + \mathbb{O}(1) = \mathbb{O}(n)$

### Space Complexity
if string has $n$ characters the space requirements will be $\mathbb{O}(n)$. For two variables a and b, which both 16-bit integers, their space requirements are constant, i.e., $\mathbb{O}(1)$.
- $\mathbb{O}(n) + \mathbb{O}(1) + \mathbb{O}(1)=\mathbb{O}(n)$


## Code

### Imperative approach 
```rust
use std::io;

pub fn main() {
  let mut input: String = String::new();

  io::stdin().read_line(&mut input).expect("Failed to read line");

  let mut a:u16 = 0; 
  let mut b:u16 = 0; 

  for ch in input.chars() {
    if ch == 'A' {
      a += 1;
    }else if ch == 'B' {
      b += 1;
    }else {
      continue;
    }
  }
  if a > b {
    println!("A");
    return;
  }
  println!("B");
}
```

### Functional approach

```rust
use std::io;

pub fn main() {
  let mut input: String = String::new();

  io::stdin().read_line(&mut input).expect("Failed to read line");

  let (a, b) = input.chars().fold((0, 0), |(a, b), ch: char| {
    match ch {
        'A' => (a + 1, b),
        'B' => (a, b + 1),
        _ => (a, b),
    }
  });

  if a > b {
    println!("A");
    return;
  }
  println!("B");
}
```


## Footnotes
[^1]: Rules taken from https://open.kattis.com/problems/basketballoneonone