# Interactions, écrans et parcours — règles de décision

> Charger aux étapes D (structure/parcours) et E (fiche écran). Sigles et statuts : voir
> `architecture.md`. Chaque pattern suit la logique des fiches de *Designing Interfaces* :
> **Quoi** (ce que fait le modèle) · **Quand** (conditions) · **Pourquoi** · **Comment**.
> Les exemples sont des illustrations génériques.

---

### I-01 · Trois couches : concepts → fonctions → présentation
- **Problème** : on dessine un écran (couleurs, cartes) avant de savoir quels objets, relations et actions il porte ; la présentation fige une mauvaise structure.
- **Règle** : décider dans l'ordre (1) objets, informations et relations, (2) fonctions et interactions, (3) présentation visuelle. Une proposition qui commence par un composant est renvoyée à la couche 1.
- **Limites** : un prototype visuel peut servir de support de test, pas de point de départ de la structure.
- **Vérifier** : chaque fiche écran remplit les sections objets → actions → présentation dans cet ordre.
- **Source** : DI ch.2 p.29–30 (PDF 49–50). **Statut** : source.

### I-02 · Écran d'accueil : répondre avant de demander, sans devenir un tableau de bord indigeste
- **Quoi** : trois modèles possibles — *accès direct* (le premier écran donne l'information utile sans saisie), *points d'entrée clairs* (peu de portes hiérarchisées vers les tâches), *tableau de bord* (état + tâches à suivre, dense).
- **Quand** : accès direct si une question domine et se devine (le client : « quand est mon prochain rendez-vous ? ») ; points d'entrée si l'utilisateur est novice ou si les usages sont variés ; tableau de bord si l'utilisateur surveille un flux en continu (back-office, direction).
- **Pourquoi** : réussir quelque chose dès les premières secondes crée la confiance ; un tableau de bord dense pour un usage occasionnel noie l'essentiel.
- **Comment** : un élément dominant ; chaque indicateur mène à son détail et sert une décision ; « à faire maintenant » avant « pour information » ; hypothèses visibles et modifiables.
- **Exemple (générique)** : tableau de bord par rôle (intervenant : sa journée ; comptable : encaissements) plutôt qu'un même écran filtré.
- **Vérifier** : chaque bloc de l'accueil a une décision ou action associée ; test « que feriez-vous en premier ? » : la réponse correspond à l'intention.
- **Source** : DI ch.2 p.51–52, 78–81 (PDF 71–72, 98–101), ch.3 p.143–147 (PDF 163–167), ch.1 p.13 (PDF 33) ; DMMT ch.7 p.85–100 (PDF 96–111). **Statut** : source ; choix par rôle = déduction.

### I-03 · Une action principale par zone, nommée par son résultat
- **Problème** : plusieurs boutons de même poids se disputent l'attention ; « OK » ne dit pas ce qui va se passer.
- **Règle** : par zone, une action primaire (forme de bouton, contraste, placée à la fin du flux de lecture, près du dernier champ), les autres atténuées et groupées par portée ; libellé = verbe + objet (« Réserver ce créneau », « Émettre la facture »). Les actions d'un objet sont à côté de l'objet.
- **Projet** : si le design system prévoit une couleur d'appel réservée à la conversion, une seule par écran ; la hiérarchie des autres actions passe par les variantes de boutons existantes du projet.
- **Vérifier** : test des 5 secondes « où cliquer pour terminer ? » ; au plus une primaire par zone ; aucun libellé « OK/Valider » seul sur une action engageante.
- **Source** : DI ch.8 p.384–386, 396–404 (PDF 404–406, 416–424) ; EIA ch.5 p.86–87 (PDF 92–93). **Statut** : source ; couleur d'appel = choix projet (le cas échéant).

### I-04 · Montrer l'essentiel, révéler le reste — sauf ce qui conditionne la décision
- **Quoi** : sections titrées (tout visible, balayable) → si encore trop, accordéons / panneaux repliables / onglets → activation progressive dans les formulaires longs.
- **Quand** : options secondaires, détails rarement consultés. **Pas** pour le prix, le délai d'annulation, un statut bloquant, une conséquence irréversible : ils restent visibles.
- **Comment** : panneau ouvert par défaut si la majorité l'ouvre (mesure requise) ; onglets seulement si l'on ne compare pas le contenu d'un onglet à l'autre.
- **Vérifier** : liste des informations décisives de l'écran — aucune n'est derrière un clic ; en test, personne ne cherche une information cachée.
- **Source** : DI ch.4 p.224–225, 238–250 (PDF 244–245, 258–270), ch.10 p.473 (PDF 493), ch.2 p.78–81 (PDF 98–101). **Statut** : source ; exception « décision » = déduction.

### I-05 · Choisir la présentation d'une liste après avoir analysé son usage
- **Règle** : avant le composant, répondre : aperçu, parcours élément par élément, recherche d'un élément, tri/filtre, réorganisation ? longueur (peut-elle être sans fin) ? ordre naturel ? regroupement ? éléments simples ou riches ? voir ou sélectionner (multi-sélection) ? mise à jour en direct ?
- **Puis** : petit écran → la liste cède la place au détail (retour évident, contexte suffisant dans la ligne) ; grand écran → liste + détail côte à côte ; comparaison fréquente → détail ouvert dans la liste. Cartes seulement si les éléments ont les mêmes actions et un contenu hétérogène ; table/liste quand on compare des champs. Liste longue → recherche ou filtre, pagination ou chargement progressif avec nombre annoncé.
- **Exemple (générique)** : liste de clients en back-office = table triable + recherche (on retrouve un nom connu) ; RDV du client = liste chronologique courte.
- **Vérifier** : fiche d'usage remplie par liste ; retour du détail → position et filtres conservés.
- **Source** : DI ch.7 p.335–374 (PDF 355–394), ch.6 p.322–323 (PDF 342–343). **Statut** : source ; conservation des filtres = déduction.

### I-06 · Assistant (Wizard) : pour le nouveau et le ramifié, pas pour le répétitif
- **Quoi** : parcours pas à pas imposé. **Quand** : tâche longue, rare, nouvelle pour l'utilisateur, avec embranchements, où le concepteur sait mieux que lui l'ordre utile (onboarding de compte, première inscription). **Pas** pour les experts ou les gestes répétés quotidiens (saisie d'une commande par un opérateur) : préférer un formulaire court.
- **Pourquoi** : réduit la charge du novice ; masque le contexte et agace l'expert ; paraît condescendant si la tâche pouvait tenir en quelques champs.
- **Comment** : étapes découpées aux points de décision ; indicateur « étape n / N » avec titres courts ; retour libre sans perte de saisie ; défauts intelligents ; sortie nommée.
- **Vérifier** : raison écrite pour avoir écarté un formulaire unique ; retour arrière conserve les saisies ; nombre d'étapes justifié.
- **Source** : DI ch.2 p.86–89 (PDF 106–109), ch.3 p.139, 189–193 (PDF 159, 209–213). **Statut** : source.

### I-07 · Éditeur de réglages (Settings Editor) : accès libre, valeurs visibles
- **Quoi** : réglages consultés et modifiés indépendamment les uns des autres. **Quand** : profil, préférences, paramètres de l'organisation. **Pas** en assistant : l'utilisateur saute d'un point à l'autre.
- **Comment** : catégories nommées par ce qu'elles règlent (tri de cartes si doute) ; valeurs courantes lisibles sans ouvrir ; emplacement d'accès stable ; convention unique d'enregistrement (immédiat ou Enregistrer/Annuler) dans tout le produit ; les réglages fréquents d'abord ; un réglage qui agit sur un autre espace (espace client, widget public) le dit et montre un aperçu ou un lien vers l'effet.
- **Vérifier** : chaque réglage trouvé en ≤ 2 niveaux depuis l'entrée Réglages ; aucun réglage à deux endroits éditables (A-06) ; convention d'enregistrement identique partout.
- **Source** : DI ch.2 p.90–96 (PDF 110–116). **Statut** : source ; « effet sur un autre espace » = déduction.

### I-08 · Exploration sûre : prévoir le retour avant l'engagement
- **Problème** : la peur d'une conséquence empêche d'essayer ; une confirmation systématique devient un clic réflexe.
- **Règle** : actions réversibles → exécution immédiate + annulation possible ; actions coûteuses ou irréversibles (argent, envoi à un tiers, annulation hors délai, suppression) → **récapitulatif** avant validation, avec « Modifier » à côté de chaque donnée et libellé nommant l'objet (« Annuler le rendez-vous du 12.10 à 14:00 »). Confirmation modale : rare, réservée à l'irréversible, jamais sur une action quotidienne.
- **Exemple** : confirmation explicite pour tout ce qui touche l'argent (« Facturer 90.– ? ») si le projet l'exige ; la rendre spécifique pour qu'elle ne devienne pas réflexe.
- **Vérifier** : pour chaque action, « comment revient-on ? » a une réponse ; aucune confirmation sur une action faite plusieurs fois par jour.
- **Source** : DI ch.1 p.12–13, 18–19 (PDF 32–33, 38–39), ch.8 p.402–421 (PDF 422–441), ch.3 p.158–165 (PDF 178–185). **Statut** : source ; règle argent = choix projet.

### I-09 · Formulaires : demander le minimum, au bon moment, en acceptant les formats
- **Règle** : chaque champ justifié (déduire plutôt que demander) ; différer ce qui n'est pas nécessaire à l'acte en cours, avec un endroit évident pour compléter plus tard ; libellé visible hors du champ (le texte d'exemple n'est jamais le libellé) ; obligatoire/facultatif marqués selon une convention unique ; formats tolérants pour dates, téléphones, montants (normaliser et réafficher) ; défauts pour ce qui est quasi certain, jamais pour un consentement ou une donnée sensible ; erreurs en ligne, à côté du champ, compréhensibles, pas seulement en rouge, validées à la sortie du champ ; succès = message + étape suivante.
- **Projet** : formats locaux via `Intl` ou l'équivalent de la plateforme ; phrases à trous à éviter (l'ordre des mots varie selon la langue).
- **Vérifier** : audit champ par champ (nécessaire ? déductible ?) ; six variantes de saisie d'une date/téléphone acceptées ; lecteur d'écran annonce libellé et erreur.
- **Source** : DI ch.1 p.16–17 (PDF 36–37), ch.10 p.471–531 (PDF 491–551) ; DMMT ch.11 p.168–169 (PDF 179–180). **Statut** : source.

### I-10 · États d'écran : chargement, vide, erreur, succès, hors-ligne, sans droit
- **Règle** : chaque écran spécifie ses états. *Chargement* : retour visible dès le geste, contenu partiel d'abord (selon le design system du projet : skeleton plutôt que spinner plein écran). *Vide* : dire pourquoi c'est vide et proposer l'action suivante qui a du sens **selon les règles réelles** (pas un bouton inopérant). *Erreur* : message humain, cause compréhensible, action de reprise, sortie vers un lieu connu. *Succès* : confirmer ce qui a été fait et la suite. *Sans droit* : distinguer « pas autorisé » de « n'existe pas » selon la règle de sécurité (ressource d'une autre organisation ou d'un autre compte → 404, si la règle de sécurité du projet le prévoit).
- **Limites** : les livres couvrent chargement, erreurs de formulaire et impasses ; les états vides et hors-ligne sont des déductions + règles projet.
- **Vérifier** : grille des états par écran dans la fiche (aucune case vide) ; test manuel de chaque état.
- **Source** : DI ch.8 p.409–414 (PDF 429–434), ch.6 p.328–330 (PDF 348–350), ch.3 p.171–173 (PDF 191–193) ; EIA ch.5 p.86–87 (PDF 92–93). **Statut** : source partielle ; vide/hors-ligne = déduction + règles UI et sécurité du projet.

### I-11 · Mobile : une colonne, grandes cibles, rien de caché derrière le survol
- **Règle** : lecture en colonne unique, le plus important en haut ; cibles ≥ 44 px espacées ; aucune information ni action essentielle accessible seulement au survol ou par geste caché (les gestes accélèrent, ne remplacent pas) ; au moins deux indices d'interactivité (forme + position/format) ; boutons côte à côte seulement si la largeur tient dans la langue la plus longue du produit et en police agrandie ; tâches courtes et reprenables (usage par intervalles, interruption).
- **Limites** : la barre de navigation en bas est décrite par DI pour le web mobile (place en haut rare), pas comme une loi ; une barre d'onglets pour 4–5 destinations est une convention de plateforme à vérifier, pas une règle des livres.
- **Vérifier** : 320 px + police 200 % + libellés dans la langue la plus longue du produit : aucun débordement ; audit des interactions dépendant du survol = vide.
- **Source** : DI ch.6 p.296–330 (PDF 316–350) ; DMMT ch.10 p.147–154 (PDF 158–165). **Statut** : source.

### I-12 · Réentrance : une tâche interrompue se reprend là où elle était
- **Règle** : conserver les saisies partielles et l'étape ; laisser une trace visible « à reprendre » ; ne jamais faire disparaître en silence ce que l'utilisateur a laissé en attente ; restaurer la dernière position au retour.
- **Exemple (générique)** : dossier client incomplet, réservation provisoire en attente de paiement (durée à définir par le produit), import CSV interrompu.
- **Vérifier** : fermer l'onglet au milieu d'un parcours puis revenir → reprise claire ; un élément en attente qui expire prévient avant.
- **Source** : DI ch.1 p.15, 19–22 (PDF 35, 39–42). **Statut** : source.

### I-13 · Stabilité spatiale et gestes cohérents
- **Règle** : navigation au même endroit, dans le même ordre, sur tous les écrans d'un espace ; même geste = même effet partout ; ne pas réordonner « intelligemment » menus et barres ; ajouter un élément dans un espace libre plutôt que déplacer l'existant.
- **Vérifier** : comparaison de captures de deux écrans d'un même espace ; changelog des déplacements d'éléments de navigation (à justifier).
- **Source** : DI ch.1 p.18–21 (PDF 38–41). **Statut** : source.

### I-14 · Répétition fluide — seulement si la répétition est observée
- **Règle** : si une opération se répète (même rendez-vous chaque semaine, même relance), offrir « refaire / dupliquer » en un geste ; ne pas construire ce raccourci sur une répétition supposée.
- **Vérifier** : observation ou données montrant la répétition ; gestes de la deuxième occurrence < première.
- **Source** : DI ch.1 p.23–24 (PDF 43–44). **Statut** : source.

### I-15 · Données denses (tableaux de bord, statistiques, finance)
Voir `donnees.md` (D-01 à D-08).
