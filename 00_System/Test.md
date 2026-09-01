## 1. Headings

### 1.1 Subsection

#### 1.1.1 H4

##### 1.1.1.1 H5

###### 1.1.1.1.1 H6

---

## 2. Text Formatting

### 2.1 Basic Formatting

Normal text.

**Bold**

*Italic*

***Bold and italic***

~~Strikethrough~~

==Highlight==

`Inline code`

[External link](https://obsidian.md)

[[Internal Note]]

[[Internal Note|Custom Name]]

---

## 3. Lists

### 3.1 Unordered List

- Item
- Item
- Item

### 3.2 Nested List

- Item
  - Nested item
    - Deeper item
  - Nested item
- Item

### 3.3 Ordered List

1. Item
2. Item
3. Item

### 3.4 Nested Ordered List

1. Item
	1. Nested Item 1
	2. Nested Item 2
2. Item

### 3.5 Task List

- [ ] Pending
- [x] Completed
- [ ] Pending

---

## 4. Blockquotes

### 4.1 Basic Blockquote

> Blockquote

### 4.2 Multiline Blockquote

> First line
>
> Second line
>
> Third line

### 4.3 Nested Blockquote

> Level one
>
> > Level two

---

## 5. Callouts

### 5.1 Standard Callouts

> [!note]
> Note

> [!abstract]
> Abstract

> [!info]
> Info

> [!tip]
> Tip

> [!success]
> Success

> [!question]
> Question

> [!warning]
> Warning

> [!failure]
> Failure

> [!danger]
> Danger

> [!bug]
> Bug

> [!example]
> Example

> [!quote]
> Quote

### 5.2 Custom Title

> [!note] Custom Title
> Content

> [!warning] Warning Title
> Content

### 5.3 Foldable Callouts

> [!note]- Collapsed
> Hidden content

> [!note]+ Expanded
> Visible content

---

## 6. Code

### 6.1 Inline Code

`code`

### 6.2 Python

```python
print("Hello World")


### 6.3 C

```c
#include <stdio.h>

int main(void) {
    return 0;
}
```

### 6.4 C++

```cpp
#include <iostream>

int main() {
    return 0;
}
```

### 6.5 JavaScript

```javascript
const value = 10;
console.log(value);
```

### 6.6 Bash

```bash
echo "Hello World"
```

### 6.7 YAML

```yaml
name: test
value: 10
```

### 6.8 JSON

```json
{
    "name": "test",
    "value": 10
}
```

### 6.9 Plain Text

```text
Plain text
```

---

## 7. Mathematics

### 7.1 Single equation (baseline)
$$
\boxed{
F = ma
}
% id: eq-qiitaasn
$$
See [[#^eq-qiitaasn]]  for Newton's second law.

### 7.2 Aligned block — test numbering
$$
\begin{aligned}
x &= a + b \\
y &= c + d \\
z &= x + y
\end{aligned}

% id: eq-5zmhiiix
$$
See [[#^eq-5zmhiiix]]  for the full derivation.

---
## 8. Tables

### 8.1 Basic Table

| Column 1 | Column 2 | Column 3 |
|---|---|---|
| Data | Data | Data |
| Data | Data | Data |
| Data | Data | Data |

### 8.2 Alignment

| Left | Center | Right |
|:---|:---:|---:|
| Text | Text | 100 |
| Text | Text | 200 |
| Text | Text | 300 |

---

## 9. Links

### 9.1 External

[Obsidian](https://obsidian.md/)

[GitHub](https://github.com/)

### 9.2 Internal

[[Home]]

[[Projects]]

[[Research]]

### 9.3 Internal Links With Custom Names

[[Home|Home Page]]

[[Projects|My Projects]]

[[Research|Research Notes]]

### 9.4 Heading Links

[[Home#Projects]]

[[Research#Experiments]]

### 9.5 Heading Links With Custom Names

[[Home#Projects|Home > Projects]]

[[Research#Experiments|Research > Experiments]]

---

## 10. Images

### 10.1 External Image

![Example Image](https://picsum.photos/800/400)

### 10.2 Image With Alt Text

![Engineering Test Image](https://picsum.photos/600/300)

### 10.3 Image Link

[Open Image](https://picsum.photos/800/400)

---

## 11. Horizontal Rules

Content above the rule.

---

Content below the rule.

---

## 12. Footnotes

Text with a footnote.[^1]

Text with another footnote.[^2]

Multiple footnotes can also be used in the same paragraph.[^1][^2]

[^1]: Footnote one.

[^2]: Footnote two.

---

## 13. HTML

### 13.1 Center

<center>
Centered text
</center>

### 13.2 Details

<details>
<summary>Click to expand</summary>

Hidden content.

</details>

### 13.3 Keyboard

<kbd>Ctrl</kbd> + <kbd>C</kbd>

<kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd>

---

## 14. Subscript and Superscript

### 14.1 Subscript

H<sub>2</sub>O

CO<sub>2</sub>

### 14.2 Superscript

x<sup>2</sup>

10<sup>3</sup>

---

## 15. Symbols

### 15.1 Greek

α β γ δ ε θ λ μ π σ φ ω

### 15.2 Mathematical

± × ÷ ≈ ≠ ≤ ≥ ∞ → ← ↑ ↓ √ ∂ ∇ ∑ ∫

### 15.3 Engineering

Ω Δ ∇ ∂ λ μ θ φ τ ω

---

## 16. Mixed Formatting

**Bold**

*Italic*

***Bold Italic***

`Inline code`

==Highlight==

~~Strikethrough~~

**Bold with *italic***

**Bold with `code`**

**Bold with ==highlight==**

*Italic with `code`*

*Italic with ==highlight==*

---

## 17. Nested Structure

## Section

Section content.

### Subsection

Subsection content.

#### Sub-subsection

Sub-subsection content.

##### Detail

Detailed content.

###### Fine Detail

Fine-detail content.

---

## 18. Final Test

Normal text with **bold**, *italic*, `inline code`, ==highlight==, and ~~strikethrough~~.

> [!note] Test Callout
> This is a test callout.

$$
\dot{x} = Ax + Bu
$$

```python
x = 10
print(x)
```

|Feature|Test|
|---|:-:|
|Markdown|✓|
|Callouts|✓|
|Code|✓|
|Math|✓|
|Tables|✓|
|Links|✓|
|Images|✓|
|HTML|✓|
|Footnotes|✓|


