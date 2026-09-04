# 🔌 Projet électronique — Carte de commande et d'acquisition

> **Conception d'une carte électronique autour d'un microcontrôleur ESP32, destinée à la commande de sorties et à l'acquisition de signaux analogiques.**

![Statut](https://img.shields.io/badge/Projet-en%20cours-orange)
![ESP32](https://img.shields.io/badge/MCU-ESP32-blue)
![PCB](https://img.shields.io/badge/PCB-2%20couches-green)
![KiCad](https://img.shields.io/badge/EDA-KiCad-red)
![Licence](https://img.shields.io/badge/License-MIT-lightgrey)

---

## 📌 Présentation

Dans le cadre de ma formation et de ma recherche d'alternance en **BTS CIEL — Cybersécurité, Informatique, Réseaux, Électronique**, j'ai réalisé ce projet afin de mettre en pratique différentes compétences liées à la **conception électronique**, à la **programmation embarquée** et à la **validation d'un système électronique**.

L'objectif est de concevoir une carte électronique compacte et reproductible permettant d'intégrer :

* un microcontrôleur **ESP32** ;
* une alimentation adaptée aux différents niveaux de tension ;
* des **entrées analogiques** pour l'acquisition de signaux ;
* des **sorties GPIO** pour la commande de périphériques ;
* une interface **USB/UART** pour la programmation et le diagnostic ;
* une connectique sur borniers ;
* un **PCB 2 couches**.

Le projet suit une démarche allant de la définition du besoin jusqu'à la conception du circuit imprimé et à la préparation des tests.

---

## 🎯 Objectifs du projet

Les principaux objectifs sont :

1. Définir l'architecture fonctionnelle de la carte.
2. Sélectionner les composants adaptés aux contraintes du système.
3. Concevoir le schéma électronique.
4. Gérer les différents niveaux d'alimentation et de logique.
5. Préparer le routage d'un PCB 2 couches.
6. Développer une première base de firmware pour l'ESP32.
7. Définir une procédure de tests et de mesures.
8. Documenter les choix techniques afin de rendre le projet reproductible.

---

## 🧩 Architecture du système

L'architecture générale peut être représentée de la manière suivante :

```text
                         ┌─────────────────────┐
                         │    Alimentation     │
                         │        5 V          │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │ Régulation /        │
                         │ adaptation 3,3 V    │
                         └──────────┬──────────┘
                                    │
                                    ▼
              ┌────────────────────────────────────────┐
              │                  ESP32                  │
              │                                        │
              │   GPIO ──────────────► Sorties         │
              │                                        │
              │   ADC ◄────────────── Entrées analog.  │
              │                                        │
              │   UART ◄────────────► USB / Debug     │
              └────────────────────────────────────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │ Connectique externe │
                         │      Borniers       │
                         └─────────────────────┘
```

---

## ⚙️ Caractéristiques principales

| Fonction                      | Caractéristique         |
| ----------------------------- | ----------------------- |
| Microcontrôleur               | ESP32                   |
| Alimentation d'entrée         | 5 V                     |
| Tension logique               | 3,3 V                   |
| Acquisition                   | Entrée(s) analogique(s) |
| Commande                      | GPIO                    |
| Communication / programmation | USB / UART              |
| Connectique                   | Borniers                |
| Circuit imprimé               | 2 couches               |
| Firmware                      | ESP32                   |
| CAO électronique              | KiCad                   |

---

## 🔋 Alimentation

La carte est prévue pour fonctionner à partir d'une alimentation **5 V**.

Une attention particulière est portée à la génération et à la distribution de la tension logique **3,3 V**, utilisée par le microcontrôleur et les différents signaux numériques.

La conception de l'alimentation doit notamment prendre en compte :

* la tension d'entrée ;
* la tension de fonctionnement du microcontrôleur ;
* la consommation des différents périphériques ;
* le découplage des alimentations ;
* la distribution des masses ;
* la stabilité de la tension 3,3 V.

> ⚠️ **Important :** avant toute fabrication, les valeurs des composants, les courants disponibles et les contraintes électriques doivent être vérifiés à partir des fiches techniques des composants utilisés.

---

## 📐 Conception électronique

La conception est réalisée en plusieurs étapes :

### 1. Cahier des charges

Identification des besoins :

* alimentation ;
* entrées ;
* sorties ;
* communication ;
* programmation ;
* contraintes mécaniques et de connectique.

### 2. Schéma électronique

Le schéma permet de définir les connexions entre :

* l'ESP32 ;
* le circuit d'alimentation ;
* les entrées analogiques ;
* les sorties GPIO ;
* l'interface USB/UART ;
* les connecteurs.

### 3. Vérification

Avant la fabrication du PCB, plusieurs contrôles doivent être effectués :

* vérification du schéma ;
* **ERC (Electrical Rules Check)** ;
* vérification des empreintes ;
* **DRC (Design Rules Check)** ;
* vérification des alimentations ;
* contrôle des connexions critiques.

### 4. Routage PCB

Le circuit imprimé est prévu en **2 couches**.

Le routage prend notamment en compte :

* la largeur des pistes ;
* le retour de masse ;
* le découplage ;
* la séparation des signaux sensibles ;
* le placement des composants ;
* l'accessibilité des connecteurs ;
* les contraintes de fabrication.

---

## 💻 Firmware

Une base de firmware est prévue pour permettre la validation des différentes fonctions de la carte.

Les premières fonctions visées sont notamment :

```text
Initialisation
     │
     ├── Configuration GPIO
     │
     ├── Initialisation ADC
     │
     ├── Initialisation UART
     │
     └── Vérification alimentation / périphériques
              │
              ▼
         Boucle principale
              │
        ┌─────┴─────┐
        ▼           ▼
   Acquisition   Commande
    analogique   des GPIO
        │           │
        └─────┬─────┘
              ▼
          Diagnostic
           via UART
```

Le firmware sera progressivement complété avec des fonctions de test permettant de valider indépendamment chaque partie du matériel.

---

## 🧪 Tests et validation

Une partie importante du projet consiste à vérifier expérimentalement le fonctionnement de la carte.

### Tests prévus

| Test               | Objectif                              | Résultat      |
| ------------------ | ------------------------------------- | ------------- |
| Alimentation 5 V   | Vérifier la tension d'entrée          | ⬜ À effectuer |
| Alimentation 3,3 V | Vérifier la tension logique           | ⬜ À effectuer |
| Continuité         | Vérifier les connexions               | ⬜ À effectuer |
| GPIO               | Vérifier les sorties numériques       | ⬜ À effectuer |
| ADC                | Vérifier l'acquisition analogique     | ⬜ À effectuer |
| UART               | Vérifier la communication             | ⬜ À effectuer |
| Consommation       | Mesurer le courant consommé           | ⬜ À effectuer |
| Test global        | Valider le fonctionnement de la carte | ⬜ À effectuer |

Les mesures pourront être réalisées à l'aide d'un **multimètre**, d'une **alimentation de laboratoire** et, lorsque nécessaire, d'un **oscilloscope**.

Les résultats seront ajoutés progressivement à ce dépôt.

---

## 📁 Organisation du dépôt

```text
Projet-lectronique/
│
├── README.md
├── LICENSE
│
├── docs/
│   ├── cahier-des-charges.md
│   ├── conception.md
│   └── tests.md
│
├── schematics/
│   └── schema-electrique.pdf
│
├── pcb/
│   ├── fichiers-kicad/
│   ├── pcb-front.png
│   └── pcb-back.png
│
├── firmware/
│   └── ...
│
├── tests/
│   └── ...
│
└── media/
    ├── prototype.jpg
    └── fonctionnement.jpg
```

> Certains dossiers peuvent être ajoutés au fur et à mesure de l'avancement du projet.

---

## 🛠️ Compétences mises en œuvre

### Électronique

* Lecture et réalisation de schémas électroniques
* Alimentation et régulation
* Logique 3,3 V
* Acquisition analogique
* Utilisation de GPIO
* Découplage et distribution d'alimentation
* Choix de composants
* Lecture de datasheets
* Diagnostic et mesures électriques

### Conception PCB

* Conception de PCB 2 couches
* Placement des composants
* Routage
* Gestion des masses et alimentations
* Vérification ERC / DRC
* Préparation des fichiers de fabrication

### Systèmes embarqués

* Microcontrôleur ESP32
* Programmation embarquée
* Configuration des GPIO
* Acquisition ADC
* Communication UART
* Débogage et validation

### Méthodologie

* Analyse du besoin
* Cahier des charges
* Recherche documentaire
* Conception
* Prototypage
* Tests
* Analyse des résultats
* Documentation technique
* Utilisation de Git / GitHub pour le suivi du projet

---

## 📊 État d'avancement

* [x] Définition de l'objectif
* [x] Définition de l'architecture
* [x] Choix du microcontrôleur
* [x] Définition des principales interfaces
* [ ] Finalisation du schéma
* [ ] Vérification ERC
* [ ] Finalisation du PCB
* [ ] Vérification DRC
* [ ] Fabrication du prototype
* [ ] Assemblage
* [ ] Développement complet du firmware
* [ ] Tests électriques
* [ ] Tests fonctionnels
* [ ] Analyse des résultats
* [ ] Documentation finale

---

## 📸 Documentation visuelle

Les différentes étapes du projet seront documentées avec des captures et photographies :

### Schéma électronique

*À ajouter*

### PCB

*À ajouter*

### Prototype

*À ajouter*

### Tests et mesures

*À ajouter*

---

## 📚 Documentation technique

Les documents techniques utilisés pour la conception seront référencés dans ce dépôt, notamment :

* fiches techniques des composants ;
* schémas ;
* documents de conception ;
* résultats de mesures ;
* notes de calcul ;
* documentation du firmware.

---

## ⚠️ État du projet

> **Projet en cours de développement.**

Le schéma et les éléments de conception présents dans ce dépôt constituent une base de **prototype et de documentation**.

Avant toute fabrication, une revue complète du schéma, des empreintes et du routage doit être réalisée, notamment à travers les vérifications **ERC / DRC** et la validation des caractéristiques électriques des composants.

---

## 🎓 Contexte

Ce projet est réalisé dans le cadre de mon parcours vers le **BTS CIEL — option B : électronique et réseaux**.

Il a pour objectif de mettre en pratique mes connaissances et de développer mes compétences dans les domaines suivants :

**Électronique • PCB • Microcontrôleurs • Programmation embarquée • Mesures • Réseaux/communication • Documentation technique**

Je souhaite poursuivre le développement de ces compétences dans le cadre d'une **alternance** afin de travailler sur des projets électroniques concrets et de progresser au contact d'une équipe professionnelle.

---

## 👤 Auteur

**Maufroy Lab**

Projet personnel — Portfolio électronique

🔗 GitHub : https://github.com/maufroy-lab

---

## 📄 Licence

Ce projet est distribué sous licence **MIT**.

Voir le fichier [`LICENSE`](LICENSE) pour plus d'informations.

