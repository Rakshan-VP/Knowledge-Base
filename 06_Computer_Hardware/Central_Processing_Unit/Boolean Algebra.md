#type/concept #domain/math #status/completed #scope/fundamental 
> [!abstract] Summary
> **Boolean algebra** is a mathematical system for representing and manipulating logical values, typically `0` and `1`. It is used to describe and simplify **logic operations and digital circuits**.

## Overview
Boolean algebra was developed by **George Boole** and formally presented in his 1854 work *An Investigation of the Laws of Thought*. It was originally developed to express **logical reasoning using mathematical notation**, rather than for computers. Its operations, such as **AND, OR, and NOT**, later became directly applicable to electrical switching circuits. With the development of digital electronics, Boolean algebra became a foundation for designing and analyzing **logic gates and digital systems**. Today, it is fundamental to **digital circuit design, processors, memory, computer architecture, and hardware description languages**. Modern CPUs ultimately implement Boolean operations using billions of transistor-based switching circuits.

## Basic Definitions
### Boolean Expression and Boolean Variables
A **Boolean variable** is a variable that can have only two possible values:
- `True (T)` or `False (F)`
- `1` or `0`

| Boolean value | Numerical value |
|---|---:|
| True (T) | 1 |
| False (F) | 0 |

A **Boolean expression** is an expression formed using Boolean variables and Boolean operations that produces a Boolean value.

For example:

$$
P + Q = R
$$

where `P`, `Q`, and `R` are Boolean variables.

If:

$$
P=1,\quad Q=0
$$

then:

$$
P+Q=1
$$

In Boolean algebra, `+` represents the **OR** operation.

### Truth Table

A **truth table** represents all possible combinations of input values and their corresponding output values in a tabular form. `T` and `F` represent True and False.

| Symbol | Value |
|---|---:|
| T | 1 |
| F | 0 |

> [!NOTE]
> For `n` Boolean variables, the number of possible input combinations is:$\boxed{2^n}$ where `n` is the number of Boolean variables.
> 
> For example, for two variables `P` and `Q`:
> $$
> 2^2=4
> $$

## Logical Operations

![center|875](booleanop.jpg)

There are three basic Boolean operations:

1. **NOT (Negation)**
2. **AND (Conjunction)**
3. **OR (Disjunction)**

Every other Boolean operation can be formed by combining these operations.

### NOT (Negation)

The **NOT** operation reverses the value of a Boolean variable.

Boolean expression:

$$
\boxed{Y=\overline{A}}
$$

| A | $\overline{A}$ |
|---|---|
| F (0) | T (1) |
| T (1) | F (0) |


### AND (Conjunction)

The **AND** operation produces `True` only when **both inputs are True**.

Boolean expression:

$$
\boxed{Y=A\cdot B}
$$

The multiplication symbol may also be omitted:

$$
A\cdot B=AB
$$

| A | B | $A\cdot B$ |
|---|---|---|
| F (0) | F (0) | F (0) |
| F (0) | T (1) | F (0) |
| T (1) | F (0) | F (0) |
| T (1) | T (1) | T (1) |


### OR (Disjunction)

The **OR** operation produces `True` when **at least one input is True**.

Boolean expression:

$$
\boxed{Y=A+B}
$$

| A | B | $A+B$ |
|---|---|---|
| F (0) | F (0) | F (0) |
| F (0) | T (1) | T (1) |
| T (1) | F (0) | T (1) |
| T (1) | T (1) | T (1) |

## Precedence
Boolean operations have a defined order of evaluation, similar to **BODMAS** in arithmetic.
The precedence is:

$$
\boxed{\text{Parentheses} > \text{NOT} > \text{AND} > \text{OR}}
$$

Therefore:

1. **Parentheses** are evaluated first.
2. **NOT** is evaluated second.
3. **AND** is evaluated third.
4. **OR** is evaluated last.

### Example

Consider:

$$
Y=A+B\cdot C
$$

Since AND has higher precedence than OR:

$$
Y=A+(B\cdot C)
$$

Let:

$$
A=F(0),\quad B=T(1),\quad C=T(1)
$$

First:

$$
B\cdot C=T(1)\cdot T(1)=T(1)
$$

Then:

$$
Y=F(0)+T(1)=T(1)
$$

Therefore:

$$
\boxed{Y=T(1)}
$$

## Properties
- **Annulment Law**  
  Any Boolean variable combined with `0` using AND gives `0`, while combined with `1` using OR gives `1`.
  $$
  \begin{aligned}
  A\cdot0 &= 0 \\
  A+1 &= 1
  \end{aligned}
  $$

- **Identity Law**  
  Combining a Boolean variable with `1` using AND or with `0` using OR leaves the variable unchanged.
  $$
  \begin{aligned}
  A\cdot1 &= A \\
  A+0 &= A
  \end{aligned}
  $$

- **Idempotent Law**  
  Combining a Boolean variable with itself produces the same variable.
  $$
  \begin{aligned}
  A+A &= A \\
  A\cdot A &= A
  \end{aligned}
  $$

- **Complement Law**  
  A Boolean variable combined with its complement produces `1` using OR and `0` using AND.
  $$
  \begin{aligned}
  A+\overline{A} &= 1 \\
  A\cdot\overline{A} &= 0
  \end{aligned}
  $$

- **Double Negation Law**  
  Taking the complement of a Boolean variable twice gives the original variable.
  $$
  \overline{\overline{A}}=A
  $$

- **Commutative Law**  
  The order of the variables does not affect the result.
  $$
  \begin{aligned}
  A+B &= B+A \\
  A\cdot B &= B\cdot A
  \end{aligned}
  $$

- **Associative Law**  
  The grouping of variables does not affect the result.
  $$
  \begin{aligned}
  A+(B+C) &= (A+B)+C \\
  A\cdot(B\cdot C) &= (A\cdot B)\cdot C
  \end{aligned}
  $$

- **Distributive Law**  
  AND can be distributed over OR, and OR can be distributed over AND.
  $$
  \begin{aligned}
  A\cdot(B+C) &= A\cdot B+A\cdot C \\
  A+(B\cdot C) &= (A+B)(A+C)
  \end{aligned}
  $$

- **Absorption Law**  
  A redundant term can be eliminated without changing the result.
  $$
  \begin{aligned}
  A\cdot(A+B) &= A \\
  A+A\cdot B &= A
  \end{aligned}
  $$

- **De Morgan's Laws**  
  Complementing an AND expression changes it to OR of the complements, while complementing an OR expression changes it to AND of the complements.
  $$
  \begin{aligned}
  \overline{A\cdot B} &= \overline{A}+\overline{B} \\
  \overline{A+B} &= \overline{A}\cdot\overline{B}
  \end{aligned}
  $$
> [!NOTE]
> **Consensus Theorem:** The term $B\cdot C$ is redundant and can be removed without changing the result.
>
> $$
> A\cdot B+\overline{A}\cdot C+B\cdot C
> =
> A\cdot B+\overline{A}\cdot C
> $$

## Related Links
### External
- [GeeksforGeeks|Boolean Algebra](https://www.geeksforgeeks.org/digital-logic/boolean-algebra/)
- [GeeksforGeeks|Properties of Boolean Algebra](https://www.geeksforgeeks.org/maths/properties-of-boolean-algebra/)
- [GeeksforGeeks|Boolean Functions](https://www.geeksforgeeks.org/digital-logic/boolean-functions/)
