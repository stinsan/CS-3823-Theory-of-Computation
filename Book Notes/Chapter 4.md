# Chapter 4: Properties of Regular Languages
## 4.1 | Closure Properties of Regular Languages
Consider the following question: Given two regular languages _L1_ and _L2_, is
their union also regular? ? It turns out that the answer is yes, a fact we express by saying
that the family of regular languages is **closed** under union. 

### Closure Under Simple Set Operations
If _L<sub>1</sub>_ and _L<sub>2</sub>_ are regular languages, then so are _L<sub>1</sub> ∪ L<sub>2</sub> , L<sub>1</sub> ∩ L<sub>2</sub> , L<sub>1</sub>L<sub>2</sub> , L<sub>1</sub>', and L∗_. We say that the family of regular languages is closed under union,
intersection, concatenation, complementation, and star-closure.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-43.png)

The family of regular languages is closed under reversal. (reversing the direction of all edges)

### Closure Under Other Operations

#### Homomorphism
Suppose _Σ_ and _Γ_ are alphabets. Then a function _h : Σ → Γ∗_ is called a **homomorphism**. In words, a homomorphism is a substitution
in which a single letter is replaced with a string.

The domain of the function _h_ is extended to strings; if _w = a<sub>1</sub> a<sub>2</sub> ··· a<sub>n</sub>_ ,
then _h (w) = h (a<sub>1</sub>) h (a<sub>2</sub>)··· h (a<sub>n</sub>)_. 

If _L_ is a language on _Σ_, then its **homomorphic image** is defined as
_h (L) = {h (w) : w ∈ L}_.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-44.png)

If we have a regular expression _r_ for a language _L_, then a regular expression for _h (L)_ can be obtained by simply applying the homomorphism to each _Σ_ symbol of _r_.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-45.png)

Regular languages are closed under homomorphism.

#### Right Quotient
Let _L1_ and _L2_ be languages on the same alphabet. Then the **right quotient**
of _L1_ with _L2_ is defined as _L1/L2 = {x : xy ∈ L1_ for some _y ∈ L2}_.

To form the right quotient of _L1_ with _L2_, we take all the strings in _L1_
that have a suffix belonging to _L2_.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-46.png)
![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-47.png)

If _L1_ and _L2_ are regular languages, then _L1/L2_ is also regular. We say that
the family of regular languages is closed under right quotient with a regular
language.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-48.png)
![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-49.png)

## 4.2 | Elementary Questions about Regular Languages
Given a language _L_ and a string _w_, can we determine whether or not _w_ is an element of _L_? This is the
**membership question** and a method for answering it is called a membership algorithm.

A regular language is given in a **standard representation** if and only if it is described by a finite automaton,
a regular expression, or a regular grammar. These are the only representations that are useful in theorems.

### Theorem 4.5
Given a standard representation of any regular language _L_ on _Σ_ and any
_w ∈ Σ∗_, there exists an algorithm for determining whether or not _w_ is in _L_.

**Proof**: Construct a DFA for _L_, and see whether or not _w_ is accepted.

### Theorem 4.6
There exists an algorithm for determining whether a regular language _L_, given
in standard representation, is empty, finite, or infinite.

**Proof**: Construct a DFA for _L_. If there is a path from the initial state to a final state, then the language is not empty.
To determine whether or not a language is infinite, find all the vertices
that are the base of some cycle. If any of these are on a path from an initial
to a final vertex, the language is infinite. Otherwise, it is finite.

### Theorem 4.7
Given standard representations of two regular languages _L1_ and _L2_, there
exists an algorithm to determine whether or not _L1 = L2_.

**Proof**: We define the language _L3 = (L1 ∩ L2') ∪ (L1' ∩ L2)_.
By closure, _L3_is regular, and we can find a DFA _M_ that accepts _L3_. Once
we have _M_, we can then use the algorithm in Theorem 4.6 to determine if
_L3_ is empty. We see that _L3 = ∅_ if and only if _L1 = L2_ (exercise 8, section 1.1).

## 4.3 | Identifying Nonregular Languages
### Using the Pigeonhole Principle
