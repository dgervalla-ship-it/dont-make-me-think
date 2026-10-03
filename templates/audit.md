# Audit / inventaire — <périmètre> — <JJ.MM.AAAA>

> Copier ce modèle dans le livrable de la tâche (spec, PR, dossier UX du projet), jamais dans le skill.
> Base : branche principale @ `<sha>`. Méthode : EIA ch.2 (inventaire) et ch.4 (audit de structure).

## 0. Cadrage
| Champ | Valeur |
|---|---|
| Changement demandé | |
| Ampleur (S / M / L — `references/validation.md` V-01) | |
| Rôles touchés (voir la partie « rôles et permissions » de la cartographie) | |
| Espaces/modules touchés | |
| Écrans de la cartographie concernés (IDs) | |
| Zones **non examinées** | |

## 1. Structure réellement accessible (audit de structure)
Enregistrer ce qui existe **tel que vécu**, pas tel que prévu. Une ligne par écran, panneau ou étape.

| ID | Route / déclencheur | Parent | Libellé du lien → titre de l'écran (écart ?) | Accès : menu / lien contextuel / URL seule / aucun | Rôles (garde front / garde API) | Type DI (Overview/Focus/Make/Do/mixte) | État (opérationnel/partiel/inaccessible/inutilisé/incertain) | Preuve |
|---|---|---|---|---|---|---|---|---|

Statut de chaque ligne : **implémenté** (code), **capture** (observé à l'écran, préciser comment), **proposé** (spec/maquette non implémentée).

## 2. Inventaire des informations et actions
| Élément (info/action) | Tâche et rôle | Fréquence (observée — source / supposée) | Urgence et conséquence d'un oubli | Contexte d'utilité (moment, appareil) | Portée (soi / contexte / équipe / organisation / plateforme) | Relations | Domicile actuel | Raccourcis actuels | Règle métier liée (établie — source / inconnue) |
|---|---|---|---|---|---|---|---|---|---|

## 3. Tâches
| Tâche | Rôle | Déclencheur | Contexte | Résultat attendu | Mode de recherche (connu / exploration / re-recherche / ne sait pas) | Écrans (IDs) |
|---|---|---|---|---|---|---|

## 4. États
| Écran | Chargement | Vide | Erreur | Succès | Hors-ligne | Sans droit / autre organisation |
|---|---|---|---|---|---|---|

## 5. Utilitaires et réglages
| Commande (session, thème, langue, installation, aide…) | Écrans où elle apparaît | Poids visuel | Raison d'une duplication (source) |
|---|---|---|---|

## 6. Constats (revue experte — non testés avec des utilisateurs)
| # | Type | Constat | Preuve | Rôle/tâche | Gravité | Règle mobilisée (ID) |
|---|---|---|---|---|---|---|

## 7. Inconnues qui changent la décision
| Inconnue | Décision bloquée | Hypothèse de travail | Qui tranche (responsable produit, registre des questions ouvertes, test) |
|---|---|---|---|
