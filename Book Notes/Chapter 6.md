# Chapter 6: Simplication of Context-Free Grammars and Normal Forms

## 6.1 | Methods for Transforming Grammars

Empty strings in grammars are a nuisance, so we want to remove it.

Let L be any context-free language, and let G = (V, T, S, P) be a context-free grammar for L - {λ}. If we make a new starting variable S0
and add the productions S0 → S|λ, we would get L.  Consequently, for all
practical purposes, there is no difference between context-free languages that include λ and those that do not. 

### A Useful Substitution Rule

#### Theorem 6.1

Suppose that G is a CFG that contains a production of form A → x<sub>1</sub> B x<sub>2</sub>. <br>
Assume that B → y<sub>1</sub> | y<sub>2</sub> | ··· | y<sub>n</sub>.

Let G' be a CFG that is constructed by deleting the production A → x<sub>1</sub> B x<sub>2</sub> and replacing it with <br>
A → x<sub>1</sub> y<sub>1</sub> x<sub>2</sub> | x<sub>1</sub> y<sub>2</sub> x<sub>2</sub> | ··· | x<sub>1</sub> y<sub>n</sub> x<sub>2</sub>. 

Then, L(G) = L(G').
