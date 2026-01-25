# CCADH - Cerveau Cybernétique à Architecture de Décision Hiérarchique

> *"Construire un cerveau, pas simuler l'intelligence"*

![Status](https://img.shields.io/badge/status-recherche-orange)
![Vision](https://img.shields.io/badge/vision-2026+-purple)

---

## 🎯 Vision

Le **CCADH** est un projet de recherche visant à créer un système cognitif inspiré du biologique, pas des mathématiques.

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

---

## 🏛️ Architecture complète

```
╔═══════════════════════════════════════════════════════════════════╗
║                            CCADH                                  ║
╠═══════════════════════════════════════════════════════════════════╣
║                                                                   ║
║  ┌─────────────────────────────────────────────────────────────┐  ║
║  │                        THALAMUS                             │  ║
║  │                   (Routeur central)                         │  ║
║  └─────────────────────────┬───────────────────────────────────┘  ║
║                            │                                      ║
║    ┌───────────────────────┼───────────────────────┐              ║
║    │                       │                       │              ║
║    ▼                       ▼                       ▼              ║
║  ┌─────────┐         ┌───────────┐         ┌─────────────┐        ║
║  │HIPPO-   │         │   MARCO   │         │   CHIMIE    │        ║
║  │CAMPE    │◄───────►│  (Cortex) │◄───────►│ (Modulation)│        ║
║  │(Mémoire)│         │ 6 couches │         │             │        ║
║  └─────────┘         └───────────┘         └─────────────┘        ║
║                            │                                      ║
║              ┌─────────────┼─────────────┐                        ║
║              │             │             │                        ║
║              ▼             ▼             ▼                        ║
║        ┌──────────┐  ┌──────────┐  ┌──────────┐                   ║
║        │ COUCHE I │  │COUCHE II │  │COUCHE III│                   ║
║        │  TEMPS   │  │  PHARES  │  │ BOOCHOM  │                   ║
║        └──────────┘  └──────────┘  └──────────┘                   ║
║              │             │             │                        ║
║              └─────────────┼─────────────┘                        ║
║                            ▼                                      ║
║                     ┌──────────┐                                  ║
║                     │COUCHE IV │                                  ║
║                     │TOKENISER │                                  ║
║                     │(Entrée)  │                                  ║
║                     └──────────┘                                  ║
║                                                                   ║
╚═══════════════════════════════════════════════════════════════════╝
```

---

## 🧩 Composants

### 1. MARCO (Cortex) ✅ Implémenté

Le **cortex** du CCADH. Gère la tokenisation et le stockage.

**6 couches biologiques** :

| Couche | Rôle | Analogie restaurant |
|--------|------|---------------------|
| IV | Tokenisation (entrée) | Réception des produits |
| I | Temps, position | Planning, frigo/congélo |
| III | BooChom (règles) | Combinaisons possibles |
| II | Phares (concepts) | Recettes créées |
| V | Signes (images) | Photos des plats |
| VI | Souvenirs (cohérence) | Le Chef |

**État actuel** :
- ✅ Dendrites (lettres → mots)
- ✅ Phares (concepts uniques)
- ✅ Tokenisation ADH des questions
- ⏳ Relations entre phares

### 2. THALAMUS (Routeur) ✅ Implémenté

Le **routeur central** qui aiguille les requêtes.

**Fonctions** :
- Reçoit les entrées (fichiers, questions)
- Détecte le type de requête
- Route vers la bonne couche
- Gère l'état global

**État actuel** :
- ✅ Routage basique
- ✅ Détection type de question
- ⏳ Routage intelligent (apprentissage)

### 3. HIPPOCAMPE (Mémoire) ⏳ À faire

**Compression et consolidation** de la mémoire.

**Rôle** :
- Compresse les poupées russes pour le stockage long terme
- Décompresse à la demande
- Gère l'oubli (pruning des connexions faibles)

**Analogie** : Le sommeil qui consolide les souvenirs.

### 4. CHIMIE (Modulation) ⏳ À faire

**Neurotransmetteurs virtuels** qui modulent l'activation.

| Chimie | Effet | Usage |
|--------|-------|-------|
| Dopamine | Renforce | Récompense, apprentissage |
| Sérotonine | Stabilise | Humeur, cohérence |
| Acétylcholine | Active | Attention, focus |
| GABA | Inhibe | Filtrage, bruit |

**Formule** :
```
poids_effectif = poids_base × dopamine × (1 / log(occurrences))
```

---

## 🔬 Concepts clés

### Règle des trois neurones

Le cerveau de **C.elegans** (ver de 1mm) a 302 neurones et peut :
- Se nourrir
- Se reproduire
- Éviter les dangers
- Apprendre

**Tout ça avec des boucles while.**

```python
# C.elegans simplifié
while vivant:
    stimulus = percevoir()
    activer_neurones(stimulus)
    propager_dendrites()
    agir()
```

**Si ça ne marche pas pour C.elegans, ça ne marchera pas pour CCADH.**

### Zones de triche autorisées

Le CCADH utilise des "roulettes" temporaires :

| Couche | Triche | Justification |
|--------|--------|---------------|
| IV | ASCII (lettres déjà reconnues) | Évite 1M neurones pour la vision |
| III | BooChom en if/else | Roulettes retirées quand ça roule |

**Partout ailleurs** : Émergence pure (while loops).

### Poupées russes

L'information s'emboîte à l'infini :

```
Niveau 0: Lettres      c, h, ê, n, e
Niveau 1: Mot          chêne
Niveau 2: Concept      arbre
Niveau 3: Catégorie    végétal
Niveau 4: Domaine      nature
...
Niveau ∞: ?
```

Chaque niveau **émerge** du précédent par répétition des patterns.

### ADH (Arbre de Décision Hiérarchique)

Marco lit :
- "Le chêne est dans la forêt"
- "Le tilleul est dans la forêt"
- "La forêt est dans la vallée"

Marco **déduit** :
```
vallée
└── forêt
    ├── chêne
    └── tilleul
```

**Question** : "Le chêne est dans la vallée ?"
**Réponse** : Oui (transitivité automatique)

---

## 📊 Scalabilité

### Objectif : 50 Go d'epub

| Métrique | LLM classique | CCADH |
|----------|---------------|-------|
| RAM requise | 100+ Go | ~150 Mo |
| GPU | Obligatoire | Non |
| Entraînement | Semaines | Temps réel |
| Coût | $$$$ | Raspberry Pi |

### Comment ?

1. **51 neurones lettres** (pas de duplication)
2. **~500k phares** (mots français uniques)
3. **Dendrites partagées** (compression préfixes)
4. **Pas de vecteurs** (juste des dictionnaires)

---

## 🗺️ Roadmap CCADH

### Phase 1 : Fondations ✅

- [x] Architecture dendritique
- [x] Thalamus basique
- [x] Tokenisation ADH
- [x] Poupées russes (4 niveaux)

### Phase 2 : Relations (En cours)

- [ ] Phares reliés (∈ appartenance)
- [ ] Transitivité automatique
- [ ] Réponses aux questions

### Phase 3 : Mémoire

- [ ] Hippocampe (compression)
- [ ] Oubli sélectif (pruning)
- [ ] Consolidation (sommeil)

### Phase 4 : Modulation

- [ ] Chimie (dopamine, etc.)
- [ ] Attention sélective
- [ ] Humeur contextuelle

### Phase 5 : Autonomie

- [ ] Moteur Elegans (while pur)
- [ ] Retrait des roulettes BooChom
- [ ] Émergence vraie

### Phase 6 : Hardware

- [ ] Standalone (.exe)
- [ ] Raspberry Pi
- [ ] "Alexa perso" offline

---

## 🆚 CCADH vs LLMs

| Aspect | LLMs (GPT, Claude) | CCADH |
|--------|-------------------|-------|
| Approche | Statistique | Structurelle |
| Entraînement | Supervisé (TB de données) | Exposition (lecture) |
| Mémoire | Contexte limité | Persistante |
| Hardware | GPU datacenter | Raspberry Pi |
| Explicabilité | Boîte noire | Chemins tracés |
| Hallucinations | Fréquentes | Impossibles (si pas lu, pas su) |
| Créativité | Combinatoire | Émergente |

---

## 💡 Applications visées

### Bibliothèque personnelle

- Indexer tous vos livres
- Recherche sémantique
- "Dans quel livre j'ai lu ça ?"

### Veille scientifique

- Digérer des centaines de papers
- Trouver les connexions
- Pas besoin de relire

### Assistant cognitif

- Mémoire externe persistante
- "Alexa mais en local"
- Vie privée respectée

### Outil de recherche

- Corpus littéraires
- Analyse linguistique
- Pas de biais statistique

---

## 👥 Équipe

### Humain

**José** - Architecte, visionnaire, Ch'ti.


### IA (sous direction humaine)

- **Claude** (Anthropic) - Architecture, code
- **Marcel** (Mistral) - Conseils, relance
- **Biloute** (ChatGPT) - Idées

---

## 📚 Lectures recommandées

- **Hofstadter, D.** - *Gödel, Escher, Bach* (1979)
- **Hofstadter, D.** - *I Am a Strange Loop* (2007)
- **Minsky, M.** - *Society of Mind* (1986)
- **Dehaene, S.** - *Reading in the Brain* (2009)
- **Eagleman, D.** - *Livewired* (2020)

---

## 📄 Licence

**AGPL-3.0**

Le CCADH est un projet de recherche ouvert. Toute amélioration doit être partagée.

---

## 🐟 Mot de la fin

> *"On n'a pas besoin d'un datacenter pour penser. C.elegans le prouve."*

Le CCADH n'est pas une course à la puissance. C'est un retour aux fondamentaux : comprendre comment **émerge** l'intelligence, pas comment la **simuler**.

```
╭─────────────────────────────────────╮
│                                     │
│   "Ches gins du Nord ont din       │
│    l'cœur el soleil qu'ils         │
│    n'ont pas dins l'temps."        │
│                                     │
│              - Proverbe Ch'ti       │
│                                     │
╰─────────────────────────────────────╯
```

**Marco est le premier pas. Le CCADH est le chemin.**
