# Chapter 3 | Regular Languages and Regular Grammars
## 3.1 | Regular Expressions

**Regular expressions** a way of describing regular languages using a combination of strings and symbols from some alphabet Σ, parentheses,
and the operators +, ·, and *.
- The language {a} is denoted by the regular expression _a_.
- The language {a, b, c} has the regular expression _a + b + c_, with "+" denoting union.
- The expression _(a + (b · c))*_ stands for the star closure of {a} ∪ {bc}, that is, the language<br/> 
{ λ, a, bc, aa, abc, bca, bcbc, aaa, aabc, ... }.

### Formal Definition of a Regular Expression
Let Σ be a given alphabet. Then
1. ∅, λ, and _a_ ∈ Σ are all regular expressions. These are called **primitive regular expressions**.
2. If _r1_ and _r2_ are regular expressions, so are _r1 + r2_, _r1 · r2_, _r1*_, and _(r1)_.
3. A string is a regular expression if and only if it can be derived from the primitive regular expressions by a finite number of applications of the rules in (2).

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-21.png)
![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-22.png)
