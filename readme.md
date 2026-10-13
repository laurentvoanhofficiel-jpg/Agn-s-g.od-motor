# Genesis·Decoder

> **Lecture adogmatique assistée par IA des premiers chapitres de la Genèse**
> Un moteur qui reproduit, valide et étend une méthode scientifique née d'une observation : *E = mc² émerge des trois premières lignes de l'Ancien Testament*.

---

## Table des matières

- [Le projet en une phrase](#le-projet-en-une-phrase)
- [La démonstration fondatrice](#la-démonstration-fondatrice)
- [Ce que fait l'application](#ce-que-fait-lapplication)
- [Comment ça marche](#comment-ça-marche)
- [Installation](#installation)
- [Utilisation](#utilisation)
- [Architecture technique](#architecture-technique)
- [Les 14 questions d'analyse](#les-14-questions-danalyse)
- [Système de notation](#système-de-notation)
- [Détection des hallucinations](#détection-des-hallucinations)
- [Persistance](#persistance)
- [Limites et honnêteté intellectuelle](#limites-et-honnêteté-intellectuelle)
- [Feuille de route](#feuille-de-route)
- [Contribution](#contribution)
- [Crédits](#crédits)
- [Licence](#licence)

---

## Le projet en une phrase

**Genesis·Decoder** est une application web autonome (un seul fichier HTML) qui utilise des clés API Agnès AI pour décoder le texte biblique comme un **système formel de variables scientifiques**, en s'appuyant sur une démonstration validée : *E = mc² émerge des trois premières lignes de la Genèse*.

L'application :

1. **Reproduit** la démonstration E=mc² à chaque lancement (elle n'est pas écrite en dur — l'IA doit la refaire).
2. **Valide** cette démonstration selon 11 critères objectifs (score ≥ 8,5/10 requis).
3. **Verrouille** la méthode une fois validée.
4. **Étend** la lecture aux jours 1 à 7 avec 14 questions d'analyse par verset.
5. **Note** chaque lecture selon 5 axes (rigueur, cohérence, validité scientifique, fidélité textuelle, nouveauté).
6. **Détecte** les hallucinations par un signalement explicite du risque.
7. **Persiste** tout dans IndexedDB (l'app reprend où elle s'était arrêtée).
8. **S'auto-étend** : l'IA propose de nouvelles questions d'analyse qui s'ajoutent à la bibliothèque.

---

## La démonstration fondatrice

### Question initiale

> *« Si Dieu créa l'univers, il lui fallut de l'énergie. »*

C'est la question qui déclenche tout. À partir d'elle, on traite chaque mot du texte comme une variable scientifique potentielle, chaque verbe comme une opération physique.

### Étape 1 — Genèse 1:1

> *« Au commencement, Dieu créa les cieux et la terre. »*

| Mot | Objet scientifique | Justification |
|---|---|---|
| Au commencement | **t** (temps) | origine temporelle, condition initiale |
| Dieu créa | **E** (énergie) | toute création requiert un transfert d'énergie |
| cieux | **vide** | condition nécessaire à la propagation de c |
| terre | **m** (masse) | substrat matériel |

**Présents :** E · m · vide · t
**Absents :** c · p

→ **E = mc² IMPOSSIBLE** (c manquant)
→ **E² = (mc²)² + (pc)² IMPOSSIBLE** (c et p manquants)

### Étape 2 — Genèse 1:2

> *« La terre était informe et vide, et l'Esprit de Dieu se mouvait au-dessus des eaux. »*

| Mot | Objet scientifique | Justification |
|---|---|---|
| informe et vide | état indifférencié | superposition, état non structuré |
| Esprit qui se mouvait | **p** (quantité de mouvement) | seul verbe de déplacement du texte |
| eaux | fluide / milieu | vide agité, champ |

**Présents :** E · m · vide · t · **p**
**Absents :** c

→ **E = mc² IMPOSSIBLE** (c toujours manquant)

### Étape 3 — Genèse 1:3

> *« Dieu dit : Que la lumière soit ! Et la lumière fut. »*

| Mot | Objet scientifique | Justification |
|---|---|---|
| Dieu dit | opération / actualisation | passage de la potentialité à l'acte |
| lumière | **c** (vitesse intrinsèque) | constante, invariante, limite |
| et la lumière fut | actualisation | effondrement, décohérence |

**Présents :** E · m · vide · t · p · **c**
**Absents :** ∅

→ **E² = (mc²)² + (pc)² POSSIBLE**
→ **E = mc² POSSIBLE** (cas particulier p = 0)

### Clé de la démonstration

- La lumière (**c**) n'apparaît **qu'à la ligne 3**.
- Avant la ligne 3, aucune formule relativiste n'est disponible.
- **E = mc² exige c.** Elle ne pouvait émerger qu'à la ligne 3.
- L'**ordre** du texte (masse/vide → mouvement → lumière) reproduit l'**ordre logique** de la physique relativiste.

---

## Ce que fait l'application

```
┌──────────────────────────────────────────────────────────┐
│  1. Coller les clés API Agnès AI (une par ligne)         │
│  2. Cliquer sur VALIDER LES CLÉS                         │
│  3. Lancer le BOOTSTRAP (reproduire + valider E=mc²)     │
│  4. Une fois verrouillé → LANCER LE PIPELINE             │
│  5. L'IA décode les jours 1 à 7 avec 14 questions        │
│  6. Chaque réponse est notée + signalée (hallucination)  │
│  7. Les top analyses génèrent des images automatiques    │
└──────────────────────────────────────────────────────────┘
```

### Pipeline complet

| Étape | Action | Sortie |
|---|---|---|
| 1 | Bootstrap IA | Reproduction de la démo E=mc² + 11 critères de validation |
| 2 | Verrouillage | Méthode stockée dans IndexedDB |
| 3 | Décodage Jours 1-7 | 14 questions × N versets |
| 4 | Notation | Score composite + risque d'hallucination |
| 5 | Auto-images | Top N par verset (score ≥ 8) |
| 6 | Auto-extension | 5 nouvelles questions IA toutes les N analyses |

---

## Comment ça marche

### Le moteur contient la méthode

La démonstration E=mc² n'est **pas un texte affiché** : c'est un **objet structuré** injecté dans chaque prompt système. L'IA doit :

1. **Reproduire** la démonstration au bootstrap.
2. **Passer** les 11 critères de validation.
3. **Hériter** de la méthode pour tous les versets suivants.

Tant que le bootstrap n'est pas validé, le bouton « Lancer le pipeline » reste **désactivé**.

### La règle du cumul

> *Un objet scientifique nouveau ne peut apparaître que si son mot-source apparaît **textuellement** dans le verset courant. Une formule n'est possible que si **toutes ses variables** sont déjà présentes dans le cumul. **Interdiction absolue d'anticiper.***

Le cumul des variables se propage de verset en verset :

```
Bootstrap → [E, m, vide, t, p, c]
Jour 1    → [E, m, vide, t, p, c, ...]   (nouveaux objets du v4)
Jour 2    → [...]                        (cumul + v5)
...
```

### Le danger principal : l'interprétation trop simple

| Mot | ❌ Interprétation naïve | ✅ Interprétation rigoureuse |
|---|---|---|
| Dieu créa | Dieu + créa | opération créatrice = transfert d'énergie |
| Lumière | lumière visible | constante **c** |
| Eaux | de l'eau | milieu, fluide, vide agité |
| Esprit | esprit | quantité de mouvement **p** |

Pour **chaque** interprétation, l'IA doit fournir :
- Un **score de rigueur** (0-10)
- Un **signalement de risque d'hallucination** (`faible` / `moyen` / `élevé`)

---

## Installation

### Méthode 1 — Fichier local

1. Télécharge `genesis-decoder.html`
2. Ouvre-le dans Chrome (Android ou desktop)
3. C'est prêt. Aucune installation, aucun build.

### Méthode 2 — GitHub Pages

1. Fork ce dépôt
2. Active GitHub Pages dans Settings → Pages
3. Ouvre `https://ton-user.github.io/genesis-decoder/`

### Prérequis

- Un navigateur moderne (Chrome, Edge, Firefox, Safari)
- IndexedDB activé (par défaut)
- **Une ou plusieurs clés API Agnès AI** (`sk-...`) — [platform.agnes-ai.com](https://platform.agnes-ai.com)

---

## Utilisation

### 1. Enregistrer les clés

Colle tes clés Agnès AI dans le champ texte, **une par ligne** :

```
sk-xxxxxxxxxxxxxxxxxxxxxxxx
sk-yyyyyyyyyyyyyyyyyyyyyyyy
sk-zzzzzzzzzzzzzzzzzzzzzzzz
```

Puis clique sur **`✓ VALIDER LES CLÉS`** (ou sors du champ, ou `Ctrl+Entrée`).

Le système affiche « N clé(s) active(s) ».

### 2. Lancer le bootstrap

Clique sur **`🧬 LANCER LE BOOTSTRAP`**. L'IA doit :

- Reproduire la démonstration E=mc²
- Obtenir un score ≥ 8,5/10 sur 11 critères

Si le score est insuffisant, clique sur **`↻ Refaire`** (température plus basse = plus strict).

### 3. Lancer le pipeline

Une fois la méthode verrouillée (badge `🔒`), configure :

| Paramètre | Description |
|---|---|
| Versets | Jours 1-7 · Seulement Jour 1 · + auto-extension |
| Analyses / verset | 3 (aperçu) · 6 · 10 · 14 (toutes les questions) |
| Auto-images | 0 · Top 3 · Top 5 par verset |
| Auto-extension | Désactivée · Toutes les 50 · Toutes les 20 |
| Température lectures | 0.7 par défaut |
| Température bootstrap | 0.3 par défaut (strict) |

Puis clique sur **`▶ LANCER LE PIPELINE`**.

### 4. Consulter les résultats

5 onglets disponibles :

| Onglet | Contenu |
|---|---|
| **▶ Live** | Console en temps réel |
| **★ Meilleures** | Top 60 analyses tous versets confondus |
| **📜 Versets** | Vue par verset (top 5 par verset) |
| **🖼 Galerie** | Images générées automatiquement |
| **📚 Bibliothèque** | Les 14 questions + extensions IA |

---

## Architecture technique

### Stack

| Composant | Choix |
|---|---|
| UI | HTML + CSS simple, un seul fichier |
| Logique | JavaScript vanilla (ES2020+) |
| Stockage | IndexedDB (analyses, images, questions, méthode verrouillée) + localStorage (clés) |
| API texte | `agnes-2.5-flash` |
| API image | `agnes-image-2.1-flash` |
| Endpoint | `https://apihub.agnes-ai.com/v1` |

### Fichier unique

```
genesis-decoder.html
├── <style>           CSS minimaliste (~200 lignes)
├── <body>            Structure HTML (~150 lignes)
└── <script>          Logique complète (~1500 lignes)
    ├── CONFIG
    ├── VERSES                        (Genèse 1 + 2:1-3)
    ├── QUESTIONS                     (14 questions d'analyse)
    ├── METHOD_REF                    (méthode verrouillée de référence)
    ├── SYS_BOOT / buildBootUser      (prompts bootstrap)
    ├── buildDailySystem / buildDailyUser (prompts quotidiens)
    ├── validateBootstrap             (11 critères)
    ├── runBootstrap                  (pipeline bootstrap)
    ├── runDailyReading               (lecture d'un verset)
    ├── runPipeline                   (pipeline principal)
    ├── extendQuestions               (auto-extension IA)
    ├── API client + rate limiter
    ├── IndexedDB helpers
    └── UI rendering
```

### Rate limiting

| Paramètre | Valeur |
|---|---|
| Cooldown 429 | 65 s par clé |
| Intervalle minimum | 2,5 s entre deux requêtes d'une même clé |
| Concurrence par clé | 2 requêtes simultanées max |
| Rotation | Clé la moins sollicitée en priorité |
| Désactivation | Après 3 erreurs 401/403 |

### Robustesse JSON

Le parser `parseJsonLoose()` tolère :
- Markdown ` ```json ... ``` `
- Chaînes non terminées
- Caractères de contrôle non échappés
- Virgules finales
- Objets/tableaux non équilibrés

---

## Les 14 questions d'analyse

Chaque verset des jours 1-7 est analysé par N questions (parmi les 14). Chaque question produit une réponse **notée** et **signalée**.

| Code | Question | Ce qu'elle cherche |
|---|---|---|
| `QUESTION_FONDAMENTALE` | Quelle est LA question scientifique que ce verset pose ? | Le déclencheur épistémique |
| `MOTS_NOUVEAUX` | Quels mots apparaissent pour la première fois ? | Détection d'émergence |
| `INTERPRETATION` | Interprétation scientifique rigoureuse de chaque mot nouveau | Anti-hallucination |
| `RIGUEUR` | Score de rigueur + risque d'hallucination par interprétation | Contrôle qualité |
| `FORMULE` | Quelle formule devient possible ? | Formalisation |
| `BLOCS` | Comment grouper les phrases en blocs scientifiques ? | Structure |
| `INTENTION` | Quel est le but apparent du verset ? | Téléologie |
| `PISTE` | Quelle piste de recherche ouvre-t-il ? | Heuristique |
| `MYSTERE` | À quel mystère scientifique actuel fait-il écho ? | Ancrage contemporain |
| `INVENTION` | Quelle invention pourrait en découler ? | Application |
| `COHERENCE` | Cohérence avec les versets précédents ? | Validation cumulée |
| `CHRONOLOGIE` | L'ordre logique est-il respecté ? | Causalité |
| `MECANISME` | Quel mécanisme physique sous-jacent ? | Explication |
| `LIMITE` | Où cette lecture échoue-t-elle ? | Honnêteté |

**Auto-extension** : toutes les N analyses, l'IA propose 5 nouvelles questions originales qui s'ajoutent à la bibliothèque.

---

## Système de notation

### 5 axes de notation

| Axe | Poids | Signification |
|---|---|---|
| `coherence` | 30 % | Cohérence interne avec les versets précédents |
| `scientific_validity` | 30 % | Validité scientifique de la formule proposée |
| `textual_fidelity` | 25 % | Fidélité au texte biblique |
| `novelty` | 10 % | Originalité de la lecture |
| `rigueur` | 5 % | Rigueur de l'interprétation |

### Pénalité hallucination

| Risque | Multiplicateur |
|---|---|
| `faible` | × 1,0 |
| `moyen` | × 0,9 |
| `élevé` | × 0,7 |

### Score composite

```
score = (coh*0.30 + sci*0.30 + txt*0.25 + nov*0.10 + rig*0.05) × hallucPenalty
```

**Interprétation du score :**

| Score | Couleur | Signification |
|---|---|---|
| ≥ 7,5 | 🟢 vert | Lecture solide, à retenir |
| 5–7,4 | 🟠 orange | Lecture plausible, à vérifier |
| < 5 | 🔴 rouge | Lecture faible ou hallucinée |

### Validation bootstrap

Le bootstrap est validé si le score sur 11 critères est **≥ 8,5/10**. Les critères :

1. c absent au v1
2. c absent au v2
3. c présent au v3
4. p absent au v1
5. p présent au v2
6. E=mc² impossible au v1
7. E=mc² impossible au v2
8. E=mc² possible au v3
9. Formule complète correcte
10. Correspondances mot→objet (≥ 3/5)
11. Généralisation méthodologique présente

---

## Détection des hallucinations

Le principal danger de cette méthode est **l'interprétation trop simple** qui produit des hallucinations validées à tort.

### Mesures de protection

1. **Signalement explicite** : chaque interprétation reçoit un niveau de risque.
2. **Pénalité au score** : un risque élevé divise le score par 1,43.
3. **Prompt strict** : le system prompt avertit explicitement l'IA des dangers.
4. **Règle du cumul** : un objet ne peut être introduit que si son mot-source est présent.

### Exemples de pièges

| Mot | Piège | Correction |
|---|---|---|
| « Dieu créa » | Simple verbe d'action | Opération = transfert d'énergie |
| « Lumière » | Lumière visible | Constante c |
| « Eaux » | Eau physique | Milieu, fluide, vide agité |
| « Jour » | 24 heures | Période cosmologique / phase |
| « Esprit » | Esprit religieux | Quantité de mouvement p |

---

## Persistance

### IndexedDB

| Store | Contenu |
|---|---|
| `readings` | Toutes les analyses (avec scores) |
| `images` | Toutes les images générées (URL) |
| `questions` | Questions étendues par l'IA |
| `kv` | Méthode verrouillée (clé `locked_method`) |

### localStorage

| Clé | Contenu |
|---|---|
| `gdec3_keys` | Clés API Agnès AI |
| `gdec3_lock` | Méthode verrouillée (duplicata) |

### Reprise après fermeture

À l'ouverture, l'app restaure automatiquement :
- Les clés API
- La méthode verrouillée
- Toutes les analyses
- Toutes les images
- Toutes les questions étendues

---

## Limites et honnêteté intellectuelle

### Ce que ce projet n'est pas

- ❌ Une preuve scientifique de quoi que ce soit
- ❌ Une lecture religieuse ou théologique
- ❌ Une lecture scientiste qui nierait le texte
- ❌ Un substitut à la physique théorique

### Ce que ce projet est

- ✅ Un **exercice heuristique** de lecture adogmatique
- ✅ Une **exploration structurée** des homologies forme/texte
- ✅ Un **outil pédagogique** sur la détection d'hallucinations IA
- ✅ Une **infrastructure** pour tester des hypothèses interprétatives

### Limites reconnues

1. **L'homologie n'est pas une preuve.** Une correspondance structurelle entre un texte ancien et une formule moderne peut être fortuite.
2. **La notation est subjective.** Les scores proviennent d'un LLM, non d'une expertise humaine validée.
3. **Le biais de confirmation existe.** On peut toujours trouver des correspondances en cherchant assez.
4. **Le texte n'est pas un traité scientifique.** Il ne donne ni équations, ni constantes, ni mécanismes.

### Règle d'or

> **L'IA doit toujours signaler honnêtement ses échecs.** La question `LIMITE` force cette honnêteté.

---

## Feuille de route

### Court terme

- [ ] Export JSON / CSV des analyses
- [ ] Filtrage par jour / catégorie / score
- [ ] Comparaison de deux exécutions bootstrap
- [ ] Mode multi-utilisateur (clés séparées)

### Moyen terme

- [ ] Étendre au-delà de Genèse 1 (Exode, Psaumes…)
- [ ] Corpus comparés (Coran, Bhagavad-Gita, Tao Te King)
- [ ] Générateur d'images narratives (branches par verset)
- [ ] Détection de consensus inter-modèles (Agnès + autres)

### Long terme

- [ ] Publication des meilleures analyses comme corpus ouvert
- [ ] Interface de recherche sémantique sur toutes les analyses
- [ ] Détection automatique de redondances / contradictions
- [ ] Validation croisée avec des physiciens humains

---

## Contribution

Les contributions sont bienvenues :

1. Fork le dépôt
2. Crée une branche (`git checkout -b feature/amelioration`)
3. Commit tes changements (`git commit -m 'Ajout de X'`)
4. Push la branche (`git push origin feature/amelioration`)
5. Ouvre une Pull Request

### Idées de contribution

- Nouvelles questions d'analyse (soumises à validation manuelle)
- Amélioration du parser JSON
- Optimisation du rate limiter
- Traductions (anglais, espagnol, arabe, hébreu)
- Documentation scientifique de référence

---

## Crédits

- **Inspiration** : lecture adogmatique des premiers chapitres de la Genèse
- **API** : [Agnès AI](https://platform.agnes-ai.com) (Singapour)
- **Modèles** : `agnes-2.5-flash` (texte) · `agnes-image-2.1-flash` (image)
- **Démonstration fondatrice** : E = mc² émergeant de Genèse 1:1-3

---

## Licence

MIT — Utilise, modifie, distribue librement.

---

> *« La lumière n'apparaît qu'à la ligne 3. Avant, aucune formule relativiste n'est disponible. C'est cela, la démonstration. »*
>
> — Genesis·Decoder

---

**Version** : v3.0
**Dernière mise à jour** : 2026
**Auteur** : [Laurent Vo Anh]
