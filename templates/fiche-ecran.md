# Fiche écran — <ID> — <nom>

> Ordre imposé par DI ch.2 (I-01) : objets → fonctions → présentation.

## Identité
| Champ | Valeur |
|---|---|
| ID cartographie / route | |
| Espace / module | |
| Rôles (garde front + garde API) et portée des données | |
| Type DI (Overview / Focus / Make / Do) | |
| Finalité (une phrase, tâche principale) | |
| Entrées (menu, liens contextuels, notifications, URL directe) → destinations | |

## 1. Objets et informations
| Information | Priorité (1 immédiate / 2 secondaire / 3 à la demande) | Domicile ici ou raccourci vers <ID> | Source de données (endpoint / requête) | Ordre (méthode + sens) |
|---|---|---|---|---|

## 2. Actions
| Action | Importance (primaire / secondaire / tertiaire) | Réversible ? | Récapitulatif ou confirmation (et pourquoi) | Permission (rôle, API) | Règle métier (source ou inconnue) |
|---|---|---|---|---|---|

## 3. Regroupements et hiérarchie
Zones de l'écran, élément dominant, sections titrées, ce qui est replié et pourquoi (I-04).

## 4. États
| État | Contenu et action proposée |
|---|---|
| Chargement | skeleton de … |
| Vide | pourquoi c'est vide + action pertinente selon règles réelles |
| Erreur | message humain + reprise + sortie |
| Succès | confirmation + suite |
| Hors-ligne | si pertinent |
| Sans droit / autre organisation | refus ou 404 selon la règle de sécurité du projet |

## 5. Mobile / grand écran
| Aspect | Mobile (≥ 320 px) | Grand écran |
|---|---|---|
| Disposition | | |
| Liste ↔ détail | | |
| Navigation | | |

## 6. Accessibilité et langues
Ordre du focus, libellés, contrastes clair/sombre, cibles tactiles suffisantes (≥ 44 px si le projet l'impose), textes de la langue la plus longue, formats locaux.

## 7. Composants réutilisés
Recherche effectuée (composants du design system du projet → bibliothèque de composants → primitives) et composants retenus.

## 8. Vérification
Contrôles techniques, test du coffre (V-03), tâche de test utilisateur (V-05).
