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

### Removing Useless Productions

#### Definition 6.1 
A variable A ∈ V is **useful** if and only if there is at least one w ∈ L(G) s.t. S ∗⇒ x A y ∗⇒ w, with x, y ∈ (V ∪ T)* ; i.e. a variable is useful if it occurs in at least one derivation. Else, it is a **useless** variable.

We desire to remove useless variables.

#### Theorem 6.2
If G is a CGF, then there is an equivalent CFG G' s.t. G' does not contain any useless variables.

### Removing λ-Productions
#### Definition 6.2
Any production of a context-free grammar of the form A → λ is called a **λ-production**. 

Any variable A for which the derivation A ∗⇒ λ is possible is called **nullable**.

#### Theorem 6.3
If G is a CFG with λ not in L(G), then there exists an equivalent grammar G' with no λ-productions.

### Removing Unit Productions
#### Definition 6.3
Any production of a context-free grammar of the form A → B, where A, B ∈ V , is called a **unit-production**.

To remove unit-productions, we use the substitution rule in theorem 6.1.

#### Theorem 6.4
If G is a CFG without λ-productions, there exists an equivalent CFG G' with no unit productions.

#### Theorem 6.5
Let L be a context-free language that does not contain λ. Then there exists
a context-free grammar that generates L and that does not have any useless
productions, λ-productions, or unit-productions.
