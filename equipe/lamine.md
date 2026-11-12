# Lamine Mbengue

- Pseudo GitHub : @lamine221-sn
- Ce que je connais déjà de Git : ...
- Ce que j'attends de cet atelier : ...

## Quiz

1. Juste après `git commit`, où se trouve mon commit ?
   → Uniquement dans l'historique local de mon Codespace (le dépôt `.git`). GitHub ne le connaît pas encore.

2. Juste après `git push`, où se trouve-t-il ?
   → Sur GitHub (le dépôt distant `origin`), et toujours en local dans mon Codespace. Les autres peuvent le récupérer avec `git pull`.

3. Que se passe-t-il si je supprime mon Codespace après un commit mais sans push ?
   → Le commit est perdu définitivement, car il n'existait que dans le Codespace et GitHub ne l'a jamais reçu.

## Stash
`git stash` met de côté les modifications non commitées, sans les perdre.
Ça permet de changer de branche pour traiter une urgence avec un dossier de travail propre.
On récupère ensuite son travail avec `git stash pop`.