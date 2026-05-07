# Microcontroleur-avec-Site-

## 📖 Description
Ce projet permet de contrôler un buzzer ou une LED a partir d'une page Web et d'une carte Esp32.

## ⚙️ Materiel utilisé

* ESP32
* LED
* BUZZER

## 💻 Logiciel Utilisé

* Arduino IDE (programmer l'ESP32)
* FileZilla (transfère de fichier)
* Oracle VirtualBox (Virtualisation de Machine)

## 🛠️ Comment fonctionne le système 

Ce système est composé en 3 partie :

## 1️⃣ ESP32 (client + serveur)

### 📤 Client HTTP
L'ESP32 à deux rôles :
  * Il envoie une valeur comprise entre 0 et 100 aléatoirement toutes les 2 secondes
  * Elle est envoyée au serveur web par une requête POST

Exemple:

```
valeur=69
```

### 🌐 Serveur web embarqué
  * L'ESP32 héberge aussi notre serveur web
  * Il écoute les requêtes qui provient de notre page Web

Exemple de mon code :

  * /led allume la LED
  * /son allume la Buzzer

Cela permet de contrôler a distance le matériel à partir de la page Web

## 2️⃣ Serveur PHP

Le serveur va recevoir et stocker des données.

###  📤 Réception de données
  * Reçois des données envoyées par l'ESP32
  * Vérifie si cette variable "valeur" existe

### 💾 Stockage
  * Aprés quelle a été vérifier elle est stocker dans un fichier créer :

```
valeur.txt
```

## 3️⃣ Interface Web

La page Web permet :

### 🖥️ Affichage 
  * Permet de voir la dernière valeur générer par l'ESP32
  * Le bouton de la LED
  * Le bouton du Buzzer

### ⚙️ Contrôle
  * Bouton LED -> Envoie une requête pour allumer la LED
  * Bouton Buzzer -> Envoie une requête pour déclencher un son

Exemple de commande :

```
http://IP_ESP32/led
```

## 📦 Installation et mise en place 

### ✏️ 1.Configuration de l'ESP32

Dans le code arduino modifier :

```
const char* ssid = "VOTRE_WIFI";
const char* password = "MOT_DE_PASSE";
const char* serverName = "http://IP_SERVEUR/index.php";
```

### 📌 Rappel :
  * Le SSID est le nom de votre WIFI
  * Le password est le Mot de passe de votre WIFI
  * Le serverName est l'adresse IP de votre serveur

### 🌐 2.Configuration du serveur PHP

  * Creer votre index.php sur la machine Ubuntu (serveur)
  * Verifier si le fichier PHP marche
  * Il est important de mettre les droit d'écriture sur le fichier valeur.txt

Ces action ce passe de le dossier html qui ce trouve sur le serveur
```
cd /var/www/html
```

### 🔑 3.Accés a l'interface Web

Mettre dans le navigateur Web l'url du serveur  :
```
http://IP_SERVEUR/index.php
```

## 💡 Aide

### Ubuntu
Toute ces commande est pour le terminal(invite de commande) du serveur
```
cd  // Permet de se deplacer en dans les dossiers 
```
``` 
mkdir // Permet de créer un fichier un dossiers
```
``` 
nano // Cette commande permet de modifier le contenue d'un fichier 
```
``` 
ch mod 777  // La commande met tous les droits concernant un fichier 
``` 
