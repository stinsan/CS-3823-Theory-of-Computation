# Chapter 5: Context Free Grammars
## 5.1 | Context-Free Grammars

A grammar _G_ = (_V, T, S, P_) is said to be **context-free** if all productions
in _P_ have the form <br> _A_ → _x_, where _A_ ∈ _V_ and _x_ ∈ (_V_ ∪ _T_)*.

A language _L_ is said to be context-free if and only if there is a context-free grammar _G_ such that _L_ = _L_(_G_).

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-59.png)

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-60.png)

Both of the above examples involve grammars that are not only contextfree, but linear. Regular and linear grammars are clearly context-free, but a context-free grammar is not necessarily linear.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-61.png)

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-62.png)

### Leftmost and Rightmost Derivations
In a grammar that is not linear, a derivation may involve sentential forms
with more than one variable. In such cases, we have a choice in the
order in which variables are replaced.

A derivation is said to be **leftmost** if in each step the leftmost variable
in the sentential form is replaced. If in each step the rightmost variable is
replaced, we call the derivation **rightmost**.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-63.png)

### Derivation Trees
A **derivation tree** is an ordered tree in which nodes are labeled with the left sides of productions
and in which the children of a node represent its corresponding right sides.
For example, Figure 5.1 shows part of a derivation tree representing the
production _A_ → _abABc_.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-64.png)

Here is the more formal defininition:
#### Definition 5.3
Let _G_ = (_V, T, S, P_) be a context-free grammar. An ordered tree is a
derivation tree for _G_ if and only if it has the following properties:
1. The root is labeled _S_.
2. Every leaf has a label from _T_ ∪ {_λ_}.
3. Every interior vertex has a label from _V_.
4. If a vertex has label _A_ ∈ _V_, and its children are labeled (from left to right) _a<sub>1</sub>, a<sub>2</sub>, ..., a<sub>n</sub>_, then _P_ must contain a production of the form _A_ → _a<sub>1</sub> a<sub>2</sub> ··· a<sub>n</sub>_ .
5. A leaf labeled _λ_ has no siblings, that is, a vertex with a child labeled _λ_
can have no other children.

A tree that has properties 3, 4, and 5, but in which 1 does not necessarily
hold and in which property 2 is replaced by 2a. Every leaf has a label from _V_ ∪ _T_ ∪ {_λ_}, is said to be a
**partial derivation tree**.

The string of symbols obtained by reading the leaves of the tree from
left to right, omitting any λ’s encountered, is said to be the **yield** of the tree.
