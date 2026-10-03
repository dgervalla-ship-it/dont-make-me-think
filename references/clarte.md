# Clarté et utilisabilité — règles de décision

> Charger à l'étape E (fiche écran) et pour toute revue UX/UI. Source principale : Krug
> (DMMT, 3e éd. 2014, web de contenu — transposer avec prudence à un SaaS authentifié).
> Sigles et statuts : voir `architecture.md`.

---

### C-01 · Évident d'abord, sinon auto-explicatif
- **Problème** : chaque micro-question (« c'est quoi ? », « c'est cliquable ? », « c'est pareil que l'autre ? ») coûte attention et confiance.
- **Règle** : pour chaque écran, lister les questions qu'un nouvel utilisateur se poserait et supprimer leur cause ; si impossible (fonction métier intrinsèquement complexe), une explication courte au point de besoin.
- **Limites** : un vocabulaire métier partagé par les professionnels (utilisateurs avancés, back-office) peut être évident pour eux et obscur pour un client : juger par rôle.
- **Vérifier** : en test, aucune pause ni doute verbalisé sur le sens d'un libellé ; revue « questions du novice » vide.
- **Source** : DMMT ch.1 p.11–19 (PDF 22–30). **Statut** : source ; jugement par rôle = déduction.

### C-02 · Les gens balaient et prennent la première option plausible
- **Règle** : chaque écran se comprend comme un panneau en quelques secondes ; l'option la plus plausible doit être la bonne. Ne pas compter sur la lecture d'un paragraphe ni sur la comparaison de toutes les options.
- **Limites** : Krug fonde le « premier choix plausible » sur une pénalité d'erreur faible ; pour une action irréversible (argent, annulation tardive, envoi), ajouter un récapitulatif (I-08). Contenus longs (textes légaux, aide) : la lecture reprend.
- **Vérifier** : test des 5 secondes (déduction) ; mesure du premier clic en test.
- **Source** : DMMT ch.2 p.21–27 (PDF 32–38) ; DI ch.1 p.14–15 (PDF 34–35). **Statut** : source ; limite irréversible = déduction.

### C-03 · Ne pas compter sur les instructions
- **Règle** : le bon chemin est le plus facile à deviner ; l'aide est intégrée à l'écran (libellé, exemple, indication sous le champ) avant toute page d'aide ou visite guidée ; une visite guidée est désactivable et rouvrable.
- **Vérifier** : en test, repérer les réussites « par détour » (écart de modèle mental) ; tâche principale réussie sans ouvrir l'aide.
- **Source** : DMMT ch.2 p.25–27 (PDF 36–38), ch.5 p.49–52 (PDF 60–63) ; DI ch.2 p.110–119 (PDF 130–139). **Statut** : source.

### C-04 · Conventions d'abord ; la clarté l'emporte sur la cohérence
- **Règle** : par défaut, composant et emplacement conventionnels (dans le projet : les composants du design system existant, les conventions du shell existant) ; innover seulement si la nouveauté est au moins aussi claire ou apporte assez pour justifier un apprentissage — preuve par test. Si une légère incohérence rend nettement plus clair, choisir la clarté et l'écrire.
- **Limites** : les conventions citées par Krug/DI (logo en haut à gauche, utilitaires en haut à droite) datent du web 2014–2020 ; vérifier les conventions mobiles actuelles.
- **Vérifier** : chaque écart aux conventions du projet a une justification et un test.
- **Source** : DMMT ch.3 p.29–33 (PDF 40–44). **Statut** : source ; conventions projet = choix projet.

### C-05 · Hiérarchie visuelle : importance = proéminence ; appartenance = regroupement
- **Règle** : un élément dominant par écran ; ce qui est lié est proche et traité pareil ; l'imbrication montre ce qui appartient à quoi ; un titre est plus proche du bloc qu'il introduit que du bloc précédent ; écran découpé en zones reconnaissables (ce que je peux faire / où je suis / navigation).
- **Vérifier** : test du plissement d'yeux ou en niveaux de gris : l'élément dominant voulu ressort en premier ; aucun titre « flottant ».
- **Source** : DMMT ch.3 p.33–41 (PDF 44–52) ; DI ch.4 p.209–223 (PDF 229–243). **Statut** : source.

### C-06 · Le cliquable doit se voir
- **Règle** : un seul traitement visuel pour les éléments d'action, jamais réutilisé pour un élément inerte ; pas d'information ni d'action révélée seulement au survol (tactile) ; une icône d'action porte un libellé (règle courante : icône métier + libellé).
- **Vérifier** : revue : un tiers désigne les éléments interactifs sans toucher ; aucun texte stylé comme un lien sans en être un.
- **Source** : DMMT ch.3 p.37–38 (PDF 48–49), ch.10 p.151–153 (PDF 162–164) ; DI ch.8 p.377–382 (PDF 397–402). **Statut** : source.

