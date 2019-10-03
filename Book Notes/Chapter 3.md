# Chapter 3 | Regular Languages and Regular Grammars
## 3.1 | Regular Expressions

**Regular expressions** a way of describing regular languages using a combination of strings and symbols from some alphabet Σ, parentheses,
and the operators +, ·, and *.
- The language {a} is denoted by the regular expression _a_.
- The language {a, b, c} has the regular expression _a + b + c_, with "+" denoting union.
- The expression _(a + (b · c))*_ stands for the star closure of {a} ∪ {bc}, that is, the language<br/> 
{ λ, a, bc, aa, abc, bca, bcbc, aaa, aabc, ... }.
