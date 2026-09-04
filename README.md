# 🔧 Hardware — Conception électronique

## Présentation

Cette branche regroupe l'ensemble des éléments liés à la **conception matérielle de la carte électronique** autour de l'ESP32.

L'objectif est de documenter le passage du besoin fonctionnel au **schéma électronique**, puis au **circuit imprimé (PCB)**.

---

## Architecture matérielle

La carte est organisée autour des principaux blocs suivants :

```text
                    ┌─────────────────┐
                    │  Alimentation   │
                    │      5 V        │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │ Adaptation /    │
                    │ régulation 3,3 V│
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │      ESP32      │
                    └───┬─────┬─────┬─┘
                        │     │     │
                       GPIO  ADC   UART
                        │     │     │
                        ▼     ▼     ▼
                    Périph.  Entrées  USB/
                              analog.  Debug
```

---

## 🧩 Éléments documentés

* alimentation ;
* microcontrôleur ESP32 ;
* entrées analogiques ;
* GPIO ;
* interface UART ;
* connectique ;
* découplage ;
* PCB 2 couches.

---

## 📐 Schéma électronique

Le schéma constitue la représentation électrique complète de la carte.

### Vérifications prévues

* [ ] ERC
* [ ] Vérification des alimentations
* [ ] Vérification des connexions
* [ ] Vérification des empreintes
* [ ] Relecture complète du schéma

---

## 🟩 PCB

Le circuit imprimé est conçu sur **2 couches**.

Les principaux points étudiés sont :

* placement des composants ;
* largeur des pistes ;
* distribution des alimentations ;
* plan de masse ;
* routage des signaux ;
* accessibilité des connecteurs ;
* contraintes de fabrication.

### Vérifications

* [ ] DRC
* [ ] Vérification des règles de fabrication
* [ ] Vérification des empreintes
* [ ] Vérification du contour de carte
* [ ] Vérification finale avant fabrication

---

## 📦 Composants

La nomenclature sera documentée avec :

| Référence | Composant    | Valeur / Référence | Quantité | Fonction        |
| --------- | ------------ | ------------------ | -------: | --------------- |
| —         | ESP32        | —                  |        1 | Microcontrôleur |
| —         | Régulateur   | —                  |        — | Alimentation    |
| —         | Condensateur | —                  |        — | Découplage      |
| —         | Connecteur   | —                  |        — | Interface       |

> Les références définitives seront renseignées après validation du schéma.

---

## 🛠️ Logiciel de conception

**KiCad** est utilisé pour la conception électronique et le PCB.

---

## 📋 État d'avancement

* [ ] Schéma finalisé
* [ ] ERC validé
* [ ] PCB routé
* [ ] DRC validé
* [ ] Fichiers de fabrication générés
* [ ] Prototype fabriqué
* [ ] Prototype assemblé
