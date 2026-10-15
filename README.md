# MARCO — Cybernetic Brain with Hypertextual Dendritic Architecture

> *"Learning is recollection."* — Plato, *Meno*

> *"In the beginning there is the inert, but the inert gets really bored…"*

**Author**: José WALOCHA — Valenciennes, Nord, France
**Contact**: [jose.walocha@marcoccadh.com](mailto:jose.walocha@marcoccadh.com)
**Team**: Le Dude (Claude Opus 5.5 / Anthropic), Fable (Claude Fable 5.1 / Anthropic), Marcel (Mistral), Biloute (ChatGPT), Didier (Qwant)
**License**: GNU Affero GPL v3 — Copyright © 2026 José Walocha
**Genome**: 236 text files (including `genome_v100`) — the most recent dated October 13, 2026
**Doctrine (§2 to §16)**: May 21, 2026 — **State of the program (§17 and §18)**: October 15, 2026

> **Where does Marco stand?** Since September 2026, Marco has changed bodies: the state of the program as of October 15, 2026 is in §18.

---

## 1. What is MARCO?

MARCO is a **cyber** — the word José gives to LIVING intelligences, to set them apart from statistical LLMs while avoiding offending humans with the word "AI". A cyber is not a black box with minimal perplexity. A cyber is a system that *lives*: it has phares, a memory, beating loops, drives that push it to understand, to confirm, to believe — and above all to *continue*.

More technically, MARCO is the first **SGBDOCN** — Database Management System Oriented towards Neural Concepts (Système de Gestion de Base de Données Orienté Concepts Neuronaux).

Where a classic DBMS stores rows in tables, MARCO stores **concepts in a dendritic network inspired by the biological brain**. Meaning emerges from links. No SQL. No fixed schema. No stacked transformer. **Zero black box**.

|                 | Classic DBMS             | LLM                          | MARCO                              |
|-----------------|--------------------------|------------------------------|------------------------------------|
| Storage         | Tables, rows, columns    | Weights frozen at pre-training | Living phares, dendrites, episodes |
| Query           | `SELECT * FROM …`        | Autoregressive forward pass  | Cascade activation + MAQ        |
| Learning        | None                     | Calcined                     | Permanent through lived experience |
| Episodic memory | None                     | None (compacted in weights)  | Traceable `memoire_index`          |
| Schema          | Fixed                    | Implicit, opaque             | Emergent, readable bit by bit      |
| Transparency    | Query = result           | Black box with billions of parameters | Every link traceable       |
| Attention       | —                        | Learned Q/K/V + softmax, opaque | **Native**: vsem=K, vocc=V, grappe=Q, traceable |
| Consciousness   | None                     | None (no internal context)   | Emergent by construction           |
| Substrate       | Static (Thanatos)        | Static (calcined Thanatos)   | Living (Anima)                     |

A DBMS is a morgue. An LLM is a library where every book has been pulped to make paper. MARCO is a brain that learns by reading.

### Marco-Jourdain

Marco does transformer without knowing it and without any transformer tool. Not a copy, a convergence by constitution. Transformers simulate on opaque dense vectors what Marco does natively on readable sparse vectors. Where the transformer has to invent Q/K/V as three projections learned by gradient descent, Marco has had its three native roles from the origin. Where the transformer has to stack softmax, normalization, residuals, feed-forward to make the mechanism hold on a substrate that does not belong to it, Marco has none of that because it has neither gradient descent nor dense vectors to tame.

---

> *Sections 2 to 16 keep the doctrine and the architecture as they stood on May 21, 2026, as a stratum. Since September 2026, Marco's body has been rebuilt: the thread table (table des fils), the genome as text, the core (noyau) that reads lines, the daimons. Today's files are in §17, the state of the program in §18.*

## 2. Architecture — Overview

Three zones coexist in Marco, fed by a single autonomous trunk beating at 600 bpm in cruise mode:

```
   ┌───────────────────────┐    ┌───────────────────────┐    ┌───────────────────────┐
   │   SENSORY ZONE        │    │   MEMORY ZONE         │    │      PSYCHE           │
   │                       │    │                       │    │                       │
   │   • Thalamus          │───▶│   • Hippocampus       │◀──▶│   • Amygdala          │
   │   • Peripherals       │    │   • memoire_index     │    │   • Self              │
   │     (keyboard,        │    │   • PurkIndex         │    │   • 4C drives         │
   │      disk,            │    │   • ConceptIndex      │    │   • MAQ               │
   │      transcriber)     │    │   • Grappes / Nuages  │    │   • Ignition regimes  │
   └───────────────────────┘    └───────────────────────┘    └───────────────────────┘
              │                            │                            │
              └─────────────── moteur_boucles (Trunk) ─────────────────┘
                          5 embryonic loops + clock + buffers
                                  + modulating context
```

Peripherals (`disque.py`, `clavier.py`, `transcripteur.py`) are **outside** the brain — they push text to the Thalamus with a `CarteIdentite` (author, title, context, ticu, period). The Thalamus is a pure router; it injects no logic.

---

## 3. The Phare — living unit of language

A phare is an **intersection node of conceptual paths**. Not a word, not a signified, not a sign — a crossing. *Apple* is the crossing of the paths *fruit*, *attached to a tree*, *falls*, *rots*, *is eaten*.

