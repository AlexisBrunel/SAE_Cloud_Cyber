# Installation d'un firewall sur le GOAD :  

Un membre du groupe est certifié stormshield et est ameme de configurer un firewall pour protéger le GOAD depuis l'extérieure.
Comme nous l'avons montrer sur le schéma réseau nous avons placer le firewall en sortie du GOAD entre la DMZ et et le réseau local.



La matrice des flux 
<br/>
| Source/Dest | 9200   | 8220   | 9997   | 80     | 443    | 53     |
|-------------|--------|--------|--------|--------|--------|--------|
| Internet    | x      | x      | x      | Allow  | Allow  | x      |
| DNS         | x      | x      | x      | x      | x      | Allow  |
| Wazuh       | x      | x      | x      | x      | Allow  | x      |
| Elastic     | Allow  | Allow  | x      | x      | x      | x      |
| Splunk      | x      | x      | Allow  | x      | x      | x      |

Pour le firewall j'utilise une OVA obtenue en passant les exams Stormshield : 

Voici la page de connexion : 


![Alt text](<ecran de connexion.PNG>)

Une fois connecté je modifie l'axès au page d'administration : 

![Alt text](acc%C3%A8saupaged'aminsitration.PNG)

Je spécifie uniquement les réseaux internes à l'accès à l'administrateur (DMZ + GOAD)

Création des objets machines  :
# Kingslanding   
![Alt text](kingslanding.PNG)

Castelblack 
![Alt text](castelblack.PNG)

Winterfell

![Alt text](winterfell.PNG)

Merren
![Alt text](merren.PNG)
Braavos 
![Alt text](braabos.PNG)
Voici tous les objets crées : 

![Alt text](machiengoad.PNG)

Création des objets en rapport avec le port  : 
### Splunk 

![Alt text](splunkobj.PNG)

### Wazuh
![Alt text](wazuhobj.PNG)

### Elastic 
![Alt text](elastic.PNG)


Une fois tous les objets machines créer nous allons mettre en place les règles NAT et de filtrage pour autorisé le traffic souhauté :

![Alt text](FiltteringGOAD.PNG)


Nous avons accepter les requêtes du réseaux interne à la DMZ  sur les ports des SIEMS, nous avons autorisé l'accées à internet en HTTP et HTTPS (avec déchiffrement SSL). Nous avons bloquer les sites coréen (pour flex sur le Firewall)

Après quelque tentative de connexion sur des sites coréen (visitekorea.or.kr)on remarque que la règle s'active  : 

![Alt text](blokcorr%C3%A9e.PNG)

Nous n'allons pas mettre plus de configuration dans le firewall.