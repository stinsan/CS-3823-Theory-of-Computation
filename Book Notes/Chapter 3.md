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

### Languages Associated with Regular Expressions
Regular expressions can be used to describe some simple languages. If _r_ is a regular expression, we will let _L(r)_ denote the language
associated with _r_.

The language _L(r)_ denoted by any regular expression _r_ is defined by the following rules:
1. ∅ is a regular expression denoting the empty set.
2. λ is a regular expression denoting {λ}.
3. For every _a_ ∈ Σ, _a_ is a regular expression denoting {_a_}.
4. _L(r1 + r2)_ = _L(r1)_ ∪ _L(r2)_
5. _L(r1 · r2)_ = _L(r1)L(r2)_
6. _L((r1))_ = _L(r1)_
7. _L(r1*)_ = _(L(r1))*_

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-23.png)

We establish a set of precedence rules for evaluation in which star-closure precedes concatenation and concatenation
precedes union. Also, the symbol for concatenation may be omitted, so we can write _r1r2_ for _r1 · r2_.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-24.png)
![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-25.png)
![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-26.png)
![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-27.png)

The last example introduces the notion of equivalence of regular expressions. We say the two regular expressions are **equivalent** if they denote the same language.
