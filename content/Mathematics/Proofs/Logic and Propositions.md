**Logic** is the study of reasoning. In Computer Science, formal logic is used to verify properties of programs, circuits, and protocols.

---
#### Propositions & Connectives
A **Proposition** is a statement that is either True ($T$) or False ($F$). We combine simple propositions using logical connectives.

| Connective      |     Symbol     | Name         | Meaning                                        |
| :-------------- | :------------: | :----------- | :--------------------------------------------- |
| **Negation**    |    $\neg P$    | NOT          | True iff $P$ is False.                         |
| **Conjunction** |  $P \land Q$   | AND          | True iff both $P$ and $Q$ are True.            |
| **Disjunction** |   $P \lor Q$   | OR           | True iff $P$ is True or $Q$ is True (or both). |
| **Implication** | $P \implies Q$ | IMPLIES      | False iff $P$ is True and $Q$ is False.        |
| **XOR**         |  $P \oplus Q$  | Exclusive OR | True iff exactly one of $P, Q$ is True.        |

**The Implication Trap ($P \implies Q$)**
- If the Hypothesis ($P$) is False, the implication is **vacuously true**, regardless of $Q$.

---
#### Quantifiers
Predicate logic extends propositional logic by introducing variables and quantifiers. Let $P(x)$ be a predicate (a function returning a boolean).

1.  **Universal Quantifier ($\forall$)**
    *   $\forall x \in S, P(x)$: "For all $x$ in set $S$, $P(x)$ is true."
    *   *Disproof:* Find **one** counterexample.

2.  **Existential Quantifier ($\exists$)**
    *   $\exists x \in S, P(x)$: "There exists an element $x$ in $S$ such that $P(x)$ is true."
    *   *Proof:* Find **one** example.

**Negating Quantifiers**
*   $\neg (\forall x, P(x)) \iff \exists x, \neg P(x)$
    *   *To say "Not everyone likes pizza" is to say "There is someone who does not like pizza".*
*   $\neg (\exists x, P(x)) \iff \forall x, \neg P(x)$

---
#### Logical Equivalence
Two statements are **logically equivalent** ($\iff$) if they have the same truth value in every possible scenario (same Truth Table).

**Crucial Equivalences:**
1.  **Contrapositive:** $(P \implies Q) \iff (\neg Q \implies \neg P)$
    *   *Note:* The Converse ($Q \implies P$) is **NOT** equivalent.
2.  **Implication as OR:** $(P \implies Q) \iff (\neg P \lor Q)$

---