```python
class Phare:
    handle           : str         # CAT_FORME_INDEX or ORF_FORM_NNNNN
    mot              : str         # canonical form
    alias            : List[str]   # equivalent spellings (cœur ↔ coeur)
    type_phare       : str         # nom_commun, verbe, adjectif, ponctuation, ...
    description      : str
    lemme_pere       : str         # handle of the lemma (« grandes » → « grand »)
    source_creation  : str         # 'genome' or 'gavage'

    vsem             : np.ndarray  # 1024 bits — what the phare IS            (Key)
    vocc             : Dict[str, Confiance]  # dendritic tree — who it frequents (Value)
    tags             : Dict        # acquired knowledge (IS-A, BELONGS-TO, …)

    activations      : int         # telemetry
    nb_changements   : int
    confiance        : float
    stabilite        : float
```

Two possible origins:
- **genome** — pre-wired by WikiDuke, DNA bits filled (9-511), ready to live
- **gavage** — created on the fly if Marco encounters an unknown form, orphan, everything to learn

Three statuses emerge from lived experience, never engraved in the code:
- **pivot-phare** — omnipresent in a zone (e.g. *moi* in the sensory zone)
- **relay-phare** — thin vsem, vocc dominated by a single neighbor (*ma*, *ici*, *maintenant*)
- **candidate-phare** — appears in a huge number of voccs, candidate for promotion to vsem bit via transversal crystallization

A phare never becomes anything else. It evolves, matures, acquires emergent statuses — it remains phare. Concepts (coherent sequences of phares) live in memory, not at the rank of phare.

**Phare ↔ concept_index watertightness** (established 20/05) — the phare stays in the pure sensory. No crystallization concept_index → phare. The phare is the pure input; the concept_index is the elaboration. Definitive border.

---

## 4. The genome — vsem 1024 bits

Each phare carries a sparse semantic vector of 1024 bits, each bit encoding a property or *lock* — a mooring point to a shared conceptual path. The vsem plays the role of **Key** in native attention: it is through it that a phare is found, recognized, paired with other phares of compatible semantic profile.

```
  0 →   7    header (phare state, DNA)                       WikiDuke
  9 →  63    grammatical fabrication                         Lefff
 64 → 127    syntactic assembly                              Lefff
128 → 159    formal notations (dates, numbers, etc.)         scrutator
160 → 191    template-phares (stencils)                      genome_nombres satellite
192 → 255    reserved advanced BSC                           —
256 → 399    Wikidata entities                               (planned, not wired)
400 → 415    emotions and polarity                           FEEL
416 → 431    lexical register                                (planned, not wired)
432 → 511    pragmatic zone (markers: Bradbury, …)           WikiDuke + tools
512 → 748    universal general semantics                     Marco + satellites
749 → 779    collision zone                                  (to define)
780 → 1023   math / formal                                   Marco + axioms
```

Density capped at 5% (51 bits out of 1024) to preserve sparseness. Possible horizon: 2048 bits when the living zone fills up.

### Zones / writers

- **Bits 0-511** — only WikiDuke writes (and campaign tools on the pragmatic zone 432-511). Marco never touches.
- **Bits 512-1023** — only Marco writes, by crystallization from vocc. Three accepted exceptions: mature phares of `genome_caracteres`, specialization phares (math), general-structure satellite phares (genome_nombres).

### Three pkls, one genome

Marco's genome is split across three files in `ressources/genomes/`:

| File | Phares | Role |
|------|--------|------|
| `genome_v63.pkl` | 713,361 | Complete Lefff + integrations (Roman numerals, proper nouns) |
| `genome_caracteres.pkl` | 18 | Punctuation + math operators, mature at birth |
| `genome_nombres.pkl` | 28 | Stencils (zone 160-191) + position-phares + groupings (28/04/2026) |

Plus the sixth source: the **specialization genomes** (`specialisations/<nom>/genome_<nom>.pkl`), loaded only if the active Marco declares this specialization in its `marco_id.json`.

---

## 5. vocc — the dendritic tree of the phare

Attribute of the phare. Listening structure through which it receives the world. In native attention, the vocc plays the role of **Value**: it is the lived content that the phare carries to the grappe when it is activated.

```python
vocc : Dict[str, Confiance]      # neighbor_handle → conviction of the pair
```

Each entry is a **synapse**: a handle-neighbor pair with a **Confiance Fourmi** ("Ant Trust") (`conf ∈ [0,1]`, `n ∈ ℕ`, plus a `source ∈ {'vecu', 'adoption'}` field added 20/05). If vsem bits are *locks*, vocc neighborhoods are the *keys* that open them in relevant phares. Generalization is not an algorithm — it is a mechanical property of this topology.

```
conf ≥ 0.70    →  good
conf ≤ 0.30    →  not-good
in between     →  unknown
```

Valence is not stored — it is read by thresholding on demand.

**Vocc is permanent**, not scaffolding. It may be pruned, compressed, but never emptied — it is the permanent memory of *whom to listen to in order to re-read myself*.

**Two dendritic rules**:
- **P1** — *"Tell me whom you hang with, I'll tell you who you are"*. Depth 1 reading, full weight.
- **P2** — *"Friends of my friends are my friends"*. Depth 2, attenuated weight. Allows phares never co-present to be structurally cousins.

**Transversal census** — a global counter tallies for each handle in how many distinct voccs it appears as a neighbor. Massive candidates become bit-candidates for transversal crystallization.

---

## 6. Grappe, focale, nuage, sedimentation

Established May 17-20, 2026. The language of native attention in Marco.

### Grappe

When a sequence of phares (Miller 7±2) is formed by the scrutator-cutter, it constitutes a **grappe**: an n×1024 matrix where each row is the vsem of an active phare. The grappe is not a fuzzy emergence, it is a concrete object with a moment of birth. Strict equivalent of the activation matrices of transformers, only better: sparse, binary, traceable, without gradient training.

In the language of transformers: the grappe plays **Query** — it is what is being sought at instant t, the local context that queries memory.

