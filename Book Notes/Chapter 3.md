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

## 3.2 | Connection Between Regular Expressions and Regular Languages
### Regular Expressions Denote Regular Languages
We now show that if we have any regular expression _r_, we can construct an nfa that accepts _L(r)_. The construction
for this relies on the recursive definition for _L(r)_ in the previous section. The figures below show an nfa for all 7 rules of the defintion for _L(r)_:

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-28.png)
![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-29.png)
![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-30.png)

### Regular Expressions for Regular Languages
A **generalized transition graph (GTG)** is a transition graph whose edges are labels with regular expressions. The label of any walk from the intial state to the final state is a concatenation of several regular expressions, and is thus a regular expression itself. The strings denoted by such regular expressions are a subset of the language accepted by the generalized transition graph, with the full
language being the union of all such generated subsets.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-31.png)

Equivalence for generalized transition graphs is defined in terms of the
language accepted and the purpose of the next bit of discussion is to produce
a sequence of increasingly simple GTGs. In this, we will find it convenient to work with complete GTGs.
A complete GTG is a graph in which all edges are present. If a GTG, after conversion from an NFA, has some edges
missing, we put them in and label them with ∅. A complete GTG with _|V |_
vertices has exactly _|V |<sup>2</sup>_ edges.
When a GTG has more than two states, we can find an equivalent graph
by removing one state at a time until two states are left.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-32.png)
![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-33.png)

These are the formal steps for turning a DFA to a regular expression (REX):

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-34.png)
![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-35.png)

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-36.png)
![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-37.png)

### Regular Expressions for Describing Simple Patterns

The relation between finite automata and regular expressions means that we can
also use regular expressions as a way of describing simple constituents of programming languages, such as identifiers, integers,
and real numbers.  
- For example, in many programming languages the set of integer constants is defined by the regular expression _sdd*_, where _s_ stands for the sign, with possible values from {+, −, λ}, and _d_ stands for the digits 0 to 9.

## 3.3 | Regular Grammars
A third way of describing regular languages is by means of certain grammars.

### Right-Linear and Left-Linear Grammars
A grammar _G = (V, T, S, P)_ is said to be **right-linear** if all productions are of the form

_A → xB_,<br/>
_A → x_,

where _A, B_ ∈ _V_ , and _X_ ∈ _T*_. 

A grammar is **left-linear** if all productions are of the form

_A → Bx_,<br/>
_A → x_.

A **regular grammar** is one that is either left or right-linear.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-38.png)
![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-39.png)

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-40.png)
