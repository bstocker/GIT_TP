# TP Git & GitHub — Parcours collaboratif

## Présentation

Bienvenue sur le TP d'initiation à **Git** et **GitHub** !

Ce parcours est structuré en **3 niveaux** à réaliser **dans l'ordre** :

- **TP1 — Fondamentaux** : fork, branches, commits, merges.
- **TP2 — Workflow GitHub professionnel** : Issues, Project board, Pull Requests, code review, conflits.
- **TP3 — Pratiques avancées** : rebase, cherry-pick, stash, GitHub Actions (CI), tags et releases.

Chaque TP s'appuie sur les acquis du précédent.

### Format

- Groupes de **3 étudiants** idéalement (2 possibles, mais charge de travail accrue).
- Tous les membres doivent avoir un compte GitHub.
- Les exercices se font **dans l'ordre** : sauter un chapitre fait perdre les points des suivants qui en dépendent.

> Les blocs grisés comme celui-ci sont des **avertissements importants** ou des conseils du prof. Lisez-les attentivement.

### Sommaire

- [TP1 — Fondamentaux (20 pts)](#tp1--fondamentaux-20-points)
- [TP2 — Workflow GitHub professionnel (30 pts)](#tp2--workflow-github-professionnel-30-points)
- [TP3 — Pratiques avancées (30 pts)](#tp3--pratiques-avancées-30-points)
- [Bonus qualité (20 pts)](#bonus-qualité-20-points)
- [Livraison finale](#livraison-finale)

### Notation globale

| TP        | Thème                                           | Points  |
| --------- | ----------------------------------------------- | ------- |
| TP1       | Fondamentaux Git                                | 20      |
| TP2       | Workflow GitHub professionnel                   | 30      |
| TP3       | Pratiques avancées                              | 30      |
| Bonus     | Qualité d'historique, commits, PR et reviews    | 20      |
| **Total** |                                                 | **100** |

---

## TP1 — Fondamentaux (20 points)

### Exercice 1.1 : Fork (2 pts)

Le **fork** copie un dépôt GitHub entièrement (avec son historique) sur votre propre compte. Vous travaillez sur la copie sans affecter l'original.

Un seul d'entre vous fork le dépôt du prof. Décidez qui : ce sera le **propriétaire** du dépôt pour tout le TP.

Vidéo d'aide : [Forker un projet](https://youtu.be/p33-7XQ29zQ)

### Exercice 1.2 : Ajouter les collaborateurs (1 pt)

Le propriétaire du dépôt :

1. Onglet `Settings` (en haut à droite du dépôt).
2. Menu de gauche : `Collaborators`.
3. Ajouter les pseudos GitHub des camarades.
4. Les camarades acceptent l'invitation reçue par email.

### Exercice 1.3 : Présentez l'équipe (2 pts)

Modifiez le bloc ci-dessous pour présenter votre équipe et la date du TP.

**Noms des étudiants :**
- Nom Prénom
- Nom Prénom
- Nom Prénom

**Date du jour :** XX/XX/20XX

Faites un **commit** et **push** sur `master`. N'importe quel collaborateur peut pusher.

> L'ordre des noms définit `collab-1`, `collab-2`, `collab-3` pour la suite du TP.

### Exercice 1.4 : Travail d'équipe en parallèle (10 pts)

Chaque collaborateur travaille **sur sa propre branche**. Les 3 missions sont indépendantes et peuvent être réalisées en parallèle.

**Bonnes pratiques attendues** : commits petits et **pertinents**, messages clairs.

#### Mission collab-1 — `feature/collab-1`

Donner un peu de gaieté au site :
- Créer `style.css` et le lier à `index.html`.
- Titre `h1` en rouge.
- Titre `h2` en vert.
- Remplacer la liste à puces (`ul`) par une liste numérotée (`ol`).

Pousser la branche sur le dépôt distant.

#### Mission collab-2 — `feature/collab-2`

Enrichir le contenu :
- Ajouter une ligne `Prof de git : Boris STOCKER` dans la liste.
- Ajouter une description courte sous chaque élément de la liste.

```html
<li>Mon élément</li>
Ma description
```

Pousser la branche sur le dépôt distant.

#### Mission collab-3 — `hotfix/collab-3`

Corriger les fautes :
- Faute dans le titre `h2`.
- Faute dans l'adresse.
- Faute dans le nom du directeur.

Pousser la branche sur le dépôt distant.

### Exercice 1.5 : Fusion (5 pts)

À ce stade, vous avez 4 branches : `master`, `feature/collab-1`, `feature/collab-2`, `hotfix/collab-3`.

Fusionnez-les sur `master` **dans cet ordre** :

1. `hotfix/collab-3` → `master`
2. `feature/collab-2` → `master` (gardez les corrections de collab-3)
3. `feature/collab-1` → `master` (gardez les modifs de collab-2 et collab-3 + ajouts de collab-1)

Pushez le résultat sur le dépôt distant. **Fin du TP1.**

---

## TP2 — Workflow GitHub professionnel (30 points)

À partir d'ici, on adopte un workflow proche d'une équipe de dev réelle :

- **Aucun push direct sur `master`** : tout passe par une **Pull Request**.
- Toute PR est **relue et approuvée** par un autre collaborateur avant merge.
- Le travail est planifié dans **Issues** + **Project board**.

### Exercice 2.1 : Mettre en place le board (3 pts)

Sur GitHub, dans votre dépôt :

1. Onglet **Projects** → `New project` → template **Board**.
2. Créez 3 colonnes : `À faire`, `En cours`, `Fait`.
3. Créez 4 **Issues** (onglet `Issues` → `New issue`) :
   - `[FEAT] Ajouter une page Contact`
   - `[FEAT] Ajouter une page Cours`
   - `[FIX] Corriger les fautes restantes`
   - `[CHORE] Ajouter un .gitignore`
4. Liez chaque issue au project, placez-les dans `À faire`.
5. **Assignez** chaque issue : collab-1 prend `Contact`, collab-2 prend `Cours`, collab-3 prend `[FIX]`. Le `[CHORE]` reste partagé.

> Une issue **bien rédigée** = titre clair, description du besoin, et critères d'acceptation sous forme de checklist Markdown :
> ```
> - [ ] Le fichier contact.html existe
> - [ ] Il est lié à style.css
> - [ ] Un lien y mène depuis index.html
> ```
> **2 points sur 3 viennent de la qualité des issues.**

### Exercice 2.2 : Protéger la branche master (1 pt)

Le propriétaire du dépôt configure `Settings → Branches → Add branch protection rule` :

- Pattern : `master`
- Cocher **Require a pull request before merging**.
- Cocher **Require approvals** → 1 approbation minimum.

À partir de maintenant, **toute** intégration sur master passe par PR avec review.

### Exercice 2.3 : Pull Requests + Code Review (12 pts)

Chaque collaborateur traite **son** issue sur sa propre branche.

Conventions de nommage :
- `feature/<slug>` pour les features
- `fix/<slug>` pour les corrections

#### Mission collab-1 — `feature/contact`
- Créer `contact.html` (titre, email factice, téléphone factice).
- Lier `style.css`.
- Ajouter un lien depuis `index.html` vers `contact.html`.

#### Mission collab-2 — `feature/cours`
- Créer `cours.html` avec une liste d'au moins 4 cours dispensés.
- Lier `style.css`.
- Ajouter un lien depuis `index.html` vers `cours.html`.

#### Mission collab-3 — `fix/typos`
- Relire **tout** `index.html` et corriger les fautes restantes (il en reste au moins une).

#### Workflow PR pour chaque mission

1. Créer la branche, commiter, pusher.
2. Ouvrir une **Pull Request** vers `master`.
3. Dans la description, ajouter `Closes #<numéro de l'issue>` (ferme automatiquement l'issue à la fusion).
4. Demander une review à un autre collaborateur (jamais l'auteur lui-même).
5. Le reviewer laisse **au moins un commentaire constructif** (suggestion, question, ou validation argumentée) avant d'approuver.
6. Une fois approuvée, **merger via l'interface GitHub**. Choisissez collectivement entre `Squash and merge` ou `Merge commit` et **soyez cohérents** sur tout le TP.

> Une review qui dit juste "lgtm" sans commentaire = **0 point sur cette PR**.

### Exercice 2.4 : Conflit volontaire à résoudre (8 pts)

Deux collaborateurs vont **volontairement** créer un conflit pour apprendre à le gérer.

1. **collab-1** crée la branche `feature/footer-1` (depuis master à jour) et ajoute juste avant `</body>` dans `index.html` :
   ```html
   <footer>© 2025 ESGI — Tous droits réservés</footer>
   ```
2. **collab-2** crée la branche `feature/footer-2` (depuis master, **avant** le merge de footer-1) et ajoute au même endroit :
   ```html
   <footer>Site réalisé dans le cadre du TP Git</footer>
   ```
3. **collab-1** ouvre une PR, fait reviewer, merge.
4. **collab-2** ouvre une PR → conflit signalé par GitHub.
5. **collab-2** doit :
   - Mettre à jour sa branche avec `master` (`git pull origin master` ou `git rebase origin/master`).
   - Résoudre le conflit en **gardant les deux footers** (l'un au-dessus de l'autre).
   - Pousser la résolution.
   - Faire valider et merger la PR.

> Le commit de résolution doit avoir un message **explicite** (par exemple `merge: combine les deux footers`), pas le message par défaut généré par Git.

### Exercice 2.5 : .gitignore + revert (6 pts)

#### Partie A — .gitignore (3 pts)

1. Sur la branche `chore/gitignore`, créez un fichier `.gitignore` qui ignore :
   ```
   *.log
   .DS_Store
   node_modules/
   .vscode/
   ```
2. Créez un fichier `debug.log` (n'importe quel contenu) et vérifiez avec `git status` qu'il **n'apparaît pas**.
3. PR + review + merge.

#### Partie B — Revert (3 pts)

Simulation : un commit cassé arrive sur `master`.

1. Quelqu'un ouvre une PR qui introduit volontairement une faute dans le titre `h1` (ex : `Le super nouveua site`).
2. La PR est mergée (oui, on merge volontairement la régression pour la suite de l'exo).
3. **Sans réécrire l'historique**, sur une nouvelle branche `revert/h1-typo`, utilisez `git revert <hash-du-commit-cassé>` pour annuler ce commit.
4. PR + review + merge.

> `git revert` ≠ `git reset`. Le premier crée un **nouveau commit qui annule** ; le second **réécrit l'historique**. Sur une branche partagée comme `master`, on revert.

---

## TP3 — Pratiques avancées (30 points)

### Exercice 3.1 : Rebase et historique propre (8 pts)

Chaque collaborateur fait une petite feature avec **3 commits "sales"** (`wip`, `fix typo`, `add feature`), puis les **squashe en 1 commit propre** avant la PR.

#### Missions

- **collab-1** — `feature/responsive` : ajouter une `@media (max-width: 600px)` simple dans `style.css`.
- **collab-2** — `feature/dark-mode` : ajouter une classe `.dark` (fond noir, texte blanc) appliquée au `body`.
- **collab-3** — `feature/nav` : ajouter une `<nav>` avec liens vers `index.html`, `contact.html`, `cours.html`.

#### Procédure

1. Faire au moins 3 commits sur la branche, dont 2 "wip".
2. Avant de pousser : `git rebase -i HEAD~3`, remplacer `pick` par `squash` (ou `s`) sur les 2 derniers, et écrire un message final propre.
3. Pousser : `git push` (ou `git push --force-with-lease` si la branche existait déjà sur le remote).
4. PR + review + merge.

> `--force-with-lease` est plus sûr que `--force` : il refuse de pousser si quelqu'un d'autre a poussé entre-temps.
> **Ne jamais force-push sur `master`.** Uniquement sur vos branches feature.

### Exercice 3.2 : Cherry-pick (5 pts)

Scénario : le prof a poussé une branche `improvements` avec 3 commits, dont seuls 2 vous intéressent.

1. Le **propriétaire du dépôt** crée la branche `improvements` (depuis master) avec 3 commits **distincts** :
   - **A** : ajoute un fichier `favicon.ico` (peut être vide) et la balise `<link rel="icon">` dans `index.html`.
   - **B** : ajoute une balise `<meta name="description" content="...">` dans `index.html`.
   - **C** : ajoute une bannière publicitaire moche (couleur fluo, texte criard).
2. Pousse la branche, **sans la merger**.
3. Sur une nouvelle branche `feature/picks` (depuis master), récupérez **uniquement A et B** :
   ```bash
   git cherry-pick <hashA> <hashB>
   ```
4. PR + review + merge.

### Exercice 3.3 : Stash (3 pts)

Tous les collaborateurs, chacun de leur côté :

1. Sur master à jour, modifiez n'importe quoi dans un fichier (sans commiter).
2. Une "urgence" tombe : il faut basculer sur une autre branche pour un mini-fix.
3. `git stash` pour sauver les modifs en cours.
4. Basculer sur une nouvelle branche `fix/urgence-<votre-prénom>`, faire un mini-fix bidon (ajouter un commentaire HTML par exemple), commiter.
5. Revenir sur master, `git stash pop` pour récupérer le travail en cours.
6. Documenter ces 5 étapes dans un fichier `STASH.md` (5 lignes max).
7. PR + review + merge **du `STASH.md`** (les fix bidon peuvent rester non mergés).

### Exercice 3.4 : GitHub Actions — CI simple (8 pts)

Vous allez ajouter un workflow qui **vérifie automatiquement** votre projet à chaque PR.

1. Sur la branche `chore/ci`, créez `.github/workflows/lint.yml` :
   ```yaml
   name: Lint HTML
   on:
     pull_request:
       branches: [master]
     push:
       branches: [master]
   jobs:
     lint:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v4
         - name: Vérifier que les pages existent
           run: |
             test -f index.html
             test -f contact.html
             test -f cours.html
         - name: Lint HTML
           run: |
             npm install -g htmlhint
             htmlhint *.html
   ```
2. PR, review, merge.
3. **Cassez volontairement** une PR (ex : retirer la balise `<html>`) et observez la CI passer en **rouge**.
4. Réparez et observez la CI passer en **vert**.

> Joignez à la PR finale **les liens vers un run rouge ET un run vert** (onglet Actions de votre dépôt).

### Exercice 3.5 : Tags & Releases (6 pts)

C'est l'heure de publier la **v1.0.0** !

1. Sur master à jour :
   ```bash
   git tag -a v1.0.0 -m "Première version stable du site"
   git push origin v1.0.0
   ```
2. Sur GitHub : **Releases** → `Draft a new release`.
3. Sélectionnez le tag `v1.0.0`.
4. Rédigez un changelog clair :
   ```markdown
   ## Nouveautés
   - Page Contact
   - Page Cours
   - Mode sombre
   - Navigation
   ## Corrections
   - Fautes orthographiques
   ## Technique
   - CI GitHub Actions
   ```
5. Publiez la release.
6. Faites une modification mineure (ex : ajustement CSS), taggez `v1.0.1`, refaites une release.

> Suivez le **versioning sémantique** : `MAJOR.MINOR.PATCH`.
> - `PATCH` (ex 1.0.0 → 1.0.1) : correction.
> - `MINOR` (1.0.1 → 1.1.0) : ajout rétrocompatible.
> - `MAJOR` (1.1.0 → 2.0.0) : changement cassant.

---

## Bonus qualité (20 points)

Notés **transversalement** sur l'ensemble du TP :

- **Atomicité des commits (5 pts)** — un commit = une idée. Pas de `wip`, `save`, ou commits-fourre-tout sur les branches mergées.
- **Messages de commit (5 pts)** — convention [Conventional Commits](https://www.conventionalcommits.org/) :
  ```
  feat(contact): ajoute la page contact
  fix(typos): corrige le nom du directeur
  chore(ci): ajoute un workflow de lint
  ```
- **Qualité des PR (5 pts)** — titre clair, description avec contexte, lien vers issue (`Closes #X`), captures d'écran si visuel.
- **Qualité des reviews (5 pts)** — commentaires constructifs, suggestions concrètes, pas de "lgtm" vide.

---

## Livraison finale

À la date butoir, votre dépôt doit présenter :

- Toutes les branches du TP1, TP2 et TP3 mergées (ou clairement abandonnées et documentées).
- Au moins 4 issues fermées.
- Au moins 2 releases publiées (`v1.0.0` et `v1.0.1`).
- Une CI GitHub Actions verte sur `master`.
- Un README à jour si vous l'avez fait évoluer.

Envoyez par email à votre prof :
- Le **lien du dépôt**.
- Les **3 pseudos GitHub** des collaborateurs.

Bon TP !
