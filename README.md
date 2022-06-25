# linux-note

Principalement pour enregistrer quelques commandes linux📝

( Cet article sera mis à jour en permanence:smile: )

## cd

Passer au répertoire personnel `~`

```cmd
cd ~
```

Passer au répertoire racine `/`

```cmd
cd /
```

Retour au niveau supérieur

```cmd
cd ..
```

Déplacez le chemin vers le précédent (il est facile de passer rapidement d'un chemin à l'autre :smile:)

```cmd
cd -
```

## man

Manuel d'instruction en ligne ( man page )

```cmd
man ls
```

![alt tag](https://i.imgur.com/3DDi208.png)

Vous pouvez également utiliser

```cmd
ls --help
```

![alt tag](https://i.imgur.com/ZSZjuVC.png)

## pwd

Voir le repertoire actuel

```cmd
pwd
```

## ls

[Youtube Tutorial - Linux 指令教學 - ls](https://youtu.be/3Zy1AWuDUHE)

Liste des fichiers

```cmd
ls -l
```

`-l` Afficher des informations détaillées ( Autorisations de fichiers )。

Cela équivaut également à un accès direct (L 的小寫)

```cmd
ll
```

在 Linux 中，Les fichiers ont tous quatre permissions

* Lisible ( r，Readable )，Utilisez les chiffres 4

* Modifiable ( w，writable )，Utilisez les chiffres 2

* Exécutable ( x，eXecute )，Utilisez les chiffres 1

* Aucune permission ( - )，Utilisez les chiffres 0

Pour être plus claire，Je l'ai organisé en tableaux:yum:

|     Caractère         |  Marque  |
|:---------------------:|:--------:|
|   r (read)            |     4    |
|   w (write)           |     2    |
|  x (execute)          |     1    |
|  - Aucune permission  |     0    |

Comme le montre l'image ci-dessous，

![alt tag](https://i.imgur.com/AzfYBhf.png)

Expliquez ensuite la signification de chaque colonne，

![alt tag](https://i.imgur.com/3TMcAtC.png)

* Colonne 1 (n° 1 sur le schéma), Privilèges d'utilisateur.

Constitué de 10 caractères.

Le premier caractère représente le type de fichier (`-` est le fichier, `d` est le répertoire, `l` est le fichier de liaison)。

Les deuxième, troisième et quatrième caractères indiquent les droits d'accès du propriétaire du fichier.。

Les cinquième, sixième et septième caractères indiquent les droits d'accès des membres du groupe auquel appartient le propriétaire du fichier.。

Les huitième, neuvième et dixième caractères indiquent les droits d'accès pour les autres utilisateurs.。

Prenons un exemple，drwxr-xr-x，

signifie qu'il s'agit d'un répertoire，

Les propriétaires ont des privilèges de lecture, d'écriture et d'exécution.，

Le groupe auquel vous appartenez n'a que des droits de lecture et d'exécution.，

Les autres utilisateurs n'ont que des droits de lecture et d'exécution.。

Pour plus de clarté, je l'ai organisé en un tableau:yum:

|                |  Propriétaire         |Groupe d'appartenance| Autres utilisateurs     |
|----------------|:---------------------:|:-------------------:|:-----------------------:|
|        d       |           rwx         |         r-x         |         r-x             |
| La représentation est un répertoire | Avec des privilèges de lecture, d'écriture et d'exécution | Privilèges de lecture et d'exécution uniquement | Privilèges de lecture et d'exécution uniquement |

Sa note d'autorité est de 755

|  Identité  	| Droits 	|   Note   	|
|:------:	|:----:	|:--------:	|
|  owner 	|  rwx 	| 4+2+1 =7 	|
|  group 	|  r-x 	| 4+0+1 =5 	|
| others 	|  r-x 	| 4+0+1 =5 	|

* Colonne 2 (n° 2 sur le tableau), Nombre de dossiers。

* Colonne 3 (n° 3 sur le plan), propriétaire。

* Colonne 4 (n° 4 sur le tableau), Groupe。

* Colonne 5 (n° 5 sur le tableau), taille du fichier。

* Colonne 6 (n° 6 sur le schéma), heure de création du fichier。

* Colonne 7 (n° 7 sur le tableau), Nom du fichier。

ls Utiliser le triage par date

```cmd
ls -t
```

Liste de fichiers spécifiques (liste de fichiers .py)

```cmd
ls *.py
```

Paramètre `-h` pour afficher la taille du fichier ou du répertoire en unités KB, MB, GB。

```cmd
ls -l -h
```

Afficher tous les fichiers (y compris les fichiers cachés)

```cmd
ls -a
```

Vous pouvez également utiliser

```cmd
ls -al
```

Vous pouvez lister directement le contenu d'un dossier

```cmd
ls Downloads
```

Comme dans home, Lister directement le contenu des téléchargements de Downloads

![alt tag](https://i.imgur.com/Dal7aSn.png)

sort

```cmd
ls -S
```

Ecrire la sortie stdout dans un fichier, vous pouvez utiliser la redirection `>` (non montré à l'écran)

```cmd
ls -lS > file.txt
```

Calculer combien de fichiers se trouvent dans le dossier

```cmd
ls | wc -l
```

## sort

* [Youtube Tutorial - Linux 指令教學 - sort , uniq](https://youtu.be/5G9gRLPBW_U)

Comme son nom l'indique, il s'agit de séquencer.

En supposant qu'il existe un `test.txt` comme suit,

```txt
c 2
a 4
y 33
b 111
e 44
j 3
k 12
```

Par défaut, on prend le début de la liste..

```cmd
❯ sort test.txt
a 4
b 111
c 2
e 44
j 3
k 12
y 33
```

L'inversion peut être réalisée `-r`, `--reverse` inverser le résultat des comparaisons

```cmd
❯ sort -r test.txt
y 33
k 12
j 3
e 44
c 2
b 111
a 4
```

Elle peut également être utilisée avec d'autres commandes, telles que

```cmd
cat test.txt | sort
```

Indiquez les colonnes à trier.

```cmd
❯ sort -n -k 2 test.txt
c 2
j 3
a 4
k 12
y 33
e 44
b 111
```

`-n`, `--numeric-sort` signifie utiliser le tri numérique.

`-k`, `--key=KEYDEF` signifie que le champ est trié. Ceci spécifie le deuxième champ.

En outre, s'il s'agit d'une case vide comme celle ci-dessus, il n'est pas nécessaire de la configurer (car elle est par défaut),

Si votre document d'aujourd'hui se présente comme suit, il est séparé par des virgules,

Vous devez ajouter plus de `-t` pour définir votre séparateur.

`-t`, `--field-separator=SEP` utiliser le SEP au lieu de la transition de non-blanc à blanc.

`test2.txt` comme suit,

```txt
c,2
a,4
y,33
b,111
e,44
j,3
k,12
```

```cmd
❯ sort -n -t , -k 2 test2.txt
c,2
j,3
a,4
k,12
y,33
e,44
b,111
```

Utilisez `,` comme séparateur avec le paramètre `-t`.

## uniq

* [Youtube Tutorial - Linux 指令教學 - sort , uniq](https://youtu.be/5G9gRLPBW_U)

Ceci est utilisé pour trouver (supprimer) les lignes en double.

```cmd
❯ uniq --help
......
Filtrer les lignes adjacentes correspondantes de INPUT (or standard input),
écriture sur la SORTIE (or standard output).
......
Note : 'uniq' ne détecte pas les lignes répétées à moins qu'elles ne soient adjacentes.
Vous pouvez vouloir trier l'entrée d'abord, ou utiliser 'sort -u' sans 'uniq'.
......
```

Veuillez noter que lorsque vous utilisez `uniq`, vous devez d'abord exécuter `sort`.

Comme `uniq' est juste une comparaison de lignes voisines, vous devez d'abord `sort' et ensuite `uniq'.

(Il est également dit dans la description ci-dessus que `uniq' ne détecte pas les lignes dupliquées à moins qu'elles ne soient adjacentes).

L'exemple `test.txt` est le suivant,

```txt
11
33
66
44
55
66
55
11
66
33
```

Si vous exécutez `uniq` sans exécuter `sort` d'abord, vous constaterez que cela ne fonctionne pas,

```cmd
❯ uniq test.txt
11
33
66
44
55
66
55
11
66
33
```

Supprime les lignes dupliquées du fichier,

```cmd
❯ sort test.txt | uniq
11
33
44
55
66
```

Vous pouvez aussi utiliser `sort -u` à la place,

```cmd
❯ sort -u test.txt
11
33
44
55
66
```

`-u`, `--unique` avec -c, vérifier l'ordre strict.

Comptez le nombre de fois qu'une ligne se répète,

```cmd
❯ sort test.txt | uniq -c
      2 11
      2 33
      1 44
      2 55
      3 66
```

`-c', `--compte' les lignes de préfixe par le nombre d'occurrences.

Si vous avez des lignes vides, vous pouvez ajouter la commande sed pour les supprimer (exemple ci-dessous)

```cmd
sort test.txt | sed '/^$/d' | uniq -c
```

Sortir toutes les lignes dupliquées,

```cmd
❯ sort test.txt | uniq -D
11
11
33
33
55
55
66
66
66
```

`-D` print all duplicate lines

Seules les lignes en double sont éditées (affichées une seule fois),

```cmd
❯ sort test.txt | uniq -d
11
33
55
66
```

`-d`, `--repeated` n'imprime que les lignes en double, une pour chaque groupe

Ne sortir que les lignes qui ne sont pas répétées,

```cmd
❯ sort test.txt | uniq -u
44
```

`-u`, `--unique` n'imprime que les lignes uniques

## cut

Utilisé pour capturer certains des caractères.

Exemple `test.txt`

```text
123
234
567
890
```

Récupérer le 2ème ou 3ème caractère

```cmd
❯ cut -c 2-3 test.txt
23
34
67
90
```

`-c`, `--characters=LIST` ne sélectionne que ces caractères

Récupérer l'avant-dernier caractère

```cmd
❯ cut -c 2- test.txt
23
34
67
90
```

Récupérer les 1er et 3ème caractères

```cmd
❯ cut -c 1,3 test.txt
13
24
57
80
```

Exclure le 2ème caractère

```cmd
❯ cut -c 2 test.txt --complement
13
24
57
80
```

`--complement` complète l'ensemble des octets, caractères ou champs sélectionnés.

(Complémentaire à d'autres caractères, c'est-à-dire excluant le caractère spécifié)

## tee

Écrire également la sortie stdout dans un fichier et l'afficher à l'écran (écraser directement file.txt)

```cmd
ls | tee file.txt
```

Écrit également la sortie stdout dans un fichier et l'affiche à l'écran (en annexe de file.txt)

```cmd
ls | tee -a file.txt
```

##  touch

Très souvent utilisé pour créer des fichiers vides

```cmd
touch file.py
```

Il est également possible de créer plusieurs fichiers vides de cette façon ( `file1.py` ~ `file1.py`)

```cmd
touch file{1..10}.py
```

## su

Changement d'utilisateur

```cmd
su <username>
```

## sudo

Ajout d'un nouvel utilisateur

```cmd
sudo useradd <username>
```

Définir le mot de passe de l'utilisateur

```cmd
sudo passwd <username>
```

Suppression de l'utilisateur

```cmd
sudo userdel <username>
```

Ajout d'un nouveau groupe

```cmd
sudo groupadd <groupname>
```

Suppression du groupe

```cmd
sudo groupdel <groupname>
```

Ajouter un utilisateur au groupe

```cmd
sudo usermod -g <groupname> <username>
```

Afficher tous les utilisateurs

```cmd
sudo cat /etc/passwd
```

Afficher tous les groupes

```cmd
sudo cat /etc/group
```

Je ne sais pas si vous avez ce problème, mais c'est pénible de devoir taper son mot de passe à chaque fois.:expressionless:

Voici une façon de le faire, mais attention, avec la commande `-S'.

```text
L'option -S (stdin) permet à sudo de lire le mot de passe depuis l'entrée
l'entrée standard au lieu du périphérique terminal.
```

Pour faire simple, tapez d'abord votre propre mot de passe pour ne pas avoir à le retaper, voici un exemple

```cmd
echo YourPwd | sudo -S groupadd <groupname>
```

## chmod

[Youtube Tutorial - Linux 教學 - chmod](https://youtu.be/qwk4Pzgtf2I)

chmod est une abréviation de change mode.

Modifier les autorisations de fichiers

```cmd
chmod XXX filename
```

Par exemple, définissez l'autorisation à rw-rw-r--.

|  Identité | Droits 	|   Note   	|
|:------:	|:----:	|:--------:	|
|  owner 	|  rw- 	| 4+2+0 =6 	|
|  group 	|  rw- 	| 4+2+0 =6 	|
|  others 	|  r-- 	| 4+0+0 =4 	|

```cmd
chmod 664 README.md
```

Commandes couramment utilisées pour modifier les permissions

```cmd
# Seul le propriétaire a un accès en lecture et en écriture
sudo chmod 600 ×××
```

```cmd
# Le propriétaire a un accès en lecture et en écriture, le groupe et les autres ont un accès en lecture seulement.
sudo chmod 644 ×××
```

```cmd
# Le propriétaire a des privilèges de lecture, d'écriture et d'exécution.
sudo chmod 700 ×××
```

```cmd
# Propriétaires : le propriétaire, le groupe, les autres ont un accès en lecture et en écriture.
sudo chmod 666 ×××
```

```cmd
# Les propriétaires, le groupe et les autres ont tous des droits de lecture, d'écriture et d'exécution.
sudo chmod -R 777 xxx
```

`-r` `-R` représente un retour en arrière récursif (tous les fichiers sous le répertoire contiennent des sous-répertoires qui seront modifiés).

Une autre façon de modifier les autorisations est d'utiliser des symboles.

Avant de l'introduire, consultez le tableau ci-dessous :wink:

|       | u = user  |          |             |                    |
|-------|-----------|----------|-------------|--------------------|
|       | g = group | + (增加) | r = read    |                    |
| chmod |           | - (移除) | w = write   | Fichier ou dossier |
|       | o = other | = (設定) | x = execute |                    |
|       | a = all   |          |             |                    |

Par exemple, définissez la permission hello à rw-rw-r--.

|  Propriétaire(u) | Groupe(g) |   Autres utilisateurs(o) |
|:-------:  	|:-------:	|:----------------------:   |
|  rw-      	|  rw- 	| r--                   	|

```cmd
chmod ug=rw,o=r hello
```

![alt tag](https://i.imgur.com/QgNuNel.png)

Comme autre exemple, définissez la permission hello à rwxr-xr--.

```cmd
chmod u=rwx,g=rx,o=r hello
```

![alt tag](https://i.imgur.com/WlX8wPL.png)

Ensuite, supposons que je veuille ajouter les permissions de l'exécutable (x) (pour toutes les personnes et tous les groupes)

```cmd
chmod a+x hello
```

![alt tag](https://i.imgur.com/KLiwPXX.png)

Supprimer tous les privilèges d'exécution (x)

```cmd
chmod a-x hello
```

Vous remarquerez que les privilèges exécutables (x) de chacun ont disparu.

![alt tag](https://i.imgur.com/O8gh3Is.png)

Je suis sûr qu'après cette série d'exercices, vous comprendrez que

Si vous ne comprenez pas, relisez-le plusieurs fois.:satisfied:

## chown

Modifier les propriétaires et les groupes de fichiers ou de répertoires。

修改檔案或目錄的擁有者

```cmd
# Changez le propriétaire de README.md (fichier) en twtrubiks (utilisateur).
chown twtrubiks README.md
```

Groupes qui modifient des fichiers ou des répertoires

```cmd
# Changez le groupe de README.md (fichier) en twtrubiksgroup (groupe).
chown :twtrubiksgroup README.md
```

Changer le propriétaire et le groupe d'un fichier ou d'un répertoire en même temps

```cmd
# 將 README.md ( 檔案 ) 的擁有者改為 twtrubiks ( 使用者 ) 以及
# 將 README.md ( 檔案 ) 的群組改為 twtrubiksgroup ( 群組 )
chown twtrubiks:twtrubiksgroup README.md
```

## ln

[Youtube Tutorial - Linux 指令教學 - ln (Symbolic Link)](https://youtu.be/jdZsO2GAf2I)

Il en existe deux types,  hard link , et Symbolic link ( soft link ),

Première introduction hard link，Note，hard link non autorisé pour les répertoires。

```cmd
ln /home/twtrubiks/Downloads/odoo-git/README.md
```

![alt tag](https://i.imgur.com/ioJXBRw.png)

La fonction de hard link signifie que le fichier sera conservé, quel que soit le fichier supprimé. à moins que vous ne supprimiez aussi le dernier fichier.

En d'autres termes, il n'y a pas de différence réelle entre hard link d'un fichier et le fichier original.

Les liens physiques (hard link) n'autorisent pas les dossiers, seulement les fichiers.

Un lien symbolique, également connu sous le nom de soft link, est un raccourci similaire à celui de Windows.:smile:

```cmd
ln -s /home/twtrubiks/Downloads/odoo-git/ dir-link
```

![alt tag](https://i.imgur.com/JGhlQZd.png)

Lorsque le corps d'un fichier est supprimé, son lien symbolique ne sera pas en mesure de lire le fichier.

Le lien symbolique d'un fichier et le corps du fichier sont deux choses différentes.

Le lien symbolique permet pour les fichiers et les dossiers.

## zip unzip

zip 3.0 enregistre déjà les permissions et la propriété des fichiers.

```cmd
sudo apt-get install zip unzip
```

zip

```cmd
zip -r <nom du fichier après compression> <fichier compressé>.
zip -r file.zip file
```

unzip

```cmd
dézipper <fichier dézippé> -d <dossier cible dézippé>
unzip file.zip -d zip_extract
```

Si vous souhaitez décompresser directement dans le répertoire courant, vous pouvez utiliser l'option `. `

```cmd
unzip file.zip -d .
```

## tar

tar **會**保存檔案的 permissions and ownership.

Compression `.tar` format

```cmd
tar cvf filename.tar source-folder
```

Décompression `.tar` format

```cmd
tar xvf filename.tar
```

## unrar

```cmd
sudo apt-get install unrar
```

Extraire filename.rar au fond du répertoire

```cmd
unrar e filename.rar
```

Lister les données pour filename.rar

```cmd
unrar l filename.rar
```

測試 filename.rar 是否完整且正確

```cmd
unrar t filename.rar
```

## wget

Outils de téléchargement

```cmd
sudo apt-get install wget
```

Téléchargez l'URL de commande

```cmd
wget http://ftp.gnu.org/gnu/wget/wget-1.20.3.tar.gz
```

Spécifiez le nom du fichier, ajoutez `-O`.

```cmd
wget -O wget.tar.gz http://ftp.gnu.org/gnu/wget/wget-1.20.3.tar.gz
```

## scp

Le nom complet est Securely Copy,

Cette méthode convient au transfert de fichiers entre Linux et Linux, ainsi qu'entre Linux et Windows.

En supposant que l'ip de Linux est 192.168.56.101, vérifiez la commande ip comme suit

```cmd
ip addr show
```

![alt tag](https://i.imgur.com/AlAeRoD.png)

Confirmez que openssh-server est installé

```cmd
sudo apt-get install openssh-server
```

Utilisez `ssh localhsot` pour tester

![alt tag](https://i.imgur.com/nYo5NNn.png)

Après que tout soit en ordre.

Envoyez le fichier de Windows à Linux (ip 192.168.56.101).

Exécutez la commande suivante à partir de cmd sous Windows.

```cmd
scp -rp fichier utilisateur@ip:chemin cible de linux
```

`-r` signifie récursif.

`-p` 代表 保存原始檔案的內容 (Preserves modification).

```cmd
scp -rp file twtrubiks@192.168.56.101:/home/twtrubiks
```

![alt tag](https://i.imgur.com/0nBrt00.png)

Ensuite, récupérez les fichiers de Linux vers Windows.

```cmd
scp -P 22 linux user@ip:target path Emplacement de destination à stocker
```

`-P` représente le port (hôte distant) qui est explicitement spécifié.

```cmd
scp -P 22 twtrubiks@192.168.56.101:/home/twtrubiks/linux_file.md .
```

`. ` représente le chemin actuel (d'autres chemins peuvent également être spécifiés).

![alt tag](https://i.imgur.com/aMnNlGI.png)

Il en va de même pour les transferts entre Linux:smile:

## mv

[Youtube Tutorial - Linux 指令教學 - mv](https://youtu.be/VhyzaEaGnL8)

déplacer (renommer) des fichiers, **déplacer des fichiers** ou **renommer des fichiers**.

Modifier le nom d'un dossier ou d'un fichier

```cmd
mv folder folder-new
mv README.md README_MV.md
```

Déplacement de fichiers

```cmd
mv README.md /examples
```

```cmd
mv file.md example/
```

D'autres paramètres sont décrits (les paramètres peuvent être utilisés en combinaison).

En mode interactif, le CLI vous demandera si vous écrasez des fichiers.

```cmd
mv -i source_file path_to_destination/
```

Mise à jour uniquement des fichiers dont les dossiers source et destination sont différents

```cmd
mv -u source_file path_to_destination/
```

## rm

[Youtube Tutorial - Linux 指令教學 - rm](https://youtu.be/JqKjBZMXn_I)

Supprimer le fichier

```cmd
rm file.md
```

Supprimer le dossier

```cmd
rm -rf mydir
```

`-r` signifie utiliser la suppression récursive récursive. (tous les fichiers du répertoire seront supprimés)

`-f` signifie suppression obligatoire (aucun avertissement ne s'affiche).

ou en utilisant la commande rmdir, le fichier

```cmd
rmdir mydir_name
```

Toutefois, veuillez noter que le dossier supprimé doit être vide, sinon il ne sera pas supprimé.

Supprimer le nom du sous-fichier spécifique.

```cmd
rm -f *.zip
```

Cela est également possible

```cmd
rm -f *demo.zip
```

## cp

[Youtube Tutorial - Linux 指令教學 - cp](https://youtu.be/ORl0YUGY728)

Dossiers de reproduction (copie)

```cmd
cp -r path_to_source/ path_to_destination/
```

`-r` `-R` signifie diffusion récursive.

Si le hemin_vers_destination n'existe pas, il sera créé automatiquement ;

S'il est présent, utilisez-le directement.

Je veux juste copier le contenu entier du fond du dossier.

```cmd
cp -r dir_1/. dir_2
cp -r dir_1/. .
```

`. ` représente ce qui se trouve dans le dossier et peut également représenter l'endroit où il se trouve actuellement.

Parfois, vous voulez sauvegarder les permissions actuelles lors de la copie, alors vous ajoutez `-p'.

```cmd
cp -r --preserve=all path_to_source/ path_to_destination/
```

`-p` `--preserver` signifie copier ensemble l'autorité actuelle et le propriétaire.

D'autres paramètres sont décrits (les paramètres peuvent être utilisés en combinaison).

En mode interactif, le CLI vous demandera si vous écrasez des fichiers.

```cmd
cp -i source_file path_to_destination/
```

Pas de questions , Direct écrasement de fichiers

```cmd
cp -n source_file path_to_destination/
```

Mise à jour uniquement des fichiers dont les dossiers source et destination sont différents

```cmd
cp -u source_file path_to_destination/
```

Imprimer l'information

```cmd
cp -v source_file path_to_destination/
```

## find

查詢檔案

Trouver un fichier ou un dossier

```cmd
sudo find / -name "dir-name"
sudo find / -name "file-name"
sudo find / -name "*.conf"
```

Recherchez le fichier README.md dans le répertoire courant.

```cmd
find . -name README.md
```

## source

La commande source est généralement utilisée lorsque vous venez de modifier un fichier d'initialisation, afin qu'il prenne effet immédiatement sans avoir à redémarrer (ou à se déconnecter et se reconnecter),

Voici quelques exemples,

```cmd
source demo.sh
```

Lisez-le dans le shell actuel, exécutez demo.sh, et demo.sh **doit** avoir l'autorisation d'exécuter.

(Le privilège d'exécution correspond à `chmod +x demo.sh`)

La directive source peut également être abrégée en `. `

```cmd
. demo.sh
```

## sh or bash

Lorsqu'il est exécuté avec `sh` ou `bash`, **pas besoin** d'avoir les privilèges d'exécution.

(Le privilège d'exécution correspond à `chmod +x demo.sh`)

```cmd
sh demo.sh
bash demo.sh
```

## ./

Utilisez `. /` à exécuter, **exige** la permission d'exécuter.

(Le privilège d'exécution correspond à `chmod +x demo.sh`)

Lorsque vous exécutez

```cmd
./demo.sh

chmod +x demo.sh
./demo.sh
```

Vous verrez un message comme `bash : . /demo.sh : Permission refusée`,

修正方法如下,

```cmd
chmod +x demo.sh
./demo.sh
```

## where

Trouvez un chemin.

Par exemple, trouvez le chemin d'accès à python3

```cmd
where python3
which python3
whereis python3
```

## tail

Afficher les dernières lignes du fichier

```cmd
tail README.md
```

Afficher plusieurs fichiers à la fois

```cmd
tail README_1.md README_2.md
```

Spécifier pour afficher les N dernières lignes du fichier

```cmd
tail -n 5 README.md
```

```cmd
tail README.md -n 5
```

Affichage continu des mises à jour, généralement sur le serveur ou en regardant les journaux.

```cmd
tail -f README.md
```

## head

S'il y a une queue, il doit y avoir une tête.:smile:

```cmd
head text.py
```

Les 10 premières lignes d'informations sont affichées par défaut.

Vous pouvez spécifier que les `n` premières lignes doivent être affichées à l'aide de la commande `-n`.

```cmd
head -n 3 text.py
```

## file

Vérifier le type de fichier

```cmd
file README.md
```

## cat

Afficher le contenu du fichier sur le terminal

```cmd
cat README.md
```

Montrer les lignes

```cmd
cat -n README.md
```

cat peut également être écrit dans un fichier

```cmd
cat <<EOT >> hello_4.txt
line 1
line 2
line 3
EOT
```

## clear

effacer l'écran du terminal ， Les touches de raccourci sont Ctrl+L

```cmd
clear
```

## grep

```cmd
# Format
grep match_pattern file_name
```

```cmd
# Format
grep "search name" README.md
```

Vous pouvez également rechercher plusieurs fichiers à la fois

```cmd
grep "name" README_1.md README_2.md
```

Vous pouvez également utiliser le caractère universel `*`.

```cmd
grep "print" *.py
```

Exclusion d'un caractère

```cmd
grep -v "match_pattern" README.md

```

`-v`, `--invert-match` select non-matching lines

Rechercher le contenu du répertoire courant

```cmd
grep -r "search name" .
```

case insensitive case (Non sensible à la casse)

```cmd
grep -i "name" README_1.md
```

Montrer les lignes

```cmd
grep -n "name" README_1.md
```

Il doit être entièrement conforme à la limite `:80` avant d'être récupéré.

```cmd
grep -w ':80' README_1.md
```

`-w`, `--word-regexp` ne comparent que des mots entiers.

## sed

Cette commande vous permet de rechercher, remplacer et supprimer rapidement du texte,

sed est principalement destiné au traitement **ligne**, et alors ce n'est pas le fichier original qui est traité, mais le fichier copié.

Langue

```cmd
sed -i '/Chaînes de caractères correspondantes/d' textfile
```

Ajoutez ceci à votre fichier texte, sinon il n'apparaîtra que dans le terminal.

刪除 empty lines

```cmd
sed -i '/^$/d' textfile
```

Supprimer les lignes avec le numéro 7

```cmd
sed -i '/7/d' textfile
```

Supprimer les lignes 1 à 5

```cmd
sed -i '1,5d' textfile
```

Supprimer toutes les lignes de hello1 à hello2

```cmd
sed -i '/hello1/, /hello2/d' textfile
```

Langue de substitution

```cmd
sed -i 's/matching string/alternate string' fichier texte
```

Remplacez le premier a qui apparaît dans chaque ligne par A

```cmd
sed -i 's/a/A' textfile
```

Remplacer toutes les occurrences de a dans chaque ligne par A

```cmd
sed -i 's/a/A/g' file
```

`g` signifie remplacer toutes les chaînes de caractères correspondantes.

Imprimer seulement les lignes avec `test` dans elles

```cmd
sed -n '/test/p' test.txt
```

`-n`, `--quiet`, `--silent` suppriment l'impression automatique de l'espace des motifs.

`p` Print the current pattern space.

sed peut également imprimer un nombre spécifié de lignes d'un fichier,

```cmd
❯ cat test.txt
1
2
3
4
5
6
```

Afficher un nombre spécifique de lignes, afficher la ligne 5

```cmd
❯ sed -n 5p test.txt
5
```

Afficher la ligne 3 et la ligne 5

```cmd
❯ sed -n -e 3p -e 5p test.txt
3
5
```

`-e` script, `--expression=script`

ajouter le script aux commandes à exécuter
Afficher les lignes 3 à 5

```cmd
❯ sed -n 3,5p test.txt
3
4
5
```

Affichage des lignes 1 à 3, et de la ligne 5

```cmd
❯ sed -n -e 1,3p -e 5p test.txt
1
2
3
5
```

## awk

Cette commande est un outil d'analyse de texte très puissant

Supposons qu'aujourd'hui nous ayons la production suivante

![alt tag](https://i.imgur.com/GhPq6sZ.png)

Colonnes de sortie 2,3,5,9

```cmd
ll | awk '{print $2,$3,$5,$9}'
```

![alt tag](https://i.imgur.com/o1exYCq.png)

Si vous trouvez cela moche, vous pouvez utiliser printf pour la mise en page.

```cmd
ll | awk '{printf "%-5s %-5s %-5s %-5s\n", $2,$3,$5,$9}'
```

![alt tag](https://i.imgur.com/9RQj28o.png)

Essayez ensuite de filtrer les données,

Retirez ceux dont le score pondéré (colonne 2) est de 2 et la colonne 3 de twtrubiks.

```cmd
ll | awk '$2 == "2" && $3 == "twtrubiks" {print $0}'
```

`$0` représente tout le contenu de la ligne.

![alt tag](https://i.imgur.com/Il9jGFp.png)

Des statistiques sont également disponibles,

Additionner les scores des notes pondérées (colonne 2) (total exclu)

Exclure la première colonne de la chaîne totale,

my_sum est la variable que nous avons définie.

```cmd
ll | awk '$1 != "total" {my_sum+=$2} END{print my_sum}'
```

![alt tag](https://i.imgur.com/o3yXZnT.png)

Vous pouvez également écrire si logique,

Filtrez ceux dont le score pondéré (colonne 2) est de 3,

Ensuite, imprimez le numéro de la ligne en cours, et mettez le nom du fichier en majuscules dans la colonne 9.

```cmd
ll | awk '{if ($2 == "3") print NR, toupper($9)}'
```

`NR` numéro d'enregistrement actuel dans le flux d'entrée total.

![alt tag](https://i.imgur.com/dzlbMAA.png)

`NF` nombre de champs dans l'enregistrement courant.

Exemple `test.txt`

```cmd
❯ cat test.txt
-rw-rw-r-- 1 twtrubiks twtrubiks 5  4月  2 20:08 a.py
```

Quantité actuelle du champ,

```cmd
❯ cat test.txt | awk '{print NF}'
9
```

Le dernier champ,

```cmd
❯ cat test.txt | awk '{print $NF}'
a.py
```

Afficher le premier champ,

```cmd
❯ cat test.txt | awk '{print $1F}'
-rw-rw-r--
```

## mkdir

Créer un dossier

```cmd
mkdir -p dir1/dir2
```

`-p` `--parents` signifie que le répertoire de niveau supérieur est créé automatiquement et qu'aucune erreur ne se produit si le répertoire existe déjà.

## kill

Arrêt forcé de l'exécution du programme.

Vous devez d'abord trouver le PID du programme, en utilisant la méthode suivante,

```cmd
kill -9 PID
```

`-9` 立刻強制停止程式執行

## killall

Une différence entre killall et kill est que vous pouvez utiliser le nom du programme,

Il n'est pas nécessaire de trouver d'abord le PID du programme,

Par exemple, si vous voulez forcer le vlc à s'arrêter

```cmd
killall vlc
```

## history

Instructions pour la saisie historique

```cmd
history
```

```cmd
history | less
```

![alt tag](https://i.imgur.com/0YKqS3Y.png)

Supposons que je ne veuille pas taper une commande aujourd'hui, je peux simplement taper ` ! `+ numéro et la commande sera exécutée automatiquement.

```cmd
!1848
```

Afficher à nouveau la dernière commande saisie (sudo est recommandé)

```cmd
!!
```

Egalement disponible avec grep,

Si je veux trouver l'historique des commandes entrées dans `git`, alors je peux utiliser la commande suivante

```cmd
history | grep git
```

Si je ne veux pas les montrer tous en même temps, je peux les mélanger et en réduire le nombre.

```cmd
history | grep git | less
```

## echo

Imprime la valeur de l'interpréteur de commandes dans l'interpréteur de commandes.

configuration EDITOR

```cmd
export EDITOR=vim
```

Voir l'actuelle EDITOR，

```cmd
echo $EDITOR
```

Affiche le shell actuel.

```cmd
echo $SHELL
```

echo peut également être écrit dans un fichier.

Méthode 1

```cmd
echo "line 1" >> hello_1.txt
```

Méthode 2 (écrire en plusieurs lignes)

```cmd
echo "line 1
line 2" >> hello_2.txt
```

Méthode 3 (écrire en plusieurs lignes)

```cmd
{
    echo 'line1;'
    echo 'line2;'
} >> hello_3.txt
```

## du

[Youtube Tutorial - Linux 指令教學 - du(Disk Usage)](https://youtu.be/JZZoJnasnHE)

La commande du est une abréviation de Disk Usage,

Avant de commencer avec du, regardons un exemple,

Utilisez `ls -l -h` pour voir le dossier debian

![alt tag](https://i.imgur.com/lXgxQop.png)

Mais si vous allez dans le dossier, vous verrez qu'il fait 17 Go,

Mais pourquoi n'est-il que de 4 Ko lorsqu'il est vu à l'extérieur du dossier ?:question:

![alt tag](https://i.imgur.com/eOTKWJj.png)

La raison en est que `ls -l -h` n'affiche pas la taille réelle du dossier, mais seulement les méta-informations,

Donc, si vous voulez voir la taille réelle, une meilleure façon est d'utiliser la commande `du' qui est décrite ci-dessous:smile:

Afficher la description de la commande du

```cmd
du --help
```

![alt tag](https://i.imgur.com/IQLpqnC.png)

```cmd
-s, --summarize       afficher seulement un total pour chaque argument
                      (Equivalent to -d 0)

-h, --human-readable  les tailles d'impression dans un format lisible par l'homme (par exemple, 1K 234M 2G)
    --inodes          list inode usage information instead of block usage

-c, --total           produire un total général

-d, --max-depth=N     affiche le total pour un répertoire (ou un fichier, avec --all)
                      only if it is N or fewer levels below the command
                      line argument;  --max-depth=0 is the same as --summarize


-a, --all             write counts for all files, not just directories
    --apparent-size   print apparent sizes, rather than disk usage; although
                      the apparent size is usually smaller, it may be
                      larger due to holes in ('sparse') files, internal
                      fragmentation, indirect blocks, and the like
```

以下兩個指令功能是相同的

```cmd
du -sh *
du --summarize --human-readable *
```

En utilisant l'exemple que nous venons de montrer, vous pouvez voir la taille réelle du dossier sur l'extérieur du dossier.

![alt tag](https://i.imgur.com/hHjxXDx.png)

Il peut aussi être utilisé avec `-d`, le nombre de niveaux dans le dossier, comme vous le verrez dans l'exemple suivant

```cmd
du -d 2 -h
```

![alt tag](https://i.imgur.com/NdbqvSz.png)

## truncate

[Youtube Tutorial - Linux 指令教學 - truncate](https://youtu.be/w2pwD1AOhPI)

Shrink or extend the size of each FILE to the specified size.

La commande truncate peut réduire ou augmenter la taille d'un fichier.

Avant de commencer avec cette commande, examinons le contexte dans lequel elle est applicable:smile:

Parfois, nous pouvons souhaiter ramener un fichier à une taille de 0, c'est-à-dire supprimer tout le contenu du fichier,

Mais pour conserver le fichier, c'est le bon moment pour utiliser cette commande:smirk:

Vous pouvez alors me demander pourquoi je ne supprime pas simplement le fichier et n'en crée pas un identique.:question:

La raison en est simple : dans le monde linux, les fichiers ont des permissions, vous devez donc faire attention aux fichiers nouvellement créés.

si le fichier sort avec exactement les mêmes permissions que le précédent (ce qui pourrait conduire à des erreurs dans le cas contraire), c'est donc relativement simple

La façon de procéder serait d'utiliser la commande truncate, qui n'efface que le contenu (taille du fichier 0),

Le reste est resté dans son état d'origine.

Afficher la description de la commande truncate,

```cmd
truncate --help
```

![alt tag](https://i.imgur.com/rOXR79N.png)

```cmd
Mandatory arguments to long options are mandatory for short options too.
-c, --no-create        do not create any files
-o, --io-blocks        treat SIZE as number of IO blocks instead of bytes
-r, --reference=RFILE  base size on RFILE
-s, --size=SIZE        set or adjust the file size by SIZE bytes
    --help     display this help and exit
    --version  output version information and exit

SIZE may also be prefixed by one of the following modifying characters:
'+' extend by, '-' reduce by, '<' at most, '>' at least,
'/' round down to multiple of, '%' round up to multiple of.
```

Ceci est illustré par l'exemple suivant,

Supposons qu'il existe un fichier `demo.txt` (comme suit)

![alt tag](https://i.imgur.com/nWoxmhn.png)

使用 truncate 將 `demo.txt` 放大到 1M,

```cmd
truncate -s 1M demo.txt
```

![alt tag](https://i.imgur.com/jeZ6Rkp.png)

注意 `du -ah` 是顯示 apparent sizes (不是 disk usage ), 所以大小不會改變.

如果你去打開 `demo.txt`, 你會發現被塞了很多東西, 因為大小要變成 1M:smile:

![alt tag](https://i.imgur.com/mgQNkNn.png)

相反的, 現在使用 truncate 將 `demo.txt` 縮小到 0,

![alt tag](https://i.imgur.com/9czKNL5.png)

如果你去打開 `demo.txt`, 你會發現裡面的資料都消失了.

![alt tag](https://i.imgur.com/vmLwz96.png)

truncate 這個指令就非常適合去清除 log, 將 log 大小歸 0, 其餘保持原樣.

清空所有日誌文件

```cmd
sudo truncate -s 0 /var/log/**/*.log
```

## ps

ps 為 Process Status 的縮寫.

列出目前 shell 底下正在執行的 processes

```cmd
ps
```

列出全部的 processes

```cmd
ps -A
```

`-A`, `-e` all processes

使用 BSD format 列出全部的 processes

```cmd
ps aux
```

`a` all with tty, including other users
`x` processes without controlling ttys
`u` user-oriented format

搭配 grep 找出對應的 PS

```cmd
ps aux | grep "postgres -c"
```

使用 PID 找出對應的 PS

```cmd
ps -o pid,rss,vsz,sz,comm -p PID
```

`RSS` 這個值和 `top` command 中的 `RES` 是相同的,

都可以當成是實體上到底佔用了多少記憶體.

`-o`, `o`, `--format <format>` user-defined format.

`-p`, `p`, `--pid <PID>` process id

## 不用密碼遠端登入 Linux

### 方法一

先確認 Linux 上有 `.ssh` 資料夾，如果沒有，

請使用以下指令建立 ( 以及權限 )，

```cmd
mkdir -p ~/.ssh
chmod 700 ~/.ssh
```

每次遠端登入 Linux 都需要密碼很麻煩，有沒有可以透過其他的方式不要輸入密碼:question:

有，先在本機電腦使用 `ssh-keygen` 產生金鑰

```cmd
ssh-keygen
```

接著你會有兩把 key ,

id_rsa.pub：公開金鑰（public key）: 要放在遠端的 Linux 伺服器上。

id_rsa：私密金鑰（private key）: 自己保護好，等同於你的 Linux 密碼。

先把自己本機 `id_rsa.pub` 傳到遠端的 Linux server 上，

接著在 Linux 上執行以下指令

( 把公開金鑰放到 `~/.ssh/authorized_keys` )

```cmd
cat id_rsa.pub >> ~/.ssh/authorized_keys
```

讓我們來測試看看吧:smile:

`ssh twtrubiks@192.168.56.101`

![alt tag](https://i.imgur.com/97ndrP8.png)

不用輸入密碼就可以登入了:thumbsup:

### 方法二

也可以透過 `ssh-copy-id` 來完成,

```cmd
ssh-copy-id -i ~/.ssh/id_rsa.pub twtrubiks@192.168.56.101
```

![alt tag](https://i.imgur.com/eR5TIJ3.png)

其實不管是方法一還是方法二, 都只是把 key 加入 `/home/<user>/.ssh`

裡的 `authorized_keys` 而已:smile:

![alt tag](https://i.imgur.com/j4BRI1J.png)

## root 使用者登入遠端 Linux

注意, 通常不會這樣做:exclamation:

雖然這個方法可以比較危險，但我還是說明一下:joy:

先設定 root 密碼，執行以下指令

```cmd
sudo passwd root
```
![alt tag](https://i.imgur.com/dsSrBJX.png)

再使用 `su -` 測試 root 密碼

![alt tag](https://i.imgur.com/nmU9cgk.png)

測試完成後，再執行 `ssh root@192.168.56.101`

![alt tag](https://i.imgur.com/BF4JWnO.png)

你會發現一直出現 Permission denied, please try again.

這時候要到 Linux 上修改 root 的 ssh 設定，

```cmd
sudo vim /etc/ssh/sshd_config
```

找到 PermitRootLogin without-password

![alt tag](https://i.imgur.com/NO85xui.png)

修改成 PermitRootLogin yes

![alt tag](https://i.imgur.com/xpyfpwW.png)

最後記得一定要重新啟動 sshd 讓它生效 (或是重開機)

```cmd
systemctl restart sshd
```

成功使用 root 登入了:satisfied:

![alt tag](https://i.imgur.com/Au4wt32.png)

## 正確保護 server

比較安全的作法通常是關閉 `PermitRootLogin` 以及 `PasswordAuthentication`,

然後只啟用 `PubkeyAuthentication` 的方式, 但這邊要注意, 一定要把你的 key 放到

server 上, 否則如果設定完不小心退出, 就很麻煩:expressionless:

( 因為不能用密碼登入, 又忘記將 key 放到 server 中 )

修改

```cmd
sudo vim /etc/ssh/sshd_config
```

禁止 root 登入, 將 `PermitRootLogin` 設為 `no`,

![alt tag](https://i.imgur.com/W6KBiXS.png)

禁止使用 password 登入, 將 `PasswordAuthentication` 設為 `no`,

![alt tag](https://i.imgur.com/L9WPRq5.png)

允許 `PubkeyAuthentication`, 設為 `yes`

![alt tag](https://i.imgur.com/iYyaAQ8.png)

補充, 還有一種是使用 PAM Authentication `UsePAM` ( AWS 就是使用這種方式 )

![alt tag](https://i.imgur.com/g3MdnKC.png)

如同說明, 如果希望只使用 PAM Authentication, 也可以把 `ChallengeResponseAuthentication` 設為 `no`.

最後記得重新啟動 sshd 讓它生效 (或是重開機)

```cmd
systemctl restart sshd
```

## 其他資訊

系統訊息

```cmd
uname -a
```

查看 cpu

```cmd
cat /proc/cpuinfo
```

查看全部的 ram 大小

```cmd
grep MemTotal /proc/meminfo
```

查看可用的 ram

```cmd
grep MemFree /proc/meminfo
```

也可以使用

```cmd
free -m
```

查看硬碟空間 ( disk free space, Human Readable )

```cmd
df -h
```

所有硬碟的訊息 ( List Drives and Mounts )

```cmd
lsblk
```

顯示所有裝置設備的資訊 ,UUID

```cmd
blkid
```

![alt tag](https://i.imgur.com/8a6V7fq.png)

目前硬碟 mount 狀態 (開機自動掛載)

```cmd
cat /etc/fstab
```

![alt tag](https://i.imgur.com/79WxI5w.png)

查看所有 pci

```cmd
lspci
```

查看所有 usb

```cmd
lsusb
```

也可以搭配 grep 搜尋，只搜尋包含 VirtualBox 的內容

```cmd
lsusb | grep VirtualBox
```

查看 ip

```cmd
ip a
```

external ip Address ( 對外的 ip )，`ifconfig.me` 是一個網站，

```cmd
curl ifconfig.me
```

查看電腦目前資訊，CPU RAM 等等

```cmd
top
```

推薦 `htop` ( 資訊更清楚 ), 建議參考 [htop-tutorial](https://github.com/twtrubiks/linux-note/tree/master/htop-tutorial) - htop tutorial:thumbsup:

透過 xrandr 修改螢幕的亮度，

先查看螢幕的 name

```cmd
xrandr | grep " connected" | cut -f1 -d " "
```

設定亮度 ( 0 - 1 )

```cmd
xrandr --output DP-1 --brightness 0.7
```

透過 systemd-analyze 查看 Linux 啟動時間

```cmd
systemd-analyze
```

查看細節

```cmd
systemd-analyze blame
```

### 關機重啟指令

指令說明可使用以下指令查看

```cmd
shutdown --help
```

![alt tag](https://i.imgur.com/lDXENf0.png)

直接關機

```cmd
shutdown -h now
```

指定時間關機

```cmd
shutdown -h 22:30
```

![alt tag](https://i.imgur.com/CE9p1gt.png)

取消關機 (例如指定時間後想要取消, 如上圖)

```cmd
shutdown -c
```

模擬關機 (可以用來確認是否設定正確)

```cmd
shutdown -k 9:30
```

重開機

```cmd
reboot
```

查看關機紀錄

```cmd
last -x shutdown
```

查看重開機紀錄

```cmd
last -x reboot
```

系統開機時間

```cmd
uptime -s
```

last system boot time

```cmd
who -b
```

### 如何進入 tty 介面

有時候開機時可能因為驅動沒裝, 導致卡在黑屏的畫面,

這時候就可以進入 tty 介面安裝驅動(需要的東西),

進入 tty 快捷建 `Ctrl+Alt+F2`

退出 tty 快捷建 `Ctrl+Alt+F7` 或 `Ctrl+Alt+(F2/F3/F4)`

### swap

如果你的本機 ram 夠大, 可以考慮把它關掉,

(有些 distro 預設是打開的 )

關閉 swap

```cmd
sudo swapoff -a
```

打開 swap

```cmd
sudo swapon -a
```

以下指令可以幫你找出哪些程式用了多少 swap

```cmd
(echo "COMM PID SWAP"; for file in /proc/*/status ; do awk '/^Pid|VmSwap|Name/{printf $2 " " $3}END{ print ""}' $file; done | grep kB | grep -wv "0 kB" | sort -k 3 -n -r) | column -t
```

![alt tag](https://i.imgur.com/uibxLSu.png)

## install packages

install

```cmd
sudo apt-get install xxx
```

如果只有 `.deb` 檔案, 可以使用以下的方式

```cmd
sudo apt install ./xxx.deb
```

update list ( 更新 packages 的最新資訊及列表 )

```cmd
sudo apt-get update
```

upgrade ( 更新軟體到最新的版本 )

```cmd
sudo apt-get upgrade
```

只更新特定的軟體, 舉例 vivaldi,

先更新再安裝就是更新軟體的意思,

```cmd
sudo apt update && sudo apt install vivaldi-stable
```

remove

```cmd
sudo apt-get --purge autoremove xxxx
```

清理不需要的 packages ( `.deb` )

```cmd
sudo apt autoclean
```

清除不需要的依賴

```cmd
sudo apt autoremove
```

## ppa add/remove

add

```cmd
sudo apt-add-repository ppa:xxxx
sudo apt update
```

remove

```cmd
sudo add-apt-repository -r ppa:xxxx
sudo apt update
```

## 無法進入 bios

```cmd
sudo vim /etc/default/grub
```

你應該會看到類似的畫面

```text
GRUB_DEFAULT="0"
GRUB_TIMEOUT_STYLE="hidden"
GRUB_TIMEOUT=10   <<<<<<
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1"
GRUB_CMDLINE_LINUX=""
```

將 GRUB_TIMEOUT 的時間改長一點, 因為有可能是太快了, 導致來不及按:disappointed_relieved:

也請記得要再執行以下的指令更新

```cmd
sudo update-grub
```

## remove snap

在 ubuntu 中, 預設會幫你安裝 snap, 但有些人不太喜歡,

因為他是私人公司為維護的:smile:

以下附上移除 snap 指令,

```cmd
sudo rm -rf /var/cache/snapd/
sudo apt autoremove --purge snapd gnome-software-plugin-snap
rm -rf ~/snap
```

## remove ubuntu 不需要的軟體

使用 ubuntu 18.04 當範例

```cmd
sudo apt purge deja-dup thunderbird rhythmbox ubuntu-web-launchers whoopsie
```

`deja-dup` ubuntu 內建備份軟體.

`whoopsie` ubuntu 錯誤報告.

如果不小心刪除到依賴 (把 settings 刪除), 可使用以下指令將它裝回來

```cmd
sudo apt-get install gnome-control-center
```

## Linux 檔案系統(結構)

[Linux-File-System/Structure](https://github.com/twtrubiks/linux-note/tree/master/linux-file-system-structure)

## 更多文章

[zsh-tmux-tutorual](https://github.com/twtrubiks/linux-note/tree/master/zsh-tmux-tutorual) - 超好用 zsh 以及 tmux。

[zsh-powerlevel10k-tutorual](https://github.com/twtrubiks/linux-note/tree/master/zsh-powerlevel10k-tutorual) - zsh 搭配 Powerlevel10k, 超漂亮 terminal。

[vim-shortcuts](https://github.com/twtrubiks/linux-note/tree/master/vim-shortcuts) - 紀錄 vim 快捷鍵

[imwheel-tutorual](https://github.com/twtrubiks/linux-note/tree/master/imwheel-tutorual) - 改善 linux 滑鼠滾動問題。

[shutter-tutorual](https://github.com/twtrubiks/linux-note/tree/master/shutter-tutorual) - Shutter is an excellent image capture tool.

[systemctl-tutorial](https://github.com/twtrubiks/linux-note/tree/master/systemctl-tutorial) - systemctl 命令是系統服務管理指令

[crontab-tutorual](https://github.com/twtrubiks/linux-note/tree/master/crontab-tutorual) - Linux Crontab

[mount-disks-at-system-startup-on-ubuntu](https://github.com/twtrubiks/linux-note/tree/master/mount-disks-at-system-startup-on-ubuntu)

[chinese-input-methods-on-ubuntu](https://github.com/twtrubiks/linux-note/tree/master/chinese-input-methods-on-ubuntu) - ubuntu 如何安裝中文輸入法

[hime-tutorial](https://github.com/twtrubiks/linux-note/tree/master/hime-tutorial) - Linux 中更像微軟更好用的中文輸入法 hime

[gnome-tweaks](https://github.com/twtrubiks/linux-note/tree/master/gnome-tweaks) - Ubuntu 安裝 GNOME Tweak tool

[htop-tutorial](https://github.com/twtrubiks/linux-note/tree/master/htop-tutorial) - htop tutorial:thumbsup:

[neofetch-tutorial](https://github.com/twtrubiks/linux-note/tree/master/neofetch-tutorial) - command-line system information tool:thumbsup:

[copyq-tutorial](https://github.com/twtrubiks/linux-note/tree/master/copyq-tutorial) - 剪貼簿:thumbsup:

[krusader-tutorial](https://github.com/twtrubiks/linux-note/tree/master/krusader-tutorial) - file manager

[fail2ban-tutorial](https://github.com/twtrubiks/linux-note/tree/master/fail2ban-tutorial) - 讓 server 更安全:smile:

[how-to-change-login-lock-background-ubuntu](https://github.com/twtrubiks/linux-note/tree/master/how-to-change-login-lock-background-ubuntu) - 修改Ubuntu 登入/鎖屏時的背景

[grub-customizer-tutorial](https://github.com/twtrubiks/linux-note/tree/master/grub-customizer-tutorial) - 安裝 grub-customizer

[enable-ubuntu-remote-tutorial](https://github.com/twtrubiks/linux-note/tree/master/enable-ubuntu-remote-tutorial) - 如何在 ubuntu 啟用遠端桌面

[linux-nfs-server](https://github.com/twtrubiks/linux-note/tree/master/linux-nfs-server) - 如何在 ubuntu 啟用 NFS Server

## 狀況排除

[fix_could_not_get_lock_dpkg_ubuntu](https://github.com/twtrubiks/linux-note/tree/master/fix_could_not_get_lock_dpkg_ubuntu) - 修正 `E: Could not get lock /var/lib/dpkg/lock` Error

[fix_network_manager_bug_ubuntu_18_04](https://github.com/twtrubiks/linux-note/tree/master/fix_network_manager_bug_ubuntu_18_04) - 修正 ubuntu 18.04 網路連線設定遺失問題.

## 其他

[Windows -> Linux 優缺點](https://github.com/twtrubiks/linux-note/tree/master/linux-is-better-than-windows) - Windows -> Linux 優缺點

[ubuntu-18-04-on-Lenovo-X1-Carbon-6](https://github.com/twtrubiks/linux-note/tree/master/ubuntu-18-04-on-Lenovo-X1-Carbon-6)

[透過 VirtualBox 安裝 Ubuntu 19.10 （以及一些個人想法）](https://youtu.be/lI1EMwhW6lE)

[VirtualBox 6.1 Linux 安裝 Guest Addition - 全屏教學](https://youtu.be/PMw6FPtbbaU)

[alternative-software](https://github.com/twtrubiks/linux-note/tree/master/alternative-software) - windows -> Linux 替代軟體

[rclone-tutorial](https://github.com/twtrubiks/linux-note/tree/master/rclone-tutorial) - rclone 是一套很棒的文件同步管理工具

[stacer-tutorial](https://github.com/twtrubiks/linux-note/tree/master/stacer-tutorial) - Linux System Optimizer and Monitoring

[cmatrix-tutorial](https://github.com/twtrubiks/linux-note/tree/master/cmatrix-tutorial) - 超酷又超沒用的 cmatrix

[sl-tutorial](https://github.com/twtrubiks/linux-note/tree/master/sl-tutorial) - sl 火車開起來

[linux-tlp-tutorial](https://github.com/twtrubiks/linux-note/tree/master/linux-tlp-tutorial) - Linux Advanced Power Management

[speedtest-cli-tutorial](https://github.com/twtrubiks/linux-note/tree/master/speedtest-cli-tutorial) - Linux speedtest-cli tutorial

[gnirehtet-tutorial-tutorial](https://github.com/twtrubiks/linux-note/tree/master/gnirehtet-tutorial) - 透過電腦讓手機上網

[scrcpy-tutorial-tutorial](https://github.com/twtrubiks/linux-note/tree/master/scrcpy-tutorial) - 使用電腦控制手機

[variety-tutorual](https://github.com/twtrubiks/linux-note/tree/master/variety-tutorual) - variety 自動更換桌面

[arandr-tutorual](https://github.com/twtrubiks/linux-note/tree/master/arandr-tutorual) - arandr 設定多螢幕工具

[inotify-tools-tutorial](https://github.com/twtrubiks/linux-note/tree/master/inotify-tools-tutorial) - inotify-tools 監控檔案變動 inotifywait

[linux-virtualbox-ssh-tutorial](https://github.com/twtrubiks/linux-note/tree/master/linux-virtualbox-ssh-tutorial) - 在 Linux 中設定 VirtualBox 把玩 ssh

[linux-virtualbox-problem](https://github.com/twtrubiks/linux-note/tree/master/linux-virtualbox-problem) - 在 Linux 中設定 VirtualBox - 常見問題

[QEMU-KVM-tutorial](https://github.com/twtrubiks/linux-note/tree/master/QEMU-KVM-tutorial) - QEMU-KVM (效能速度比 virtualbox 更好)

[smartmontools-tutorial](https://github.com/twtrubiks/linux-note/tree/master/smartmontools-tutorial) - smartmontools 教學

[hdparm-tutorial](https://github.com/twtrubiks/linux-note/tree/master/hdparm-tutorial) - hdparm 教學

[fstrim-ssd-tutorial](https://github.com/twtrubiks/linux-note/tree/master/fstrim-ssd-tutorial) - fstrim ssd 教學

[Linux 桌面環境 Desktop Environment](https://github.com/twtrubiks/linux-note/tree/master/linux-de)

[認識 Linux 發行版 distribution](https://github.com/twtrubiks/linux-note/tree/master/linux-distro)

[KDE setting](https://github.com/twtrubiks/linux-note/tree/master/kde-settings)

## Reference

* [Linux Command 命令列指令與基本操作入門教學](https://blog.techbridge.cc/2017/12/23/linux-commnd-line-tutorial/)

## Donation

文章都是我自己研究內化後原創，如果有幫助到您，也想鼓勵我的話，歡迎請我喝一杯咖啡:laughing:

綠界科技ECPAY ( 不需註冊會員 )

![alt tag](https://payment.ecpay.com.tw/Upload/QRCode/201906/QRCode_672351b8-5ab3-42dd-9c7c-c24c3e6a10a0.png)

[贊助者付款](http://bit.ly/2F7Jrha)

歐付寶 ( 需註冊會員 )

![alt tag](https://i.imgur.com/LRct9xa.png)

[贊助者付款](https://payment.opay.tw/Broadcaster/Donate/9E47FDEF85ABE383A0F5FC6A218606F8)

## 贊助名單

[贊助名單](https://github.com/twtrubiks/Thank-you-for-donate)

## License

MIT license