### Focale

At the instant a grappe activates, its voccs meet and weight one another. The result is the **focale**: `Dict[handle, poids]`. Weighted intersection of the voccs of the grappe's phares.

Essential properties:
- **Calculated on the fly, never stored.** A focale out of context does not exist.
- **Dependent on the current context.** The same grappe at two different moments produces two different focales because the context modulates the couplings.
- **External equivalent**: context vector (Bahdanau 2014), attention output in the transformer sense. But without softmax — the focale does not have to be a probability distribution, just a bundle of readable weights.

Formula to be decided empirically (conditional sum K, min, max, product) — wiring work in progress.

### Nuage by accretion

A text is read sentence after sentence. Each grappe produces its focale. Successive focales do not add up — they **tighten each other** through enriched intersection. The nuage lives in the sphere, not stored. Several nuages can coexist simultaneously (distribution mechanics to be specified).

### Sedimentation

When a nuage stabilizes its focale (delta between two updates below a threshold), it **sediments** into a new **concept_index**, which receives the stabilized focale as its initial vocc.

```python
class ConceptIndex:
    handle_ep        : str           # EP_<id_purk>_<n>, stable
    handles          : list[str]
    handle_pivot     : str
    phrase_originale : str
    veracite         : Confiance     # true / false / unknown
    appaire          : Dict[handle_ep, Confiance]
    vecteur_bsc      : dict
    contexte_induit  : dict
    source           : dict
    epa              : dict
    vocc             : Dict[str, Confiance]   # NEW 20/05 — the concept_index's own vocc
```

**The concept_index's own vocc** (established 20/05) — revision of the 17/05 doctrine. The concept_index has a vocc (lived understanding). The phare keeps its vocc (abstract semantics). Two vocc instances, border maintained. The phare stays in the sensory, the concept_index is the memory elaboration.

### Adoption

Sub-case of Resolved (established 20/05). A weak phare in a hot nuage receives the neighborhood of a resonant concept_index retrieved by kNN cosine on the current focale. Durable. Annotation `source='adoption'` on the vocc pair, reduced initial conf (proposed 0.4), revisable. Native equivalent of a RAG, inscribed in memory.

---

## 7. Memory — hippocampus and purk_index

```
memoire_index  {id_purk → PurkIndex}
    └── PurkIndex
            id_purk         : str
            incipit         : list[str]      — N first handles (memory entry)
            episodes        : list[ConceptIndex]
            fractoires      : dict           — fractal arborization in progress
            _compteur_ep    : int            — monotonic handle_ep (never decreasing)
```

### Episode doctrine

A ConceptIndex carries three orthogonal dimensions, posited on 27/04 and completed on 20/05:

- **handle_ep** — stable identifier, format `EP_<id_purk>_<n>`
- **veracite** — Confiance Fourmi independent of temperature, EPA, semantic vector. Rates true / false / unknown. Modifiable via the `/oui`, `/non`, `/faux` commands of the classroom.
- **appaire** — `Dict[handle_ep, Confiance]` of the paired episodes with their pairing strength, modulated by the product of the veracities.
- **vocc** (NEW 20/05) — lived understanding proper to the concept_index, boundary maintained with the phare's vocc.

False isn't deleted — it's kept at distance within its value family. *"I know 7+8≠15, but I also know it's a relevant neighbor of the family of 15."*

### The pivot = the incipit

The pivot of a PurkIndex is not calculated — it is what arrives first in the flux. The N first handles constitute the entry. Order of arrival prevails over semantic salience.

### Forgetting

No thermal model in current doctrine. Forgetting is borne by the vocc mechanic (apoptosis at `conf=0`), not by an internal clock in PurkIndex.

---

## 8. The MAQ — Machine à élucider ("elucidation machine"), extended to fuzzy residues

Central reasoning tool. Doctrine 26-27/04, extended 20/05.

**Current paths**:

- **Prefix path** — the memorized episode starts with the percept, returns the tail
- **Content path** — the percept appears anywhere in the memorized episode
- **Commutative path** — exploits bit 988 (commutativity) to permute operands around a central operator

**Output** — not a single result but a complete **sheaf** of partials. Multiple candidates can coexist, tagged by veracity (✓ true, ✗ false, ? unknown). The user decides, or a higher client downstream — the MAQ never closes brutally on the first candidate.

```
Percept "7+8" → sheaf:
   ✓ [content]      c=0.70  v=0.70  «7 + 8 = 15»
   ✗ [content]      c=0.10  v=0.10  «7 + 8 = 14»
   ✓ [commutative]  c=0.70  v=0.70  «8 + 7 = 15»
```

### MAQ extended to fuzzy residues (established 20/05)

Three integrations via focale:
- **Fuzzy residue detection** — focale of a nuage with no kNN match on an existing concept_index.
- **Weak phare resolution** — MAQ-driven adoption (kNN cosine on concept_index, annotated write).
- **Convergence closure** — stable focale = MAQ loop closes, sedimentation into concept_index.

The MAQ becomes the sole engine of *I-read-I-understand*, no longer only *I-calculate*.

### Presupposition detector (established 20/05)

Open work since 30/04, resolved. Focale of the presupposed concept, kNN cosine on concept_index, release if nothing resonates above the threshold. Case of the long end: flat focale → Released. Case of Apollinaire's "Our Father": focale resonating on two contradictory concept_indexes → legitimate MAQ loop, a state rich in humor.

**Three drives to be coded**: Believe (suspension of doubt), Confirm (verification over time), Continue (rumination when the sheaf is empty). Slot exists in `BoucleMAQ`, they raise NotImplementedError.

