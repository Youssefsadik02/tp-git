Nom, Prénom : SADIK Youssef

## B1-Git - Partie 1 : Création du dépôt et _commits_

- Ouvrir un terminal (terminal _Git Bash_ à privilégier)

- Créer, en ligne de commande, un répertoire `tp-git`
 --> mkdir tp-git

- Se déplacer dans le répertoire
 --> cd tp-git

- Vérifier qu'on est dans le bon répertoire en affichant le chemin du répertoire courant
  --> on utilise la commande 'pwd'

- Initialiser un dépôt Git
 --> git init

- Lister tous les fichiers du répertoire (y compris les fichiers cachés) pour s'assurer que le répertoire `.git` à été créé
 --> ls -a 

- Ouvrir ce répertoire sous VS Code
  --> git config --global editor.core "code -w" ==> pour utiliser Vscode comme editeur 
  --> puis la commande "code ."  en s'assurant d'etre dans le repertoire .git  

- Exécuter `git status` et copier/coller la sortie
   --> On branch master

     No commits yet

     nothing to commit (create/copy files and use "git add" to track)


- Créer le fichier `fichier1.md` avec un contenu quelconque et l'enregistrer (vous pouvez utiliser VS Code pour créer et éditer des fichiers)

  - Attention, il s'agit bien de créer un nouveau fichier, et non un répertoire. Il en sera de même tout au long de ce TP.

- Créer le fichier `fichier2.md` avec un contenu quelconque et l'enregistrer

- Exécuter `git status` et copier/coller la sortie
	On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        fichier1.md
        fichier2.md

nothing added to commit but untracked files present (use "git add" to track)


- Ajouter `fichier1.md` à l'index de Git (zone de _Staging_)
 --> git add fichier1.md

- Exécuter `git status` et copier/coller la sortie
  --> On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   fichier1.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        fichier2.md


- Créer un _commit_ avec pour message : "Ajout de fichier1.md"
 --> git commit -m "ajout du fichier1.md"


- **_VALIDATION PROF01_**

- Exécuter `git status` et copier/coller la sortie
  --> On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        fichier2.md

nothing added to commit but untracked files present (use "git add" to track)

    

- Modifier `fichier1.md` et enregistrer
    --> modification sur VScode


- Exécuter `git status` et copier/coller la sortie
  --> On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   fichier1.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        fichier2.md

no changes added to commit (use "git add" and/or "git commit -a")


- Ajouter `fichier1.md` et `fichier2.md` à la zone de _Staging_
  --> git add fichier1.md fichier2.md

- Créer un _commit_ "Ajout de fichier2.md et modification de fichier1.md"

  --> git commit -m " Ajout de fichier2.md et modification de fichier1.md"


- Exécuter `git status` et copier/coller la sortie
   --> On branch master
nothing to commit, working tree clean

- Copier/coller l'ID des deux premiers _commits_ (utiliser `log`) :
  --> git log

  - ID _commit_ 1 : 3b98ef2b465dcea30f18f67b6950eab0c5e208a6

  - ID _commit_ 2 : c8dd3632fb762824ca5b62c0e5abdae256bb67f7 

- Que signifie qu'un fichier est "_tracked_" ou "_untracked_" ?
   --> tracked signifie que Git suit le fichier
   --> untracked signifie que Git ne suit pas le fichier  

