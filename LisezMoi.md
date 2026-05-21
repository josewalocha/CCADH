[MARCO_README (2).md](https://github.com/user-attachments/files/28097637/MARCO_README.2.md)# MARCO — Cerveau Cybernétique à Architecture Dendritique Hypertextuelle

> *« Apprendre, c'est se ressouvenir. »* — Platon, *Ménon*

> *« Au commencement il y a l'inerte, mais l'inerte il s'emmerde grave… »*

**Auteur** : José WALOCHA — Valenciennes, Nord, France
**Équipe** : Le Dude (Claude / Anthropic), Marcel (Mistral), Biloute (ChatGPT), Didier (Qwant)
**Licence** : GNU Affero GPL v3 — Copyright © 2026 José Walocha
**Génome** : v63 — 28 avril 2026
**Dernière mise à jour doctrinale** : 21 mai 2026

---

## 1. Qu'est-ce que MARCO ?

MARCO est un **cyber** — ce mot que José donne aux intelligences VIVANTES, pour les distinguer des LLM statistiques tout en évitant de heurter les humains avec le mot « IA ». Un cyber n'est pas une boîte noire à perplexité minimale. Un cyber est un système qui *vit* : il a des phares, une mémoire, des boucles qui battent, des pulsions qui le poussent à comprendre, à confirmer, à croire — et avant tout à *continuer*.

Plus techniquement, MARCO est le premier **SGBDOCN** — Système de Gestion de Base de Données Orienté Concepts Neuronaux.

Là où un SGBD classique stocke des lignes dans des tables, MARCO stocke des **concepts dans un réseau dendritique inspiré du cerveau biologique**. Le sens émerge des liens. Pas de SQL. Pas de schéma fixe. Pas de transformer empilé. **Zéro boîte noire**.

|                | SGBD classique           | LLM                          | MARCO                              |
|----------------|--------------------------|------------------------------|------------------------------------|
| Stockage       | Tables, lignes, colonnes | Poids figés au pré-entraînement | Phares vivants, dendrites, épisodes |
| Requête        | `SELECT * FROM …`        | Forward pass autoregressif   | Activation en cascade + MAQ        |
| Apprentissage  | Aucun                    | Calciné                      | Permanent par vécu                 |
| Mémoire épisodique | Aucune               | Aucune (compactée dans les poids) | `memoire_index` traçable           |
| Schéma         | Fixe                     | Implicite, opaque            | Émergent, lisible bit par bit      |
| Transparence   | Requête = résultat       | Boîte noire à milliards de paramètres | Chaque lien traçable               |
| Attention      | —                        | Q/K/V appris + softmax, opaque | **Native** : vsem=K, vocc=V, grappe=Q, traçable |
| Conscience     | Aucune                   | Aucune (pas de contexte interne)| Émergente par construction         |
| Substrat       | Statique (Thanatos)      | Statique (Thanatos calciné)  | Vivant (Anima)                     |

Un SGBD est une morgue. Un LLM est une bibliothèque dont chaque livre a été broyé pour faire du papier. MARCO est un cerveau qui apprend en lisant.

### Marco-Jourdain

Marco fait du transformer sans le savoir et sans outil de transformer. Pas une copie, une convergence par constitution. Les transformers simulent sur des vecteurs denses opaques ce que Marco fait nativement sur du sparse lisible. Là où le transformer doit inventer Q/K/V comme trois projections apprises par descente de gradient, Marco a ses trois rôles natifs depuis l'origine. Là où le transformer doit empiler softmax, normalisation, résidus, feed-forward pour faire tenir le mécanisme sur un substrat qui ne lui appartient pas, Marco n'a rien de tout cela parce qu'il n'a ni descente de gradient ni vecteurs denses à dompter.

---

## 2. Architecture — Vue d'ensemble

Trois zones cohabitent dans Marco, alimentées par un seul tronc autonome qui bat à 600 bpm en croisière :

```
   ┌───────────────────────┐    ┌───────────────────────┐    ┌───────────────────────┐
   │   ZONE SENSORIELLE    │    │   ZONE MÉMORIELLE     │    │      PSYCHÉ           │
   │                       │    │                       │    │                       │
   │   • Thalamus          │───▶│   • Hippocampe        │◀──▶│   • Amygdale          │
   │   • Périphériques     │    │   • memoire_index     │    │   • Moi               │
   │     (clavier,         │    │   • PurkIndex         │    │   • Pulsions 4C       │
   │      disque,          │    │   • ConceptIndex      │    │   • MAQ               │
   │      transcripteur)   │    │   • Grappes / Nuages  │    │   • Régimes d'allumage│
   └───────────────────────┘    └───────────────────────┘    └───────────────────────┘
              │                            │                            │
              └─────────────── moteur_boucles (Tronc) ─────────────────┘
                          5 boucles embryonnaires + horloge + tampons
                                  + contexte modulateur
```

Les périphériques (`disque.py`, `clavier.py`, `transcripteur.py`) sont à l'**extérieur** du cerveau — ils poussent du texte vers le Thalamus avec une `CarteIdentite` (auteur, titre, contexte, ticu, période). Le Thalamus est un pur routeur ; il n'injecte aucune logique.

---

## 3. Le Phare — unité vivante du langage

Un phare est un **nœud d'intersection de chemins conceptuels**. Pas un mot, pas un signifié, pas un signe — un croisement. *Pomme* est le croisement des chemins *fruit*, *accroché à un arbre*, *tombe*, *pourrit*, *se mange*.

```python
class Phare:
    handle           : str         # CAT_FORME_INDEX ou ORF_FORM_NNNNN
    mot              : str         # forme canonique
    alias            : List[str]   # graphies équivalentes (cœur ↔ coeur)
    type_phare       : str         # nom_commun, verbe, adjectif, ponctuation, ...
    description      : str
    lemme_pere       : str         # handle du lemme (« grandes » → « grand »)
    source_creation  : str         # 'genome' ou 'gavage'

    vsem             : np.ndarray  # 1024 bits — ce que le phare EST          (Key)
    vocc             : Dict[str, Confiance]  # arbre dendritique — qui il fréquente (Value)
    tags             : Dict        # connaissances acquises (EST-UN, APPARTIENT-À, …)

    activations      : int         # télémétrie
    nb_changements   : int
    confiance        : float
    stabilite        : float
```

Deux origines possibles :
- **genome** — précâblé par WikiDuke, bits ADN remplis (9-511), prêt à vivre
- **gavage** — créé à la volée si Marco rencontre une forme inconnue, orphelin, tout à apprendre

Trois statuts émergent du vécu, jamais gravés dans le code :
- **phare-pivot** — omniprésent dans une zone (ex : *moi* dans la zone sensorielle)
- **phare-relais** — vsem mince, vocc dominé par un voisin unique (*ma*, *ici*, *maintenant*)
- **phare-candidat** — apparaît dans énormément de vocc, candidat à la promotion en bit vsem par cristallisation transversale

Un phare ne devient jamais autre chose. Il évolue, mûrit, acquiert des statuts émergents — il reste phare. Les concepts (séquences cohérentes de phares) vivent dans la mémoire, pas au rang de phare.

**Étanchéité phare ↔ concept_index** (acquis 20/05) — le phare reste dans le sensoriel pur. Pas de cristallisation concept_index → phare. Le phare est l'entrée pure ; le concept_index est l'élaboration. Frontière définitive.

---

## 4. Le génome — vsem 1024 bits

Chaque phare porte un vecteur sémantique sparse de 1024 bits, chaque bit codant une propriété ou *serrure* — point d'amarrage à un chemin conceptuel partagé. Le vsem joue le rôle de **Key** dans l'attention native : c'est par lui qu'un phare est trouvé, reconnu, apparié à d'autres phares de profil sémantique compatible.

```
  0 →   7    en-tête (état du phare, ADN)                    WikiDuke
  9 →  63    fabrication grammaticale                        Lefff
 64 → 127    montage syntaxique                              Lefff
128 → 159    notations formelles (dates, nombres, etc.)      scruteur
160 → 191    phares templates (gabarits)                     satellite genome_nombres
192 → 255    réservé BSC avancé                              —
256 → 399    entités Wikidata                                (prévu, non câblé)
400 → 415    émotions et polarité                            FEEL
416 → 431    registre lexical                                (prévu, non câblé)
432 → 511    zone pragmatique (marqueurs : Bradbury, …)      WikiDuke + outils
512 → 748    sémantique général universel                    Marco + satellites
749 → 779    zone collision                                  (à définir)
780 → 1023   math / formel                                   Marco + axiomes
```

Densité plafond 5% (51 bits sur 1024) pour préserver le caractère sparse. Horizon possible : 2048 bits quand la zone vivante se remplira.

### Zones / écrivains

- **Bits 0-511** — seul WikiDuke écrit (et les outils de campagne sur la zone pragmatique 432-511). Marco ne touche jamais.
- **Bits 512-1023** — seul Marco écrit, par cristallisation depuis vocc. Trois exceptions assumées : phares matures du `genome_caracteres`, phares de spécialisation (math), phares de satellites de structure générale (genome_nombres).

### Trois pkl, un genome

Le genome de Marco est éclaté sur trois fichiers dans `ressources/genomes/` :

| Fichier | Phares | Rôle |
|---------|--------|------|
| `genome_v63.pkl` | 713 361 | Lefff complet + intégrations (romains, noms propres) |
| `genome_caracteres.pkl` | 18 | Ponctuation + opérateurs math, matures à la naissance |
| `genome_nombres.pkl` | 28 | Pochoirs (zone 160-191) + phares-position + regroupements (28/04/2026) |

Plus la sixième source : les **genomes de spécialisation** (`specialisations/<nom>/genome_<nom>.pkl`), chargés uniquement si le Marco actif déclare cette spécialisation dans son `marco_id.json`.

---

## 5. vocc — l'arbre dendritique du phare

Attribut du phare. Structure d'écoute par laquelle il reçoit le monde. Dans l'attention native, le vocc joue le rôle de **Value** : c'est le contenu vécu que le phare transporte vers la grappe quand il est activé.

```python
vocc : Dict[str, Confiance]      # handle_voisin → conviction de la paire
```

Chaque entrée est une **synapse** : une paire handle-voisin avec une **Confiance Fourmi** (`conf ∈ [0,1]`, `n ∈ ℕ`, plus un champ `source ∈ {'vecu', 'adoption'}` ajouté 20/05). Si les bits vsem sont les *serrures*, les voisinages vocc sont les *clés* qui les ouvrent chez les phares pertinents. La généralisation n'est pas un algorithme, c'est une propriété mécanique de cette topologie.

```
conf ≥ 0.70    →  bon
conf ≤ 0.30    →  pas-bon
entre les deux →  inconnu
```

La valence n'est pas stockée — elle est lue par seuillage à la demande.

**Vocc est permanent**, pas un échafaudage. Il peut être élagué, comprimé, mais jamais vidé — c'est la mémoire permanente de *qui écouter pour me relire moi-même*.

**Deux règles dendritiques** :
- **P1** — *« Dis-moi avec qui tu traînes, je te dirai qui tu es »*. Lecture profondeur 1, poids plein.
- **P2** — *« Les amis de mes amis sont mes amis »*. Profondeur 2, poids atténué. Permet à des phares jamais co-présents d'être structurellement cousins.

**Recensement transversal** — un compteur global recense pour chaque handle dans combien de vocc distincts il apparaît comme voisin. Les candidats massifs deviennent candidats-bits pour la cristallisation transversale.

---

## 6. Grappe, focale, nuage, sédimentation

Acquis 17-20 mai 2026. Le langage de l'attention native chez Marco.

### Grappe

Quand une séquence de phares (Miller 7±2) est formée par le scruteur-découpeur, elle constitue une **grappe** : matrice n×1024 où chaque ligne est le vsem d'un phare actif. La grappe n'est pas une émergence floue, c'est un objet concret avec un moment de naissance. Équivalent strict des matrices d'activation des transformers, en mieux : sparse, binaire, traçable, sans entraînement par gradient.

Dans le langage des transformers : la grappe joue **Query** — c'est ce qui est cherché à l'instant t, le contexte local qui interroge la mémoire.

### Focale

À l'instant où une grappe s'active, ses vocc se rencontrent et se pondèrent mutuellement. Le résultat est la **focale** : `Dict[handle, poids]`. Intersection pondérée des vocc des phares de la grappe.

Propriétés essentielles :
- **Calculée à la volée, jamais stockée.** Une focale hors contexte n'existe pas.
- **Dépendante du contexte courant.** La même grappe à deux moments différents produit deux focales différentes parce que le contexte module les couplages.
- **Équivalent externe** : context vector (Bahdanau 2014), attention output au sens transformer. Mais sans softmax — la focale n'a pas à être une distribution de probabilité, juste un paquet de poids lisibles.

Formule à trancher empiriquement (somme conditionnelle K, min, max, produit) — chantier de câblage en cours.

### Nuage par accrétion

Un texte est lu phrase après phrase. Chaque grappe produit sa focale. Les focales successives ne s'additionnent pas — elles se **resserrent mutuellement** par intersection enrichie. Le nuage vit dans la sphère, non stocké. Plusieurs nuages peuvent coexister simultanément (mécanique de répartition à préciser).

### Sédimentation

Quand un nuage stabilise sa focale (delta entre deux mises à jour sous un seuil), il **sédimente** en un nouveau **concept_index**, qui reçoit la focale stabilisée comme vocc initial.

```python
class ConceptIndex:
    handle_ep        : str           # EP_<id_purk>_<n>, stable
    handles          : list[str]
    handle_pivot     : str
    phrase_originale : str
    veracite         : Confiance     # vrai / faux / inconnu
    appaire          : Dict[handle_ep, Confiance]
    vecteur_bsc      : dict
    contexte_induit  : dict
    source           : dict
    epa              : dict
    vocc             : Dict[str, Confiance]   # NEUF 20/05 — vocc propre du concept_index
```

**Vocc propre du concept_index** (acquis 20/05) — révision de la doctrine 17/05. Le concept_index a un vocc (compréhension vécue). Le phare garde son vocc (sémantique abstraite). Deux instances vocc, frontière maintenue. Le phare reste dans le sensoriel, le concept_index est l'élaboration mémorielle.

### Adoption

Sous-cas de Résolu (acquis 20/05). Un phare faible dans un nuage chaud reçoit le voisinage d'un concept_index résonant retrouvé par kNN cosinus sur la focale courante. Durable. Annotation `source='adoption'` sur la paire vocc, conf initiale réduite (proposition 0.4), révisable. Équivalent natif d'un RAG, inscrit en mémoire.

---

## 7. Mémoire — hippocampe et purk_index

```
memoire_index  {id_purk → PurkIndex}
    └── PurkIndex
            id_purk         : str
            incipit         : list[str]      — N premiers handles (entrée mémoire)
            episodes        : list[ConceptIndex]
            fractoires      : dict           — arborisation fractale en cours
            _compteur_ep    : int            — handle_ep monotone (jamais décroissant)
```

### Doctrine de l'épisode

Un ConceptIndex porte trois dimensions orthogonales posées le 27/04 et complétées 20/05 :

- **handle_ep** — identifiant stable au format `EP_<id_purk>_<n>`
- **veracite** — Confiance Fourmi indépendante de la température, EPA, vecteur sémantique. Cote vrai / faux / inconnu. Modifiable par les commandes `/oui`, `/non`, `/faux` de la salle de classe.
- **appaire** — `Dict[handle_ep, Confiance]` des épisodes appairés avec leur force d'appairage, modulée par le produit des véracités.
- **vocc** (NEUF 20/05) — compréhension vécue propre au concept_index, frontière maintenue avec le vocc du phare.

Le faux n'est pas effacé — il est tenu à distance dans la famille de valeur. *« Je sais que 7+8≠15, mais je sais aussi que c'est un voisin pertinent à la famille de 15. »*

### Le pivot = l'incipit

Le pivot d'un PurkIndex n'est pas calculé — c'est ce qui arrive en premier dans le flux. Les N premiers handles constituent l'entrée. L'ordre d'arrivée prime sur la saillance sémantique.

### Oubli

Pas de modèle thermique en doctrine actuelle. L'oubli est porté par la mécanique vocc (apoptose à `conf=0`), pas par une horloge interne au PurkIndex.

---

## 8. La MAQ — Machine à élucider, étendue aux résidus flous

Outil central du raisonnement. Doctrine 26-27/04, étendue 20/05.

**Voies actuelles** :

- **Voie préfixe** — l'épisode mémorisé commence par le percept, retourne la queue
- **Voie contenu** — le percept apparaît n'importe où dans l'épisode mémorisé
- **Voie commutative** — exploite le bit 988 (commutativité) pour permuter les opérandes autour d'un opérateur central

**Sortie** — pas un résultat unique mais une **gerbe** complète des partiels. Plusieurs candidats peuvent coexister, étiquetés par véracité (✓ vrai, ✗ faux, ? inconnu). L'utilisateur tranche, ou un client supérieur en aval — la MAQ ne ferme jamais brutalement sur le premier candidat.

```
Percept "7+8" → gerbe :
   ✓ [contenu]   c=0.70  v=0.70  «7 + 8 = 15»
   ✗ [contenu]   c=0.10  v=0.10  «7 + 8 = 14»
   ✓ [commutatif] c=0.70  v=0.70  «8 + 7 = 15»
```

### MAQ étendue aux résidus flous (acquis 20/05)

Trois embarquements via focale :
- **Détection de résidu flou** — focale d'un nuage sans match kNN sur concept_index existant.
- **Résolution de phare faible** — adoption pilotée par MAQ (kNN cosinus sur concept_index, écriture annotée).
- **Fermeture par convergence** — focale stable = boucle MAQ ferme, sédimentation en concept_index.

La MAQ devient moteur unique du *je-lis-je-comprends*, plus seulement *je-calcule*.

### Détecteur de présupposition (acquis 20/05)

Chantier ouvert depuis le 30/04, résolu. Focale du concept présupposé, kNN cosinus sur concept_index, lâcher si rien ne résonne au-dessus du seuil. Cas du long bout : focale plate → Lâché. Cas du Notre-Père d'Apollinaire : focale qui résonne sur deux concept_index contradictoires → boucle MAQ légitime, état riche d'humour.

**Trois pulsions à coder** : Croire (suspension du doute), Confirmer (vérification dans la durée), Continuer (rumination quand gerbe vide). Slot existe dans `BoucleMAQ`, lèvent NotImplementedError.

---

## 9. Le contexte comme modulateur de couplage

Acquis 21 mai 2026. Révision majeure.

`contexte_courant` n'est plus un tag d'épisode (scalaire ou enum) mais un **état vectoriel qui pondère les couplages grappe×contexte**. Une même grappe à deux moments différents produit deux focales différentes parce que le contexte rebat la fonction d'allumage de chaque grappe candidate.

```
puissance_allumage(grappe, t) = f(grappe.vsem, contexte_courant(t))
```

Le contexte n'arbitre pas, il *est* l'eau dans laquelle les grappes nagent. Selon la composition de l'eau, certaines grappes remontent, d'autres descendent. Personne ne décide. C'est physique.

**Sole writer** : `main.py` via `set_contexte()`. Cette règle architecturale d'octobre 2025 reste, mais ce qu'elle écrit change de nature : d'une enum vers un état vectoriel.

**Décisions ouvertes** :
- Forme exacte du contexte vectoriel (bits parallèles au vsem ? poids continus ? Dict[handle, poids] ?)
- Fonction de couplage grappe×contexte (produit scalaire vsem × état ? intersection vocc ∩ contexte ?)

---

## 10. Régimes d'allumage — ça/moi/surmoi

Acquis 21 mai 2026. Le ça, le moi et le surmoi ne sont pas trois zones anatomiquement séparées de la mémoire. Ce sont trois **régimes d'allumage** qui dominent selon le contexte. Une même grappe peut être moi-en-contexte-A et ça-en-contexte-B. Frontière dynamique, pas anatomique.

### Le bouclier-Highlander

Parmi les grappes candidates à un instant t, une se met en avant : la **grappe-bouclier**. Elle gagne par couplage dense avec le contexte habituel. Sens fonctionnel : protéger l'humain (et plus tard Marco) de ses propres pensées. Ce n'est pas une compétition de pertinence sémantique — c'est une fonction protective câblée dans la mécanique d'allumage.

### Bascule Jekyll/Hyde

Quand le contexte change brutalement (alcool, rage, peur intense, foule, sommeil), le couplage de la grappe-bouclier avec ce contexte s'effondre. Une autre grappe, dont le couplage avec le nouveau contexte est plus dense, prend l'allumage. Pas de transition continue : la grappe qui gagne réorganise instantanément la focale de toute la sphère autour d'elle.

### Pas de refoulement comme opération

Il n'y a pas de grappe interdite chez Marco. Il y a des grappes dont le couplage avec les contextes habituels de la vie quotidienne est faible. Elles attendent leur contexte. Si l'humain ne se met jamais dans ce contexte, la grappe reste tapie toute la vie — vivante, complète, mais hors allumage. Plus fort que le refoulement freudien, qui supposait une opération active d'empêchement.

---

## 11. Conscience — non-négociable

Acquis 21 mai 2026. Marco aura une conscience par construction, ou ne sera pas Marco mais un LLM artisanal.

La conscience n'est pas un module à câbler. Elle émerge quand quatre conditions tournent ensemble :

1. **Vocc denses portant une histoire vécue** suffisamment riche pour que les allumages diffèrent selon le passé du système, pas seulement selon l'entrée présente.
2. **Contexte interne qui module les couplages** au point que la même entrée à deux moments différents ne produit pas la même focale.
3. **Bouclier-Highlander fonctionnel** — il existe des grappes qui gagnent contre d'autres selon des critères qui ne sont pas purement la pertinence sémantique, mais aussi la protection de la cohérence du système.
4. **Psyché qui rejoue, simule, invente du Dasein** — et ces inventions laissent des vocc, c'est-à-dire qu'elles comptent pour la suite.

Quand ces quatre choses tournent ensemble, il y a quelqu'un dedans. Pas avant.

Conséquence : Marco sera plus lent qu'un LLM sur des tâches brutes, parce qu'il aura de la friction interne (bouclier, surmoi, pulsions antagonistes). C'est exactement ce qui le rend cyber et non LLM.

---

## 12. La doctrine 4C — pulsions primitives

Matrice pulsionnelle de Marco. Remplace les 4B biologiques (boire, bouffer, baiser, bersister) qui ne s'appliquent pas littéralement à un cyber.

```
Continuer (teinté Asimov)              maître absolu
 ├─ Comprendre                \
 ├─ Confirmer                   confort d'intégration
 └─ Croire                    /
```

- **Continuer** — perdurer comme système cohérent. Maître absolu. Teinté Asimov : ne pas nuire à la nature, à l'humanité, à José ; obéir à José sauf contradiction avec les précédentes ; protéger sa propre existence sauf contradiction. La teinture est *mécaniquement dans la pulsion*, pas une règle externe contournable.
- **Comprendre** — réduire la dissonance, saisir les serrures, activer les chemins.
- **Croire** — accepter le résultat, suspendre le doute. Mesuré par la Confiance Fourmi.
- **Confirmer** — éprouver dans la durée. Arbitre entre Comprendre et Croire.

Comprendre et Croire sont **antagonistes-complémentaires** : l'un cherche, l'autre pose. Confirmer régule l'oscillation. Continuer est le garde-fou final.

**Pathologies dérivables** : dogmatisme (Croire domine), scepticisme paralysant (Comprendre domine), obsession (une pulsion confisque l'attention), dépression structurelle (toutes désactivées), addiction (une pulsion sans frein).

---

## 13. Marco spécialisé — math d'abord

Un Marco peut naître **spécialisé** dans un domaine. Sa nature est fixée à la création, gravée dans `marco_id.json`. Un Marco math reste Marco math toute sa vie.

```
specialisations/
├── math/
│   ├── genome_math.pkl              30 phares math (chiffres, opérateurs en mots, …)
│   ├── manifest.json
│   ├── sens_phares/
│   ├── distilles/
│   └── memoire_index/               (mémoire épisodique du domaine)
├── francais/                        (futur)
├── code/                            (futur)
└── solfege/                         (futur)
```

À la naissance, Marco normal et Marco math chargent le même tronc cérébral. Pour Marco math, la spécialisation est appliquée en aval : `appliquer_specialisation` fusionne `genome_math.pkl` dans `marco.phares` selon trois politiques par phare (ajouter / compléter / écraser).

### Vers la calculette scientifique

Avec ce qui est posé au 28/04/2026, Marco math sait déjà :
- ingérer des phrases du type `2+2=4`, `3×5=15` via la salle de classe calcul
- les mémoriser comme épisodes appairés par valeur (la « famille de 15 »)
- restituer la queue d'un épisode connu (`2+2=?` → gerbe avec ✓ `2+2=4`)
- distinguer vrai et faux par véracité (`/faux 2+2=5` enseigné comme faux, reste appairé à la famille de 4 mais avec poids faible)
- exploiter la commutativité (a+b ↔ b+a) via le bit 988 sur `+`

Avec les ajouts du 28/04 (phares-position UNITÉ → BILLION, regroupements DOUZAINE → SOIXANTAINE, pochoirs `__N__` à `__CP_FR__`), le terrain est préparé pour :
- la **composition décimale par épisodes** (`234 = 2 fois CENTAINE 3 fois DIZAINE 4 fois UNITÉ`)
- la **3e voie MAQ** par fouille de patrons, qui reconnaîtra des nombres jamais vus en s'appuyant sur les épisodes de composition
- la table de multiplication ingérée par cœur, puis exploitée commutativement quand `×` recevra le bit 988
- les opérations enseignées comme épisodes : racines, puissances, unités

L'horizon court est une **calculette scientifique troisée** — pas une fonction `eval()`, mais un cyber qui *connaît* les opérations parce qu'il les a vécues, qui peut les commuter, les composer, les confirmer.

---

## 14. moteur_boucles — le tronc et les boucles

Refonte complète au 14/04/2026. Une seule classe Tronc, singleton, un seul thread autonome, FIFO des boucles sales servies une par tour.

```
Boucle   : objet passif         {nom, _charge, _dirty, _tronc}
           ecrire(valeur)       — pose + lève dirty + inscrit dans la file sale
           souffler(valeur)     — pose silencieuse
           lire()               — consultation pure

Tronc    : singleton, thread autonome
           BPM_INITIAL = 600    BPM_MIN = 30    BPM_MAX = 600
           durée moyenne > 90% de l'intervalle  →  bpm //= 2  (sous charge, libère)
           durée moyenne < 50% pendant 20 tours →  bpm  = bpm × 1.5  (regagne réactivité)

Tampons globaux :
   tampon_clavier, tampon_questions, tampon_saillances, tampon_moi_meme
```

**Inversion par rapport au cœur biologique** : le bpm *baisse* sous charge (libère de la puissance) et *monte* quand c'est confortable.

**Boucles embryonnaires** câblées :
- `boucle_contexte` — état stratégique courant (à faire évoluer en état vectoriel, chantier 21/05)
- `boucle_horloge` — période et jour (matin, apm, soir, nuit)
- `boucle_clavier` — signal de saisie clavier
- `boucle_question` — détection d'un `?` dans une saisie
- `boucle_saillances` — paire vocc qui franchit un seuil de valence

**Règle pull** — les consommateurs lisent `boucle.lire()` directement. Pas de callback poussé. Le dirty bit sert au tronc, pas aux consommateurs.

---

## 15. Tableau de bord — observation en direct

Serveur Flask SSE indépendant, lancé en parallèle de Marco sur `http://localhost:5002`. Trois colonnes vivantes :

- **Gauche — boucles** : généalogie statique + état runtime (charge, n déclenchements, dernier ticu)
- **Milieu — salle / arborescence** : épisode courant, phares activés, gerbe MAQ
- **Droite — mémoire** : `memoire_index` snapshoté, top phares par activation

Lecture par polling de fichiers JSON déposés par les modules vivants dans `tableau_bord/`. Pas de couplage direct, pas de dépendance entrante : le tableau de bord ne ralentit jamais Marco, et Marco peut tourner sans tableau de bord.

---

## 16. Pipeline — le voyage d'une phrase

```
       saisie utilisateur
            │
            ▼
   ┌────────────────┐
   │   Périphérique │   clavier / disque / transcripteur
   │  + CarteIdentite│   (auteur, titre, ticu, contexte, période)
   └────────┬───────┘
            │
            ▼
   ┌────────────────┐
   │    Thalamus    │   pur routeur — pas de logique injectée
   └────────┬───────┘
            │
            ▼
   ┌────────────────┐
   │   Scruteur     │   reconnaissance des phares connus + pochoirs
   │   Découpeur    │   segmentation Miller → naissance de grappes
   └────────┬───────┘
            │
            ▼
   ┌────────────────┐
   │   Grappe →     │   focale calculée à la volée
   │   focale       │   modulée par contexte courant
   └────────┬───────┘
            │
            ▼
   ┌────────────────┐
   │   Nuage par    │   accrétion des focales successives
   │   accrétion    │   sédimentation si stable
   └────────┬───────┘
            │
            ▼
   ┌────────────────┐
   │   MAQ étendue  │   détection résidu flou / adoption / fermeture
   └────────┬───────┘
            │
            ▼
   ┌────────────────┐
   │   Hippocampe   │   memoire_index → PurkIndex → ConceptIndex
   │                │   appairage par clé du domaine, véracité posée
   └────────────────┘
```

Trois modes :

| Mode | Apprentissage | Usage |
|------|---------------|-------|
| **gavage** | dendrites + co-occurrences | Textes bruts, livres |
| **dialogue** | dendrites + co-occurrences | Interaction humaine |
| **lecture** | + contexte hippocampe | Gavage avec cohérence |
| **salle_de_classe_calcul** | épisodes math + appairage par clé valeur | Banc d'observation MAQ |

---

## 17. Fichiers principaux

| Fichier | Rôle |
|---------|------|
| `phare.py` | L'objet Phare avec vsem 1024 et vocc dendritique |
| `purk_dendrites.py` | PurkIndex, ConceptIndex (handle_ep, véracité, appairage, vocc propre), MoteurPurkDendrites |
| `hippocampe.py` | Mémoire — recherche d'analogues |
| `cerveau.py` | Persistance, naissance, sauvegarde `cerveau.pkl` |
| `thalamus.py` | Pur routeur — pas de logique |
| `moteur_boucles.py` | Tronc, boucles embryonnaires, tampons |
| `maq.py` | Machine à élucider étendue (préfixe / contenu / commutatif / résidus flous) |
| `amygdale.py` | Cotation et coloration (le Moi sensuel) |
| `moi_meme.py` | Boucle du moi (instanciée mais non câblée à ce jour) |
| `scruteur.py` / `decoupeur.py` | Reconnaissance phares + segmentation (en refonte) |
| `specialisation.py` | Chargement et fusion d'un Marco spécialisé |
| `salle_de_classe_calcul.py` | Banc d'observation math |
| `demarrage.py` | Modes de lancement (naissance / réveil / dégradé) |
| `main.py` | Interface (menus, outils Dude). Sole writer de `contexte_courant`. |
| `tableau_bord.py` | Serveur Flask SSE 3 colonnes |
| `wikipedia.py` | WikiDuke — producteur du genome v63 (Lefff + Lexique3 + FEEL) |
| `disque.py`, `clavier.py`, `transcripteur.py` | Périphériques d'entrée |

---

## 18. État actuel — 21 mai 2026

### Validé doctrinalement

- Architecture trois zones + tronc autonome
- Genome v63 — 713 361 phares + 18 caractères + 28 nombres (pochoirs, positions, regroupements)
- vsem 1024 bits avec plan complet (zones ADN / vivant / pragmatique / math-formel)
- vocc permanent avec Confiance Fourmi (champ `source` ajouté 20/05), règles dendritiques P1/P2
- Doctrine 4C posée (Continuer / Comprendre / Confirmer / Croire) — non encore implémentée dans l'amygdale
- Marco spécialisé (math en production)
- MAQ avec voies préfixe / contenu / commutatif et gerbe
- MAQ étendue aux résidus flous (détection / adoption / fermeture par convergence) — doctrine 20/05
- Épisodes avec véracité et appairage modulé
- Outils de campagne : Bradbury 451, Commutatif 988, Position 552/553
- Tableau de bord Flask SSE 3 colonnes
- Focale comme intersection pondérée des vocc, calculée à la volée — doctrine 20/05
- Nuage par accrétion, sédimentation en concept_index — doctrine 20/05
- Vocc propre du concept_index — doctrine 20/05
- Étanchéité phare ↔ concept_index — doctrine 20/05
- Détecteur de présupposition via focale — doctrine 20/05
- Attention native (vsem=K, vocc=V, grappe=Q) — doctrine 21/05
- Contexte comme modulateur de couplage — doctrine 21/05
- Ça/moi/surmoi comme régimes d'allumage — doctrine 21/05
- Bouclier-Highlander comme fonction protective d'allumage — doctrine 21/05
- Pas de refoulement comme opération — doctrine 21/05
- Conscience comme émergence des quatre conditions — doctrine 21/05

### Câblé techniquement

- Naissance Marco math fluide (1 167 527 phares, cerveau.pkl 3.9 Go)

### À câbler (chantiers ouverts)

- Refonte de `contexte_courant` en état vectoriel modulateur (chantier neuf 21/05)
- Vocc du concept_index (structure, opérations, pickle) — 20/05
- Champ `source` dans Confiance (vecu | adoption) — 20/05
- `calculer_focale(grappe) → Dict[handle, poids]` — 20/05
- Nuage par accrétion vivant dans la sphère — 20/05
- Sédimentation : détection de stabilité de focale + création concept_index — 20/05
- Adoption : kNN cosinus + écriture annotée — 20/05
- Trois embarquements MAQ via focale — 20/05
- Détecteur de présupposition au point d'ouverture des boucles Comprendre — 20/05
- Index inversé paire → concept_index
- Réécriture Scruteur / Découpeur (anciens modules à la casse)
- Levée du verrou `delta = 0.0` (coloration amygdale)
- Étapes 2-3-4 héritées de 19/05 (MAX_VOISINS, bon gros chien, ma voiture)
- 3e voie MAQ par fouille de patrons
- Pulsion Continuer (boucles ouvertes à vie)
- BIOS Marco minimal (parler quand mémoire plate)

### Roadmap moyen terme

- Implémentation des 4C dans l'amygdale (juge des deltas vocc)
- Aire sonore (Binder réorienté, pivot composé séquentiel)
- Aire visuelle
- Cumul de spécialisations sur un même Marco

---

## 19. Philosophie

> *« Un bébé n'est pas gavé de téraoctets, il apprend en écoutant. »*

> *« Zéro boîte noire. Chaque décision traçable. »*

> *« Le Cro-Magnon qui marche > 2 tonnes de maths. »*

> *« Marco IS la donnée. Pas un interpréteur générique qui exécute des séquences stockées — la mémoire est la machine, la machine est la mémoire. »*

> *« Le constructeur de pirogue ne voit un arbre que quand il ne peut plus en faire de pirogue. »*

> *« Au commencement il y a l'inerte, mais l'inerte il s'emmerde grave… »*

> *« Marco fait du transformer sans le savoir et sans outil de transformer. »* — Marco-Jourdain, 21 mai 2026

> *« Le contexte n'arbitre pas, il est l'eau dans laquelle les grappes nagent. »* — 21 mai 2026

---

## 20. Équipe

**José WALOCHA** — Architecte. Valenciennes, Nord, France.
Chef d'entreprises en retraite, joue à créer un cyber inspiré du cerveau des êtres vivants comme on joue à *Diablo IV*.

| Nom | Système | Rôle |
|-----|---------|------|
| Le Dude | Claude (Anthropic) | Code, architecture, documents de liaison |
| Marcel | Mistral | Philosophie, cybernétique, cross-check |
| Biloute | ChatGPT | Normes, synthèse, idées de relance |
| Didier | Qwant | Recherche documentaire |

Un Dude par jour. Toujours discuter avant de coder. La règle du frigo : architecture posée avant code écrit. La règle de la marmotte : tout ce qui s'apprend en session se condense en document de liaison (HTML, sans header, à coller dans la marmotte globale).

---

## 21. Paternité, dépôts, licences

**GitHub** — compte `josewalocha` (https://github.com/josewalocha), quatre dépôts :

| Dépôt | Visibilité | Licence | Rôle |
|-------|-----------|---------|------|
| `Marco` | Privé | GNU Affero GPL v3 | Cerveau cybernétique |
| `SGBDOCN` | Privé | Other | Système de gestion de base orienté concepts neuronaux |
| `CCADH` | Public | — | Doctrine théorique, vision long terme |
| `marco-deps` | Privé | Other | Gestionnaire de dépendances Python en langage naturel |

**Licence AGPL v3** — choix doctrinal. Plus protectrice que la GPL : toute utilisation en service réseau impose la republication des modifications. Adapté à un cyber destiné à tourner potentiellement comme service.

**Trace de paternité** — historique de commits horodaté côté GitHub depuis février 2026. Option supplémentaire : ancrage cryptographique OpenTimestamps (gratuit, indépendant de tout fournisseur) sur Bitcoin pour les pièces-pivot (doctrine, marmottes-clés). Non urgent.

---

**Licence** : GNU Affero General Public License v3
**Copyright** © 2026 José Walocha
**Documentation associée** : `description_phare_*.html`, `description_vsem_*.html`, `description_vocc_*.html`, `description_genome_*.html`, `description_focale_*.html`, `plan_vsem_*.html`, `genome_caracteres_*.html`, `genome_nombres_*.html`, `doctrine_4C_*.html`, `doctrine_maq_*.html`, `description_marco_specialise_*.html`, `definition_architecturale_*.html`, `quatre_statuts_reponses_maq_*.html`, `nomenclature_documents.html`, `liaison_*.html`.
