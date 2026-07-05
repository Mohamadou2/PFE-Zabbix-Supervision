# PFE-Zabbix-Supervision

# 🔍 Système de Supervision Réseau Zabbix pour Mauripost

**Projet de Fin d'Études - Licence DAII**  
Université de Nouakchott, Faculté des Sciences et Techniques, Département Informatique

---

## 📋 À Propos

Ce projet présente la **conception, le déploiement et la configuration d'un système de supervision réseau centralisé** utilisant **Zabbix 7.0 LTS** au sein de **Mauripost** (Société Mauritanienne des Postes).

### 🎯 Objectifs Atteints

✅ **Centralisation** : Supervision unique de l'infrastructure complète (serveurs, switches, firewall)  
✅ **Détection proactive** : Pannes détectées en **< 5 minutes** (amélioration de **95%**)  
✅ **Alertes automatiques** : Notifications email instantanées aux administrateurs  
✅ **Historique ** : Traçabilité complète des événements  
✅ **Sécurisation** :  SNMP sécurisé, pare-feu restrictif  

---

## 📊 Résultats Mesurés
--------------------------------------------------------------------------
| **Métrique**                | **Avant** | **Après** | **Amélioration** |
|-----------------------------|-----------|-----------|------------------|
| Détection de panne          | 2–8 h     | < 5 min   | ↓ 95%            |
| MTTR (temps de résolution)  | 4 h       | 1 h 30    | ↓ 62%            |
| Disponibilité               | 95%       | 99,5%     | ↑ 4,5%           |
| Visibilité infrastructure   | 0%        | 100%      | ✓               |
| Historique des données      | Aucun     | ✓        | ✓                |
---------------------------------------------------------------------------


---

## 🏗️ Architecture

🧩 Architecture de supervision Zabbix
Ce schéma illustre la topologie du réseau supervisé par Zabbix, intégrant un pare-feu pfSense, des machines virtuelles, et un laboratoire EVE‑NG pour la simulation d’équipements réseau.

🔹 1. Zabbix Monitoring
Composé du serveur Zabbix et de la base de données (DB).

Adresse réseau : 192.168.5.10/24.

Supervise les autres machines via Agent Zabbix et les équipements EVE‑NG via SNMP/ICMP.

🔹 2. Machines supervisées
Hébergent les agents Zabbix pour la collecte des métriques.

Incluent :

Web Server (serveur applicatif)

Windows (poste client)

Debian (machine Linux)

Connectées au réseau via DHCP fourni par pfSense.

🔹 3. pfSense Firewall
Fonctionne comme pare‑feu, serveur DHCP, et passerelle du réseau.

Adresse : 192.168.5.1/24.

Distribue les adresses IP et assure la sécurité du trafic interne.

🔹 4. EVE‑NG LAB (équipements simulés)
Contient les routeurs et commutateurs virtuels.

Relié au réseau 192.168.5.0/24 par un cloud virtuel.

Communication avec Zabbix via SNMP/ICMP pour la supervision.

---

## 🛠️ Technologies Utilisées

### Infrastructure
- **VirtualBox** : Virtualisation
- **Ubuntu Server 24.04 LTS** : Système d'exploitation serveur
- **Debian 13** : Alternative testée

### Base de Données
- **MySQL 8.0** : Stockage données et historique

### Web
- **Apache 2.4** : Serveur web
- **PHP 8.3** : Backend Zabbix

### Supervision
- **Zabbix 7.0 LTS** : Plateforme de supervision
- **SNMP v2c/v3** : Protocole pour équipements réseau
- **ICMP (Ping)** : Vérification basique disponibilité


---

## 📁 Structure du Projet

```
rapport/
├── Rapport_Final_PFE_Zabbix.pdf     # Mémoire complet

presentation/
├── Presentation_Soutenance.pptx     # Slides soutenance (17 slides)
└── Trascription.md                 # Script pour 10 minutes



demo/
├── video-demo
```

---

## 🚀 Installation Rapide

