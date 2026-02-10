CAHIER DES EXIGENCES : PROJET INFRA-AUTOMATION

1. Exigences Fonctionnelles (EF) Ce que les scripts (Ansible & Python) doivent exécuter.

EF01 - Provisionnement : Le système d'automatisation (Ansible) doit installer les dépendances nécessaires (Docker, Pip) sur la machine cible "PROD" sans intervention humaine.

EF02 - Sécurisation Réseau : Le système doit configurer le pare-feu (UFW/Iptables) de la cible pour n'autoriser que le trafic SSH (Port 22) et Web (Port 80), et rejeter tout le reste.

EF03 - Déploiement Service : Le système doit déployer un serveur web (conteneur Nginx) affichant une page de bienvenue simple et personnalisée.

EF04 - Vérification de Service (IVVQ) : Le script de validation (Pytest) doit vérifier automatiquement que le code de réponse HTTP est 200 (OK) et que le port 80 est ouvert.

EF05 - Audit de Sécurité : Le système doit exécuter un scan de sécurité (Lynis).

2. Exigences Non Fonctionnelles (ENF) Les contraintes de l'environnement de travail.

Contraintes Techniques (EC)

EC01 - Topologie 3-Tiers : L'infrastructure doit strictement respecter le découpage :

Machine A : Orchestrateur (WSL/PC Hôte).

Machine B : Serveur d'Application (VM Ubuntu Server).

Machine C : Client de Validation (VM Ubuntu Server)


EC02 - Réseau : La communication entre le Contrôleur et la Cible doit se faire via un réseau privé (Host-Only) avec adressage IP statique, isolé d'Internet.

EC03 - Idempotence : Les scripts de déploiement (Ansible) doivent pouvoir être relancés plusieurs fois sans casser le système ni créer de doublons.

Sécurité (ES)

ES01 - Authentification : La connexion SSH entre le Contrôleur et la Cible doit se faire par clé publique/privée (pas de mot de passe en clair).

ES02 - Moindre Privilège : Le conteneur Nginx ne doit pas avoir accès aux privilèges root de la machine hôte.

