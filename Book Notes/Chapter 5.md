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
