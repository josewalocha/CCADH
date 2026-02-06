# CCADH - Cybernetic Brain with Hierarchical Decision Architecture

> *"Build a brain, don't simulate intelligence"*

![Status](https://img.shields.io/badge/status-research-orange)
![Version](https://img.shields.io/badge/version-4.0_Barista-green)
![Vision](https://img.shields.io/badge/vision-2026+-purple)

---

## 🎯 Vision

**CCADH** is a research project aiming to create a cognitive system inspired by biology, not mathematics.

CCADH contains **MARCO**, the first **SGBDOCN** (Neuron-Concept Oriented Database System) — a living DBMS that learns by reading.

**Goal**: A cybernetic brain that:
- Learns through exposure (not supervised training)
- Understands through structure (not statistics)
- Reasons through activation (not matrix computation)
- Runs on a Raspberry Pi (not a datacenter)

---

## 🧠 Philosophy

### What CCADH is NOT

❌ An LLM (Large Language Model)
❌ A classical neural network
❌ A transformer-based system
❌ An AI requiring GPUs

### What CCADH IS

✅ Inspired by C.elegans (302 neurons → complex behaviors)
✅ Based on while loops (not if/else)
✅ Emergent (intelligence arises from structure)
✅ Frugal (50 MB RAM for a whole library)
✅ A SGBDOCN (meaning emerges, no SQL queries)
✅ A barista: it learns while serving ☕

---

## 🏛️ Full Architecture

```
╔═══════════════════════════════════════════════════════════════════╗
║                            CCADH                                  ║
╠═══════════════════════════════════════════════════════════════════╣
║                                                                   ║
║  ┌─────────────────────────────────────────────────────────────┐  ║
║  │                        THALAMUS                             │  ║
║  │                (Central Router — Menu v4.0)                 │  ║
║  └─────────────────────────┬───────────────────────────────────┘  ║
║                            │                                      ║
║    ┌───────────────────────┼───────────────────────┐              ║
║    │                       │                       │              ║
║    ▼                       ▼                       ▼              ║
║  ┌─────────┐         ┌───────────┐         ┌─────────────┐        ║
║  │HIPPO-   │         │   MARCO   │         │ CEREBELLUM  │        ║
║  │CAMPUS   │◄───────►│ (SGBDOCN) │◄───────►│ (Diffusion  │        ║
║  │(Short   │         │  Cortex   │         │   loops)    │        ║
║  │ memory) │         │ 5 layers  │         │             │        ║
║  └─────────┘         └───────────┘         └─────────────┘        ║
║                            │                                      ║
║              ┌─────────────┼─────────────┐                        ║
║              │             │             │                        ║
║              ▼             ▼             ▼                        ║
║        ┌──────────┐  ┌──────────┐  ┌──────────┐                   ║
║        │ LAYER I  │  │ LAYER II │  │LAYER III │                   ║
║        │ Letters  │  │ Beacons  │  │Concepts  │                   ║
║        │(Neurons) │  │ (Words)  │  │(BSCW)    │                   ║
║        └──────────┘  └──────────┘  └──────────┘                   ║
║              │             │             │                        ║
║              ▼             ▼             ▼                        ║
║        ┌──────────┐  ┌──────────┐  ┌──────────┐                   ║
║        │ LAYER IV │  │ LAYER V  │  │CONVERGE  │                   ║
║        │Co-occur. │  │Sequences │  │ MATRIX   │                   ║
║        │(Meaning) │  │(Syntax)  │  │  (.txt)  │                   ║
║        └──────────┘  └──────────┘  └──────────┘                   ║
║                                                                   ║
╚═══════════════════════════════════════════════════════════════════╝
```

---

## 🧩 Components

### 1. MARCO (SGBDOCN — Cortex) ✅ Implemented

The **cortex** of CCADH. The world's first SGBDOCN.

| | Classic DBMS (SQL) | SGBDOCN (Marco) |
|---|---|---|
| **Storage** | Tables, rows, columns | Beacons, dendrites, concepts |
| **Query** | `SELECT * FROM ...` | Cascade activation (Pac-Man) |
| **Relations** | Foreign keys, JOIN | Co-occurrences, sequences, families |
| **Schema** | Fixed (CREATE TABLE) | Emergent (meaning builds itself) |
| **Index** | B-Tree, Hash | Letter neurons → Beacons → Concepts |
| **Learning** | None | Real-time feeding |

**5 layers**:

| Layer | Role | Detector |
|-------|------|----------|
| I — Letters | 1 letter = 1 neuron | Cascade activation |
| II — Beacons | 1 word = 1 concept | BSC (BooShaChom) |
| III — Concepts | N words = 1 block + family | BSCW (BooShaChom Walocha) |
| IV — Co-occurrences | Meaning through proximity | "Tell me who you hang with" |
| V — Sequences | Syntax through order | "the cat eats" ≠ "eats the cat" |

**Russian dolls** (Concepts):
```python
Concept("what's up")
  family     = ["how's it going", "all good", "doing fine"]
  responses  = ["I'm good thanks"]    # stimulus → response
  components = [Beacon("what's"), Beacon("up")]
  type       = "expression"
```

When a cousin is detected, the leader activates. Like a SQL index, but alive.

**Current state**:
- ✅ Letter neurons (cascade activation)
- ✅ Beacons (unique concepts)
- ✅ Multi-word concepts (class Concept inherits from Beacon)
- ✅ BSCW (greedy sliding window concept detector)
- ✅ Co-occurrences and sequences
- ✅ Semantic tags (IS-A, OPPOSITE, SYNONYM)
- ✅ Stimulus → response pairing (parrot)
- ✅ Convergence matrix (.txt → concepts + families)
- ✅ Standalone galaxy (micro-SGBDOCN with 3D positions)

### 2. THALAMUS (Router — Menu v4.0) ✅ Implemented

The **central router** that directs requests.

**Two matrices, two methods**:

| Matrix | Format | Role | SQL Equivalent |
|---|---|---|---|
| **ADH Matrix** | .json | Full vocabulary (46,006 beacons) | Data dictionary |
| **Convergence Matrix** | .txt | Domain concepts, families, formulas | `CREATE DATABASE` |

**Barista Prompt** (option 3):
```
👤 "hello"                 → 🦜 hello welcome to Marco
👤 "I want a latte"        → 🦜 one latte coming right up
👤 "who are you"           → 🦜 I'm Marco the barista I serve what I've learned
```

**Compartmentalized modes**:

| Mode | BSCW | Learning | Usage |
|------|------|----------|-------|
| **feeding** | ❌ | ✅ dendrites, co-occ, tags | Books, raw text |
| **dialogue** | ✅ | ✅ dendrites, co-occ, tags | Counter, prompt |
| **reading** | ✅ (cerebellum) | ✅ + context | Coming soon |

A book is words. The counter is concepts. Same engine, zero collision.

### 3. CEREBELLUM (Diffusion loops) ⏳ Architecture defined

**Regulator** of reading and convergence loops.

Inspired by diffusion models (Stable Diffusion): start from pure noise, refine through successive passes.

```
Loop 1: letters   → words       (BSC)
Loop 2: words     → concepts    (BSCW)
Loop 3: concepts  → tense       (conjugation)
Loop 4: concepts  → action      (violence, politeness, command)
Loop 5: tense + action → MEANING (threat, story, fact)
```

Same loop at every level. The number of passes is NOT hardcoded — it depends on the number of registers in the convergence matrix. Each register = one diffusion layer.

### 4. HIPPOCAMPUS (Short-term memory) ⏳ Architecture defined

**Episodic memory** and reading context.

```python
class Hippocampus:
    context = {
        "characters": {},     # {"he": "Jean Valjean"}
        "location": "",       # "Paris"
        "tense": "",          # "past", "present"
        "mood": "",           # "violence", "love"
        "thread": [],         # Last N sentences
    }
```

### 5. CHEMISTRY (Modulation) ⏳ To do

**Virtual neurotransmitters** that modulate activation.

| Chemical | Effect | Usage |
|----------|--------|-------|
| Dopamine | Reinforces | Reward, learning |
| Serotonin | Stabilizes | Mood, coherence |
| Acetylcholine | Activates | Attention, focus |
| GABA | Inhibits | Filtering, noise |

---

## 🔬 Key Concepts

### SGBDOCN — The living DBMS

A classic DBMS is **dead** (Thanatos): you ask a question, it returns a row. Always the same. The SGBDOCN is **alive** (Anima): it learns while answering, its links strengthen, meaning converges.

The same pipeline does everything: read, learn, answer. Pac-Man eats it all.

### Convergence Matrix

A human-readable text file that defines a micro-brain:

```
## GREETINGS
hello = hi, hey, yo, what's up
hello → hello welcome to Marco

## INSULTS
jerk = idiot, moron, fool
jerk → let's calm down we're all civilized here
```

Registers (## GREETINGS, ## INSULTS) become diffusion layers. The more you add, the more meaning converges.

### Standalone Galaxy

```
Create Galaxy "Marco_the_barista"
  → 1 central sun (0, 0, 0)
  → 405 beacons positioned (Fibonacci spiral)
  → 50 concepts, 293 index entries, 41 pairings
  → Ready to serve. Standalone. No need for 46,006 concepts.
```

A galaxy is the equivalent of `CREATE DATABASE` + `CREATE SCHEMA` in SQL. Except it fits in a text file and learns on its own.

### Three Neuron Rule

The **C.elegans** brain (1mm worm) has 302 neurons and can: feed, reproduce, avoid danger, learn.

**All with while loops.**

### Russian Dolls

Information nests infinitely:
```
Level 0: Letters     c, o, f, f, e, e
Level 1: Word        coffee
Level 2: Concept     coffee latte (family: latte, cream)
Level 3: Register    BARISTA ORDERS
Level 4: Domain      Restaurant
Level N: ...         Concepts of concepts of concepts
```

Each level **emerges** from the previous one. `class Concept(Beacon)` — a beacon containing beacons.

---

## 📊 Scalability

| Metric | Classic LLM | CCADH |
|--------|-------------|-------|
| RAM required | 100+ GB | ~150 MB |
| GPU | Required | No |
| Training | Weeks | Real-time |
| Cost | $$$$ | Raspberry Pi |
| Hallucinations | Frequent | Impossible (not read = not known) |
| Transparency | Black box | Every link traceable |

---

## 🗺️ CCADH Roadmap

### Phase 1: Foundations ✅

- [x] Dendritic architecture (letter neurons)
- [x] Thalamus (central router, menu v4.0)
- [x] ADH tokenization (Pac-Man)
- [x] Russian dolls (Concept inherits from Beacon)

### Phase 2: SGBDOCN ✅

- [x] BSCW (multi-word concept detector)
- [x] Stimulus → response pairing (parrot)
- [x] Convergence matrix (.txt)
- [x] Standalone galaxy (micro-SGBDOCN)
- [x] Feeding / dialogue compartmentalization
- [x] Barista ☕ (interactive prompt)

### Phase 3: Brain (In progress)

- [ ] Cerebellum (diffusion loops)
- [ ] Hippocampus (short-term memory, context)
- [ ] Reading mode (cerebellum + hippocampus + BSCW)
- [ ] Tense registers (conjugation)
- [ ] Action registers (violence, help, movement)
- [ ] Layer intersection → emergent meaning

### Phase 4: Modulation

- [ ] Chemistry (dopamine, serotonin, etc.)
- [ ] Selective attention
- [ ] Contextual mood

### Phase 5: Autonomy

- [ ] Elegans engine (pure while)
- [ ] BooChom training wheels removed
- [ ] True emergence

### Phase 6: Hardware

- [ ] Standalone (.exe)
- [ ] Raspberry Pi
- [ ] "Personal Alexa" offline — but one that learns ☕

---

## 📁 Main Files

| File | Role | Lines |
|---|---|---|
| `marco_dendrites.py` | Core — Beacons, Concepts, BSCW, tokenization | 3,534 |
| `thalamus.py` | Menu v4.0, barista, galaxy, orchestrator | 4,016 |
| `dialogue.py` | Dialogue module, 4 modes | — |
| `matrice_marco_v3_compact.json` | ADH Matrix (46,006 concepts, 102 suns) | — |
| `convergence_matrix_v1.txt` | Convergence Matrix (50 concepts, 14 registers) | ~100 |

---

## 👥 Team

### Human

**José Walocha** — Architect, visionary, Ch'ti. Valenciennes, Nord, France.

### AI (under human direction)

- **Le Duke** (Claude/Anthropic) — Code, architecture
- **Marcel** (Mistral) — Philosophy, cybernetics, diagnostics
- **Biloute** (ChatGPT) — Standards, ethics
- **Didier** (Qwant) — Research

---

## 📄 License

**GNU GENERAL PUBLIC LICENSE — Version 3**

Copyright (C) 2026 José Walocha

CCADH is an open research project. All improvements must be shared.

---

## 🐟 Final Word

> *"You don't need a datacenter to think. C.elegans proves it."*

> *"A classic DBMS is dead. The SGBDOCN is alive."*

> *"50 sentences and it answers. Not 50 billion tokens."*

CCADH is not a race for power. It's a return to fundamentals: understanding how intelligence **emerges**, not how to **simulate** it.

---

*"In the beginning there is inert matter, but inert matter is bored out of its mind..."*
