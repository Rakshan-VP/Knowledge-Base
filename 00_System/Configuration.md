## Introduction

Configuration reference for the vault's **appearance, organization, plugins, and note conventions**.
## Setup
### Core Plugins

- **Community Plugins** — Enable third-party plugins.
- **File Explorer** — Main file and folder structure.
- **Graph View** — Visualize note relationships.
- **Tags** — Browse and manage tags.
- **Workspaces** — Save workspace layouts.
### Community Plugins

- **Calendar** — Calendar navigation.
- **Iconize** — Customize file and folder icons.
- **File Color** — Color files and folders.
- **Colored Tags** — Color-code tags.
- **File Explorer Note Count** — Show note counts.
- **File Explorer ++** — Pin important notes.
- **Homepage** — Set the vault homepage.
- **Git** — Version control and vault backup.
- **Code Styler** — Style code blocks.
- **Ninja Cursor** — Customize the cursor.
- **Omnisearch** — Full-vault search.
- **Commander** — Add custom commands to the interface.
- **Tasks** — Manage tasks.

> [!Info] 
> Add to the **Tab Bar**:
> ```text
Omnisearch: Vault Search 
> ```

---
## Layout

**Left Sidebar**
- File Explorer
- Graph View

**Right Sidebar**
- Tags
- Calendar

**Tab Bar**
- Omnisearch: Vault Search

**Workspace**
- Enabled

---

## Appearance
### Theme

**Obsidianite**
### Fonts

```text
Interface  → Adwaita Mono
Text       → Adwaita Mono
Monospace  → Source Code
```

---

## Visual Style
### Headings

```text
Title → 38px, centered, bold
H1    → 34px
H2    → 27px
H3    → 21px
```

- **Title / H1:** `#F3DFA2`
    
- **H2:** `#D4A94F`
    
- **H3:** `#7FB7B0`
    
- **Bold:** `#D8895F`
    
- **Italic:** `#B99A8E`
    

H2 uses `>` and H3 uses `>>` as visual prefixes.
### Spacing

```text
H2 → 1.5em top / 0.5em bottom
H3 → 1.2em top / 0.5em bottom
```
### Links

- Internal → `#35519E`
- External → `#A13A5E`
- Unresolved → `#5A5A5A`

Links use a filled, rounded style without underlines.

---

## Tags

Use four dimensions:

```text
#type/<value>
#domain/<value>
#status/<value>
#scope/<value>
```
### Type

Defines **what the note is**.

- `concept` — Explains **what something is and how it works**.
- `method` — Explains **how to perform, solve, or approach something**.
- `reference` — Provides **quick-lookup information** such as commands, parameters, shortcuts, or specifications.
- `derivation` — Shows **how something is mathematically or logically obtained**.
- `application` — Shows **how a concept or method is used in a practical context**.
- `implementation` — Describes a **software, hardware, or computational realization**.
- `setup` — Covers **installation, configuration, preferences, and environment setup**.
### Domain

Defines **the subject area**.

```text
mathematics
control
engineering
programming
electronics
mechanical
robotics
```

> Extend as needed.

### Status

Defines **the state of the note**.

- `learning` — Currently being developed.
- `complete` — Finished.
- `verified` — Checked and confirmed.

### Scope

Defines **technical depth**.

- `fundamental` — Basic principles and prerequisites.
- `intermediate` — Builds on fundamentals.
- `advanced` — Complex, specialised, or highly technical.

---
## Folder Colors

Use these 16 colors sequentially for top-level folders:

```text
#E53935
#F4511E
#FB8C00
#FDD835
#9CCC65
#43A047
#00897B
#00ACC1
#039BE5
#1E88E5
#3949AB
#5E35B1
#8E24AA
#D81B60
#AD1457
#6D1B7B
```

---

## Folder Structure

```text
00_System/
01_Mathematics/
02_Physics/
03_Control/
04_Robotics/
.
.
.
.
.
.
.
98_Inbox/
99_Archive/
```

---

# References

- [Obsidian Setup Reference](https://www.youtube.com/watch?v=ZQTj8ZSDFw4)