#  Projet DevOps : Déploiement Automatisé avec Ansible

Ce projet a pour but de monter une infrastructure locale simulant un environnement de production réel, puis d'automatiser son déploiement via Ansible.

## 🏗️rchitecture (Semaine 1)

L'infrastructure est composée de 3 machines interconnectées via un réseau privé virtuel.

| Machine | Rôle | OS | IP Privée (Host-Only) | RAM |
|---------|------|----|-----------------------|-----|
| **Machine A** | Machine de controle (Mon PC) | Windows/WSL | 192.168.56.1 |  |
| **Machine B** | Serveur PROD | Ubuntu Server 22.04 | **192.168.56.10** | 2048 Mo |
| **Machine C** | Serveur TEST | Ubuntu Server 22.04 | **192.168.56.20** | 2048 Mo |

### Schéma Réseau
```mermaid
graph TD;
    A[Machine A - Controle ] -->|SSH| B[Machine B - PROD .10];
    A -->|SSH| C[Machine C - TEST .20];
    B <-->|Ping| C;