### Prérequis
- VirtualBox 7.0+
- 4GB RAM minimum
- Ubuntu/Debian serveur

### Étapes d'installation

```bash
# 1. Mise à jour système
sudo apt update && sudo apt upgrade -y

# 2. Installation MySQL
sudo apt install mysql-server -y
sudo mysql_secure_installation

# 3. Installation Zabbix
wget https://repo.zabbix.com/zabbix/7.0/debian/pool/main/z/zabbix-release/zabbix-release_7.0-2+debian12_all.deb
sudo dpkg -i zabbix-release_7.0-2+debian12_all.deb
sudo apt update
sudo apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf -y

# 4. Configuration base de données
sudo mysql -u root -p < /usr/share/zabbix-sql-scripts/mysql/server.sql.gz

# 5. Démarrage services
sudo systemctl restart zabbix-server zabbix-agent apache2

# 6. Accès interface
# Ouvrir navigateur : http://localhost/zabbix
# Login : Admin / zabbix
```

Pour installation complète, voir `https://www.zabbix.com/documentation/7.0/fr/manual/installation`

---

## 🎓 Compétences Développées

✅ **Administration Système**
- Gestion OS Linux (Ubuntu/Debian)
- Configuration réseau TCP/IP
- Gestion utilisateurs et permissions

✅ **Bases de Données**
- MySQL : création schémas, requêtes, optimisation

✅ **Réseaux et Protocoles**
- SNMP v2c/v3 : supervision équipements
- ICMP (Ping) : vérification connectivité
- SSH : connexion sécurisée

✅ **Supervision et Monitoring**
- Zabbix 7.0 : configuration complète
- Items, triggers, templates, alertes
- Dashboards et graphiques

✅ **Sécurité Informatique**
- Configuration pare-feu
- Authentification et autorisations

✅ **Gestion de Projet**
- Analyse besoins
- Conception architecture
- Tests et validation
- Documentation professionnelle

---

## 📖 Rapport et Présentation

- **[Rapport PDF complet](rapport/Rapport_Final_PFE_Zabbix.pdf)** 
- **[Présentation soutenance](presentation/Presentation_Soutenance.pptx)** 
- **[Notes de présentation](presentation/speaker-notes.md)** : Script  par slide

---

---

## 👨‍💼 Auteur

**Mamadou Abou Ba**
- Étudiant en Licence DAII
- Université de Nouakchott, Faculté des Sciences et Techniques
- Email : mamadouaboubamail@gmail.com
- GitHub : [@Mohamadou2](https://github.com/Mohamadou2)
- LinkedIn : www.linkedin.com/in/mamadou-abou-ba-6433432a3

### Encadrants
- **Encadrant Académique** : Pr. Ahmed Mohamed Lemine Mamoune (FST)
- **Encadrant Professionnel** : Mr. Beyni ould Maouloud (Mauripost)

---


## 🤝 Contribution

Ce projet est complété, mais les retours sont les bienvenus pour les futures améliorations !

N'hésitez pas à :
- ⭐ Star ce repository
- 🔖 Partager avec d'autres étudiants
- 💬 Poser des questions en issues
- 📝 Suggérer des améliorations

---



---

## 🙏 Remerciements

- **Mauripost** : pour m'avoir accueilli et fourni l'infrastructure
- **Pr. Mamoune** : pour l'encadrement académique
- **Mr. Mawloud** : pour le guidance professionnel
- **Université de Nouakchott** : pour la formation
- **Communauté Zabbix** : documentation et support

---

## 📞 Contact & Support

Pour questions ou support :
- 📧 Email : mamadouaboub38@gmail.com
- 💬 GitHub Issues : Poser vos questions ici
- 🔗 LinkedIn : www.linkedin.com/in/mamadou-abou-ba-6433432a3

---

**Dernière mise à jour** : Juin 2026  
**Statut** : ✅ Projet complété - Soutenance réussie  
**Grade** : À déterminer par le jury

---

*Merci de votre intérêt pour ce projet ! 🙏*
