# Index des sources et registre de lecture

> Les livres ne sont **pas** inclus dans ce dépôt (droits d'auteur) : ce sont des références à
> des ouvrages que l'utilisateur possède. Aucune reproduction : règles reformulées, citations ≤ 10 mots.
> Les numéros de pages ci-dessous correspondent aux éditions listées ; avec une autre édition ou un
> autre fichier, les décalages imprimé/PDF sont à recalculer.

## 1. Fichiers et éditions

| Sigle | Ouvrage | Édition de référence | PDF (fait foi pour les pages) | Texte brut |
|---|---|---|---|---|
| **EIA** | Lisa Maria Martin, *Everyday Information Architecture* | A Book Apart, © 2019, ISBN 978-1-937557-75-1 (1re éd.) | 134 p., calibre ; **p. PDF = p. imprimée + 6** | dump texte brut |
| **DI** | J. Tidwell, C. Brewer, A. Valencia, *Designing Interfaces*, 3e éd. | O'Reilly, janv. 2020, ISBN 978-1-492-05196-1 | 602 p. ; **p. PDF = p. imprimée + 20** | dump texte brut |
| **DMMT** | Steve Krug, *Don't Make Me Think, Revisited*, 3e éd. | New Riders, © 2014 | 214 p. ; **p. PDF = p. imprimée + 11** (folio « [ n ] ») | dump texte brut |

Décalages établis par détection des folios sur les pages (EIA : 113 pages concordantes ; DI : 538 ; DMMT : 182).

### Qualité des versions
- **PDF** : extraction `pdftotext -layout` complète ; pages quasi vides = ouvertures de chapitre ou pleines images. Les figures ne sont pas dans le texte : examinées visuellement quand le principe en dépend (liste §3).
- **Texte brut / Markdown** (version de travail) : aucun titre `#`, aucune image, aucun tableau ; blocs ``` parasites (≈ 820 à 2 800 lignes selon le livre), césures, en-têtes et folios partiels. Comparaison de 3 passages par livre avec le PDF : DI identique (chapitre 9 entier : 0 divergence) ; EIA et DMMT divergent par en-têtes, légendes et encadrés intercalés ; la Table 9-1 de DI est aplatie.
- **Règle** : citer les pages depuis le PDF ; le Markdown sert à la recherche plein texte et aux paragraphes de corps, jamais aux tableaux, figures, encadrés ni numéros de page.

## 2. Méthode de lecture (transparence)
Lecture du texte des chapitres listés, consignes : paraphrase, références imprimé + PDF, « explicite » vs « déduction ». Contrôle : environ 30 références retrouvées au texte à la page annoncée (échantillon des principes utilisés dans le skill), 4 corrigées au passage. Les principes non contrôlés un à un restent fondés sur la lecture.

## 3. Registre de lecture

### EIA — lu intégralement (PDF 1–134)
| Chapitre | Imprimé | PDF | Statut | Inexploitable | Figures examinées |
|---|---|---|---|---|---|
| Introduction | 1–3 | 7–9 | intégral | — | — |
| 1 Systems of Organization (LATCH) | 4–17 | 10–23 | intégral | captures 1.1–1.9 (légendes seules) | — |
| 2 Content Analysis (audits, inventaire) | 18–35 | 24–41 | intégral | tableurs 2.1–2.4 (légendes) | — |
| 3 Categories and Labels (critères, 4 facteurs, libellés) | 36–55 | 42–61 | intégral | 3.1–3.13 (légendes) | — |
| 4 Site Structure (audit de structure, sitemaps) | 56–74 | 62–80 | intégral | 4.1–4.7 (cellules non lues ; colonnes décrites p.61–62) | — |
| 5 Navigation and Wayfinding | 75–98 | 81–104 | intégral | 5.1–5.11, 5.13 (légendes) | **5.12** modes de recherche (PDF 100) |
| 6 Tags and Taxonomies | 99–115 | 105–121 | intégral | 6.1–6.12 (légendes) | — |
| Conclusion, Resources, Index | 116–126 | 122–132 | intégral | — | — |

Non décrits par le livre : protocoles de tri de cartes et de test d'arborescence (outils seulement cités).

### DI — chapitres utiles lus ; autres signalés
| Chapitre | Imprimé | PDF | Statut | Figures examinées |
|---|---|---|---|---|
| 1 Designing for People | 1–26 | 21–46 | intégral | — |
| 2 Organizing the Content (couches, MECE, Overview/Focus/Make/Do, patterns) | 27–127 | 47–147 | intégral ; Media Browser, Canvas Plus Palette, Tags lus mais non retenus | 2-12/13, 2-34/35, 2-43/44 |
| 3 Getting Around (modèles de navigation, patterns) | 129–208 | 149–228 | intégral ; Fat Menus, Sitemap Footer, Annotated Scroll Bar non retenus | 3-1 à 3-10, 3-13, 3-18, 3-26/27, 3-32, 3-50 à 3-54 |
| 4 Layout of Screen Elements | 209–254 | 229–274 | intégral | 4-1, 4-23, 4-34 |
| 5 Visual Style | 255–294 | 275–314 | **partiel** : 255–282 lus ; styles 282–294 survolés | — |
| 6 Mobile Interfaces | 295–334 | 315–354 | intégral | 6-6 |
| 7 Lists of Things | 335–374 | 355–394 | intégral | 7-7 |
| 8 Doing Things: Actions and Commands | 375–432 | 395–452 | intégral | 8-9 |
| 9 Showing Complex Data | 433–469 | 453–489 | intégral | 9-1 à 9-5, 9-11 à 9-17, 9-25 à 9-27 |
| 10 Forms and Controls | 471–531 | 491–551 | intégral | — |
| 11 UI Systems / Atomic Design | 533–556 | 553–576 | **survol** (section frameworks non lue) | — |
| 12 Beyond the Screen | 557–559 | 577–579 | lu, sans objet | — |

Non traité par le livre : tableaux de gestion denses (voir `references/donnees.md` « Hors livre »), agenda, états vides, skeleton, WCAG chiffré.

### DMMT — lu intégralement (ch.1–13)
| Chapitre | Imprimé | PDF | Statut | Figures examinées |
|---|---|---|---|---|
| 1 Don't make me think | 10–19 | 21–30 | intégral | — |
| 2 How we really use the Web | 20–27 | 31–38 | intégral | — |
| 3 Billboard Design 101 | 28–41 | 39–52 | intégral | p.34, 35, 36, 40 |
| 4 Animal, Vegetable, or Mineral | 42–47 | 53–58 | intégral | — |
| 5 Omit needless words | 48–53 | 59–64 | intégral | — |
| 6 Street signs and Breadcrumbs (trunk test) | 54–83 | 65–94 | intégral | p.65, 66, 81, 82, 83 |
| 7 Big Bang Theory (accueil) | 84–100 | 95–111 | intégral | — |
| 8 Farmer and Cowman | 102–109 | 113–120 | intégral | — |
| 9 Usability testing | 110–141 | 121–152 | intégral (notes de marge de la séance type partiellement mêlées) | — |
| 10 Mobile | 142–163 | 153–174 | intégral | p.148–153 |
| 11 Usability as common courtesy | 164–171 | 175–182 | intégral | — |
| 12 Accessibility | 172–181 | 183–192 | intégral | — |
| 13 Guide for the perplexed | 182–191 | 193–202 | intégral | — |

Spécifique à 2014 / sites de contenu (à transposer avec prudence) : accueil « grande porte », slogan, onglets, recrutement et indemnités, bascule « site complet », critique du flat design, WCAG/Section 508 de l'époque.

## 4. Correspondance règles du skill → livres
| Fichier | Règles | Sources principales |
|---|---|---|
| `references/architecture.md` | A-01…A-16 | EIA ch.1–6 ; DI ch.2–3, 7 ; DMMT ch.6 |
| `references/interactions.md` | I-01…I-15 | DI ch.1–4, 6–8, 10 ; DMMT ch.7, 11 |
| `references/clarte.md` | C-01…C-12 | DMMT ch.1–5, 10–12 ; DI ch.4–6 |
| `references/donnees.md` | D-01…D-08 | DI ch.2, 6–9 |
| `references/validation.md` | V-01…V-08 | DMMT ch.6, 8–10, 13 ; EIA ch.4 |
| `references/arbitrages.md` | T1…T13 | croisement des trois |
