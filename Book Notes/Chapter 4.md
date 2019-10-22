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
