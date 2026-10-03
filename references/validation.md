# Validation — contrôles techniques, revue experte, tests avec utilisateurs

> Charger à l'étape F. Trois niveaux de preuve **qui ne se remplacent pas** :
> 1. **Contrôle technique** : automatisable, prouve la conformité (lint, types, tests, a11y, i18n).
> 2. **Revue experte** : un agent ou un designer applique les règles ; produit des *hypothèses de problèmes*.
> 3. **Test avec utilisateurs** : observe des personnes réelles faire des tâches ; seul niveau qui dit si l'expérience fonctionne.
> Ne jamais écrire « parfait », « intuitif » ou « validé » sur la seule base des niveaux 1–2.
> Écrire « revue experte — non testé avec des utilisateurs » quand c'est le cas.

---

## V-01 · Proportionner la validation au changement

| Ampleur | Exemples | Contrôles minimum |
|---|---|---|
| **S** — libellé, état, composant local | texte d'erreur, état vide, bouton | portes techniques du diff ; revue C-01/C-07/C-09 ; captures dans chaque langue livrée (au moins la plus longue), clair+sombre, 375 px |
| **M** — écran ou parcours d'un rôle | nouvelle page, refonte d'un formulaire | S + fiche écran complète ; test du coffre (V-03) ; parcours clavier ; Playwright du parcours si existant ; tâches de test préparées (V-05) |
| **L** — navigation, espace, plusieurs rôles | réorganisation d'un menu, parcours transversal | M + mise à jour de la cartographie ; matrice des conséquences par rôle ; test de libellés ou arborescence ; session de test utilisateurs **planifiée** avant de déclarer l'amélioration |

## V-02 · Portes techniques du dépôt (à adapter aux outils du projet)

| Porte | Commande | Quand |
|---|---|---|
| Formatage | formateur du projet en mode vérification | chaque push |
| Lint + types | linter et vérification de types du projet | diff de code front |
| Tests unitaires front | suite de tests du projet (couverture des routes si elle existe) | diff de code front |
| Parcours E2E | tests de bout en bout du projet — rejouer ceux du parcours touché | diff d'écran/parcours |
| Terminologie | garde terminologique du projet, si elle existe | chaque push |
| Contrat d'API | régénération du client/contrat d'API puis vérification qu'aucun diff ne subsiste | route modifiée |
| Contrastes | tests de contraste des tokens/couleurs, si présents | tokens/couleurs |
| Parité i18n | test de parité des clés de traduction, si présent | clés ajoutées |

