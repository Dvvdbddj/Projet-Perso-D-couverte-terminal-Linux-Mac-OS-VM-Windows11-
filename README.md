# Projet-Perso-D-couverte-terminal-Linux-Mac-OS- + Logiciel wireshark et nmap
Découverte du terminal sur mac et interface sous linux
prise de notes des commandes de bases

| **Commande**         | **Note / Explication**                              |
| -------------------- | --------------------------------------------------- |
| cd                | Se déplacer dans un répertoire                      |
| cd ..              | Revenir au répertoire parent (un niveau en arrière) |
| cd /               | Aller à la racine du système                        |
| cd ~               | Aller au répertoire personnel (home)                |
| clear              | Vider l’écran du terminal                           |
| mkdir nom_dossier  | Créer un dossier                                    |
| rmdir nom_dossier  | Supprimer un dossier vide                           |
| nom_du_logiciel -h | Afficher l’aide et les options d’un logiciel        |
| pwd                | Afficher le chemin du dossier actuel                |
| ls                 | Lister les fichiers et dossiers                     |


Instalatation de logiciels comme wiresharks 

open -a Wireshark

Wireshark sert à analyser les paquets et decouvrir les hôtes sur le réseau virtuel
Exemple de Filtre d'Affichage 

Wireshark (GUI) — capture & analyse réseau
| Objectif | Exemple de Filtre d'Affichage |
|---|---|
| Voir uniquement le trafic **HTTP** | http |
| Voir le trafic vers une **IP spécifique** | ip.addr == 192.168.1.1 |
| Voir le trafic sur un **Port spécifique** | tcp.port == 443 ou udp.port == 53 |
| Exclure les paquets **ARP** | !arp ou not arp |
| Combiner les critères | ip.addr == 192.168.1.1 and tcp.port == 80 |

Analyse de port ouvert sur nmap en récuperant une ip sur wireshark (illégal)

notes 

analyse forcée (pour contourner les routeurs): nmap -Pn <adresse_IP>
| **Objectif du Scan** | **Commande Nmap** | **Description** |
|---|---|---|
| **Scan de base**d'un hôte | nmap <adresse_IP> | Liste les ports ouverts et les services les plus courants sur la cible spécifiée. |
| **Scan de sous-réseau** | nmap 192.168.1.0/24 | Scanne toutes les adresses IP du sous-réseau (ex: de 192.168.1.1 à 192.168.1.254). |
| **Scan rapide** | nmap -F <adresse_IP> | N'analyse que les **100 ports** les plus couramment utilisés. |
| **Détection d'OS**et version de services | nmap -A <adresse_IP> | Effectue une **analyse agressive** pour identifier le système d'exploitation et la version exacte des services sur les ports ouverts. |
| **Scan furtif**(SYN Scan) | nmap -sS <adresse_IP> | Moins susceptible d'être journalisé par certains pare-feu, car il n'établit pas une connexion TCP complète (nécessite des privilèges *root*, donc utilisez sudo nmap -sS <adresse_IP> si le scan échoue). |
| **Scan de ports spécifiques** | nmap -p 22,80,443 <adresse_IP> | Ne scanne que les ports TCP 22 (SSH), 80 (HTTP) et 443 (HTTPS). |

