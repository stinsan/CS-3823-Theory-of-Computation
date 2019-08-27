# Chapter 1.2: Three Basic Concepts
### Languages

An **alphabet** is any finite set of symbols. 
- Σ = {a, b, c}

A **string (or word)** over Σ is any sequence of symbols from Σ.
- w = abb

The **length** of a string w is denoted by |w|.
- |abb| = 3

The **empty string** (of length zero) is denoted by ε.

A **substring** of a string x is any string of consecutive symbols in x.

If w is a string, and v and u are substrings of w such that w = vu, then v is a **prefix** and u is a **suffix**.

**Concatenation** of strings x and y is to place the two strings after one another.
- abb · bb = abbbb
- Note that x · ε = ε · x = x ∀ x
- For any integer i ≥ 0, x<sup>i</sup> = i copies of x concatenated
- Note that x<sup>0</sup> = ε

A **language** is any set of strings over an alphabet.

There are **finite languages**:
- ∅ (empty language)
- {ε}
- {a, bb}

and **infinite languages**:
- {a<sup>n</sup>b<sup>n</sup> | n ≥ 0}

