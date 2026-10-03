# Architecture de l'information — règles de décision

> Charger aux étapes C (classer) et D (structurer). Principes reformulés ; aucune règle
> métier ne vient de ces livres. Sigles : **EIA** = *Everyday Information Architecture*,
> **DI** = *Designing Interfaces* 3e éd., **DMMT** = *Don't Make Me Think, Revisited*.
> Pages : « p. imprimée (PDF n) ». Statut : **source** (soutenu explicitement), **déduction**
> (raisonnement de synthèse, justifié), **choix projet** (décision du projet, sourcée dans le dépôt).
> Les exemples sont des **illustrations génériques** (ex. un SaaS de réservation et de facturation), jamais des faits d'usage.

---

### A-01 · Structurer autour de ce que l'utilisateur fait, pas autour de l'organisation
- **Problème** : des rubriques calquées sur les tables, les équipes ou les modules internes obligent l'utilisateur à connaître le fonctionnement interne de l'organisation.
- **Règle** : chaque rubrique de premier niveau répond à « je veux… » ; aucune ne porte le nom d'une table, d'un service ou d'un module technique sans justification par une tâche.
- **S'applique si** : on crée ou révise une navigation. **Limites** : le découpage par audience (client / partenaire) est rarement bon sur un site public, mais dans un espace authentifié le rôle est connu après connexion : l'argument d'auto-sélection tombe, celui des tâches reste.
- **Pour décider** : liste des tâches (étape B), vocabulaire des utilisateurs.
- **Exemple (générique)** : « Factures » et « Règlements » sont deux objets comptables ; pour le client la tâche peut être « savoir ce que je dois » — à vérifier par test avant de fusionner quoi que ce soit.
- **Vérifier** : tableau rubrique ↔ tâche ; aucune rubrique sans tâche ; comparaison avec le schéma de données : pas de correspondance un-à-un non justifiée.
- **Source** : EIA ch.3 p.39–47 (PDF 45–53) ; DI ch.2 p.28–30 (PDF 48–50). **Statut** : source ; nuance « espace authentifié » = déduction (EIA traite des sites publics).

### A-02 · Chaque rubrique a un critère d'entrée et de sortie ; pas de tiroir à bazar
- **Problème** : une rubrique définie comme « le reste » (Divers, Autres, Liens rapides, « tout ce qui ne tient pas ailleurs ») devient un endroit que les gens évitent et où rien ne se retrouve.
- **Règle** : écrire pour chaque rubrique une définition d'appartenance (inclut / exclut + exemples limites) et la tester sur **tous** les éléments inventoriés. Un élément qui ne rentre nulle part fait réviser le critère ou le libellé — pas une exception silencieuse. Les catégories ne se recouvrent pas et couvrent tout (MECE).
- **S'applique si** : toujours. **Limites** : un élément peut être *accessible* de plusieurs endroits (voir A-06) ; il n'a qu'un seul *domicile*.
- **Pour décider** : inventaire complet (étape A).
- **Exemple (générique)** : une rubrique « Compte » définie comme « tout ce qui ne tient pas dans la barre » est un critère résiduel, donc un risque de fourre-tout. Critère à tester : *Compte = ce qui concerne l'utilisateur en tant que titulaire d'un dossier (identité, documents, facturation, préférences), hors activité principale du produit*. La session (déconnexion) est une commande utilitaire, pas un contenu de Compte.
- **Vérifier** : un tiers range 10 éléments pris au hasard avec les seules définitions ; désaccords = critère à revoir. Grep des libellés « Divers / Autres / Plus / Liens utiles ».
- **Source** : EIA ch.3 p.37–38, 48–53 (PDF 43–44, 54–59), ch.5 p.86–88 (PDF 92–94) ; DI ch.2 p.31 (PDF 51). **Statut** : source ; test des 10 éléments = déduction ; critère de Compte = hypothèse à valider.

