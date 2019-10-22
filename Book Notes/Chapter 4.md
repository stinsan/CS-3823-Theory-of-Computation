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

Suppose _Σ_ and _Γ_ are alphabets. Then a function _h : Σ → Γ∗_ is called a **homomorphism**. In words, a homomorphism is a substitution
in which a single letter is replaced with a string.

The domain of the function _h_ is extended to strings; if _w = a<sub>1</sub> a<sub>2</sub> ··· a<sub>n</sub>_ ,
then _h (w) = h (a<sub>1</sub>) h (a<sub>2</sub>)··· h (a<sub>n</sub>)_. 

If _L_ is a language on _Σ_, then its **homomorphic image** is defined as
_h (L) = {h (w) : w ∈ L}_.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-44.png)
