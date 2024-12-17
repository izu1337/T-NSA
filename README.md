# Projet : Configuration d'une Infrastructure Réseau et Serveur

- Description du projet :

Ce projet consiste à configurer une infrastructure réseau composée de 4 machines virtuelles connectées entre elles dans des réseaux privés. Les machines communiquent via un serveur passerelle basé sur OpenBSD pour gérer le trafic et assurer l'accès Internet aux clients internes. Un serveur web est configuré pour héberger des pages web et fournir une base de données MySQL.

## Configuration :

### VM 1 : Passerelle (OpenBSD 7.6)
- Rôle : Serveur passerelle pour les réseaux internes.

### Réseaux :

- NAT : Pour permettre l'accès à Internet.

- 3 sous-réseaux privés :

  - LAN-1 : Administrateur (192.168.42.0/26)

  - LAN-2 : Serveur Web (192.168.42.64/26)

  - LAN-3 : Employés (192.168.42.128/26)

Services configurés :

- DHCPD : Attribuer des IP dynamiques pour les clients.
- PF (Packet Filter) : Configuré pour le NAT et le routage des paquets.

### VM 2 : Serveur Web (FreeBSD 14)

- Rôle : Hébergement de sites web et base de données MySQL.

Services installés :

- NGINX : Serveur web.

- PHP 7.4 : Pour l'exécution des pages dynamiques.

- MySQL 8.0 : Gestion de la base de données.

- Adresse IP : 192.168.42.70 via DHCP.

### VM 3 : Machine Client Employé
- Rôle : Client utilisateur pour tester l'accès au serveur web.
- Adresse IP : Dynamique via DHCP.

### VM 4 : Machine Client Administrateur
- Rôle : Administration du réseau et des services.
- Adresse IP : Dynamique via DHCP.

## Instructions de Test

- Vérification de la Passerelle (VM 1)

Ping depuis les clients :
```bash
ping 192.168.42.1
```
- Test d'accès à Internet depuis VM 3 & 4 :
```bash
ping 8.8.8.8
```

2. Test du Serveur Web (VM 2)
Accéder au site web :Depuis un navigateur sur VM 3 ou VM 4, accédez à l'adresse :

http://192.168.42.70

Test de la base de données : Connexion à MySQL

```bash
mysql -u root -p
```

