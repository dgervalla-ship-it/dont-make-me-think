# Consulter et mettre à jour la cartographie

La **méthode** (ce skill) est durable ; la **cartographie** décrit l'état du produit à une date
et un commit donnés. Elle vieillit à chaque changement : la traiter comme une hypothèse à
revérifier, jamais comme une vérité. Si le projet n'en a pas, en démarrer une minimale (voir §4)
après accord de l'utilisateur ; l'emplacement se découvre dans le dépôt (dossier docs/UX existant)
ou se propose.

## 1. Quelle partie lire selon la tâche

Parties types d'une cartographie (les noms de fichiers varient selon le projet) :
**vue d'ensemble**, **rôles et permissions**, **objets métier**, **écrans par espace**,
**arborescences / navigation**, **parcours**, **diagnostic** (constats ouverts),
**proposition cible**, **couverture** (routes inventoriées vs routes du code).

| Tâche | Lire d'abord | Puis |
|---|---|---|
| Nouvelle fonctionnalité | vue d'ensemble, objets métier | écrans de l'espace, parcours |
| Évolution d'un module | écrans de l'espace (section du module) | diagnostic (constats ouverts du module) |
| Réorganiser une page | ligne de l'écran | arborescences, proposition cible |
| Audit de navigation | arborescences, rôles et permissions | diagnostic, correspondance avec la cible |
| Modifier un parcours | parcours | écrans traversés, rôles et permissions |
| Revue UX/UI | écrans de l'espace + diagnostic | références du skill |
| Plusieurs rôles | rôles et permissions, parcours (relais) | écrans de chaque espace touché |

Toujours vérifier dans le code que la ligne lue est encore vraie (date du dernier commit du composant cité ; relire la garde de rôle).

## 2. Déclencheurs de mise à jour (dans la même PR / le même lot que le changement)

| Changement | Parties à mettre à jour |
|---|---|
| Route ajoutée, supprimée, renommée ou déplacée | écrans de l'espace ; arborescences ; couverture (total des routes) ; correspondance si la route était prévue par la cible |
| Entrée de menu (navigation, barre, console) | arborescences ; ligne de l'écran (colonne entrées) |
| Rôle ou permission (garde front, garde API, politique de données) | rôles et permissions ; lignes des écrans concernés |
| Entité, statut ou transition (migration) | objets métier (en plus du modèle de données du projet) |
| Parcours (étape, relais entre rôles, notification) | parcours |
| Constat corrigé ou nouveau | diagnostic (statut + preuve de fermeture ; fiche dans le registre des manquements du projet si non corrigé) |
| Proposition cible réalisée ou abandonnée | proposition cible, correspondance |

## 3. Règles d'écriture
- Chaque ligne garde : ID stable (ne jamais réutiliser un ID supprimé), preuve (`fichier:ligne` ou doc §), état, date de vérification.
- Distinguer **implémenté** / **observé à l'écran** / **proposé**. Une route n'est pas une fonctionnalité accessible.
- Mettre à jour l'en-tête du fichier touché : date + commit de référence.
- Diagrammes (Mermaid ou équivalent) : un par vue, petits ; un arbre ne montre pas tous les chemins (liens contextuels listés à part).
- Contrôle de couverture après modification : le nombre de pages du code (fichiers de routes) = nombre de routes inventoriées ; noter la commande utilisée dans la partie couverture.

## 4. Démarrer une cartographie minimale (si absente)
1. Inventaire des routes (A-15) avec ID stable, parent, libellé, type d'écran, accès, rôles.
2. Tableau rôles × espaces × portée des données (voir `contexte-projet.md`).
3. Liste des parcours principaux par rôle (déclencheur → résultat).
4. Diagnostic : constats avec preuve et statut.
Rester petit : une cartographie incomplète mais vraie vaut mieux qu'une cartographie large et périmée.
