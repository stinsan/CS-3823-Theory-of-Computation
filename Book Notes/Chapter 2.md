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

_δ (q<sub>0</sub>, a) = q<sub>1</sub>,_

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

## 2.2 | Nondeterministic Finite Accepters
### Definition of a Nondeterministic Accepter

A **nondeterministic finite accepter (NFA)** is defined by the quintuple

_M = (Q, Σ, δ, q<sub>0</sub>, F)_,

where _Q, Σ, q<sub>0</sub>, F_ are defined as for DFAs, but

_δ : Q × (Σ ∪ {λ}) → 2<sup>Q</sup>_.

**Three major differences between NFAs and DFAs**:
1. If, for instance, the current state is _q<sub>1</sub>_, the symbol _a_ is read, and _δ (q<sub>1</sub>, a) = {q<sub>0</sub>, q<sub>2</sub>}_ , then either _q<sub>0</sub>_ or _q<sub>2</sub>_ could be the next state of the NFA.
2. We allow _λ_ as the second argument of _δ_. This means that the nfa can make a transition without consuming an input symbol. Although we still assume that the input mechanism can only travel to the right, it is possible that it is stationary on some moves.
3. Finally, the set _δ (q<sub>i</sub> , a)_ may be empty, meaning that there is no transition defined for this specific situation.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-6.png)

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-7.png)

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-8.png)

For an NFA, the **extended transition function** is defined so that _δ* (q<sub>i</sub> , w)_
contains _q<sub>j</sub>_ if and only if there is a walk in the transition graph from _q<sub>i</sub>_ to
_q<sub>j</sub>_ labeled _w_. This holds for all _q<sub>i</sub>_ , _q<sub>j</sub> ∈ Q_, and _w ∈ Σ*_. 

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-9.png)

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-10.png)

The language _L_ accepted by an NFA _M = (Q, Σ, δ, q<sub>0</sub> , F)_ is defined as the
set of all strings accepted in the above sense. Formally,

_L(M) = {w ∈ Σ* : δ* (q<sub>0</sub> , w) ∩ F = ∅}_.

In words, the language consists of all strings _w_ for which there is a walk
labeled _w_ from the initial vertex of the transition graph to some final vertex.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-11.png)

## 2.3 | Equivalence of Deterministic and Nondeterministic Finite Accepters

Two finite accepters, M<sub>1</sub> and M<sub>2</sub>, are said to be **equivalent** if

_L(M<sub>1</sub>) = L(M<sub>2</sub>)_

that is, if they both accept the same language.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-12.png)

For every DFA, there is an equivalent NFA. For every NFA, there is an equivalent DFA.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-13.png)

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-14.png)

**Procedure to Convert NFA to DFA (Theorem 2.2)**:
1. Create a graph _G<sub>D</sub>_ with vertex {_q0_}. Identify this vertex as the initial vertex. <br/>
2. Repeat the following steps until no more edges are missing. <br/>
Take any vertex {_qi, qj, ..., qk}_ of _G<sub>D</sub>_ that has no outgoing edge for some _a_ ∈ _Σ_. <br/>
Compute δ*<sub>N</sub> (_qi, a_),  δ*<sub>N</sub> (_qj, a_), ...,  δ*<sub>N</sub> (_qk, a_). <br/>
If <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; δ*<sub>N</sub> (_qi, a_) ∪ δ*<sub>N</sub> (_qj, a_) ∪ ... ∪ δ*<sub>N</sub> (_qk, a_) = {_ql, qm, ..., qn_},<br/>
create a vertex for _G<sub>D</sub>_ labeled {_ql, qm, ..., qn_} if it does not already exist. <br/>
Add _G<sub>D</sub>_ an edge from {_qi, qj, ..., qk_} to {_ql, qm, ..., qn_} and label it with _a_.<br/>
3. Every state of _G<sub>D</sub>_ whose label contains any _qf_ ∈ _F<sub>N</sub>_ is identified as a
final vertex.<br/>
4. If _M<sub>N</sub>_ accepts λ, the vertex {_q0_} in _G<sub>D</sub>_ is also made a final vertex.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-15.png)
![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-16.png)
![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-17.png)

