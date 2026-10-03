---
name: dont-make-me-think
description: Use when creating, changing, reorganizing or reviewing any screen, navigation, menu, form, list, dashboard, user journey, information architecture, labels or onboarding, or when auditing the UX of a web app, SaaS, mobile app, website or internal tool, including changes touching several user roles. Triggers (French) « refonte », « réorganiser », « navigation », « arborescence », « parcours », « audit UX », « revue UI », « où placer », « menu », « écran », « formulaire ».
---

# Don't Make Me Think — architecture de l'information et UX produit

Méthode de décision fondée sur trois livres (EIA, DI, DMMT — `sources/index-sources.md`) et
appliquée à une cartographie vérifiable du produit (voir `references/cartographie-maj.md`).
**Principe** : aucune décision UX sans constat prouvé, tâche nommée, règle sourcée et moyen de
validation. Les livres ne fournissent **aucune** règle métier propre au produit.

## Première utilisation sur un projet
Avant l'étape 0, construire le contexte du projet : suivre `references/contexte-projet.md`
(sources de vérité, rôles, routes, design system, registre des décisions). Sans ce contexte,
tout est hypothèse.
**Sans dépôt** (projet décrit en conversation, maquette, entretien produit) : pas de cartographie ;
livrer la proposition étiquetée [H] + la liste des questions bloquantes, et dire que rien n'est vérifié dans le code.

## Règles non négociables
1. **Ne rien inventer du métier** (prérequis, annulation, paiement, droit, conformité) : source projet (spec, ADR, réglage) ou « inconnu » → registre des questions ouvertes du projet (ou en créer un si absent). Une valeur **donnée par l'utilisateur** dans la demande se note [C] (décision du demandeur) ; ses effets non précisés (portée, rétroactivité, qui la modifie) restent des inconnues.
2. **Fréquence** : observée (source) ou étiquetée *supposée*. Jamais déduite de la visibilité d'un bouton.
3. **Existant ≠ proposé ≠ hypothèse** ; route ≠ fonctionnalité accessible (vérifier menu, garde front, garde API, droits de données).
4. **Une information = un domicile** ; les autres emplacements sont des raccourcis reliés (A-06).
5. **Aucune rubrique fourre-tout** : critère d'inclusion/exclusion écrit (A-02).
6. **Préserver** règles métier, permissions, contrats d'API et composants existants (design system du projet d'abord). Avant toute proposition touchant un droit, un rôle ou une règle : chercher les décisions **tranchées** (registre des questions ouvertes, ADR, journal de décisions) — une proposition de la cartographie peut être périmée ou contraire à une décision.
7. **Revue experte ≠ test utilisateur.** Jamais « parfait » ni « validé » sans observation.
8. Une inconnue qui **change matériellement** la décision → demander à l'utilisateur ; sinon avancer avec une hypothèse [H] écrite.

## Workflow

| Étape | Faire | Charger | Sortie |
|---|---|---|---|
| **0. Cadrer** | Ampleur S/M/L (V-01), rôles et espaces touchés | `references/validation.md` §V-01, `references/cartographie-maj.md` §1 | cadrage |
| **A. Auditer l'existant** | Lire la partie pertinente de la cartographie et les audits existants du projet, **puis revérifier dans le code** (routes, menus, gardes, composants, états, données). Distinguer implémenté / observé / proposé | cartographie du projet, `references/contexte-projet.md` | `templates/audit.md` §0–1 |
| **B. Tâches** | Déclencheur, contexte, résultat, mode de recherche, rôle | `references/architecture.md` A-13 | audit §3 |
| **C. Classer** | Pour chaque info/action : tâche, fréquence (source), urgence, contexte, portée, relations, domicile, raccourcis ; critères des rubriques ; LATCH pour explorer groupement **et** ordre | `references/architecture.md` A-01…A-06, A-14 | audit §2 |
| **D. Structurer** | Modèle de navigation par zone, arborescence justifiée, libellés, parcours, vue d'ensemble ↔ détail, contextes parallèles. Options comparées **seulement** si arbitrage réel | `architecture.md` A-07…A-12 ; `interactions.md` ; `arbitrages.md` | `templates/decision-ux.md` |
| **E. Spécifier les écrans** | Finalité, priorités, actions et poids, regroupements, immédiat vs à la demande, états, mobile vs grand écran | `interactions.md`, `clarte.md`, `donnees.md` (écrans denses) | `templates/fiche-ecran.md` |
| **F. Vérifier** | Conséquences sur les autres espaces/rôles ; portes techniques ; revue V-04 ; test du coffre V-03 ; tâches de test V-05 ; **mise à jour de la cartographie** | `validation.md`, `cartographie-maj.md` §2 | contrôles + diff cartographie |

**Profondeur** : S → A (écran seul), E, F-technique. M → A–F pour un rôle. L → A–F complet, tous rôles touchés, cartographie mise à jour, test utilisateurs planifié.

Pour mener une refonte complète en plusieurs lots (multi-agents, file de fusion), voir `prompts/refonte-loop.md` (modèle à adapter).

## Critères de sortie
- [ ] Chaque proposition suit la chaîne constat [F] → tâche → règle [S] → proposition → conséquences → validation
- [ ] Statuts [F]/[S]/[D]/[C]/[H] présents ; références livres avec chapitre et pages (imprimée / PDF)
- [ ] Domicile unique + critères de rubrique écrits ; aucune règle métier inventée
- [ ] États (chargement, vide, erreur, succès, hors-ligne, sans droit) spécifiés
- [ ] Conséquences par rôle/espace listées ; permissions et contrats inchangés ou décision d'architecture prévue
- [ ] Validation : technique + revue + tâche de test utilisateur ; formulation honnête du niveau de preuve
- [ ] Cartographie mise à jour si route, menu, rôle, permission, entité ou parcours changent

## Signaux d'alerte — s'arrêter
| Pensée | Réalité |
|---|---|
| « La navigation proposée semble bonne, je la reprends » | C'est une hypothèse : l'évaluer contre les tâches et les décisions d'architecture existantes |
| « Les utilisateurs utilisent surtout… » | Source ? Sinon [H] |
| « Je range le reste dans Compte / Réglages » | Critère résiduel = fourre-tout (A-02) |
| « Délai d'annulation, prérequis, plafond : je mets une valeur plausible » | Règle métier inventée : inconnu + registre des questions ouvertes |
| « Doublon de bouton, je supprime » / « aucune raison trouvée » | Chercher la raison partout avant : commentaires, historique git (`git log -S`), registre des manquements, ADR, audits UX ; distinguer l'exigence (ex. une déconnexion **visible**) de l'emplacement |
| « La revue est concluante, l'UX est bonne » | Revue experte = hypothèses ; test utilisateur requis |
| « Trois clics max » | Aucune source ; arbitrer répétition × incertitude (T2) |
