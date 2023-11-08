# Landing TP
Niveau 1
🎯 Quels sont les deux différents types d'hyperviseur existant, et quelles sont leur différence ?
```
Bare metal et heberge
```
Connectez-vous en SSH aux machines
```
ssh root@172.16.64.2 et ssh root@172.16.64.3
```
Changez le nom d'hôte des machines pour avoir respectivement vm-landing1 et vm-landing2
```
nano hostname sur les 2 machines
```
🎰 Trouvez l'adresse IP locale des machines
```
ip a
```
Quelle est l'adresse de broadcast ?
172.16.64.255

Trouvez le masque de sous-réseau des machines
ip a

Trouvez l'adresse MAC des machines
 link/ether 08:00:27:ac:1d:48 et  link/ether 08:00:27:32:d7:72

 Pingez l'adresse publique du site www.ynov.com avec une des deux machines
 PING www.ynov.com (104.26.11.233) 56(84) bytes of data.
64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=1 ttl=56 time=45.8 ms

Sur chaque machine, créez respectivement un utilisateur labo-user1 et labo-user2.
 useradd labo-user1 et  useradd labo-user2 sur chaque machine

Changez son mot de passe, puis de compte et connectez-vous avec l'utilisateur labo-user-1
sudo passwd labo-user1
su labo-user1

 🎰 Essayez de lire le contenu du fichier /var/log/tallylog
 cat: /var/log/tallylog: Permission denied. Cette erreur apparait car la commande cat ne peut pas encore etre utilisée

 Retentez avec la commande sudo cat
 Il y a une autre erreur qui dit labo-user1 is not in the sudoers file

 Ajoutez cet utilisateur au groupe wheel et retentez
  usermod -aG wheel labo-user1
  le groupe wheel fait référence à groupe système qui dispose de privilèges lui permettant l'exécution de commandes à accès restreint. 
  cat ne fonctionne toujours pas car labo-user1 n'est pas un sudoer

  Retentez en changeant d'utilisateur et en passant root
🎯 Ca devrait marcher. Pourquoi ?
su root
cat /var/log/tallylog 
ça marche car root est un sudoer



