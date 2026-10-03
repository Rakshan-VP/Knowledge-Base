#type/concept #domain/hardware #status/learning #scope/fundamental 
> [!abstract] Summary
> **Transistors** are tiny electronic switches that turn electrical signals **on and off**, and billions of them wired together perform the **logic operations** that let a CPU compute. Modern chips pack these switches at **nanometer scale**, enabling the speed and complexity of today's processors. Every calculation a computer does ultimately boils down to patterns of transistors switching states.

## Overview

Before transistors, computers used **vacuum tubes** and mechanical relays — bulky, power-hungry, and unreliable, since tubes burned out often and machines like **ENIAC** filled entire rooms while still crashing frequently. The transistor, invented at **Bell Labs in 1947**, replaced these with a **solid-state device** that could switch current far more reliably, using far less power and space. This breakthrough happened because engineers needed a smaller, sturdier alternative to tubes to make electronics practical and scalable. Over subsequent decades, transistors shrank dramatically (following what became known as **Moore's Law**), allowing millions and eventually billions to be etched onto a single silicon chip. In a CPU, these transistors are arranged into **logic gates** (AND, OR, NOT, etc.), which combine to form the **arithmetic and control circuits** that execute instructions — making the transistor the **fundamental building block** of all modern computing.

## Types of Transistors

Transistors can be broadly classified into two main categories: **Bipolar Junction Transistors (BJTs)** and **Field-Effect Transistors (FETs)**. Each category contains several types with different construction and operating characteristics.
- **BJT** — Bipolar Junction Transistor
    - **NPN** — Negative-Positive-Negative
    - **PNP** — Positive-Negative-Positive
- **FET** — Field-Effect Transistor
    - **JFET** — Junction Field-Effect Transistor   
    - **MOSFET** — Metal-Oxide-Semiconductor Field-Effect Transistor

## Bipolar Junction Transistor (BJT)
A **BJT (Bipolar Junction Transistor)** is a three-terminal semiconductor device used mainly for **switching and amplification**. A BJT has three terminals:
- **Base (B)** — Controls the current flowing through the transistor.
- **Collector (C)** — The terminal through which the controlled current flows into the transistor in an NPN transistor.
- **Emitter (E)** — Supplies charge carriers and is the terminal through which current leaves an NPN transistor.

### NPN Transistor
![center|200](npn.png)

An NPN transistor consists of a **P-type Base** sandwiched between two **N-type regions**:
- **Collector (C)** — Collects electrons from the Base region.
- **Base (B)** — A small base current controls a much larger collector-emitter current.
- **Emitter (E)** — Emits electrons into the Base region.

When the Base is made sufficiently positive with respect to the Emitter:
1. The **Emitter injects electrons** into the thin Base region.
2. Because the Base is very thin, most electrons pass through it.
3. The positive Collector attracts these electrons.
4. A large current therefore flows from **Collector to Emitter**.
<div class="clear"></div>

A **small Base current controls a much larger Collector current**.


### PNP Transistor
![center|200](pnp.png)

A PNP transistor has an **N-type Base** sandwiched between two **P-type regions**:
- **Emitter (E)** — Emits holes into the Base region.
- **Base (B)** — Controls the current flowing through the transistor.
- **Collector (C)** — Collects holes from the Base region.

When the Base is made sufficiently negative with respect to the Emitter:
1. The **Emitter injects holes** into the thin Base region.
2. Because the Base is very thin, most holes pass through it.
3. The Collector attracts these holes.
4. A large current therefore flows from **Emitter to Collector**.
   
Again, a **small Base current controls a much larger Collector-Emitter current**.

### NPN vs PNP

| **Property**             | **NPN**             | **PNP**             |
| ------------------------ | ------------------- | ------------------- |
| Structure                | N-P-N               | P-N-P               |
| Main carriers            | Electrons           | Holes               |
| Base relative to Emitter | More positive       | More negative       |
| Conventional current     | Collector → Emitter | Emitter → Collector |
| Typical use              | Low-side switching  | High-side switching |

## Field-Effect Transistor (FET)
A **FET (Field-Effect Transistor)** is a three-terminal semiconductor device used mainly for **switching and amplification**. A FET has three terminals:
- **Gate (G)** — Controls the current flowing through the transistor.
- **Drain (D)** — The terminal through which current flows into the channel.
- **Source (S)** — The terminal through which current flows out of the channel.

Unlike a BJT, a FET is a **voltage-controlled device**. The voltage applied to the Gate controls the current flowing between the Drain and Source.

### JFET
**JFET (Junction Field-Effect Transistor)** controls the current between the Drain and Source using an electric field produced by a **reverse-biased PN junction**.

![center|875](JFET.png)

JFETs are available in two types:
- **N-channel JFET** — Has an N-type channel with P-type Gate regions.
- **P-channel JFET** — Has a P-type channel with N-type Gate regions.

The terminals have the same functions in both:
- **Drain (D)** — Current flows through the channel toward the Drain.
- **Gate (G)** — Controls the width of the channel.
- **Source (S)** — Supplies the charge carriers to the channel.

The main difference is the **polarity and charge carriers**:

|               | **N-channel**               | **P-channel**               |
| ------------- | --------------------------- | --------------------------- |
| Channel       | N-type                      | P-type                      |
| Gate regions  | P-type                      | N-type                      |
| Main carriers | Electrons                   | Holes                       |
| Gate voltage  | Negative relative to Source | Positive relative to Source |
When the Gate is reverse biased with respect to the channel:
1. The Gate-channel PN junction becomes reverse biased.
2. The depletion region becomes wider.
3. The channel becomes narrower.
4. The Drain-Source current decreases.

Therefore, in both types, the **Gate voltage controls the Drain-Source current by varying the channel width**.

### MOSFET

**MOSFET (Metal-Oxide-Semiconductor Field-Effect Transistor)** is a FET in which the Gate is electrically insulated from the semiconductor by an oxide layer.

There are two main channel types:
- **N-channel MOSFET**
- **P-channel MOSFET**

![center|875](mosfetmodes.png)

MOSFETs operate in two modes:
- **Enhancement mode** — Normally OFF; an appropriate Gate voltage creates a conducting channel.
- **Depletion mode** — Normally ON; an appropriate Gate voltage reduces the channel conductivity.



The terminals have the same functions in both:
- **Gate (G)** — Controls the channel using an electric field.
- **Drain (D)** — Terminal through which current flows through the channel.
- **Source (S)** — Supplies the main charge carriers to the channel.

The main difference is the **channel type, charge carriers, and Gate voltage polarity**:

| | N-channel | P-channel |
|---|---|---|
| Channel | N-type | P-type |
| Main carriers | Electrons | Holes |
| Gate voltage | Positive relative to Source | Negative relative to Source |
| Charge carriers attracted by Gate | Electrons | Holes |

For an **N-channel MOSFET**, making the Gate sufficiently **positive relative to the Source** attracts electrons toward the semiconductor surface and forms an N-type conducting channel.

For a **P-channel MOSFET**, making the Gate sufficiently **negative relative to the Source** attracts holes toward the semiconductor surface and forms a P-type conducting channel.

In both types:

1. The Gate voltage creates an electric field.
2. The electric field controls the formation or conductivity of the channel.
3. The channel connects the Drain and Source.
4. The Drain-Source current is controlled by the Gate-Source voltage.

Therefore, a MOSFET is a **voltage-controlled device**.


## Related Links
### Notes

### External
- [GeeksforGeeks|Transistor](https://www.geeksforgeeks.org/electronics-engineering/what-is-transistor/#how-do-transistors-work)
- [GeeksforGeeks|Difference Between BJT and FET](https://www.geeksforgeeks.org/electrical-engineering/difference-between-bjt-and-fet/)
- [tutorialspoint|Basic Electronics - Types of Transistors](https://www.tutorialspoint.com/basic_electronics/basic_electronics_types_of_transistors.htm)



<span class="note-nav">[[Transistors|◀ Previous Note]] <span class="next-note">[[Logic Gates|Next Note ▶]]</span></span>
