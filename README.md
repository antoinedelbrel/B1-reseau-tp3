# B1-reseau-tp3

# I.Création et utilisation simples d'une VM CentOs    

## 1 à 4 vu et fait en cours

## 5.Faire joujou avec quelques commandes
  
A faire :  
* on fait un `ping` hôte --> VM :  

![Blop](./ping_vm_1.png "ping")

* on fait un `ping` VM --> hôte :
Pour cela on écrit `ping 10.33.1.54` et on obtient 5 packets transmitted, 15 received, 0% packet lost.

* Afficher la table de routage :  
De l'hôte : Il faut écrire `route print`.   
De la VM : Il faut écrire `ip route`.  
La ligne qui leur permet de discuter via le réseau host-only est l'adresse de réseau.

* On écrit `curl www.google.com` pour télécharger le fichier google.

* Pour télécharger dig sur centOS il faut faire `sudo yum install bind-utils`.
On possède désormais la commande dig. Maintenant on fait la commande `dig ynov.com`et on obtient son IP : `10.33.10.20`.
On obtient exactement la même en faisant `dig google.com`.


# II.Notion de ports et de SSH
## 1.Exploration des ports locaux
* Utilisation de `ss` : 
On fait un `ss -p -n -l4`, le `-p` permet de connaitre l'application qui ecoute sur ce port, le `-n` permet d'avoir un numéro de port plutot qu'un nom et enfin le `-l4` nous dit qu'il faut se mettre sur l'IPV4 (l=listening).  

## 2.SSH
On connecte putty a notre VM en mettant l'adresse IP de notre VM dans putty, maintenant on contrôle la VM grâce a putty.

## 3.Firewall
### A.SSH : 
On change le numéro du port sur lequel notre serveur écoute en accedant au fichier `/etc/ssh/sshd_config` avec la commande `sudo nano` (on met le port numéro 2222 en enlevant le # devant pour que ça ne soit pas un commentaire). Tout cela on le fait sur Putty.  
Pour redémarrer le serveur et enregistrer les modifications on tape la commande `systemctl restart sshd`.  
Pour vérifier que notre serveur SSH écoute sur notre port on utilise la commande `ss-altnp4`.  
Cependant la connexion n'aboutit pas quand on essaie de se connecter a ce port. Elle est impossible car le firewall ne l'autorise pas.  
Pour que le firewall l'autorise il faut taper la commande `firewall-cmd --add-port=2222/tcp --permanent` on fait la connexion sur le port 2222 ensuite on utilise la commande `firewall-cmd --reload` et grâce a cela les modifications sont ajoutées.

### B.`netcat`





 
  