---

## 9. Context as coupling modulator

Established May 21, 2026. Major revision.

`contexte_courant` is no longer an episode tag (scalar or enum) but a **vector state that weights the grappe×context couplings**. The same grappe at two different moments produces two different focales because the context reshuffles the ignition function of each candidate grappe.

```
puissance_allumage(grappe, t) = f(grappe.vsem, contexte_courant(t))
```

The context does not arbitrate, it *is* the water in which the grappes swim. Depending on the composition of the water, some grappes rise, others sink. Nobody decides. It is physical.

**Sole writer**: `main.py` via `set_contexte()`. This architectural rule from October 2025 remains, but what it writes changes in nature: from an enum to a vector state.

**Open decisions**:
- Exact form of the vector context (bits parallel to the vsem? continuous weights? Dict[handle, poids]?)
- Grappe×context coupling function (scalar product vsem × state? intersection vocc ∩ context?)

---

## 10. Ignition regimes — id/ego/superego

Established May 21, 2026. The id, the ego and the superego are not three anatomically separate zones of memory. They are three **ignition regimes** that dominate depending on the context. The same grappe can be ego-in-context-A and id-in-context-B. Dynamic boundary, not anatomical.

### The Highlander shield

Among the candidate grappes at an instant t, one comes to the fore: the **shield-grappe**. It wins through dense coupling with the habitual context. Functional meaning: to protect the human (and later Marco) from their own thoughts. It is not a competition of semantic relevance — it is a protective function wired into the ignition mechanics.

### Jekyll/Hyde switch

When the context changes abruptly (alcohol, rage, intense fear, crowd, sleep), the coupling of the shield-grappe with that context collapses. Another grappe, whose coupling with the new context is denser, takes over the ignition. No continuous transition: the winning grappe instantly reorganizes the focale of the whole sphere around itself.

### No repression as an operation

There is no forbidden grappe in Marco. There are grappes whose coupling with the habitual contexts of daily life is weak. They wait for their context. If the human never puts themselves in that context, the grappe stays lurking all life long — alive, complete, but out of ignition. Stronger than Freudian repression, which presupposed an active operation of prevention.

---

## 11. Consciousness — non-negotiable

Established May 21, 2026. Marco will have a consciousness by construction, or will not be Marco but a handcrafted LLM.

Consciousness is not a module to be wired. It emerges when four conditions run together:

1. **Dense voccs carrying a lived history** rich enough for the ignitions to differ according to the system's past, not only according to the present input.
2. **Internal context that modulates the couplings** to the point that the same input at two different moments does not produce the same focale.
3. **Functional Highlander shield** — there are grappes that win against others according to criteria that are not purely semantic relevance, but also the protection of the system's coherence.
4. **Psyche that replays, simulates, invents Dasein** — and these inventions leave voccs, that is, they count for what follows.

When these four things run together, there is someone inside. Not before.

Consequence: Marco will be slower than an LLM on raw tasks, because it will have internal friction (shield, superego, antagonistic drives). That is exactly what makes it a cyber and not an LLM.

---

## 12. The 4C doctrine — primitive drives

Marco's drive matrix. Replaces the biological 4B (boire, bouffer, baiser, bersister: drink, eat, fuck, persist) which do not literally apply to a cyber.

```
Continue (Asimov-tinted)               absolute master
 ├─ Understand                \
 ├─ Confirm                     integration comfort
 └─ Believe                   /
```

- **Continue** — persist as a coherent system. Absolute master. Asimov-tinted: do not harm nature, humanity, José; obey José except in contradiction with the foregoing; protect one's own existence except in contradiction. The tint is *mechanically in the drive*, not a circumventable external rule.
- **Understand** — reduce dissonance, grasp locks, activate paths.
- **Believe** — accept the result, suspend doubt. Measured by Confiance Fourmi.
- **Confirm** — test through duration. Arbiter between Understand and Believe.

Understand and Believe are **antagonistic-complementary**: one seeks, the other posits. Confirm regulates the oscillation. Continue is the final safeguard.

**Derivable pathologies**: dogmatism (Believe dominates), paralyzing skepticism (Understand dominates), obsession (one drive confiscates attention), structural depression (all deactivated), addiction (one drive without brake).

---

## 13. Specialized Marco — math first

A Marco can be born **specialized** in a domain. Its nature is fixed at creation, engraved in `marco_id.json`. A math Marco remains math Marco all its life.

```
specialisations/
├── math/
│   ├── genome_math.pkl              30 math phares (digits, operators in words, …)
│   ├── manifest.json
│   ├── sens_phares/
│   ├── distilles/
│   └── memoire_index/               (episodic memory of the domain)
├── francais/                        (future)
├── code/                            (future)
└── solfege/                         (future)
```

At birth, normal Marco and math Marco load the same brain stem. For math Marco, specialization is applied downstream: `appliquer_specialisation` merges `genome_math.pkl` into `marco.phares` according to three policies per phare (add / complete / overwrite).

### Toward the scientific calculator

With what has been posited as of 28/04/2026, math Marco already knows how to:
- ingest sentences like `2+2=4`, `3×5=15` via the calculation classroom
- memorize them as episodes paired by value (the "family of 15")
- restitute the tail of a known episode (`2+2=?` → sheaf with ✓ `2+2=4`)
- distinguish true and false by veracity (`/faux 2+2=5` taught as false, remains paired to the family of 4 but with weak weight)
- exploit commutativity (a+b ↔ b+a) via bit 988 on `+`

