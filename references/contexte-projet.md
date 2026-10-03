# Construire le contexte du projet (première utilisation)

> À exécuter une fois par projet, puis à revérifier avant chaque usage : le contexte vieillit
> à chaque changement du code. Ne jamais l'inventer : tout ce qui n'est pas trouvé est étiqueté
> **inconnu** et, s'il change une décision, versé au registre des questions ouvertes du projet
> (le créer s'il n'existe pas). Les trois livres ne fournissent aucune règle métier.

## 1. Procédure

| # | Chercher | Où (à découvrir dans le dépôt) | Noter |
|---|---|---|---|
| 1 | **Sources de vérité produit** | README, dossiers `docs/`, specs, ADR, journal de décisions, PRD, instructions d'agents (`CLAUDE.md`, `AGENTS.md`), registre des questions ouvertes | liste des documents + date ; décisions déjà **tranchées** |
| 2 | **Produit et espaces** | docs produit, routes, écrans de connexion | les espaces distincts (ex. back-office, espace client, console admin, site public), leur public, leur point d'entrée |
| 3 | **Rôles et permissions** | modèle d'authentification, gardes front et API, politiques d'accès aux données | rôles, portée des données de chacun (soi / équipe / organisation / plateforme), écarts entre menus et gardes API |
| 4 | **Carte des écrans** | routeur / dossier des pages, fichier de configuration de la navigation, menus | routes, entrées de menu par rôle, écrans accessibles par URL seule |
| 5 | **Design system et composants** | bibliothèque de composants, tokens, règles UI du projet, conventions d'icônes, thème clair/sombre | composants existants à réutiliser **avant** d'en créer ; contraintes (contrastes, tailles tactiles) |
| 6 | **Langues et formats** | fichiers de traduction, configuration i18n | langues livrées, langue source, règles de ton, formats locaux |
| 7 | **Glossaire** | glossaire, garde terminologique, docs | un terme = un concept (A-16) |
| 8 | **Portes de validation** | scripts de test, lint, types, e2e, a11y, contrat d'API | commandes à exécuter à l'étape F (V-02) |
| 9 | **Usage réel** | analytics, retours utilisateurs, tickets, audits UX existants | fréquences **observées** ; sinon toutes les fréquences restent [H] |

## 2. Résultat attendu
Un court tableau (dans le livrable de la tâche, ou dans le dossier UX du projet s'il existe) :
espaces et rôles ; faits vérifiés avec preuve (`fichier:ligne`, doc) ; **inconnues** (qui tranche) ;
hypothèses de travail étiquetées [H]. Même statuts que les décisions : [F] fait vérifié ·
[D] déduction · [C] choix existant du projet ou décision explicite du demandeur · [H] hypothèse.

## 3. Règles
- Un fait sans preuve est une hypothèse.
- Une inconnue qui change matériellement la décision → demander à l'utilisateur (règle 8 du skill).
- Revérifier le contexte dans le code avant chaque usage (la date du dernier commit des fichiers cités).
- Si le projet n'a ni cartographie ni registre des questions ouvertes, proposer de les créer (voir `cartographie-maj.md`) sans les imposer.
