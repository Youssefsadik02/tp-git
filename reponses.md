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