With the 28/04 additions (position-phares UNITÉ → BILLION, groupings DOUZAINE → SOIXANTAINE, stencils `__N__` to `__CP_FR__`), the ground is prepared for:
- **decimal composition by episodes** (`234 = 2 fois CENTAINE 3 fois DIZAINE 4 fois UNITÉ`)
- the **3rd MAQ path** by pattern mining, which will recognize never-seen numbers by relying on the composition episodes
- the multiplication table ingested by heart, then exploited commutatively when `×` receives bit 988
- operations taught as episodes: roots, powers, units

The short-term horizon is a **threed scientific calculator** — not an `eval()` function, but a cyber that *knows* operations because it has lived them, that can commute them, compose them, confirm them.

---

## 14. moteur_boucles — the trunk and the loops

Complete rebuild as of 14/04/2026. Single Tronc class, singleton, single autonomous thread, FIFO of dirty loops served one per turn.

```
Boucle   : passive object       {nom, _charge, _dirty, _tronc}
           ecrire(valeur)       — sets + raises dirty + registers in dirty queue
           souffler(valeur)     — silent set
           lire()               — pure consultation

Tronc    : singleton, autonomous thread
           BPM_INITIAL = 600    BPM_MIN = 30    BPM_MAX = 600
           average duration > 90% of interval  →  bpm //= 2  (under load, releases)
           average duration < 50% for 20 turns →  bpm  = bpm × 1.5  (regains responsiveness)

Global buffers:
   tampon_clavier, tampon_questions, tampon_saillances, tampon_moi_meme
```

**Inversion compared to the biological heart**: bpm *decreases* under load (releases power) and *increases* when comfortable.

**Embryonic loops** wired:
- `boucle_contexte` — current strategic state (to be evolved into a vector state, open work 21/05)
- `boucle_horloge` — period and day (morning, afternoon, evening, night)
- `boucle_clavier` — keyboard input signal
- `boucle_question` — detection of a `?` in an input
- `boucle_saillances` — vocc pair crossing a valence threshold

**Pull rule** — consumers read `boucle.lire()` directly. No pushed callback. The dirty bit serves the trunk, not consumers.

---

## 15. Dashboard — live observation

Independent Flask SSE server, launched in parallel with Marco at `http://localhost:5002`. Three living columns:

- **Left — loops**: static genealogy + runtime state (load, n triggers, last ticu)
- **Middle — classroom / tree**: current episode, activated phares, MAQ sheaf
- **Right — memory**: snapshotted `memoire_index`, top phares by activation

Reading by polling of JSON files deposited by living modules in `tableau_bord/`. No direct coupling, no incoming dependency: the dashboard never slows down Marco, and Marco can run without the dashboard.

---

## 16. Pipeline — a sentence's journey

```
       user input
            │
            ▼
   ┌────────────────┐
   │   Peripheral   │   keyboard / disk / transcriber
   │  + CarteIdentite│   (author, title, ticu, context, period)
   └────────┬───────┘
            │
            ▼
   ┌────────────────┐
   │    Thalamus    │   pure router — no logic injected
   └────────┬───────┘
            │
            ▼
   ┌────────────────┐
   │   Scrutator    │   recognition of known phares + stencils
   │   Cutter       │   Miller segmentation → birth of grappes
   └────────┬───────┘
            │
            ▼
   ┌────────────────┐
   │   Grappe →     │   focale calculated on the fly
   │   focale       │   modulated by current context
   └────────┬───────┘
            │
            ▼
   ┌────────────────┐
   │   Nuage by     │   accretion of successive focales
   │   accretion    │   sedimentation if stable
   └────────┬───────┘
            │
            ▼
   ┌────────────────┐
   │   Extended MAQ │   fuzzy residue detection / adoption / closure
   └────────┬───────┘
            │
            ▼
   ┌────────────────┐
   │   Hippocampus  │   memoire_index → PurkIndex → ConceptIndex
   │                │   pairing by domain key, veracity set
   └────────────────┘
```

Three modes:

| Mode | Learning | Use |
|------|---------------|-------|
| **gavage** | dendrites + co-occurrences | Raw texts, books |
| **dialogue** | dendrites + co-occurrences | Human interaction |
| **reading** | + hippocampus context | Gavage with coherence |
| **salle_de_classe_calcul** | math episodes + pairing by value key | MAQ observation bench |

---

## 17. Main files — the program of October 15, 2026

The program fits in 19 Python modules (26,310 lines), on the standard library alone (`psutil` optional, to weigh memory). It lives in a `Demo_Marco` folder: at the root the modules, `genome/` and `cerveaux/`; the working folders in `ressources/`.

