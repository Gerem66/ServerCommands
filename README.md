# ServerCommands

## Ubuntu
### Utilisateurs et permissions
| Commande | Description |
|-|-|
| adduser USERNAME | Ajouter un utilisateur |
| usermod -aG sudo USERNAME | Ajouter un utilisateur dans le groupe "sudo" |
| visudo | Afficher la configuraition "sudo" |

### SSH
| Commande | Description |
|-|-|
| nano /etc/ssh/sshd_config | Modifier le "PermitRootLogin" pour désactiver la connexion depuis l'utilisateur root (question de sécurité) |
| service sshd restart | Redémarrer le ssh daemon pour prendre en compte les modifications de configuration |

### FailToBan
| Commande | Description |
|-|-|
| apt install fail2ban | Bloquer les utilisateurs (et les bots) de bruteforce le serveur |
| nano /etc/fail2ban/jail.conf | Pour modifier le nombre d'échec avant les tempban, et leurs durée |

### Pare-feu
| Commande | Description |
|-|-|
| iptables -L | Lister les règles du pare-feu |
| iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW,EESTABLISHED -j ACCEPT | Accepter les communications entrantes sur l'interface eth0 du protocole tcp (ssh) sur le port de destination 22 |
| iptables -A OUTPUT -i eth0 -p tcp --sport 22 -m state --state NEW,EESTABLISHED -j ACCEPT | Accepter les communications sortantes sur l'interface eth0 du protocole tcp (ssh) depuis le port de 22 |
| iptables -P INPUT DROP | Refuser tous les types de connexions non cités dans les règles précédentes |
