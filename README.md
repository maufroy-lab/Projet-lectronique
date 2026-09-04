# 💻 Firmware — ESP32

## Présentation

Cette branche contient le **firmware embarqué** destiné à l'ESP32 de la carte électronique.

Le firmware est principalement développé comme **logiciel de mise en service, de diagnostic et de validation du matériel**.

---

## 🧠 Architecture logicielle

```text
                         main.cpp
                            │
              ┌─────────────┼─────────────┐
              ▼             ▼             ▼
           GPIO            ADC           UART
              │             │             │
              ▼             ▼             ▼
          Entrées /      Mesures       Diagnostic
           sorties      analogiques    / console
```

---

## 📁 Organisation

```text
firmware/
├── README.md
├── platformio.ini
└── src/
    ├── main.cpp
    ├── config.h
    ├── gpio.cpp
    ├── gpio.h
    ├── adc.cpp
    ├── adc.h
    ├── uart.cpp
    └── uart.h
```

---

## ⚙️ Fonctions

### GPIO

* configuration des broches ;
* lecture des entrées ;
* commande des sorties ;
* tests matériels.

### ADC

* acquisition analogique ;
* lecture des valeurs ADC ;
* conversion en tension ;
* transmission des mesures via UART.

### UART

* messages de diagnostic ;
* affichage des mesures ;
* aide au débogage.

---

## 🛠️ Environnement

| Élément         | Technologie |
| --------------- | ----------- |
| Microcontrôleur | ESP32       |
| Langage         | C/C++       |
| Framework       | Arduino     |
| Build system    | PlatformIO  |
| Communication   | UART        |

---

## ▶️ Compilation

Installer **PlatformIO**, puis compiler et téléverser le projet sur l'ESP32.

La configuration de la cible et du moniteur série se trouve dans :

```text
platformio.ini
```

Configuration série actuelle :

```text
115200 bauds — 8N1
```

---

## ⚠️ Configuration matérielle

Les numéros de GPIO et les paramètres ADC doivent correspondre au **schéma électronique validé**.

Les constantes de configuration sont centralisées dans :

```text
src/config.h
```

---

## 📈 État

* [ ] Configuration GPIO
* [ ] ADC
* [ ] UART
* [ ] Tests matériels
* [ ] Gestion des erreurs
* [ ] Validation sur prototype
