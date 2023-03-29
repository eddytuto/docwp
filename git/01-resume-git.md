# Résumé des commandes git et github

## Création d'un dépôt local

- Dans l'explorateur pour voir les fichiers caché : **affichage/éléments masqu**és (qu'il faut côcher)
- Le dépôt locat se nomme; **.git**
- Dans visual code sélectionner le dossier du **thème** et avec touche droite le la souris **open in integrated terminal**
- git init (on exécute une seule fois cette commande. Permet de créer le dossier **.git**
- git status (permet de vérifier l'état de notre dépôt:)
  - Des fichiers doivent être indexé si ils apparaissent en rouge
  - en vert ils ont été indexé et on doit faire un commit
  - après avoir fait un commit le dépôt est clair
- git **add --all** ou **git add .**
- git **commit -m "s2c1 on décrit les modification"**
- **git log**
- **git log --oneline**
- **git remote add 4w4 https://github.com/eddytuto/2023-4w4-gr1.git** (créer un alias qui pointe vers votre dépôt github)
- **git branch -m main** (change le nom de la branche master pour main)
- **git branch lab1** (créer la branche «lab1» )
- **git checkout lab1** (pour changer de branche vers «lab1»)
- **git log --oneline** (les branches lab1 et main pointe vers le même commit)
- **git chechout main** (pour activer la branche « main »)
- git push 4w4 main (pousse la branche active «main» vers github dans le dépôt 4w4 vers la branche main)
- git checkout lab1
- git push 4w4 lab1
- git branch lab2
- git checkout lab2
- git push 4w4 lab2 (pousse la branche active lab2 vers 4w4 dans la branche lab2)

### Comment modifier le message d'un dernier commit

La commande pour modifier le message du dernier commit sur Git est:

> git commit --amend -m "Nouveau message de commit"

- Cette commande permet de modifier le dernier message de commit que vous avez effectué. Elle utilise l'option --amend pour modifier le commit existant plutôt que d'en créer un nouveau. Vous pouvez remplacer "Nouveau message de commit" par le nouveau message que vous souhaitez utiliser. Après avoir exécuté cette commande, Git ouvrira votre éditeur de texte par défaut pour vous permettre de modifier le message de commit. Modifiez le message, enregistrez et fermez l'éditeur de texte pour finaliser la modification.
- Notez que si vous avez déjà poussé le commit sur un dépôt distant, vous devrez forcer la poussée du commit modifié en utilisant la commande

> git push --force.
### Références
> https://devconnected.com/how-to-undo-last-git-commit/
