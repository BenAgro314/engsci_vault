TARGET DECK: Main Deck

What is a *predicate* $p$? #fc 
A boolean function
<!--ID: 1623634582052-->


What are *types* (in PDDL), ie. how are they formulated? #fc 
As unary predicates
<!--ID: 1623634582085-->


What is a *fact* in PDDL? #fc
It is a predicate $p$ evaluated on an object tuple $\bar{x}$ that evaluates to true
<!--ID: 1623634582089-->


What is a *literal* in PDDL? #fc 
A fact or negated fact
<!--ID: 1623634582092-->


What is a *state* in PDDL? #fc 
A set of literals 
<!--ID: 1623634582095-->


What are the three components of a PDDL action? #fc 
- parameter tuple $\bar{X} = \langle X_1, ..., X_k \rangle$
- literal preconditions $pre(a)$
- literal effects $eff(a)$
<!--ID: 1623634582098-->


What is an *action instance* (as opposed to an *action*)? #fc 
It is anaction with it's parameters $\bar{X}$ replaced with objects $\bar{x}$.
<!--ID: 1623634582100-->


When is an action instance *applicable* in state $\mathcal I$? #fc
If $(pre^+(a(\bar{x})) \subseteq \mathcal I) \text{ and } (pre^-(a(\bar{x}))\cap \mathcal I = \emptyset$, where the $+$ and $-$ denote the positive and negative literals in the precondition. In words this means that all the true literals of the precondition must be in the state, and non of the false literals.
<!--ID: 1623634582103-->


What is the latex symbol for $\cap$ ? #fc 
`\cap`
<!--ID: 1623634582106-->


What is the latex symbol for $\emptyset$ ? #fc 
`\emptyset`
<!--ID: 1623634582109-->


What is the latex symbol for $ \subseteq $ ? #fc 
`\subseteq`
<!--ID: 1623634582112-->


What is the result of applying action instance $a(\bar{x})$ to state $\mathcal I$? #fc 
A new state
$$(\mathcal I \; \backslash eff^-(a(\bar{x}))) \; \cup \; eff^+(a(\bar{x}))$$. In words, it is the old state without the negative literals and with the new positive literals.
<!--ID: 1623634582115-->

What is a *stream* in PDDLstream? #fc
A conditional generator $s(\bar{X})$ endowed with a declarative specification of any facts its inputs and outputs always satisfy. 
<!--ID: 1623669204435-->

What does $s.domain$ mean, for a stream $s$? #fc 
The set of facts on the input parameters $s.input$ that specify the set of object tuples $\bar{x}$ for which $s(\bar{X})$ is defined. (such as "typing" information)
<!--ID: 1623671337543-->


What does $s.certified$ mean? #fc 
It is the set of certified redicates on both $s.input$ and $s.output$ that assert any facts that $\langle \bar{x}, \bar{y} \rangle$ satisfy. 
(the properties the outputs are guarenteed to satisfy. 
<!--ID: 1623671337578-->
