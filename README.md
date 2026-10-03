# Don't Make Me Think — skill Claude Code d'architecture de l'information et d'UX produit

Skill pour Claude Code qui guide toute décision d'interface (écran, navigation, menu, formulaire,
liste, tableau de bord, parcours, libellés, onboarding, audit UX) sur **n'importe quel projet
logiciel** : application web, SaaS, application mobile, site, outil interne.

Principe : aucune décision UX sans constat prouvé, tâche nommée, règle sourcée et moyen de
validation. La méthode s'appuie sur trois ouvrages de référence (sigles EIA, DI, DMMT, détaillés
dans `sources/index-sources.md`) et sur une cartographie vérifiable du produit.

## Installation

```bash
git clone https://github.com/dgervalla-ship-it/dont-make-me-think.git ~/.claude/skills/dont-make-me-think
```

`SKILL.md` se trouve à la racine du dépôt : le dossier cloné est directement le skill.

## Mise à jour

```bash
cd ~/.claude/skills/dont-make-me-think && git pull
```

## Utilisation

- Invocation explicite : `/dont-make-me-think`
- Déclenchement automatique : demandes de refonte, navigation, arborescence, parcours, audit UX,
  revue UI, « où placer », menu, écran, formulaire.
- À la première utilisation sur un projet, le skill construit le contexte du projet
  (`references/contexte-projet.md`) : sources de vérité, rôles, routes, design system, décisions.

## Structure

| Dossier / fichier | Rôle |
|---|---|
| `SKILL.md` | règles non négociables, workflow 0→F, critères de sortie, signaux d'alerte |
| `references/` | règles de décision : architecture de l'information, interactions, clarté, données, validation, arbitrages, mise à jour de la cartographie, construction du contexte projet |
| `templates/` | modèles : audit/inventaire, décision UX, fiche écran |
| `prompts/` | modèle de prompt pour une refonte multi-lots (à adapter) |
| `tests/` | cas de test du skill (RED → GREEN → REFACTOR) |
| `sources/` | index des trois ouvrages et registre de lecture (références de pages) |

## Sources et droits d'auteur

Ce dépôt **ne contient aucun contenu des livres** : uniquement des règles reformulées, avec
références de chapitres et de pages. Les ouvrages sont des références à des livres que
l'utilisateur doit posséder pour vérifier les pages citées (éditions indiquées dans
`sources/index-sources.md`) :

- *Everyday Information Architecture* (EIA)
- *Designing Interfaces*, 3e éd. (DI)
- *Don't Make Me Think, Revisited*, 3e éd. (DMMT)

Les livres ne fournissent aucune règle métier : celles-ci viennent toujours du projet ou restent
des questions ouvertes.
