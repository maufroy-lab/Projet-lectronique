💻 Firmware ESP32
Présentation

Ce dossier contient le firmware développé pour le microcontrôleur ESP32 de la carte électronique.

Le firmware a pour objectif de permettre la mise en service, le diagnostic et la validation des différentes fonctions matérielles de la carte.

Il est organisé en plusieurs modules afin de séparer les différentes fonctions du système :

    configuration générale ;
    gestion des GPIO ;
    acquisition analogique ;
    communication UART ;
    programme principal.

Architecture logicielle

                    ┌──────────────────┐
                    │     main.cpp     │
                    │ Programme        │
                    │ principal        │
                    └────────┬─────────┘
                             │
              ┌──────────────┼──────────────┐
              ▼              ▼              ▼
       ┌─────────────┐ ┌─────────────┐ ┌─────────────┐
       │   gpio.cpp  │ │   adc.cpp   │ │  uart.cpp   │
       │             │ │             │ │             │
       │ Entrées /   │ │ Acquisition │ │ Diagnostic  │
       │ sorties     │ │ analogique  │ │ / console   │
       └─────────────┘ └─────────────┘ └─────────────┘

Fonctions prévues
GPIO

Le module GPIO permet de :

    configurer les broches ;
    commander les sorties numériques ;
    lire les entrées numériques ;
    réaliser des tests fonctionnels de la carte.

ADC

Le module ADC permet de :

    lire une tension analogique ;
    convertir la valeur ADC en valeur exploitable par le programme ;
    afficher les mesures via UART ;
    vérifier le fonctionnement de l'entrée analogique.

UART

La liaison UART est utilisée pour :

    afficher les informations de diagnostic ;
    afficher les mesures ;
    signaler les erreurs éventuelles ;
    faciliter le développement et le débogage.

Séquence de démarrage

Au démarrage de l'ESP32 :

Démarrage
   │
   ▼
Initialisation UART
   │
   ▼
Configuration GPIO
   │
   ▼
Initialisation ADC
   │
   ▼
Message de diagnostic
   │
   ▼
Boucle principale
   │
   ├── Lecture des entrées
   ├── Acquisition analogique
   ├── Commande des sorties
   └── Transmission des informations UART

Tests logiciels

Le firmware est également utilisé comme outil de validation du matériel.

Les fonctions développées permettent notamment de vérifier :
Fonction 	Méthode
Alimentation 	Lecture et mesure externe
GPIO 	Activation/désactivation des sorties
ADC 	Lecture d'une tension connue
UART 	Communication avec le PC
Fonctionnement global 	Exécution du programme de test
Environnement de développement

Le firmware peut être compilé et téléversé avec :

    PlatformIO
    Arduino framework
    ESP32
    langage C/C++

La configuration du projet est disponible dans platformio.ini.
État du firmware

    Initialisation ESP32
    Configuration GPIO
    Lecture des entrées
    Configuration ADC
    Acquisition analogique
    Communication UART
    Programme de test matériel
    Gestion des erreurs
    Validation sur prototype
