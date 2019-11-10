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

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-65.png)

### Relation Between Sentential Forms and Derivation Trees
#### Theorem 5.1
Let _G_ = (_V, T, S, P_) be a context-free grammar. Then for every _w_ ∈ L(_G_),
there exists a derivation tree of _G_ whose yield is _w_. Conversely, the yield of
any derivation tree is in L(_G_). . Also, if t<sub>G</sub> is any partial derivation tree for
_G_ whose root is labeled _S_, then the yield of t<sub>G</sub> is a sentential form of _G_.

## 5.2 | Parsing and Ambiguity
Given a string _w_ of terminals, we want to know whether or not _w_ is in L(_G_). If so, we may want to find a derivation of _w_. An
algorithm that can tell us whether _w_ is in L(_G_) is a membership algorithm.
The term **parsing** describes finding a sequence of productions by which a
_w_ ∈ L(_G_) is derived.

### Parsing and Membership
Given a string _w_ in L(_G_), we can parse it in a rather obvious fashion:
We systematically construct all possible (say, leftmost) derivations and see
whether any of them match _w_. 

Specifically, we start at round one by looking
at all productions of the form _S_ → _x_.  If none of these
results in a match with _w_, we go to the next round, in which we apply
all applicable productions to the leftmost variable of every _x_. We will call this **exhaustive search parsing** or
**brute force parsing**. It is a form of **top-down parsing**, which we can
view as the construction of a derivation tree from the root down.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-66.png)
![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-67.png)

Exhaustive search parsing is inefficient. Additionally, while the method always parses a _w_ ∈ L(_G_), it is possible that
it never terminates for strings not in L(_G_). This issue can be overcome if we don't have any productions of the form _A_ → λ as well as those of the form _A_ → _B_.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-68.png)

#### Theorem 5.2
Suppose that _G_ = (_V, T, S, P_) is a context-free grammar that does not have
any rules of the form
_A_ → λ, or _A_ → _B_,
where _A, B_ ∈ _V_ . Then the exhaustive search parsing method can be made
into an algorithm that, for any _w_ ∈ Σ∗, either produces a parsing of _w_ or
tells us that no parsing is possible.

Exhaustive searching is still limited in its practical use because of its inefficiency, though. In fact, the work for exhaustive search parsing may grow exponentially with the length of the string.

#### Theorem 5.3
For every context-free grammar there exists an algorithm that parses any
_w_ ∈ L(_G_) in a number of steps proportional to |_w_|<sup>3</sup>.

The book does not go into detail about this theorem, stating that "A method in which the work rises with the
third power of the length of the string, while better than an exponential
algorithm, is still quite inefficient."

What we would like to have is a parsing method that takes time proportional to
the length of the string. We refer to such a method as a **linear time parsing
algorithm**. We do not know any linear time parsing methods for contextfree languages in general, but such algorithms can be found for restricted, but important, special cases.

#### Definition 5.4
A context-free grammar _G_ = (_V, T, S, P_) is said to be a **simple grammar**
or **s-grammar** if all its productions are of the form
_A_ → _ax_,
where _A_ ∈ V , _a_ ∈ T, _x_ ∈ _V_∗, and any pair (_A, a_) occurs at most once in _P_.

If _G_ is an s-grammar, then any string _w_ in L(_G_) can be parsed with an
effort proportional to |_w_|.

### Ambiguity in Grammars and Languages
#### Definition 5.5
A context-free grammar _G_ is said to be ambiguous if there exists some _w_ ∈ L(_G_) that has at least two distinct derivation trees. Alternatively, ambiguity implies the existence of two or more leftmost or rightmost
derivations.
![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-69.png)

Ambiguity is a common feature of natural (spoken) languages, but in programming languages,
where there should be only one interpretation of each statement, ambiguity
must be removed when possible. We do so by rewriting the grammar in an equivalent, unambiguous form.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-70.png)

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-71.png)
![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-72.png)

One way to resolve the ambiguity is to rewrite the grammar so that only one
parsing is possible.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-73.png)
![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-74.png)

#### Definition 5.6
If _L_ is a context-free language for which there exists an unambiguous grammar, then _L_ is said to be unambiguous. If every grammar that generates _L_ is ambiguous, then the language is called **inherently ambiguous**.

![](https://github.com/stinsan/CS-3823-Theory-of-Computation/blob/master/Screenshots/toc-75.png)