- Pourquoi doit-on passer les fichiers par la zone de _Staging_ (l'index) avant de les committer ?
  --> La zone de staging permet d'ajouter des modifications avant de les commiter, ce qui permet de réviser ces modifications avant de les enregistrer de manière permanente.

- **_VALIDATION PROF02_**
## B1-Git - Partie 2 : Gestion de branches

_Cette partie est à faire sur le même dépôt que la partie précédente. C'est la suite._

- Créer une branche `fonctionnalite1`
   --> git branch fonctionnalite1

- Lister les branches
  --> git branch
  -->  fonctionnalite1
   * master

- Se déplacer sur la branche `fonctionnalite1`
  --> git checkout fonctionnalite1 
  --> Switched to branch 'fonctionnalite1'


- Lister les branches
  --> git branch 
  --> 
* fonctionnalite1
  master


- Que représente l'étoile à côté des noms des branches ?
   -->représente la branche sur laquelle on est.

- Créer un nouveau fichier `fichier3.md`
 --> touch fichier3.md

- Modifier le fichier `fichier2.md`
  --> modification sur VScode

  - Comment utiliser VS Code pour qu'il nous montre les différences entre l'ancienne version de `fichier2.md` et la version courante que l'on vient d'éditer ?
 --> En utilisant l'icone du "source controle" à gauche sur VScode

- Committer ces deux modifications : "Fonctionnalité 1 - première phase"
--> git add fichier2.md 
--> git add fichier3.md
--> git commit -m "fonctionnalité 1 - première phase"
  


- Créer un nouveau fichier `fichier4.md`
 --> touch fichier4.md

- Modifier de nouveau le fichier `fichier2.md`
 --> modif sur Vscode

- Committer ces deux modifications : "Fonctionnalité 1 - terminée"
--> git add fichier2.md fichier4.md
 --> git commit -m "fonctionnalité 1 -terminée"



- **_VALIDATION PROF03_**

- Afficher la liste des fichiers du répertoire
--> ls 
--> fichier1.md  fichier2.md  fichier3.md  fichier4.md

- Se déplacer sur la branche `master`
--> git switch master 

- Afficher la liste des fichiers du répertoire
--> ls 
--> fichier1.md fichier2.md

- Pourquoi les deux sorties sont-elles différentes ? Les fichiers ont-ils disparus ?

--> car chaque branche est une ligne de développement indépendente. les fichiers d'une branche ne sont pas automatiquement présents dans une autre branche. les fichier ne sont pas disparus.

- Créer une nouvelle branche `fonctionnalite2`
--> git branch fonctionnalite2 
--> git checkout fonctionnalite2

  - Cette branche ne va pas avoir toutes les données incluses dans `fonctionnalite1`. Pourquoi ?
--> parcequ'on vient de créer la branche fonctionnalité2 à partir de la branche master

  - Qu'aurait-il fallu faire si on avait souhaité démarrer la branche `fonctionnalite2` en intégrant les modifications récentes de `fonctionnalite1` ?

--> On devait créer la branche fonctionnalité2 d'après la branche fonctionnalité1

- Se déplacer sur la nouvelle branche `fonctionnalite2`
--> git switch fonctionnalite2

- Créer un nouveau fichier `fichier5.md`
--> touch fichier5.md

- Faire un _commit_ intégrant cette ajout : "Ajout fichier5.md"
--> git add fichier5.md
--> git commit -m "Ajout fichier5.md"

--> [fonctionnalite2 07c2dab] Ajout fichier5.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 fichier5.md


- Entrer la commande `git log --oneline --decorate --graph --all` pour visualiser, sur le terminal, le graphe des _commits_ sur toutes les branches

--> git log --oneline --decorate --graph --all

--> * f32710c (HEAD -> fonctionnalite2) Ajout fichier5.md
| * 18f125a (fonctionnalite1) fonctionnalité 1- terminée
| * 9fff35c Fonctionnalité 1- prmière phase
|/
* 9a9cf69 (master) Ajout de fichier2.md et modification de fichier1.md
* e6bdd2b ajout du fichier1.md

  - Noter la « déviation » entre les deux branches, à partir de la branche `master` (schématisée sous forme de traits)
  - l'option `--all` permet de visualiser toutes les branches, pas seulement celle sur laquelle on est:
  - l'option `--oneline` affiche les _commits_ sur une seule ligne
  - l'option `--graph` affiche le log sous forme de graphe
  - (utilisez si besoin les touches haut/bas pour naviguer dans la sortie de cette commande et `Q` pour quitter)

- Installer l'extension VS Code _Git Graph_ et visualiser le graphe actuel des _commits_ à l'aide de cette extension


  - Sur cette représentation, que représente les points ?
--> les commits 

  - Comment voit-on sur quelle branche on est actuellement ?
--> Sur Vscode, en utilisant l'extension Git Graph, la branche qui se met en gras, et qui se met après un cercle non remplie et coloré par la meme couleur de la branche, c'est la branche sur laquelle on est.

- **_VALIDATION PROF04_**

Cette partie est à faire sur le même dépôt que la partie précédente. C'est la suite.

On considère que la branche originale (master ou main) est la branche d'intégration, c'est-à-dire celle qui va contenir l'historique de toutes les modifications développées au fur et à mesure dans les branches annexes

Se déplacer sur la branche master

Noter le changement dans l'onglet Git Graph
On va maintenant intégrer la branche fonctionnalite1, qui est terminée, dans la branche d'intégration (ça s'appelle une fusion, ou un merge) : fusionner avec la branche fonctionnalite1

Noter le changement dans l'onglet Git Graph. Que signifie la mention Fast-forward indiquée par la sortie de la commande ?

--> les branches master et fonctionnalite1 sont reliées.

