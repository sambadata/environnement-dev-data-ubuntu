# environnement-dev-data-ubuntu

# Ubuntu Developpeur.se Data - Basic Stack 

# 14/11/2019

## GIT (eca)

installer Git en Local




## UBUNTU (a)

- vérifier que l'environnement ubuntu 18.04 est à jour
-- mettre à jour ubuntu

		sudo apt-get update
		sudo apt-get upgrade




## Carnet de suivi dev data (eca)

- tester plateforme wordpress.com, blogger ?


## CHROME BROWSER (a)

IMPORTANT :

Avant toute installation, il faut toujour vérifier la mise à jour du système d'exploitation (OS), Ubuntu avec les commandes suivantes saisies dans le terminal:

sudo apt-get update
sudo apt-get upgrade


### Installer navigateur Chrome avec le terminal (en ligne de commande) (ok)

Ouvrir le terminal de commande (Ctrl+Alt+touche T)

### Install Google Chrome on Ubuntu 18.04 LTS from the Command Line (ok)

sudo nano /etc/apt/sources.list.d/google-chrome.list

Copier et coller la ligne suivante dans le fichier google-chrome.list qui s'est ouvert :

deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

Une fois copié, faire Ctrl+O, puis valider avec touche "Entrée" puis appuyer les touches CTRL+X 

wget https://dl.google.com/linux/linux_signing_key.pub

sudo apt-key add linux_signing_key.pub

sudo apt install google-chrome-stable


##### source :
https://www.linuxbabe.com/ubuntu/install-google-chrome-ubuntu-18-04-lts


15/11

## GMAIL (a)

se rendre sur :
https://accounts.google.com/signup/v2/webcreateaccount?service=mail&continue=https%3A%2F%2Fmail.google.com%2Fmail%2F%3Fpc%3Dtopnav-about-n-en&flowName=GlifWebSignIn&flowEntry=SignUp


## DISCORD (a)


### install discord (ok)

- discord :
Chat vocal et textuel tout-en-un gratuit, sécurisé, qui fonctionne sur PC et smartphone
https://discordapp.com

- Installer discord sur ubuntu avec snapcraft :

aller sur :
https://snapcraft.io/discord

puis, Ouvrir le navigateur Chrome 

Dans la barre d'adresse, saisir l'adresse url suivante :
https://snapcraft.io/store

dans la recherche, saisir le mot "discord" et appuyer sur la touche "entrée"

cliquer sur le lien "discord".

lorsque la page (https://snapcraft.io/discord) s'ouvre, cliquer sur le bouton "install" en haut à droite, cliquer ensuite sur l'icone pour copier et coller la commande suivante dans le terminal :

sudo snap install discord

### creation profil utilisateur sur discord (a)

Une fois installer, aller sur ubuntu et cliquer sur le lanceur d'application dans la barre de tâches.

saisir "discord" dans la recherche

lorsque l'application s'affiche, suivre les consignes pour créer son profil utilisateur

plus d'infos :
https://marmelab.com/blog/2019/05/15/creer-et-publier-une-application-web-sur-linux-grace-aux-snaps.html


## GIT (a)

### créer un compte sur github (a)

#### creation profil utilisateur (ok)

https://github.com/

#### modification profil utilisateur (ok)
https://github.com/sambadata

#### créer un nouveau dépôt (ok)

aller sur :
https://github.com/new

entrer le nom du dépôt "hello-word" dans "Repository name"

cliquer sur "Initialize this repository with a README" pour générer un fichier README.md dans le dépôt "hello-world"

### Git en local (a)

#### installer git sur ubuntu 18.04 (ok)

ouvrir le terminal de commande (Ctrl+Alt+touche T) et saisir :

sudo apt update
sudo apt install git
git --version
git config --global user.name "Your Name"
git config --global user.email "youremail@domain.com"

si jamais il faut modifier quelquechose, saisir la commande suivante :

nano ~/.gitconfig

plus d'infos :
https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-18-04-quickstart

#### Clone du dépôt "hello-word" en local (ok) 

ouvrir le terminal de commande (Ctrl+Alt+touche T)

Pour aller dans le répertoire /Documents (et éventuellement dans un dossier spécifique où on souhaite se placer), saisir : 

cd ~/Documents/

ensuite, une fois dans le dossier de votre choix à l'intérieur du dossier /Documents, saisir

git clone https://github.com/sambadata/hello-word.git

#### Vérifier les clés SSH existantes (SSH Keys) présent en local sur notre laptop avec la commande (ok)

ls -al ~/.ssh

Par defaut, si elle existe, les clés publiques (public keys) sont :

id_rsa.pub
id_ecdsa.pub
id_ed25519.pub

Si il n'existe pas de paires de clés privées/publiques présentes en local sur le laptop ou que l'on ne souhaite utiliser les clés existantes, on peut en générer avec les commandes suivantes :


ssh-keygen -t rsa -b 4096 -C "votre-email@example.com"

puis suivre les instructions qui s'affichent.

#### ajouter les clés SSH (SSH Key) à ssh-agent (ok)

- lancer ssh-agent en activité background sur ubuntu : 
eval "$(ssh-agent -s)"

- ajouter la clé privée (private key) dans le ssh-agent :
ssh-add ~/.ssh/id_rsa

Si on a créé une clé privée avec un nom différent de id_rsa alors penser à remplacer id_rsa dans la commande avec le nom spécifique de la clé privée.

plus d'infos :
https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

#### ajouter notre clé SSH (SSH key) (ok)

- copier la SSH key dans le presse-copie (clipboard) avec les commandes suivantes :

sudo apt update
sudo apt-get install xclip

xclip -sel clip < ~/.ssh/id_rsa.pub

- enregistrer la clé publique dans votre compte sur github.com :

cliquer sur la flèche en haut à droite, à côté du picto, puis sliquer sur "Settings" > SSH and GPG keys.

Puis, cliquer sur le bouton "New SSH key".

Donner un nom dans "Title" et coller le contenu de la clé dans "Key".

Cliquer enfin sur le bouton "Add SSH key" 



#### Tester la connexion SSH avec github (ok)

ouvrir le terminal de commande (Ctrl+Alt+touche T)

- saisir la commande :

ssh -T git@github.com

Si le message suivant apparaît "You've successfully authenticated, but GitHub does not provide shell access." alors  passer à l'étape ci-après.

#### activer les connexions SSH avec HTTPS (ok)

les connexions avec github doivent pouvoir se faire sur le port 443.

Pour cela, il faut configurer le fichier config qui se trouve dans le dossier .ssh/ en l'éditant :

sudo nano ~/.ssh/config 

dans le fichier qui apparaît, coller les lignes suivantes :

Host github.com
  Hostname ssh.github.com
  Port 443

Sauvegarder en faisant 

Ctrl+O puis, valider avec la touche "entrée" puis Ctrl+X pour quitter le fichier et revenir sur le terminal.

Re-tester la connexion avec github toujours avec la commande suivante :
ssh -T git@github.com

plus d'infos:
https://help.github.com/en/github/authenticating-to-github/testing-your-ssh-connection
https://help.github.com/en/github/authenticating-to-github/using-ssh-over-the-https-port



 
