### C-07 · Tout élément est du bruit jusqu'à preuve du contraire
- **Règle** : chaque élément visible justifie sa présence par une tâche de l'écran ; retirer ce qui ne sert pas ; les commandes rares (préférences d'affichage, déconnexion) ne concurrencent pas le contenu.
- **Exemple (générique)** : thème + langue + déconnexion dans l'en-tête de chaque page d'un espace client = trois éléments utilitaires au même poids que le titre.
- **Vérifier** : chaque élément supprimé ne dégrade aucun test de tâche ; inventaire des éléments par écran avec leur tâche.
- **Source** : DMMT ch.3 p.38–41 (PDF 49–52). **Statut** : source.

### C-08 · Des choix sans effort valent mieux qu'un compte de clics
- **Règle** : un choix ambigu (« je suis quel type ? », deux rubriques qui se ressemblent) coûte plus que plusieurs choix évidents. Pas de règle des « trois clics ». Réduire le nombre de gestes quand le chemin est **répété souvent** ou lent (voir `arbitrages.md` T2). Quand un choix difficile est inévitable, un guidage bref, au moment et à l'endroit du choix.
- **Vérifier** : en test, pas d'hésitation marquée aux embranchements ; pour les tâches quotidiennes, nombre de gestes mesuré et comparé à un plafond fixé par l'équipe.
- **Source** : DMMT ch.4 p.43–47 (PDF 54–58). **Statut** : source.

### C-09 · Supprimer les mots inutiles
- **Règle** : retirer le texte promotionnel et les consignes préalables ; déplacer chaque consigne là où l'on agit ; remplacer une phrase qui renvoie ailleurs par un lien actionnable. Viser la moitié, puis encore la moitié (ordre de grandeur volontairement provocateur de Krug).
- **Limites** : textes légaux et contenus pédagogiques ne se raccourcissent pas arbitrairement ; ton et registre de langue selon la règle éditoriale du projet.
- **Vérifier** : comptage de mots avant/après sans perte en test ; aucun paragraphe d'introduction sans information utilisable.
- **Source** : DMMT ch.5 p.49–52 (PDF 60–63). **Statut** : source.

### C-10 · Réservoir de bonne volonté
- **Règle** : faciliter les trois tâches principales de chaque rôle ; montrer sans détour tarifs, délais, frais, conditions d'annulation **tels que définis par le produit ou l'organisation** et un contact ; ne pas punir un format de saisie ; ne pas demander d'information inutile ; offrir une sortie élégante après chaque erreur possible ; s'excuser quand on ne peut pas faire mieux.
- **Limites** : les conditions (délais, frais) viennent des réglages du produit ou de règles métier établies — jamais inventées.
- **Vérifier** : en test, noter les soupirs/agacements et les rattacher à une cause ; revue : informations d'argent et de délai visibles avant engagement.
- **Source** : DMMT ch.11 p.165–171 (PDF 176–182). **Statut** : source.

### C-11 · Accessibilité : clarté pour tous, puis actions à fort effet
- **Règle** : corriger d'abord ce qui déroute tout le monde ; puis titres hiérarchisés, libellés associés aux champs, accès clavier complet avec focus visible, contraste suffisant dans les deux thèmes, alternatives textuelles, pas de couleur seule pour porter un sens, lien d'évitement.
- **Limites** : les livres ne donnent pas de ratios chiffrés ni WCAG 2.x ; seuils = règles du projet (ex. contraste AA, cibles tactiles ≥ 44 px, taille de texte minimale) et tests existants de contraste.
- **Vérifier** : parcours complet au clavier ; lecteur d'écran sur les parcours principaux ; tests de contraste verts.
- **Source** : DMMT ch.12 p.173–181 (PDF 184–192) ; DI ch.1 p.24–25 (PDF 44–45), ch.5 p.258–264 (PDF 278–284). **Statut** : source ; seuils = choix projet.

### C-12 · Langues : prévoir les libellés longs et l'ordre des mots
- **Règle** : libellés courts qui tiennent dans la langue la plus longue du produit (l'allemand, par exemple, allonge souvent les libellés) ; pas de phrases à trous dont l'ordre dépend de la langue ; pas de boutons côte à côte si la largeur n'est pas garantie ; formats locaux via `Intl` ou l'équivalent de la plateforme.
- **Vérifier** : captures dans la langue la plus longue à 320 px ; aucune chaîne en dur (règle i18n du projet).
- **Source** : DI ch.6 p.306–309 (PDF 326–329), ch.10 p.486 (PDF 506). **Statut** : source partielle ; application aux langues livrées = choix projet.
