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

## 2.4 | Reduction of the Number of States in Finite Automata
![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-18.png)

Two states _p_ and _q_ of a DFA are called **indistinguishable** if <br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; _δ* (p, w) ∈ F_ implies _δ* (q, w) ∈ F_, and _δ* (p, w) ∉ F_ implies _δ* (q, w) ∉ F_, <br/>
<br/>
for all _w ∈ Σ*_. If, on the other hand, there exists some string _w ∈ Σ*_ such that<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;_δ* (p, w) ∈ F_ and _δ* (q, w) ∉ F_,<br/>
<br/>
or vice versa, the the states _p_ and _q_ are said to be **distinguishable** by a string _w_.

One method for reducing the states of a dfa is based on finding and
combining indistinguishable states. We first describe a method for finding
pairs of distinguishable states.

**Finding Pairs of Distinguishable States**:
1. Remove all inaccessible states. This can be done by enumerating all simpel paths of the graph of the DFA starting at the initial state. Any state not part of some path is inaccessible.
2. Consider all pairs of states (_p, q_).  If p ∈ F and q ∉ F or vice versa, mark the pair (_p, q_) as distinguishable.
3. Repeat the following step until no previously unmarked pairs are marked.
For all pairs (_p, q_) and all _a ∈ Σ_, </br> compute _δ (p, a) = p<sub>a</sub>_ and _δ (q, a) = q<sub>a</sub>_.
If the pair (_p<sub>a</sub>_, _q<sub>a</sub>_) is marked as distinguishable, mark (_p, q_) as distinguishable.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-19.png)

Once the indistinguishability classes are found, the construction of the
minimal dfa is straightforward.

**Construction of the Minimal DFA**:

Given a DFA _M = (Q, Σ, δ, q<sub>0</sub>, F)_, we construct a reduced DFA _M' = (Q', Σ, δ', q<sub>0</sub>', F')_
as follows.

1. Find pairs of distinguishable states to generate the equivalence classes, say {_q<sub>i</sub>, q<sub>j</sub> , ..., q<sub>k</sub>_},
as described.
2. For each set {_q<sub>i</sub>, q<sub>j</sub> , ..., q<sub>k</sub>_} of such indistinguishable states, create a state
labeled _ij...k_ for _M'_.
3. For each transition rule of _M_ of the form _δ (q<sub>r</sub>, a) = q<sub>p</sub>_, find the sets to which _q<sub>r</sub>_ and _q<sub>p</sub>_ belong. If If _q<sub>r</sub> ∈ {q<sub>i</sub>, q<sub>j</sub> , ..., q<sub>k</sub>}_ and _q<sub>p</sub> ∈ {q<sub>l</sub>, q<sub>m</sub> , ..., q<sub>n</sub>}_, add to δ' a rule _δ'(ij...k, a) = lm...n_.
4. The initial state _q<sub>0</sub>'_ is that state of _M'_ whose label includes the 0.
5. _F'_ is the set of all the states whose label contains _i_ such that _q<sub>i</sub> ∈ F_.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-20.png)
