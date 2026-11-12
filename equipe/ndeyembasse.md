# Ndeye Mbasse Ndiaye 

- Pseudo GitHub :ndiayendeyembasse32-sys
- Ce que je connais déjà de Git :git est un moyen pratique de regrouper tous ces projets et de develloper des performances adequates en tant que bon informaticien
- Ce que j'attends de cet atelier : ...
## Quiz

1. Juste après `git commit`, où se trouve mon commit ?
   → Uniquement dans l'historique local de mon Codespace (le dépôt `.git`). GitHub ne le connaît pas encore.

2. Juste après `git push`, où se trouve-t-il ?
   → Sur GitHub (le dépôt distant `origin`), et toujours en local dans mon Codespace. Les autres peuvent le récupérer avec `git pull`.

3. Que se passe-t-il si je supprime mon Codespace après un commit mais sans push ?
   → Le commit est perdu définitivement, car il n'existait que dans le Codespace et GitHub ne l'a jamais reçu.
   ## Stash

La commande `git stash` permet de mettre temporairement de côté des modifications non commitées afin de nettoyer l'espace de travail. Cela permet de changer de branche librement pour traiter une urgence. On récupère ensuite son travail en cours grâce à `git stash pop`.