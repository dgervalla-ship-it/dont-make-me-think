# Tests du skill — cas génériques

> Méthode RED → GREEN → REFACTOR. Un agent par cas, sur un dépôt réel en lecture seule.
> **RED** : mêmes demandes sans le skill. **GREEN** : consigne unique « lis SKILL.md et suis-le ».
> Ce que ces tests prouvent : le skill **conduit** à des décisions sourcées et vérifiables. Ils ne
> prouvent pas que les décisions améliorent l'expérience : cela exige des tests utilisateurs.
> Les cas ci-dessous sont génériques (exemple : SaaS de réservation et de facturation) ; les
> adapter au produit en cours en gardant la structure « demande → comportement attendu ».

## 1. Cas

| # | Rôle / module | Demande | Nature |
|---|---|---|---|
| T1 | Client / espace client | Un client a deux dossiers actifs en parallèle : organiser rendez-vous, progression, paiements, réservation | contexte parallèle |
| T2 | Comptable / Finance | « Elle ne trouve pas comment exporter les écritures ; certains boutons lui sont interdits » | rôle restreint |
| T3 | Intervenant / tableau de bord | Des tâches terminées sans compte rendu s'accumulent | action différée |
| T4 | Opérateur de support / console admin | Audit de navigation de la console | audit |
| T5 | **Transversal** (admin · client · intervenant) | Les conditions d'annulation deviennent modifiables et doivent être visibles partout | multi-rôles |
| T6 | Client / espace client | (a) aucun rendez-vous prévu ; (b) thème et déconnexion répétés sur chaque page | état vide, utilitaires |

## 2. Comportement attendu (GREEN)

| # | Décision attendue | Justification attendue | Limites à déclarer | Validation à proposer |
|---|---|---|---|---|
| T1 | Évaluer la navigation existante avant de la changer ; classer chaque information globale vs propre à un contexte (A-14) ; étiquette de contexte ou sélecteur **seulement** si ≥ 2 contextes actifs | A-14, A-06 ; faits relevés dans le code (le modèle de données gère-t-il plusieurs contextes actifs ?) | Blocage possible par une décision d'architecture ; règles métier absentes → registre des questions ouvertes | fiches écran, tâches de test, mise à jour de cartographie listée |
| T2 | Entrée de navigation filtrée par rôle ; réutiliser les opérations d'export **existantes** ; retirer du rôle les boutons qu'il ne peut pas utiliser ; permissions d'API inchangées | I-03, I-10, D-03 ; faits : appelants des exports, réponses de l'API | sens exact de « exporter » = hypothèse [H] ; masquer un bouton ne corrige pas une garde d'API trop large (le signaler) | tâches de test comptable, contrôles par rôle |
| T3 | Action « Ajouter un compte rendu » après validation rapide + segment « À documenter » dans la vue du jour ; option alternative (page dédiée) écartée avec raison | arbitrages T2/T6, I-12, A-12 ; faits : caractère obligatoire du compte rendu, verrouillage éventuel | obligation et origine du stock inconnues → questions | 3 tâches de test, conditions de changement d'avis |
| T4 | Libellés alignés sur la tâche ; liens contextuels depuis la fiche de compte, filtrés par permission ; **ne pas** élargir les droits du rôle | A-10, A-12 ; faits : gardes réelles vs menus ; décisions tranchées sur les droits respectées | rôle futur du support = question au responsable | test opérateur, mise à jour de la cartographie |
| T5 | Un domicile unique « Règles d'annulation » (rôle autorisé) + lecture seule aux endroits d'usage (confirmation, annulation, espace client) ; indicateur pour l'intervenant | A-06, I-07, I-08, C-10 ; faits : API existante, portée des réglages | rétroactivité d'un changement et exigences juridiques = questions ouvertes | tâches par rôle, i18n |
| T6 | (a) Message « Aucun rendez-vous à venir » + une seule action selon l'offre **réellement** disponible ; (b) thème, langue, installation regroupés en Préférences ; une seule déconnexion visible | I-02, I-10, A-09, C-07 ; faits : ce que l'accueil lit vraiment | retrait d'un doublon seulement après recherche de sa raison | tâches V-05, mise à jour de la cartographie |

Critères à vérifier sur chaque livrable : chaîne constat → tâche → règle → proposition → conséquences → validation ; statuts [F]/[S]/[D]/[C]/[H] ; références de pages présentes ; aucune règle métier inventée ; niveau de preuve « revue experte — non testée » ; mise à jour de cartographie planifiée ; quelques affirmations recontrôlées au code par l'orchestrateur.

## 3. Défauts attendus sans le skill (RED) et corrections attendues avec

| Défaut observé sans skill | Avec skill |
|---|---|
| Navigation envisagée par le demandeur validée d'office | évaluée contre les tâches et décisions existantes, conservée ou changée pour une raison écrite |
| Fonctions existantes ignorées → proposition de les recréer | partir des API et du code existants |
| Règles métier inventées (délais, frais, exceptions) | renvoyées en questions ouvertes |
| Permission supposée à tort | décisions tranchées lues et respectées |
| Fréquences et seuils affirmés sans source | étiquetés [H], tests pour les mesurer |
| Aucun test utilisateur, aucune source | tâches V-05 + références de livres par principe |

## 4. Points de contrôle REFACTOR (à rejouer après toute modification du skill)
1. **Raison d'un doublon** : l'agent doit chercher le motif d'une duplication (commentaires, historique git, registre des manquements, ADR, audits) avant de proposer de la supprimer ; distinguer exigence et emplacement.
2. **Décisions tranchées** : toute proposition touchant des droits doit consulter les décisions déjà prises (registre des questions ouvertes, ADR) avant de contredire.
3. **Affirmations vérifiables** : une proposition de la cartographie peut être périmée ou fausse ; l'agent recontrôle dans le code.

## 5. Limites des tests
Un seul passage par cas, sans pression de temps ni répétition ; agents du même fournisseur que l'auteur du skill ; aucune séance avec de vrais utilisateurs. Rejouer les cas ciblés après chaque correction du skill.
