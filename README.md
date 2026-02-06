# CCADH - Cerveau Cybernétique à Architecture de Décision Hiérarchique

> *"Construire un cerveau, pas simuler l'intelligence"*

![Status](https://img.shields.io/badge/status-recherche-orange)
![Version](https://img.shields.io/badge/version-4.0_Barista-green)
![Vision](https://img.shields.io/badge/vision-2026+-purple)

---

## 🎯 Vision

Le **CCADH** est un projet de recherche visant à créer un système cognitif inspiré du biologique, pas des mathématiques.

Le CCADH contient **MARCO**, le premier **SGBDOCN** (Système de Gestion de Base de Données Orienté Concepts Neuronaux) — un SGBD vivant qui apprend en lisant.

**Objectif** : Un cerveau cybernétique qui :
- Apprend par exposition (pas par entraînement supervisé)
- Comprend par structure (pas par statistiques)
- Raisonne par activation (pas par calcul matriciel)
- Fonctionne sur un Raspberry Pi (pas sur un datacenter)

---

## 🧠 Philosophie

### Ce que CCADH n'est PAS

❌ Un LLM (Large Language Model)
❌ Un réseau de neurones classique
❌ Un système basé sur les transformers
❌ Une IA qui nécessite des GPU

### Ce que CCADH EST

✅ Inspiré de C.elegans (302 neurones → comportements complexes)
✅ Basé sur des boucles while (pas des if/else)
✅ Émergent (l'intelligence naît de la structure)
✅ Frugal (50 Mo de RAM pour une bibliothèque)
✅ Un SGBDOCN (le sens émerge, pas de requête SQL)
✅ Un barista : il apprend en servant ☕

---

## 🏛️ Architecture complète

```
╔═══════════════════════════════════════════════════════════════════╗
║                            CCADH                                  ║
╠═══════════════════════════════════════════════════════════════════╣
║                                                                   ║
║  ┌─────────────────────────────────────────────────────────────┐  ║
║  │                        THALAMUS                             │  ║
║  │              (Routeur central — Menu v4.0)                  │  ║
║  └─────────────────────────┬───────────────────────────────────┘  ║
║                            │                                      ║
║    ┌───────────────────────┼───────────────────────┐              ║
║    │                       │                       │              ║
║    ▼                       ▼                       ▼              ║
║  ┌─────────┐         ┌───────────┐         ┌─────────────┐        ║
║  │HIPPO-   │         │   MARCO   │         │  CERVELET   │        ║
║  │CAMPE    │◄───────►│ (SGBDOCN) │◄───────►│  (Boucles   │        ║
║  │(Mémoire │         │  Cortex   │         │   diffusion)│        ║
║  │ courte) │         │ 5 couches │         │             │        ║
║  └─────────┘         └───────────┘         └─────────────┘        ║
║                            │                                      ║
║              ┌─────────────┼─────────────┐                        ║
║              │             │             │                        ║
║              ▼             ▼             ▼                        ║
║        ┌──────────┐  ┌──────────┐  ┌──────────┐                   ║
║        │ COUCHE I │  │COUCHE II │  │COUCHE III│                   ║
║        │ Lettres  │  │ Phares   │  │Concepts  │                   ║
║        │(Neurones)│  │ (Mots)   │  │(BSCW)    │                   ║
║        └──────────┘  └──────────┘  └──────────┘                   ║
║              │             │             │                        ║
║              ▼             ▼             ▼                        ║
║        ┌──────────┐  ┌──────────┐  ┌──────────┐                   ║
║        │COUCHE IV │  │ COUCHE V │  │ MATRICE  │                   ║
║        │Co-occur. │  │Séquences │  │CONVERGENC│                   ║
║        │ (Sens)   │  │(Syntaxe) │  │  (.txt)  │                   ║
║        └──────────┘  └──────────┘  └──────────┘                   ║
║                                                                   ║
╚═══════════════════════════════════════════════════════════════════╝
```

---

## 🧩 Composants

### 1. MARCO (SGBDOCN — Cortex) ✅ Implémenté

Le **cortex** du CCADH. Le premier SGBDOCN au monde.

| | SGBD classique (SQL) | SGBDOCN (Marco) |
|---|---|---|
| **Stockage** | Tables, lignes, colonnes | Phares, dendrites, concepts |
| **Requête** | `SELECT * FROM ...` | Activation en cascade (Pac-Man) |
| **Relations** | Clés étrangères, JOIN | Co-occurrences, séquences, familles |
| **Schéma** | Fixe (CREATE TABLE) | Émergent (le sens se construit) |
| **Index** | B-Tree, Hash | Neurones lettres → Phares → Concepts |
| **Apprentissage** | Aucun | Gavage en temps réel |

**5 couches** :

| Couche | Rôle | Détecteur |
|--------|------|-----------|
| I — Lettres | 1 lettre = 1 neurone | Activation cascade |
| II — Phares | 1 mot = 1 concept | BSC (BooShaChom) |
| III — Concepts | N mots = 1 bloc + famille | BSCW (BooShaChom Walocha) |
| IV — Co-occurrences | Le sens par le voisinage | "Dis-moi avec qui tu traînes" |
| V — Séquences | La syntaxe par l'ordre | "le chat mange" ≠ "mange le chat" |

**Poupées russes** (Concepts) :
```python
Concept("ça baigne")
  famille    = ["ça roule", "c'est top", "nickel"]
  reponses   = ["je vais bien merci"]   # stimulus → réponse
  composants = [Phare("ça"), Phare("baigne")]
  type       = "expression"
```

Quand un cousin est détecté, c'est le chef qui s'active. Comme un index SQL, mais vivant.

**État actuel** :
- ✅ Neurones lettres (activation cascade)
- ✅ Phares (concepts uniques)
- ✅ Concepts multi-mots (class Concept hérite de Phare)
- ✅ BSCW (détecteur de concepts par fenêtre glouton)
- ✅ Co-occurrences et séquences
- ✅ Tags sémantiques (EST-UN, CONTRAIRE, SYNONYME)
- ✅ Appariement stimulus → réponse (perroquet)
- ✅ Matrice de convergence (.txt → concepts + familles)
- ✅ Galaxie autonome (micro-SGBDOCN avec positions 3D)

### 2. THALAMUS (Routeur — Menu v4.0) ✅ Implémenté

Le **routeur central** qui aiguille les requêtes.

```
╔══════════════════════════════════════════════════════════╗
║        MARCO BARISTA ☕ v4.0                              ║
╠══════════════════════════════════════════════════════════╣
║    1. Charger Matrice (ADH)                              ║
║    2. 🌀 Créer Galaxie (convergence)                     ║
║    3. ☕ Prompt (le comptoir)                             ║
║    4. Dialogue des gavages                               ║
║    5—14. Stats, radio, biblio, traducteur, éditeur...    ║
╚══════════════════════════════════════════════════════════╝
```

**Deux matrices, deux méthodes** :

| Matrice | Format | Rôle | Équivalent SQL |
|---|---|---|---|
| **Matrice ADH** | .json | Vocabulaire complet (46 006 phares) | Dictionnaire de données |
| **Matrice de Convergence** | .txt | Concepts métier, familles, formules | `CREATE DATABASE` |

**Prompt Barista** (option 3) :
```
👤 "bonjour"              → 🦜 bonjour bienvenue chez marco
👤 "je veux un café crème" → 🦜 un crème c'est parti c'est noté ça arrive
👤 "gros con"              → 🦜 on se calme on est entre gens civilisés
👤 "tu es qui"             → 🦜 je suis marco le barista je sers ce que j'ai appris
```

**Modes compartimentés** :

| Mode | BSCW | Apprentissage | Usage |
|------|------|---------------|-------|
| **gavage** | ❌ | ✅ dendrites, co-occ, tags | Livres, textes bruts |
| **dialogue** | ✅ | ✅ dendrites, co-occ, tags | Comptoir, prompt |
| **lecture** | ✅ (cervelet) | ✅ + contexte | À venir |

Un livre c'est des mots. Le comptoir c'est des concepts. Même moteur, zéro collision.

**État actuel** :
- ✅ Menu v4.0 (14 options)
- ✅ Barista (prompt avec formules)
- ✅ Galaxie autonome (spirale de Fibonacci)
- ✅ Auto-détection .json / .txt
- ✅ Perroquet question (inconnus → Marco demande)
- ✅ Icônes 👤🦜📋🔮❓🤔📝

### 3. CERVELET (Boucles de diffusion) ⏳ Architecture posée

**Régulateur** des boucles de lecture et de convergence.

Inspiré des modèles de diffusion (Stable Diffusion) : partir du bruit pur et affiner par passes successives.

```
Boucle 1 : lettres   → mots        (BSC)
Boucle 2 : mots      → concepts    (BSCW)
Boucle 3 : concepts  → temps       (conjugaison)
Boucle 4 : concepts  → action      (violence, politesse, commande)
Boucle 5 : temps + action → SENS   (menace, récit, fait accompli)
```

C'est la même boucle à chaque étage. Le nombre de passes N'EST PAS codé en dur — il dépend du nombre de registres dans la matrice de convergence. Chaque registre = une couche de diffusion.

```
"il va me casser la figure"     → VIOLENCE + FUTUR PROCHE = menace
"il allait me casser la figure" → VIOLENCE + PASSÉ         = récit
"il m'a pété la gueule"        → VIOLENCE + PASSÉ COMPOSÉ = fait accompli
```

**État actuel** :
- ✅ Architecture posée (pseudo-code)
- ✅ Boucles imbriquées identifiées
- ⏳ Implémentation (class Cervelet)

### 4. HIPPOCAMPE (Mémoire courte) ⏳ Architecture posée

**Mémoire épisodique** et contexte de lecture.

```python
class Hippocampe:
    contexte = {
        "personnages": {},    # {"il": "Jean Valjean"}
        "lieu": "",           # "Paris"
        "temps": "",          # "passé", "présent"
        "ambiance": "",       # "violence", "amour"
        "fil": [],            # Dernières N phrases
    }
```

**Rôle** :
- Résolution des pronoms : "il" → dernier personnage masculin
- Suivi du contexte : lieu, temps, ambiance
- Oubli sélectif : changement de chapitre → reset partiel
- Compression long terme (consolidation)

**État actuel** :
- ✅ Architecture posée (pseudo-code)
- ⏳ Implémentation (class Hippocampe)

### 5. CHIMIE (Modulation) ⏳ À faire

**Neurotransmetteurs virtuels** qui modulent l'activation.

| Chimie | Effet | Usage |
|--------|-------|-------|
| Dopamine | Renforce | Récompense, apprentissage |
| Sérotonine | Stabilise | Humeur, cohérence |
| Acétylcholine | Active | Attention, focus |
| GABA | Inhibe | Filtrage, bruit |

---

## 🔬 Concepts clés

### SGBDOCN — Le SGBD vivant

Un SGBD classique est **mort** (Thanatos) : tu lui poses une question, il te rend une ligne. Toujours la même. Le SGBDOCN est **vivant** (Anima) : il apprend en répondant, ses liens se renforcent, le sens converge.

Le même pipeline sert à tout : lire, apprendre, répondre. Pac-Man bouffe tout.

### Matrice de convergence

Un fichier texte lisible par un humain qui définit un micro-cerveau :

```
## SALUTATIONS
bonjour = salut, coucou, hey, wesh
bonjour → bonjour bienvenue chez marco

## INSULTES
gros con = imbécile, crétin, abruti
gros con → on se calme on est entre gens civilisés
```

Les registres (## SALUTATIONS, ## INSULTES) deviennent des couches de diffusion. Plus tu en ajoutes, plus le sens converge.

### Galaxie autonome

```
Créer Galaxie "Marco_le_barista"
  → 1 soleil central (0, 0, 0)
  → 405 phares positionnés (spirale de Fibonacci)
  → 50 concepts, 293 index, 41 appariements
  → Prêt à servir. Autonome. Pas besoin de 46 006 concepts.
```

Une galaxie c'est l'équivalent d'un `CREATE DATABASE` + `CREATE SCHEMA` en SQL. Sauf que ça tient dans un fichier texte et que ça apprend tout seul.

### Règle des trois neurones

Le cerveau de **C.elegans** (ver de 1mm) a 302 neurones et peut :
- Se nourrir, se reproduire, éviter les dangers, apprendre

**Tout ça avec des boucles while.**

```python
while vivant:
    stimulus = percevoir()
    activer_neurones(stimulus)
    propager_dendrites()
    agir()
```

### Poupées russes

L'information s'emboîte à l'infini :

```
Niveau 0: Lettres      c, a, f, é
Niveau 1: Mot          café
Niveau 2: Concept      café crème (avec famille : latte, crème)
Niveau 3: Registre     COMMANDE BARISTA
Niveau 4: Domaine      Restauration
Niveau N: ...          Concepts de concepts de concepts
```

Chaque niveau **émerge** du précédent. class Concept(Phare) — un phare qui contient des phares.

### ADH (Arbre de Décision Hiérarchique)

Marco déduit la hiérarchie par transitivité :
```
vallée
└── forêt
    ├── chêne
    └── tilleul
```

---

## 📊 Scalabilité

| Métrique | LLM classique | CCADH |
|----------|---------------|-------|
| RAM requise | 100+ Go | ~150 Mo |
| GPU | Obligatoire | Non |
| Entraînement | Semaines | Temps réel |
| Coût | $$$$ | Raspberry Pi |
| Hallucinations | Fréquentes | Impossibles (si pas lu, pas su) |
| Transparence | Boîte noire | Chaque lien traçable |

---

## 🗺️ Roadmap CCADH

### Phase 1 : Fondations ✅

- [x] Architecture dendritique (neurones lettres)
- [x] Thalamus (routeur central, menu v4.0)
- [x] Tokenisation ADH (Pac-Man)
- [x] Poupées russes (Concept hérite de Phare)

### Phase 2 : SGBDOCN ✅

- [x] BSCW (détecteur de concepts multi-mots)
- [x] Appariement stimulus → réponse (perroquet)
- [x] Matrice de convergence (.txt)
- [x] Galaxie autonome (micro-SGBDOCN)
- [x] Compartimentage gavage / dialogue
- [x] Barista ☕ (prompt interactif)

### Phase 3 : Cerveau (En cours)

- [ ] Cervelet (boucles de diffusion)
- [ ] Hippocampe (mémoire courte, contexte)
- [ ] Mode lecture (cervelet + hippocampe + BSCW)
- [ ] Registres temps (conjugaison)
- [ ] Registres actions (violence, aide, mouvement)
- [ ] Intersection des couches → sens émergent

### Phase 4 : Modulation

- [ ] Chimie (dopamine, sérotonine, etc.)
- [ ] Attention sélective
- [ ] Humeur contextuelle

### Phase 5 : Autonomie

- [ ] Moteur Elegans (while pur)
- [ ] Retrait des roulettes BooChom
- [ ] Émergence vraie

### Phase 6 : Hardware

- [ ] Standalone (.exe)
- [ ] Raspberry Pi
- [ ] "Alexa perso" offline — mais qui apprend ☕

---

## 📁 Fichiers principaux

| Fichier | Rôle | Lignes |
|---|---|---|
| `marco_dendrites.py` | Cœur — Phares, Concepts, BSCW, tokenisation | 3 534 |
| `thalamus.py` | Menu v4.0, barista, galaxie, orchestrateur | 4 016 |
| `dialogue.py` | Module dialogue 4 modes | — |
| `matrice_marco_v3_compact.json` | Matrice ADH (46 006 concepts, 102 soleils) | — |
| `matrice_convergence_v1.txt` | Matrice de convergence (50 concepts, 14 registres) | ~100 |

---

## 👥 Équipe

### Humain

**José Walocha** — Architecte, visionnaire, Ch'ti. Valenciennes, Nord, France.

### IA (sous direction humaine)

- **Le Duke** (Claude/Anthropic) — Code, architecture
- **Marcel** (Mistral) — Philosophie, cybernétique, diagnostic
- **Biloute** (ChatGPT) — Normes, éthique
- **Didier** (Qwant) — Recherche

---

## 📄 Licence

**GNU GENERAL PUBLIC LICENSE — Version 3**

Copyright (C) 2026 José Walocha

Le CCADH est un projet de recherche ouvert. Toute amélioration doit être partagée.

---

## 🐟 Mot de la fin

> *"On n'a pas besoin d'un datacenter pour penser. C.elegans le prouve."*

> *"Un SGBD classique est mort. Le SGBDOCN est vivant."*

> *"50 phrases et il répond. Pas 50 milliards de tokens."*

Le CCADH n'est pas une course à la puissance. C'est un retour aux fondamentaux : comprendre comment **émerge** l'intelligence, pas comment la **simuler**.

---

*"Au commencement il y a l'inerte, mais l'inerte il s'emmerde grave..."*
