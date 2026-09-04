# 🧪 Measurements — Mesures et validation

## Objectif

Cette branche regroupe les **mesures expérimentales** réalisées sur la carte électronique.

L'objectif est de confronter les valeurs théoriques aux valeurs réellement mesurées et d'identifier les éventuels écarts.

---

## 🔬 Méthode

La campagne de validation suit une progression :

```text
Inspection
    ↓
Continuité
    ↓
Alimentation
    ↓
Signaux numériques
    ↓
ADC
    ↓
UART
    ↓
Validation globale
```

---

## 📋 Campagne de mesures

| ID  | Mesure             | Instrument                | Statut |
| --- | ------------------ | ------------------------- | ------ |
| M01 | Tension d'entrée   | Multimètre                | ⬜      |
| M02 | Tension 3,3 V      | Multimètre                | ⬜      |
| M03 | Courant consommé   | Multimètre                | ⬜      |
| M04 | GPIO               | Multimètre / oscilloscope | ⬜      |
| M05 | ADC                | Multimètre                | ⬜      |
| M06 | UART               | PC / terminal série       | ⬜      |
| M07 | Validation globale | Plusieurs                 | ⬜      |

---

## 📊 Présentation des résultats

Chaque mesure doit comporter :

* la condition de test ;
* l'instrument utilisé ;
* la valeur théorique ;
* la valeur mesurée ;
* l'écart ;
* une conclusion.

### Exemple

| Paramètre | Théorie | Mesure | Écart |
| --------- | ------: | -----: | ----: |
| 3V3       |  3,30 V |      — |     — |

---

## ⚠️ Traçabilité

Les valeurs présentes dans cette branche correspondent à des **mesures expérimentales**.

Aucune valeur ne doit être renseignée sans avoir été effectivement mesurée.

Les anomalies et corrections sont également documentées afin de conserver la trace de la démarche de diagnostic.

---

## 📈 Bilan

La campagne de mesures permettra de déterminer :

* la conformité des alimentations ;
* le comportement réel des entrées/sorties ;
* les performances de l'ADC ;
* la stabilité du système ;
* les éventuels écarts entre théorie et pratique.
