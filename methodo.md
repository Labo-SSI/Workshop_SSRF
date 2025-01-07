Tester quelque payloads, pour voir si classic , semi blind ou blind:

-   http://localhost
-   https://localhost
-   url requestbin

Si restrictions sur url: 
- Open redirect quelque part dans l'application?
- **https://nip.io**
- https://book.hacktricks.wiki/en/pentesting-web/ssrf-server-side-request-forgery/url-format-bypass.html
- 302 redirect: https://github.com/siefr3dus/Tools/blob/main/redirect.py
- DNS rebinding: https://lock.cmpxchg8b.com/rebinder.html
- https://portswigger.net/web-security/ssrf/url-validation-bypass-cheat-sheet

Essayer tous les ports sur localhost en http et https, commencer par ports communs https://github.com/danielmiessler/SecLists/blob/master/Discovery/Infrastructure/common-http-ports.txt

Essayer les range d'ip en commençant par Class C (192.168.0.0), puis Class B (172.16.0.0), et peut etre Class A (10.0.0.0)

Tester aussi des ips cloud:
AWS:
- http://169.254.169.254

Google cloud:
- http://169.254.169.254
- http://metadata.google.internal
- http://metadata

Pour aller plus loin: https://book.hacktricks.wiki/en/pentesting-web/ssrf-server-side-request-forgery/cloud-ssrf.html

## Classic

Regarder des longueurs de reponse qui sont differents pour differencier ouvert et fermé

Essayer les autres protocoles: file, dict, sftp, tftp , ldap, **gopher** 

## Semi blind

Essayer de trouver 2 reponses differentes / 2 code http different pour differencier ouvert et fermé

## Blind

Essayer de trouver 2 temps de reponses differentes, en general ouvert plus rapide que fermé



## Ensuite pour tous:

Si ports 3306, 5432, 9000, 11211, 6379, 10050 ou 25 ouverts, essayer d'utiliser le protocol gopher pour interagir avec = peut-etre rce

https://github.com/tarunkant/Gopherus

Si gopher bloqué:
- - 302 redirect: https://github.com/siefr3dus/Tools/blob/main/redirect.py


Sinon etre bete et utiliser https://github.com/swisskyrepo/SSRFmap

If all else fails, command injection: `; sleep 10`