Découvrir les commandes réelles dans le dépôt (scripts du gestionnaire de paquets, Makefile/justfile, documentation de contribution, instructions d'agents) ; respecter les consignes du projet sur la CI et l'exécution locale. Ne pas inventer de commande.

## V-03 · Test du coffre adapté au SaaS (revue experte)

Adapté de DMMT ch.6 p.82–83 (PDF 93–94). Ouvrir un écran **par son URL directe** (comme depuis une notification), le regarder brièvement (ou flouté, capture réduite) et répondre sans hésiter :

| # | Question | Élément attendu |
|---|---|---|
| 1 | Quelle application et **quel espace** (ex. back-office, espace client, console admin) ? | identité + marqueur d'espace |
| 2 | Quelle page ? | titre = libellé du lien d'entrée |
| 3 | Quelles rubriques principales existent ? | navigation globale visible (sauf parcours focalisé) |
| 4 | Que puis-je faire ici ? | action principale identifiable |
| 5 | Où suis-je dans l'ensemble ? | rubrique active doublement marquée ; retour/parent |
| 6 | Comment retrouver une information ailleurs ? | navigation + recherche **si** l'espace en a besoin (listes longues, back-office) — ne pas l'exiger mécaniquement |

Tout élément non trouvé = constat. Pour un **parcours focalisé** (paiement, assistant), les questions 3 et 6 sont remplacées par « comment en sortir sans perdre mon travail ? ».

## V-04 · Revue experte d'écran (liste courte)

- [ ] Type d'écran unique ou hiérarchie claire des finalités (A-07)
- [ ] Élément dominant = tâche principale (C-05) ; une action primaire par zone (I-03)
- [ ] Éléments liés regroupés ; titres collés à leur bloc (C-05)
- [ ] Cliquable reconnaissable ; rien d'essentiel au survol (C-06)
- [ ] Chaque texte aide à agir (C-09) ; libellés = mots du rôle (A-10)
- [ ] Informations décisives visibles (I-04) ; récapitulatif avant engagement (I-08)
- [ ] États chargement / vide / erreur / succès / hors-ligne / sans droit (I-10)
- [ ] Utilitaires discrets, non dupliqués sans raison (A-09)
- [ ] Domicile unique des informations, raccourcis reliés (A-06)
- [ ] Clavier, focus, contrastes, libellés, deux thèmes (C-11) ; 320 px + langue la plus longue (C-12)
- [ ] Permissions : l'écran n'affiche pas d'action que l'API refusera ; ressource d'une autre organisation = 404 (si la règle de sécurité du projet le prévoit)

## V-05 · Préparer un test avec utilisateurs (méthode Krug, adaptée)

Source : DMMT ch.9 p.110–141 (PDF 121–152), ch.10 p.160–163 (PDF 171–174).

1. **Rythme** : court et fréquent (ordre de grandeur de Krug : une demi-journée par mois, 3 participants par cycle). Mieux vaut plusieurs petits cycles qu'une grosse étude.
2. **Participants** : recruter large, mais avec le savoir métier nécessaire au rôle (un opérateur de back-office pour un écran de gestion ; un client pour l'espace client). **Publics protégés (mineurs, données sensibles)** : aucun test sans cadre de consentement validé par le responsable du produit et conforme au droit applicable — si inconnu, ne pas improviser. Données : comptes et données **synthétiques** uniquement, jamais de données de production.
3. **Tâches** : scénarios concrets avec déclencheur et objectif, jamais le nom du bouton (« Vous voulez décaler votre rendez-vous de jeudi à la semaine suivante » et non « cliquez sur Déplacer »). Environ 35 min de tâches pour une séance d'une heure. Fournir les données nécessaires (compte de démonstration).
4. **Séance** : accueil (« on teste le produit, pas vous »), questions de contexte, visite de l'écran d'accueil sans cliquer, tâches à voix haute, questions finales. Ne pas aider sauf blocage réel ; relancer par « à quoi pensez-vous ? ». Mobile : appareil tenu naturellement, écran + doigts visibles pour les observateurs.
5. **Débrief le jour même** : chaque observateur donne ses 3 problèmes les plus graves **observés** ; retenir les 10 pires, les classer ; une correction, un responsable par problème, dans la capacité réelle ; liste séparée des corrections rapides. Résister à « ajouter une explication » ; souvent il faut retirer. Ignorer les erreurs brèves que l'utilisateur corrige seul (« kayak ») — sauf parcours critique (argent) ou participant en situation de handicap.
6. **Trace** : compte rendu court ; chaque problème non corrigé dans le lot → entrée du registre des manquements du projet (ou, à défaut, du registre des questions ouvertes).

Format d'une tâche de test :

| Champ | Contenu |
|---|---|
| Rôle et compte | ex. client avec deux dossiers actifs (données synthétiques) |
| Déclencheur | la situation qui motive l'action |
| Consigne donnée | formulation sans vocabulaire d'interface |
| Succès observable | état final vérifiable (écran, donnée) |
| Signaux à noter | hésitations, retours arrière, mots cherchés absents |
| Hypothèse validée / invalidée | la décision UX que la tâche met à l'épreuve |

## V-06 · Méthodes d'architecture non décrites par les livres

Tri de cartes et test d'arborescence sont **cités** par EIA (outils, ch.4 p.73 / PDF 79 ; Resources p.121 / PDF 127) mais **pas décrits**. Si on les utilise, s'appuyer sur une autre source méthodologique, citée, et ne pas l'attribuer aux trois livres.

## V-07 · Trancher les désaccords par l'observation

Un débat « je préfère X » devient une tâche de test datée avec un critère observable. Les goûts de l'équipe et l'« utilisateur moyen » ne tranchent pas. Source : DMMT ch.8 p.103–109 (PDF 114–120).

## V-08 · Ce que la validation ne couvre pas encore

- Mesure quantitative (taux de réussite, analytics, A/B) : exclue par Krug ; si ajoutée, la documenter comme source externe.
- Satisfaction/attrait : pas mesurés par un test d'utilisabilité (DMMT ch.13 p.188 / PDF 199).
