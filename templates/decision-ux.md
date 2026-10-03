# Décision UX — UXD-<n> — <titre court>

> Une décision par fiche. Chaîne obligatoire : **constat → tâche → principe sourcé →
> proposition → conséquences → validation**. Chaque affirmation porte son statut :
> [F] fait vérifié (preuve) · [S] principe des livres (réf.) · [D] déduction (raison) ·
> [C] choix existant du projet (décision d'architecture / règle) · [H] hypothèse à valider.

| Champ | Contenu |
|---|---|
| Date / auteur | |
| Écrans / rôles (IDs cartographie) | |
| Ampleur (S/M/L) | |

## 1. Constat [F]
Ce qui se passe aujourd'hui, avec preuve (fichier:ligne, route, capture, doc).

## 2. Tâche et utilisateur
Rôle, tâche, déclencheur, contexte, fréquence (**observée** avec source, sinon **[H] supposée**).

## 3. Principes mobilisés [S]
| ID règle | Ce qu'elle dit ici | Réf. livre (chap., p. imprimée / PDF) |
|---|---|---|
Tension éventuelle : T-n de `references/arbitrages.md` et contexte qui fait pencher.

## 4. Options (seulement si un arbitrage réel existe)
| Option | Avantages | Inconvénients | Conditions où elle serait meilleure |
|---|---|---|---|

## 5. Proposition
Décision concrète : quoi, où (domicile + raccourcis), libellé, action principale, états. Réutilisation : composants existants cherchés (où ?) et retenus.

## 6. Conséquences
| Autre espace / rôle / module | Effet | Action requise |
|---|---|---|
Règles métier, permissions, contrats d'API, i18n (langues livrées), décisions d'architecture à réviser : lister ou « aucune ».

## 7. Limites de la proposition
Ce qu'elle ne règle pas ; hypothèses [H] dont elle dépend.

## 8. Validation
| Niveau | Contrôle | Critère de réussite |
|---|---|---|
| Technique | | |
| Revue experte | | |
| Utilisateurs | tâche de test (V-05) | |

## 9. Ce qui ferait changer d'avis
Donnée ou résultat de test qui invaliderait la décision.

## 10. Mise à jour de la cartographie
Parties de la cartographie du projet à modifier (voir `references/cartographie-maj.md`).
