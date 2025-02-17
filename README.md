# logs
dans un premier temps je crée du trafic
![trafic](https://github.com/The-flosh/logs/blob/main/ressources/trafic.JPG)
par défaut la structure du fichiée access.log de apache2 est srtucturer comme ceci :
---
*exemple*:
192.168.1.10 - - [17/Feb/2025:12:34:56 +0000] "GET /index.html HTTP/1.1" 200 3456 "http://google.com" "Mozilla/5.0"
---
192.168.1.10 : Adresse IP du client
- : Identifiant RFC 1413 (généralement vide)
- : Nom d'utilisateur (authentification HTTP, souvent vide)
[17/Feb/2025:12:34:56 +0000] : Date et heure de la requête
"GET /index.html HTTP/1.1" : Méthode HTTP, ressource demandée et version du protocole
200 : Code de réponse HTTP (succès)
3456 : Taille de la réponse en octets
"http://google.com"	: Référent (site depuis lequel l'utilisateur est venu)
"Mozilla/5.0"	: User-Agent (navigateur et système d’exploitation du client)
---
apres avoir crée du trafic je vrai verfiée mes logs qui sont par la meme occasion tous par defaut dans le meme fichiée le access.log
donc pour voir les requetes qui ont réussi j'utilise la commande : grep ' 200 ' /var/log/apache2/access.log
![réussi](https://github.com/The-flosh/logs/blob/main/ressources/réussi.JPG)
---
pour le partit avec les erreur j'utilise : grep ' 404 ' /var/log/apache2/access.log
![error](https://github.com/The-flosh/logs/blob/main/ressources/error.JPG)
---
et enfin pour voir les ip qui ont le plus fréquentée mon serveur web j'utilise : awk '{print $1}' /var/log/apache2/access.log | sort | uniq -c | sort -nr | head  
![error](https://github.com/The-flosh/logs/blob/main/ressources/ip%20fréquente.JPG)