--> Indique que la fusion entre les deux branches peut être effectuée de manière linéaire sans créer de commit de fusion supplémentaire. Cela se produit lorsque la branche qu'on fusionne est directement en avance de la branche sur laquelle on se trouve, et aucune modification n'a été apportée à cette dernière depuis la création de la branche qu'on fusionne.

On veut maintenant fusionner fonctionnalite2 dans la branche d'intégration (master). Effectuer cette fusion.

--> git merge fonctionnalite2

Noter le changement dans l'onglet Git Graph. Que signifie la mention Merge made by the ... strategy indiquée par la sortie de la commande ?

--> dans l'onglet Git Graph on voit que les deux branches master et fonctionnalite2 partages les mêmes commits. la sortie indique que la fusion des branches à été effectuée en utilisant la stratégie ORT (Ostensibily Recursive's Twin). ORT est utilisé pour améliorer les performances et la gestion des conflits lors des opérationns de fusion.

Quelle est la différence fondamentale avec la fusion précédente ?

--> la différence est que lors de la fusion précédente, la branche master 

Créer une nouvelle branche fonctionnalite3, se déplacer dessus, et modifier le fichier fichier1.md en y ajoutant une ligne de texte. Committer : "Modification fichier1 pour fonctionnalité 3"

Comment utiliser Git Graph pour qu'il nous montre les différences entre l'ancienne version de fichier1.md et la version courante que l'on vient de committer ?

--> En cliquant sur la l'icone de source et controle à gauche pour afficher l'ancienne version à coté de la version actuelle.

Repartir sur master, et modifier fichier1.md en y ajoutant aussi une ligne (différente de celle qu'on a ajoutée sur l'autre branche) ; ajouter à l'index et commit

Tenter de fusionner la branche fonctionnalite3 avec master

Que se passe-t-il et pourquoi ?
--> La fusion a échoué, car il y a un conflit de modification de fichier1 dans les deux branches master et fonctionnalite3

Lancer un git status:

Que doit-on faire si on veut annuler la fusion en cours ? (ne pas lancer la commande)
--> on utilise la commande " git merge --abort " 

On veut résoudre le conflit. Plusieurs possibilités :

Conserver uniquement les modifications faites dans fonctionnalite3
Conserver uniquement les modifications faites dans master
Conserver les deux modifications
Supprimer les deux modifications ou remanier sensiblement le fichier pour les intégrer correctement
Git nous laisse totalement la main et ne va pas essayer d'imposer l'un de ces choix pour nous, ni nous assister dans l'application automatique de l'un d'entre eux : il faut examiner le(s) fichier(s) en conflit et éditer nous-mêmes

Ouvrir le fichier en question sous VS Code

La chaîne <<<<<<<<<< marque le début du conflit
La chaîne >>>>>>>>>> marque la fin du conflit
La chaîne ========== sépare les deux versions
Éditer le fichier pour faire en sorte d'intégrer les deux modifications ; à la fin de l'édition :

Il ne doit plus y avoir de marques quelconques en dehors des ajouts fonctionnels originaux, c'est-à-dire pas de <<<<<<<<<<, ni de mentions de nom de branche, etc. : vous rendez le fichier tel qu'il doit apparaître dans le commit de fusion, avec les conflits résolus manuellement
Sauvegarder
Ajouter les modification à l'index et committer

NB : parfois, plusieurs fichiers sont en conflit ; le processus est identique, il faut juste résoudre les conflits sur tous les fichiers

NB : les conflits de fusion sont fréquents lorsqu'on travaille en collaboration (plusieurs personnes vont travailler sur le même fichier pour remplir deux fonctionnalités différentes)

Les branches créées n'ont plus de raison d'exister

Elles avaient pour but de créer une déviation afin de travailler sur des fonctionnalités individuelles, sans interférer avec le travail des autres, avant de les fusionner dans la branche d'intégration
On va vouloir nettoyer le dépôt en les supprimant
Cela ne va bien sûr pas supprimer tous les commits qui y sont associés
Attention cependant d'éviter en général de supprimer une branche qui n'a pas encore été intégrée à la branche d'intégration, sauf on souhaite vraiment abandonner le développement de cette branche
Ne pas réutiliser une branche qui a déjà été intégrée pour démarrer une nouvelle piste : toujours utiliser une nouvelle branche
Nouvelle tâche ? => nouvelle branche à partir d'un commit de la branche d'intégration (en général le plus récent)
Tâche terminée ? => fusion dans la branche d'intégration et suppression de la branche
Supprimer les trois branches fonctionnalitex (attention : on ne peut pas supprimer une branche sur laquelle on est)
