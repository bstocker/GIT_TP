# Elimane Kane

- Pseudo GitHub : @elimanekanee06
- Ce que je connais déjà de Git : les commandes de base (status, add, commit, push, pull) et la notion de dépôt
- Ce que j'attends de cet atelier : apprendre à travailler en équipe avec Git et GitHub, notamment les branches, les pull requests et la CI


## Quiz

1. Juste après `git commit`, où se trouve mon commit ? Uniquement dans l'historique local de mon Codespace. GitHub et mes coéquipiers ne le voient pas.
2. Juste après `git push`, où se trouve-t-il ? Dans mon Codespace et sur GitHub donc il est  visible et récupérable par les autres avec `git pull`.
3. Que se passe-t-il si je supprime mon Codespace après un commit mais sans push ? Le commit est perdu car il n'existait que dans mon Codespace.
## Stash
La commande `git stash` permet de mettre de côté des modifications non commitées (brouillon) pour retrouver un espace de travail propre. Cela permet de changer de branche pour traiter une urgence sans perdre son travail en cours. On récupère ensuite ce travail avec `git stash pop`.