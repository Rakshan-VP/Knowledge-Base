#type/concept #domain/hardware #status/completed #scope/fundamental 
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

![center|800](nmos.gif)

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

## BJT vs FET

| **Property**      | **BJT**                                                 | **FET**                                                             |
| ----------------- | ------------------------------------------------------- | ------------------------------------------------------------------- |
| Full form         | Bipolar Junction Transistor                             | Field-Effect Transistor                                             |
| Control           | Current-controlled                                      | Voltage-controlled                                                  |
| Input impedance   | Low to moderate                                         | Very high                                                           |
| Input current     | Requires base current                                   | Very little gate current                                            |
| Power consumption | Higher at input                                         | Very low at input                                                   |
| Switching speed   | Generally lower                                         | Generally higher                                                    |
| Noise             | Generally higher                                        | Generally lower                                                     |
| Thermal stability | More prone to thermal runaway                           | Generally better                                                    |
| Gain              | High current gain                                       | High voltage gain                                                   |
| Size              | Larger                                                  | Smaller                                                             |
| Integration       | Good                                                    | Excellent                                                           |
| Main types        | NPN, PNP                                                | JFET, MOSFET                                                        |
| Main advantage    | High transconductance and good linearity                | Very high input impedance and low power consumption                 |
| Main disadvantage | Requires input current and has thermal-runaway concerns | Sensitive to static/ESD, and some types have lower transconductance |

## Transistors Used in CPUs
Different types of transistors have been used in CPUs throughout the development of computing:

| Type | Transistors | Usage |
|---|---|---|
| **BJT** | NPN, PNP | Early transistorized computers |
| **MOSFET** | NMOS, PMOS | Modern CPUs |
| **FinFET** | NMOS, PMOS | Modern CPU processes |
| **GAA / Nanosheet** | NMOS, PMOS | Newer CPU processes |

Modern CPUs use **MOSFET-based CMOS logic**, where **NMOS and PMOS** transistors work together. We will first use **NPN transistors** to understand how transistor-level logic works, and later move to CMOS.

### Digital Logic Convention
From now on:
- **High voltage = `1`**
- **Low voltage = `0`**

### NPN Transistor Logic

For the upcoming circuits, we will use an NPN transistor as a switch:

- **Base** → Input
- **Collector** → Output
- **Emitter** → GND (`0`)
- **Collector** → `VCC (1)` through a pull-up resistor

| Input | Transistor | Output |
|:---:|:---:|:---:|
| `0` | OFF | `1` |
| `1` | ON | `0` |
![center](notgate.gif)
When the input is `0`, the transistor is OFF and the pull-up resistor makes the Collector `1`.

When the input is `1`, the transistor turns ON and pulls the Collector toward GND, making the output `0`.

$$
IN = 0 \Rightarrow OUT = 1
$$

$$
IN = 1 \Rightarrow OUT = 0
$$

Therefore:

$$
OUT = \overline{IN}
$$

This is the basic **NOT gate**.

The output is taken from the **Collector** because the Collector voltage changes between `VCC` and GND depending on whether the transistor is OFF or ON.

> [!NOTE]
> The Collector is connected to `VCC` through a **pull-up resistor**, not directly.

Before building the logic gates, we will first look at **Boolean algebra**, and then use NPN transistors to implement the corresponding logic gates. After that, we will study **CMOS logic** using NMOS and PMOS transistors.
## Related Links
### Notes

### External
- [GeeksforGeeks|Transistor](https://www.geeksforgeeks.org/electronics-engineering/what-is-transistor/#how-do-transistors-work)
- [GeeksforGeeks|Difference Between BJT and FET](https://www.geeksforgeeks.org/electrical-engineering/difference-between-bjt-and-fet/)
- [tutorialspoint|Basic Electronics - Types of Transistors](https://www.tutorialspoint.com/basic_electronics/basic_electronics_types_of_transistors.htm)
- [Intel|The Transistor,Explained](https://www.intel.com/content/www/us/en/newsroom/tech101/the-transistor-explained.html)

<span class="note-nav">[[Transistors|◀ Previous Note]] <span class="next-note">[[Boolean Algebra|Next Note ▶]]</span></span>