### A-03 · Justifier les critères par quatre facteurs
- **Problème** : une structure fondée sur une seule source (le marketing, l'existant, l'intuition de l'équipe) échoue.
- **Règle** : pour chaque rubrique de premier niveau, documenter : besoin utilisateur, objectif de l'organisation/du produit, état actuel (ce qui existe et est utilisé), capacité future (qui maintient ce contenu).
- **S'applique si** : révision de structure. **Limites** : si besoin et objectif divergent, les sources ne donnent pas d'arbitrage → décision du responsable produit, consignée dans le registre des questions ouvertes du projet.
- **Pour décider** : recherche utilisateur (souvent absente → hypothèse), décisions d'architecture (ADR), audit.
- **Vérifier** : fiche à quatre lignes par rubrique ; les « inconnu » y sont écrits.
- **Source** : EIA ch.3 p.38–46 (PDF 44–52). **Statut** : source.

### A-04 · La profondeur suit la fréquence et l'urgence ; rien d'essentiel n'est amputé
- **Problème** : tout mettre au premier niveau sature l'écran ; tout enfouir cache l'urgent.
- **Règle** : ce qui est fréquent **ou** urgent (conséquence d'un oubli) est au premier niveau ou sur l'accueil ; le rare reste atteignable par un chemin visible et prévisible. Mobile n'autorise pas à supprimer une fonction : il autorise à la placer plus loin.
- **S'applique si** : toujours. **Limites** : la fréquence doit être **observée** ou étiquetée **supposée** ; une fréquence supposée ne justifie qu'une hypothèse à tester.
- **Pour décider** : fréquence (source ?), urgence, conséquence d'omission, contexte d'utilité.
- **Exemple (générique)** : un justificatif manquant qui bloque une réservation est rare mais urgent → signal sur l'accueil quand il existe, domicile dans Compte › Documents.
- **Vérifier** : pour chaque élément du premier niveau, sa fréquence ou urgence est écrite avec sa source ; test : une tâche rare est trouvée sans aide.
- **Source** : DI ch.2 p.33–34 (PDF 53–54), ch.3 p.133–135 (PDF 153–155) ; DMMT ch.10 p.147–149 (PDF 158–160). **Statut** : source ; critère « urgence » = déduction (combinaison fréquence DI + arbitrage DMMT).

### A-05 · Chaque liste a une méthode d'ordre nommée
- **Problème** : un ordre implicite ou opaque fait perdre le sens (un ancien élément affiché avant un récent).
- **Règle** : pour chaque liste, écrire la méthode (temps, catégorie, alphabet, valeur, lieu) et le sens. Les objets datés affichent leur date. L'alphabet sert à retrouver un nom connu dans une longue liste, pas à découvrir.
- **S'applique si** : toute liste. **Limites** : un ordre par « importance » doit reposer sur un critère que l'utilisateur reconnaît.
- **Pour décider** : ce que l'utilisateur sait déjà de l'élément (sa date ? son nom ?), longueur de la liste.
- **Exemple (générique)** : rendez-vous à venir = chronologique croissant ; historique = décroissant ; commentaires d'un intervenant = par date de rendez-vous, rattachés au rendez-vous.
- **Vérifier** : une ligne « ordre + raison » par liste dans la fiche écran.
- **Source** : EIA ch.1 p.5–17 (PDF 11–23) ; DI ch.2 p.32 (PDF 52), ch.7 p.335–338 (PDF 355–358). **Statut** : source.

### A-06 · Une information = un domicile ; les raccourcis y renvoient
- **Problème** : la même donnée affichée et modifiable à plusieurs endroits diverge, se contredit ou fait douter de la bonne version ; à l'inverse, un domicile unique mais introuvable depuis le contexte oblige à des allers-retours.
- **Règle** : désigner pour chaque information ou action **un emplacement principal** (le domicile : vue complète, modification, historique). Ailleurs, n'afficher qu'un **raccourci** : extrait en lecture, même libellé, lien vers le domicile, jamais une seconde version éditable. Documenter tous les chemins d'accès.
- **S'applique si** : une information sert plusieurs tâches. **Limites** : une action très fréquente peut s'exécuter depuis le raccourci (ex. confirmer) si elle appelle la même logique et le même contrat de données.
- **Pour décider** : tâches qui ont besoin de l'information, fréquence, risque de divergence.
- **Exemple (générique)** : le prochain rendez-vous a pour domicile *Mes RDV* ; l'accueil en montre un extrait avec lien vers le détail ; déplacer/annuler vit dans le détail.
- **Vérifier** : matrice information × écrans (domicile D / raccourci R) : exactement un D par ligne ; libellés identiques ; aucune édition hors D sans justification écrite.
- **Source** : EIA ch.4 p.59–60 (PDF 65–66), ch.5 p.77–78 (PDF 83–84) ; DI ch.2 p.31 (PDF 51). **Statut** : déduction — synthèse de « MECE, une place pour chaque chose » (DI) et « recenser toutes les structures d'accès » (EIA) ; aucun livre ne nomme la distinction domicile/raccourci.

### A-07 · Donner un type à chaque écran : vue d'ensemble, détail, création, tâche
- **Problème** : des écrans au rôle flou mélangent liste, détail et formulaire ; l'utilisateur ne peut pas apprendre « comment marche un écran ».
- **Règle** : classer chaque écran en *Overview* (liste), *Focus* (un objet), *Make* (créer), *Do* (tâche). Un gabarit par type. La relation vue d'ensemble → détail suit la largeur : sur mobile, la liste cède la place au détail avec retour évident et contexte suffisant dans la liste ; sur grand écran, liste et détail peuvent coexister.
- **S'applique si** : étape D/E. **Limites** : un accueil est souvent un Overview de plusieurs objets — rester sobre (voir I-02).
- **Exemple (générique)** : Mes RDV = Overview ; détail d'un RDV = Focus ; Réserver = Do ; Préférences = Do (éditeur de réglages).
- **Vérifier** : chaque fiche écran porte un type unique ; deux écrans de même type partagent la structure ; depuis un détail, retour à la liste en un geste avec position conservée.
- **Source** : DI ch.2 p.35–38 (PDF 55–58), ch.7 p.341–352 (PDF 361–372), ch.3 p.155–158 (PDF 175–178). **Statut** : source ; conservation de la position = déduction.

### A-08 · Choisir un modèle de navigation par zone, avant les composants
- **Problème** : on choisit « barre du bas » ou « menu » avant de savoir comment les écrans se relient.
- **Règle** : pour chaque zone, choisir le modèle — hub (accueil liste, on entre, on revient), entièrement connecté (barre globale), arbre, pas à pas, pyramide (liste + précédent/suivant). Les modèles se combinent. La navigation globale reste présente dans les zones de consultation ; elle se réduit dans les parcours focalisés (réservation, paiement), qui gardent une sortie nommée.
- **Limites** : la navigation partout coûte de l'espace et signale que quitter est sans conséquence — à éviter au milieu d'un engagement.
- **Pour décider** : nombre de sections, profondeur, besoin de passer d'une section à l'autre.
- **Exemple (générique)** : consultation (Accueil, Mes RDV, Progrès, Compte) = connecté ; Réserver → paiement = pas à pas avec indicateur d'étape et sortie « Quitter la réservation ».
- **Vérifier** : schéma par zone avec son modèle ; chaque écran sans barre a une sortie nommée.
- **Source** : DI ch.3 p.135–142 (PDF 155–162), p.171–173 (PDF 191–193) ; DMMT ch.6 p.67 (PDF 78). **Statut** : source.

### A-09 · Séparer navigation de contenu, commandes utilitaires et liens contextuels
- **Problème** : déconnexion, thème, langue ou installation mêlés aux rubriques ou répétés partout volent l'attention et l'espace.
- **Règle** : trois familles. *Globale* : les rubriques de tâches. *Utilitaire* : session, préférences d'affichage, aide — regroupée en **un** point discret, au même endroit sur chaque écran, jamais au premier plan visuel. *Contextuelle* : liens au sein d'un contenu. Une commande utilitaire n'est dupliquée que pour une raison écrite (ex. sécurité), et la duplication est traitée comme un raccourci (A-06).
- **Limites** : les emplacements « en haut à droite » décrits par les livres sont des conventions web ; sur mobile, vérifier les conventions de la plateforme. Garder peu d'utilitaires (ordre de grandeur de DMMT : 4–5).
- **Exemple (générique)** : espace client où la déconnexion figure en en-tête **et** en pied, thème et langue dans l'en-tête de chaque page. Si un motif documenté (ex. appareils partagés) exige une déconnexion **visible**, c'est une exigence de présence, pas d'emplacement ; retirer un doublon reste possible si un point visible demeure.
- **Vérifier** : inventaire des utilitaires par écran ; chaque doublon a une raison écrite ; aucun utilitaire n'est l'élément visuellement dominant.
- **Source** : EIA ch.5 p.77–78 (PDF 83–84) ; DI ch.3 p.131–133 (PDF 151–153), p.185–188 (PDF 205–208) ; DMMT ch.6 p.65–70 (PDF 76–81). **Statut** : source ; « doublon = raccourci justifié » = déduction.

### A-10 · Libellés : les mots de l'utilisateur, précis, parallèles
- **Problème** : jargon interne, noms inventés, libellés vagues ou incohérents font hésiter.
- **Règle** : prendre les mots des utilisateurs du rôle (source citée) ; un libellé dit ce qu'on trouve derrière ; même forme grammaticale dans un groupe, sauf rupture voulue et marquée visuellement ; possessif (« Mes ») seulement s'il clarifie le propriétaire. Le titre de l'écran reprend le libellé cliqué.
- **Limites** : la forme parallèle ne doit pas produire un sens faux ; le sens prime. i18n : vérifier la longueur allemande (C-12).
- **Exemple (générique)** : « Progrès » vs « Mes commandes » : l'un nomme un résultat, l'autre un objet. À départager par test de libellés, pas par préférence (voir `tests/cas-tests.md`).
- **Vérifier** : tableau libellé / source du mot / forme ; test de compréhension (« qu'attendez-vous derrière ? ») ; libellé du lien = titre de l'écran (contrôle automatisable).
- **Source** : EIA ch.3 p.51–54 (PDF 57–60) ; DMMT ch.1 p.11–19 (PDF 22–30), ch.6 p.74–76 (PDF 85–87). **Statut** : source.

### A-11 · Chaque écran dit où l'on est, même en arrivant par un lien
- **Problème** : via une notification ou un e-mail, l'utilisateur atterrit au milieu de l'app sans repère.
- **Règle** : titre visible, rubrique active marquée par au moins deux indices (pas la couleur seule), retour évident ; un lien profond ouvre la ressource visée (après connexion si nécessaire) et non l'accueil.
- **Limites** : le fil d'Ariane sert les hiérarchies profondes ; à deux niveaux, un titre + retour suffit. Ne remplace jamais une bonne navigation.
- **Vérifier** : test du coffre adapté (V-03) sur des écrans tirés au hasard ; ouvrir l'URL d'un détail déconnecté → connexion → retour au détail.
- **Source** : EIA ch.5 p.82–85 (PDF 88–91) ; DMMT ch.6 p.74–83 (PDF 85–94), ch.10 p.150 (PDF 161) ; DI ch.3 p.165–170 (PDF 185–190), p.193–198 (PDF 213–218). **Statut** : source.

### A-12 · Pas d'impasse ; chemins en nombre mesuré
- **Problème** : un écran sans suite bloque ; un écran avec dix accès concurrents paralyse.
- **Règle** : chaque écran a un but principal, une action principale et une sortie ; ne pas multiplier les modules qui mènent au même contenu. Les états vides et d'erreur sont des écrans comme les autres : ils proposent l'étape suivante.
- **Limites** : « moins, mais pas trop peu » — aucune source ne donne de nombre.
- **Vérifier** : chaque fiche écran remplit « action principale » et « sortie » ; comptage des accès vers un même contenu, justifiés.
- **Source** : EIA ch.5 p.78–82, 86–87 (PDF 84–88, 92–93) ; DI ch.3 p.171–173 (PDF 191–193). **Statut** : source ; extension aux états vides = déduction.

### A-13 · Identifier le mode de recherche de chaque tâche
- **Problème** : une structure qui ne sert que celui qui sait déjà quoi chercher abandonne les autres.
- **Règle** : pour chaque tâche, nommer le mode : élément connu (je sais quoi et où), exploration, re-recherche (retrouver ce que j'ai déjà vu), « je ne sais pas ce que je dois savoir ». Concevoir l'accès en conséquence ; ne pas compter sur une recherche textuelle pour compenser une structure faible.
- **Exemple (générique)** : « retrouver mon RDV » = re-recherche (accès direct, pas de navigation) ; « préparer mon rendez-vous » peut relever de « je ne sais pas quoi préparer » → proposer le contenu depuis le RDV, pas le cacher dans une rubrique.
- **Vérifier** : colonne « mode » dans l'inventaire des tâches ; test avec un novice sans vocabulaire interne.
- **Source** : EIA ch.5 p.89–94, 97 (PDF 95–100, 103), fig. 5.12 examinée. **Statut** : source ; exemples = adaptation.

### A-14 · Contextes parallèles (plusieurs espaces de travail, comptes ou dossiers simultanés) : choisir la granularité du contexte
- **Problème** : un utilisateur gère plusieurs contextes en parallèle (plusieurs dossiers, abonnements, organisations) ; les informations se mélangent, ou au contraire il doit changer de « mode » pour voir son agenda complet.
- **Règle** : classer chaque information selon sa portée — **globale** (identité, agenda, facturation de l'utilisateur, préférences) ou **propre à un contexte** (progression, historique, offres réservables du dossier). Puis choisir :
  - (a) **vue unifiée + étiquette de contexte** sur chaque élément propre (défaut quand l'agenda et l'argent sont globaux et que le nombre de contextes est petit) ;
  - (b) **sélecteur de contexte** en tête des seules zones propres à un contexte (Progrès, parcours de réservation), avec contexte actif nommé en permanence et mémorisé ;
  - (c) **espace séparé par contexte** — seulement si les contextes partagent peu de données (rare ; à éviter si l'agenda est commun).
  Un utilisateur à un seul contexte ne voit aucun sélecteur.
- **S’applique si** : un utilisateur gère plusieurs contextes en parallèle. **Limites** : aucune des trois sources ne traite ce cas ; le choix doit être validé par test. Ne pas utiliser la couleur seule pour distinguer les contextes. Un filtre suppose un attribut défini et renseigné partout (vérifier le modèle de données).
- **Pour décider** : portée de chaque information ; nombre réel de contextes simultanés (inconnu → [H]) ; support backend (le modèle de données gère-t-il vraiment plusieurs contextes actifs ?) ; besoin de comparer côte à côte.
- **Vérifier** : colonne « portée » dans l'inventaire ; test : l'utilisateur distingue sans erreur deux éléments de contextes différents dans l'agenda ; changer de contexte puis revenir conserve l'état ; utilisateur mono-contexte : zéro élément de sélection.
- **Source** : DI ch.2 p.105–109 (PDF 125–129) Many Workspaces, p.97–104 (PDF 117–124) Alternative Views ; EIA ch.6 p.106–110 (PDF 112–116) filtres ; DI ch.5 p.258–264 (PDF 278–284) couleur non exclusive. **Statut** : déduction (transposition explicite ; aucun livre ne parle de contextes multiples).

### A-15 · Documenter la structure comme un inventaire vivant
- **Problème** : l'équipe parle d'écrans inexistants avec des mots différents ; des écrans restent orphelins.
- **Règle** : tenir la liste des écrans avec ID stable, parent, libellé approuvé, type (A-07), statut (implémenté / capture / proposé), domicile des informations (A-06) et tous les chemins d'accès. Les libellés de l'inventaire = libellés de l'UI.
- **Vérifier** : chaque route du code apparaît dans l'inventaire et inversement ; aucun écran orphelin.
- **Source** : EIA ch.4 p.57–74 (PDF 63–80). **Statut** : source.

### A-16 · Un terme = un concept
- **Problème** : « rendez-vous / réservation / séance / créneau » employés indifféremment font croire à des objets différents.
- **Règle** : utiliser le glossaire du projet (documentation ou garde terminologique, à découvrir ; sinon en proposer un) ; tout nouveau terme d'interface y est ajouté avec sa définition avant usage.
- **Vérifier** : grep des variantes ; garde terminologique du dépôt (si elle existe) verte.
- **Source** : EIA ch.6 p.100–101, 110–113 (PDF 106–107, 116–119). **Statut** : source ; glossaire = choix projet.
