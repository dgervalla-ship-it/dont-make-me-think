# Données, listes longues, tableaux de bord — règles de décision

> Charger pour les écrans de gestion denses (clients, agenda, finance, statistiques, administration).
> Source : DI ch.9 lu en entier (p.433–469 / PDF 453–489) + ch.2, 7. **Limite majeure** : le
> livre ne traite pas les tableaux de gestion denses (colonnes figées, densité, sélection
> multiple, actions groupées, édition en ligne, tableau responsive, export, agenda). Toute règle
> sur ces sujets est une **déduction** ou doit citer une autre source.

---

### D-01 · Nommer la forme des données avant le composant
- **Règle** : écrire le modèle (tabulaire, temporel, hiérarchique, réseau, géographique, texte) et la question principale (retrouver, comparer, surveiller, repérer une exception) ; si deux formes conviennent, dire pourquoi l'une est écartée.
- **Exemple (générique)** : agenda = temporel ; clients = tabulaire ; finance = tabulaire + série temporelle.
- **Vérifier** : la fiche écran contient « forme + question + forme écartée ».
- **Source** : DI ch.9 p.434–435 (PDF 454–455). **Statut** : source.

### D-02 · Faire ressortir l'exception sans faire lire
- **Règle** : les éléments qui demandent une action (impayé, document expiré, tâche non traitée) se distinguent par une variable perçue d'un coup d'œil (couleur **sémantique** via token, position, poids) **doublée** d'un signe non chromatique (icône + libellé). Une seule emphase par signal ; pas d'emphase uniforme.
- **Vérifier** : dans une liste de 30 lignes, un testeur désigne toutes les lignes en alerte sans les lire (seuil de déduction) ; rendu en niveaux de gris lisible.
- **Source** : DI ch.9 p.435–439 (PDF 455–459), fig. 9-1 à 9-5 examinées. **Statut** : source ; application = déduction.

### D-03 · Trier, filtrer, retrouver — avec un défaut pensé
- **Règle** : colonnes comparables triables, tri par défaut documenté et indiqué ; filtres à contrôles simples placés près des données, résultat immédiat, valeur « Tous » explicite, combinables ; recherche qui **recentre** sur l'élément trouvé quand le contexte compte ; état « aucun résultat » avec action (réinitialiser les filtres).
- **Projet** : filtres et tri partageables dans l'URL (bonne pratique web « URL comme état » — non issue du livre).
- **Vérifier** : chaque liste documente tri par défaut, colonnes triables, filtres ; retour depuis un détail → filtres et position conservés.
- **Source** : DI ch.9 p.439–445, 455–458 (PDF 459–465, 475–478) ; ch.2 p.32 (PDF 52). **Statut** : source ; URL = choix projet.

### D-04 · Valeur exacte accessible sans survol
- **Règle** : étiquettes directes pour les valeurs clés, info-bulles pour le reste, légende sur le même écran ; toute valeur nécessaire à une décision lisible au toucher et au clavier.
- **Vérifier** : parcourir un graphique au clavier et sur tactile : chaque valeur décisive est atteignable.
- **Source** : DI ch.9 p.445–451 (PDF 465–471) ; ch.8 p.387 (PDF 407). **Statut** : source ; exigence clavier = déduction (règles d'accessibilité du projet).

### D-05 · Tableau de bord : l'état et les prochaines actions, sur une page
- **Règle** : partir des questions que le rôle doit résoudre ; retirer ou atténuer le reste ; « à traiter » en tête ; sections titrées ; courbes et barres simples plutôt que jauges, camemberts, 3D ; listes/tableaux quand le chiffre exact compte ; chaque bloc mène à son détail.
- **Projet** : réutiliser les primitives de graphiques et d'indicateurs du design system, si elles existent, avant d'en créer.
- **Vérifier** : un utilisateur du rôle répond à 3 questions types sans défiler ni ouvrir un détail (seuil de déduction, à tester).
- **Source** : DI ch.2 p.78–81 (PDF 98–101), ch.4 p.238–239 (PDF 258–259). **Statut** : source.

### D-06 · Détail d'une ligne : à côté, à la place ou en place
- **Règle** : grand écran et consultation en série → liste + détail côte à côte (flèches pour passer au suivant) ; petit écran → détail en plein écran, retour restituant filtres, tri et défilement ; comparaison de quelques lignes → déploiement en place.
- **Source** : DI ch.7 p.338–352 (PDF 358–372). **Statut** : source ; restitution = déduction.

### D-07 · Listes longues
- **Règle** : première page utile d'emblée ; pagination lisible (page courante marquée, bornes désactivées, total si connu) ou chargement progressif annoncé ; accès direct (recherche, saut par initiale) ; actions de ligne visibles au focus et au toucher, jamais uniquement au survol ; création en ligne seulement si les validations métier restent respectées.
- **Source** : DI ch.7 p.339–340, 365–373 (PDF 359–360, 385–393), ch.6 p.322–323 (PDF 342–343), ch.8 p.387–388 (PDF 407–408). **Statut** : source ; réserve métier = choix projet.

### D-08 · Comparer sur une même échelle
- **Règle** : séries comparées alignées sur un axe commun ; petites vues répétées identiques (échelle, taille) ; mini-courbes dans une colonne possibles ; éviter les petites vues multiples sur mobile.
- **Source** : DI ch.9 p.462–468 (PDF 482–488). **Statut** : source.

### Hors livre — à sourcer si utilisé
Colonnes figées, redimensionnement, masquage de colonnes, densité, sélection multiple et actions groupées, édition en ligne, virtualisation, tableaux responsives, alignement des nombres, export, vues calendrier. Citer la source externe retenue dans la décision UX.
