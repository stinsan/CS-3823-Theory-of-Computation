# Chapter 2: Finite Automata
## 2.1 | Deterministic Finite Accepters
### Deterministic Accepters and Transition Graphs

A **deterministic finite accepter (dfa)** is defined by the quintuple

_M = (Q, Σ, δ, q<sub>0</sub>, F)_,

where:

- *Q* is a finite set of **internal states**
- *Σ* is a finite set of symbols called the **input alphabet**
- *δ: Q × Σ → Q* is a total function called the **transition function**
- *q<sub>0</sub>* ∈ Q is the **initial state**
- *F ⊆ Q* is a set of **final states**

**How does a dfa work?**
- At the initial time, it is assumed to be in the initial state q<sub>0</sub>, with its input
mechanism on the leftmost symbol of the input string.
- Each move of the automaton consumes one input symbol and advances the input mechanism one space to the right.
- When the end of the string is reached, the string is accepted if the automaton is in one of its final states.
Otherwise the string is rejected.
- The transitions from one internal state to another are governed by the transition function δ.

**The Transition Function**:

For example, if

_δ (q<sub>0</sub>, a) = q1,_

then if the dfa is in state _q<sub>0</sub>_ and the current input symbol is _a_, the dfa will go into state _q<sub>1</sub>_.

**Transition Graphs**: used to visualize and represent finite automata where the vertices represent states and the edges
represent transitions

> More formally, if _M_ is a deterministic finite accepter,
then its associated transition graph _G<sub>M</sub>_ has exactly _|Q|_ vertices, each one
labeled with a different _q<sub>i</sub> ∈ Q_. For every transition rule _δ(q<sub>i</sub>, a) = q<sub>j</sub>_, the
graph has an edge (_q<sub>i</sub>, q<sub>j</sub>_) labeled _a_. The vertex associated with _q<sub>0</sub>_ is called
the **initial vertex**, while those labeled with _q<sub>f</sub> ∈ F_ are the **final vertices**.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-0.png)

### Languages and Deterministic Finite Accepters
**Language**: the language accepted by a dfa _M = (Q, Σ, δ, q<sub>0</sub>, F)_ is the set of all strings
on _Σ_ accepted by _M_. 

In formal notation, 

_L(M) = {w ∈ Σ* : δ* (q<sub>0</sub>, w) ∈ F}_.

From this, we can define non-acceptance as

_L'(M) = {w ∈ Σ*: δ* (q<sub>0</sub>, w) ∉ F}_

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-1.png)

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-2.png)

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-3.png)

### Regular Languages

Every finite automaton accepts some language. If we consider all possible
finite automata, we get a set of languages associated with them. We will call
such a set of languages a **family**.

A language _L_ is called **regular** if and only if there exists some deterministic
finite accepter _M_ such that _L = L(M)_.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-4.png)

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-5.png)

# 2.2 | Nondeterministic Finite Accepters