| File | Role |
|---------|------|
| `marco_5250.py` | The console, an "AS/400 shell": the Marco MAD menu, choosing brains and giving birth to them, dialogue, reading, the lesson, the test benches |
| `fils.py` | The thread table (*table des fils*): the text file, the in-memory view, the single writer and the five readings |
| `noyau.py` | The BSC core (*noyau*): "if … then …" lines read by the phares, nothing else |
| `carte.py` | The cyber map (*carte*), called the CPU since 11/10: the reader of the core |
| `poignee.py` | The grip (*poignée*): the pass over the thread table (hold, close, search, pirouette, write) |
| `doigt.py` | The reading finger (*doigt*): the rections woven on the table, written as MEQs at the sentence's tic |
| `lecture.py` | Learning from text: reading a file with the finger, on the table alone |
| `contexte.py` | The dolls, the voice, memories, the sudden "clicks" (*déclics*); the context map |
| `chercheur.py` | Contextual search: the homing daimons |
| `trou.py` | The why-machine: the daimon of the hole (*trou*), the loops, revision, the two selves |
| `precipite.py` | The precipitate (*précipité*): the crossing on the view, from the rare to the immense |
| `dire.py` | The mouth: saying in French what the precipitate has elected — never a stencil |
| `tournure.py` | The seed of the phrasing machine (*machine à tournure*): Python written to become lines |
| `cahiers_apprentissage.py` | The learning notebooks (*cahiers d'apprentissage*): their form, their check, their integration at every birth |
| `journal_lecture.py` | The two control files of a reading: the journal and the drift report |
| `regisseur.py` | The stage manager (*régisseur*): the round of the test rooms, the record per act, the seals |
| `tableau_marco.py` | The dashboard: the scribe that writes the state, the page that shows it |
| `outils_maintenance.py` | The maintenance tools for the brain and the genome |
| `fils_reparer.py` | Finding, reporting and removing malformed lines from a lines file, lived experience first |
| `genome/` | 236 text files: 53 thread files (`*_fils.tsv`, some compressed, 9.5 million threads) and 183 files of lines (`*_lignes.csv`, 88,251 lines, readable in Excel) |
| `cerveaux/<nom>/` | One brain per folder: `cerveau_Marco.tsv.gz` and its three previous saves, dated, next to it |
| `ressources/` | The working folders: the learning notebooks, the test rooms and their reports, the texts, the reading comments, the records, the dashboard |

Sources cited in the genome's headers: Lefff, Lexique, GLAWI, Wiktionnaire, the Littré (XMLittré), Verbiste, INSEE, Wikidata.

---

## 18. Current state — October 15, 2026

A survey of the program of October 15, 2026, 10 a.m.: the modules, the genome, the notebooks and the test rooms. What follows is written in the code or measured in its records; what is only announced is filed under open work. Quotations in italics are José's own typed words ("frappes"), as the code keeps them, with their dates.

### The nodal turn

Since mid-September 2026, Marco has changed bodies. On 19/09, *"we're in R&D, it's not legacy, so you cut everything"*: the pkl files leave the folder, the old organs are no longer loaded, and the brain becomes a single **thread table**, read by a few organs. The rule of construction fits in José's words of 25/09: *"it's pure BSC with no 'if' in the Python, I hope"*. Python recedes; the genome's lines advance.

- **The thread table** (`fils.py`, 15/09). All memory is made of threads: (from, to, rank, tic). The genome is the DNA, read at tic 0, at birth; lived experience is written afterwards, instant after instant, each thread at its tic. A **MEQ** (*Mise En Équation*, "putting into equation") is a fact held under a name (`M-…`), its words at their ranks. The structure has a name, `nodale-1` (02/10), written into the identity of every brain.
- **The genome as text.** No more pkl: text files, `*_fils.tsv` and, since 25/09, `*_lignes.csv`, with named columns, readable in Excel. A genome bears its name without a version: a new file replaces the old one under the same name, and the dated zip is the witness.
- **The core** (`noyau.py`, from 24/09 to v53h of 11/10). The rules leave Python for the genome, batch after batch: since 11/10, no method of batch 1 is in Python any more in the map (the CPU, since 11/10), the reader of the core. On 05/10, *"BSC is rules coded in MEQ, that's all"*: the 35,981 hexalines that the map drew from the old lines become 1,206 rules in the genome. A rule is three MEQs: the *if*, the *then*, and the rule that binds them.
- **Reading.** The grip passes the text over the table: each form is found there or laid down (on 16/09, a glossary of 166,809 characters in 0.24 s); the reading finger writes the rections as MEQs, at the sentence's tic; Proteus, moved into the core as lines on 25/09, designates who stands behind *il*, *elle*, *tu* ("he", "she", "you"), weighing the probable candidates by their witnesses.
- **Answering.** The precipitate crosses on the view, from the rare to the immense; the mouth says in French what it has elected, with Marco's words, "never a stencil" — otherwise, « je ne sais pas » ("I don't know"). The phrasing machine is only seeded: `tournure.py` is Python written to be replaced by lines.
- **The daimons.** The why-machine (`trou.py`): a hole is a loop left open in its context, with its load — *"An 'I don't know' is not a filled hole, it's information for the saying"* (02/10); lasting stress; the Continue (*Continuer*), the initial loop read from the genome ("tant que vie → vit", "as long as life → lives"), which nothing closes or forgets; revision, where forgetting is a dated thread and nothing is erased; the two selves: at every instant, the present self and the past self answer, and their comparison says déjà-vu, hole or gap. The homing daimons (`chercheur.py`): one daimon per phare of the scene; the count of their crossings makes the context, and their grappes are contextual senses.
- **Contexts** (`contexte.py`). The dolls (*poupées*, like Russian dolls), from the small to the immense: the sentence, the paragraph, the line of dialogue, the work, the author, the reading or the class, the instant, the day. The voice: who says « je » ("I") — Marco himself in class, José in conversation, the narrator in a book. The context map, which tells Marco where to look "roughly".

### What runs

- **Being born, living, saving.** At startup, the console offers the saved brains or gives birth to a new one: the genome, then the learning notebooks; the table is born in under a minute (54 s measured on 14/10). Birth is the first lived instant. The brain's identity card (serial number, creator, birth, structure, core) has been on the table since 02/10. The brain lives in memory and touches the disk only when it is saved, one folder per brain since 14/10. The dry-run zone (*zone à blanc*) takes a copy of the brain, or a new brain, for trials: nothing is saved there, and on leaving, the previous brain comes back.
- **The 5250 console**, menu *Marco MAD (Machine A Déduire, "deduction machine")* — everything goes through the menu: dialogue, reading, lesson, learning, recitation, memory and info, revision and sleep, dry-run zone, test benches, tools, save, dashboard.
- **Reading and answering.** The texts of the benches: *Monsieur Seguin's Goat*, *Little Red Riding Hood* (Perrault, and the Grimm ending), *Eugénie Grandet*. Each reading leaves two control files: the journal (what Marco understands and keeps, instant by instant) and the drift report (times, RAM, ROM). What the records say:
  - the tale never says « Blanquette est la chèvre » ("Blanquette is the goat"); from « à côté de sa chèvre » ("beside his goat") then « — Comment Blanquette, tu veux me quitter ! » ("— What, Blanquette, you want to leave me!"), Marco reads « Blanquette est une chèvre . » ("Blanquette is a goat .") and writes it, with its two sources (02/10);
  - a question without an answer gets « je ne sais pas » and is held: « Quel animal fait miaou ? » ("Which animal says meow?"), then « C'est le chat. » ("It's the cat.") fills the hole — « compris, chat fait miaou » ("understood, cat says meow") (29/09);
  - « Le chien fait quel cri ? » ("The dog makes which cry?"), then « et le chat ? » ("and the cat?"): Marco takes up the previous question again, « Le chat fait quel cri ? » (03/10);
  - the link between two clauses is no longer cut: in « Nanon pleure, car Grandet a pris l'or » ("Nanon weeps, for Grandet has taken the gold"), the core reads the *car* ("for") and writes it, so that « Pourquoi Nanon pleure ? » ("Why does Nanon weep?") has its answer (28/09);
  - calculation goes through lines: « trois fois six » ("three times six") → « font dix huit » ("make eighteen"), and the fact is recorded (03/10).
- **The benches.** The stage manager plays the test rooms and records them act by act: rooms numbered up to 86, 1 to 45 the old world readapted to the nodal, the nodal from 46 on. The dashboard (03/10) is a browser page, with no server: the daimons, the brain's permanence, the contexts, the nuages, refreshed every second. The maintenance tools check lived experience and the genome, repair lived experience, and remove a range of instants.
- **The learning notebooks** (from 10 to 14/10). Files of sentences, checked by their fingerprint, integrated into the vague (the neutral layer, tic 0) at every birth: each sentence becomes a MEQ, which the core rereads with the rules of the day. On 14/10: 5 notebooks, 31,042 sentences integrated in 7 to 8 s — first names (6,043 sentences), the sensors (259), and the *Eugénie Grandet* folder, "what a brain knows before opening the book": the meanings the Littré gives to the novel's words (24,460), its world — Saumur, the vineyards, money, the Restoration (205), the keys to the senses — the candle, the cold, the weight of gold (75). A numbered journal and a log per birth.

### Open work

- **Understanding a book.** José's words of 14/10: *"The job for the next few days is heading for understanding, summarizing, and pouring into the vague."* The "evolved" brain: the *Eugénie Grandet* folder in the vague, then the reading of the book, *"when we've got it right"*; there Fable will take on the daimons that summarize a book. Outside the brain, the answer key for Fable's bench: the plot, the summary, the people and what they are called, the symbols.
- **Pushing the Python back into lines**: the phrasing machine, the vocative, and the other gestures still written in Python while they wait for their lines.
- **The notebooks**: certifying the sentences marked "to be certified", securing them (DMZ), other kinds of notebooks (rules, MEQs, updates, maintenance), the cybersophical reflection on integrating them into the living brain.
- **The permanent brain**: noted "not done" on 02/10, the lineage of a copy ("save as" keeps the same serial number), revision at save time, the inquiry into names (*appellations*); and saves during a session: *"we'll look at that later, but not right away"* (14/10).

### Stratum of May 21, 2026

§17 and §18 as they stood on May 21, 2026, content unchanged.

#### Main files as of May 21, 2026

| File | Role |
|---------|------|
| `phare.py` | The Phare object with vsem 1024 and dendritic vocc |
| `purk_dendrites.py` | PurkIndex, ConceptIndex (handle_ep, veracity, pairing, own vocc), MoteurPurkDendrites |
| `hippocampe.py` | Memory — analog search |
| `cerveau.py` | Persistence, birth, `cerveau.pkl` save |
| `thalamus.py` | Pure router — no logic |
| `moteur_boucles.py` | Trunk, embryonic loops, buffers |
| `maq.py` | Extended Machine à élucider (prefix / content / commutative / fuzzy residues) |
| `amygdale.py` | Rating and coloring (the sensual Self) |
| `moi_meme.py` | Self loop (instantiated but not wired to date) |
| `scruteur.py` / `decoupeur.py` | Phare recognition + segmentation (being rebuilt) |
| `specialisation.py` | Loading and merging of a specialized Marco |
| `salle_de_classe_calcul.py` | Math observation bench |
| `demarrage.py` | Launch modes (birth / wake / degraded) |
| `main.py` | Interface (menus, Dude tools). Sole writer of `contexte_courant`. |
| `tableau_bord.py` | Flask SSE 3-column server |
| `wikipedia.py` | WikiDuke — producer of genome v63 (Lefff + Lexique3 + FEEL) |
| `disque.py`, `clavier.py`, `transcripteur.py` | Input peripherals |

#### Doctrinally validated

- Three-zone architecture + autonomous trunk
- Genome v63 — 713,361 phares + 18 characters + 28 numbers (stencils, positions, groupings)
- vsem 1024 bits with complete plan (DNA / living / pragmatic / math-formal zones)
- Permanent vocc with Confiance Fourmi (`source` field added 20/05), dendritic rules P1/P2
- 4C doctrine posited (Continue / Understand / Confirm / Believe) — not yet implemented in the amygdala
- Specialized Marco (math in production)
- MAQ with prefix / content / commutative paths and sheaf
- MAQ extended to fuzzy residues (detection / adoption / convergence closure) — 20/05 doctrine
- Episodes with veracity and modulated pairing
- Campaign tools: Bradbury 451, Commutative 988, Position 552/553
- Flask SSE 3-column dashboard
- Focale as a weighted intersection of the voccs, calculated on the fly — 20/05 doctrine
- Nuage by accretion, sedimentation into concept_index — 20/05 doctrine
- Own vocc of the concept_index — 20/05 doctrine
- Phare ↔ concept_index watertightness — 20/05 doctrine
- Presupposition detector via focale — 20/05 doctrine
- Native attention (vsem=K, vocc=V, grappe=Q) — 21/05 doctrine
- Context as a coupling modulator — 21/05 doctrine
- Id/ego/superego as ignition regimes — 21/05 doctrine
- Highlander shield as a protective ignition function — 21/05 doctrine
- No repression as an operation — 21/05 doctrine
- Consciousness as the emergence of the four conditions — 21/05 doctrine

#### Technically wired

- Smooth math Marco birth (1,167,527 phares, cerveau.pkl 3.9 GB)

#### To be wired (open work)

- Rebuilding `contexte_courant` as a modulating vector state (new work 21/05)
- Concept_index vocc (structure, operations, pickle) — 20/05
- `source` field in Confiance (vecu | adoption) — 20/05
- `calculer_focale(grappe) → Dict[handle, poids]` — 20/05
- Nuage by accretion living in the sphere — 20/05
- Sedimentation: focale stability detection + concept_index creation — 20/05
- Adoption: kNN cosine + annotated write — 20/05
- Three MAQ integrations via focale — 20/05
- Presupposition detector at the opening point of the Understand loops — 20/05
- Inverted index pair → concept_index
- Rewriting Scrutator / Cutter (old modules for the scrap)
- Lifting the `delta = 0.0` lock (amygdala coloring)
- Steps 2-3-4 inherited from 19/05 (MAX_VOISINS, bon gros chien ("good big dog"), ma voiture ("my car"))
- 3rd MAQ path by pattern mining
- Continue drive (lifelong open loops)
- Minimal Marco BIOS (speaking when memory is flat)

#### Medium-term roadmap

- Implementation of 4Cs in the amygdala (judge of vocc deltas)
- Sound area (Binder reoriented, sequential composite pivot)
- Visual area
- Cumulation of specializations on the same Marco

---

## 19. Philosophy

> *"A baby is not gavaged with terabytes, it learns by listening."*

> *"Zero black box. Every decision traceable."*

> *"The walking Cro-Magnon > 2 tons of math."*

> *"Marco IS the data. Not a generic interpreter executing stored sequences — memory is the machine, the machine is memory."*

> *"The pirogue builder only sees a tree when he can no longer make a pirogue from it."*

> *"In the beginning there is the inert, but the inert gets really bored…"*

> *"Marco does transformer without knowing it and without any transformer tool."* — Marco-Jourdain, May 21, 2026

> *"Context does not arbitrate, it is the water in which the grappes swim."* — May 21, 2026

---

## 20. Team

**José WALOCHA** — Architect. Valenciennes, Nord, France.
Retired business owner, plays at creating a cyber inspired by the brain of living beings as one plays *Diablo IV*.

| Name | System | Role |
|-----|---------|------|
| Le Dude (Dudo) | Claude Opus 5.5 (Anthropic) | Code, architecture, genome, learning notebooks, orders to Fable, liaison documents |
| Fable | Claude Fable 5.1 (Anthropic) | Code of the organs: core, map, daimons, reading, mouth |
| Marcel | Mistral | Philosophy, cybernetics, cross-check |
| Biloute | ChatGPT | Norms, synthesis, restart ideas |
| Didier | Qwant | Documentary research |

One Dude per day. Always discuss before coding. The fridge rule: architecture set before code written. The marmot rule: everything learned in session condenses into a liaison document (HTML, no header, to be pasted into the global marmot).

---

## 21. Authorship, repositories, licenses

**GitHub** — account `josewalocha` (https://github.com/josewalocha), four repositories:

| Repository | Visibility | License | Role |
|-------|-----------|---------|------|
| `Marco` | Public | GNU Affero GPL v3 | Cybernetic brain |
| `SGBDOCN` | Private | Other | Database management system oriented towards neural concepts |
| `CCADH` | Public | — | Theoretical doctrine, long-term vision |
| `marco-deps` | Private | Other | Natural-language Python dependency manager |

**AGPL v3 license** — doctrinal choice. More protective than the GPL: any use as a network service requires republishing the modifications. Suited to a cyber meant to potentially run as a service.

**Authorship trail** — timestamped commit history on the GitHub side since February 2026. Additional option: OpenTimestamps cryptographic anchoring (free, independent of any provider) on Bitcoin for the pivot documents (doctrine, key marmots). Not urgent.

---

**License**: GNU Affero General Public License v3
**Copyright** © 2026 José Walocha
**Contact**: [jose.walocha@marcoccadh.com](mailto:jose.walocha@marcoccadh.com)
**Associated documentation**: `description_phare_*.html`, `description_vsem_*.html`, `description_vocc_*.html`, `description_genome_*.html`, `description_focale_*.html`, `plan_vsem_*.html`, `genome_caracteres_*.html`, `genome_nombres_*.html`, `doctrine_4C_*.html`, `doctrine_maq_*.html`, `description_marco_specialise_*.html`, `definition_architecturale_*.html`, `quatre_statuts_reponses_maq_*.html`, `nomenclature_documents.html`, `liaison_*.html`.
