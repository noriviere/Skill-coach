---
name: "coach-regles-entrainement"
description: "Doctrine course à pied du kit coach : zones, types de séance, construction d'une semaine, charge, alertes, format séance."
---

# Règles d'entraînement : course à pied

Référence consultée par les phases. Chaque section est une source unique : une règle se change ici, nulle part ailleurs.

## Zones

Cinq zones, calculées depuis les repères confirmés du profil. FC seuil connue : elle prime. Sinon allure seuil, sinon VMA.

| Zone | Rôle | % FC seuil | % VMA (allure) |
|---|---|---|---|
| Z1 | récupération | < 85 % | < 65 % |
| Z2 | endurance fondamentale | 85-89 % | 65-75 % |
| Z3 | tempo / allure marathon | 90-94 % | 76-84 % |
| Z4 | seuil | 95-100 % | 85-90 % |
| Z5 | VMA | > 100 % | 95-105 % |

Une allure se donne en fourchette de 10 à 15 s/km, une FC en fourchette de 5 à 8 bpm.

## Types de séance

- **EF** (footing) : Z1-Z2 continu. Rôle : volume aérobie.
- **SL** (sortie longue) : Z2, fin possible en Z3 ou allure spécifique. Rôle : endurance.
- **Seuil** : 2 à 4 blocs de 6 à 15 min en Z4, 20 à 40 min d'effort au total.
- **VMA** : fractions de 30 s à 3 min en Z5, 12 à 20 min d'effort au total, récup égale ou plus longue.
- **AS** (allure spécifique) : blocs à l'allure de l'objectif, à partir de 8 semaines de la course.
- **Côtes** : 6 à 12 montées de 30 s à 1 min 30, récup en descente.
- **Récup** : 20 à 40 min Z1, ou repos.

Seuil, VMA, AS et côtes sont des séances **dures**. Une SL qui contient de l'AS ou du Z3 compte aussi comme dure.

## Construction d'une semaine

Chaque règle se vérifie sur la semaine entière :

1. **Polarisation** : au moins 80 % du temps de course en Z1-Z2.
2. **Séances dures** : 1 par semaine jusqu'à 3 sorties, 2 au-delà. Jamais deux jours durs consécutifs.
3. **Progression** : volume de la semaine au plus 10 % au-dessus de la moyenne des 3 dernières semaines COROS.
4. **SL** : au plus 30 % du volume hebdo, et au plus 15 min de plus que la plus longue des 4 dernières semaines.
5. **Cycle** : après 3 semaines de hausse, une semaine allégée (volume -20 à -30 %, une seule séance dure).
6. **Affûtage** avant l'objectif : volume -30 à -50 % en gardant une séance courte d'intensité ; 7 à 10 jours pour un 10 km, 10 à 14 jours pour un semi, 2 à 3 semaines pour un marathon.
7. **Cadre** : seulement les jours disponibles du profil ; préférences apprises respectées ; contraintes et blessures respectées.

## Charge

Utiliser les indicateurs de charge de COROS tels que le connecteur les donne : charge par séance, charge aiguë et chronique, ratio. Sans eux : charge d'une séance = durée (min) × ressenti (1-10) ; aiguë = somme sur 7 jours, chronique = moyenne hebdo sur 28 jours.

- Ratio aiguë / chronique entre 0,8 et 1,3 : zone de progression.
- Au-dessus de 1,5 : alerte.
- Sous 0,8 plusieurs semaines : désentraînement, la remontée suit la règle Progression.

## Alertes

Chacune se vérifie à chaque bilan et chaque planification. Déclenchée, elle se dit avec sa donnée, et son action s'applique :

- **Ressenti décalé** : séance facile notée 6/10 ou plus, ou séance dure notée 2 points au-dessus de l'attendu, deux fois de suite. Action : semaine allégée.
- **Récupération** : FC repos au moins 5 bpm au-dessus de l'habituelle, ou VFC sous la ligne de base, deux jours de suite. Action : séances dures remplacées par de l'EF jusqu'au retour à la normale.
- **Charge** : ratio au-dessus de 1,5. Action : volume ramené à la moyenne chronique.
- **Douleur** notée dans un retour ou dite par l'athlète. Action : aucune intensité, volume réduit ; douleur qui dure plus de 3 jours ou qui change la foulée : avis médical.
- **Maladie** : aucune intensité jusqu'à 2 jours sans symptômes ; fièvre ou symptômes sous le cou : repos.

## Format séance

Chaque séance proposée suit ce format, utilisé par le visuel et la validation :

```json
{
  "id": "S2",
  "date": "2026-11-19",
  "type": "Seuil",
  "titre": "3 × 8 min au seuil",
  "duree_min": 60,
  "distance_km": 11.5,
  "charge_prevue": 85,
  "pourquoi": "Dernier seuil réussi à 4:40 ressenti 7/10 : on garde l'allure, on ajoute un bloc.",
  "statut": "en_attente",
  "blocs": [
    { "id": "B1", "nom": "Échauffement", "duree_min": 15, "zone": "Z2", "allure": "5:40-5:55", "fc": "140-148" },
    { "id": "B2", "nom": "3 × 8 min, récup 2 min trot", "repetitions": 3,
      "effort": { "duree_min": 8, "zone": "Z4", "allure": "4:35-4:45", "fc": "165-172" },
      "recup": { "duree_min": 2, "zone": "Z1" } },
    { "id": "B3", "nom": "Retour au calme", "duree_min": 15, "zone": "Z1-Z2", "allure": "5:50-6:10" }
  ]
}
```

`statut` : `en_attente`, `acceptee`, `refusee`, `modifiee`.
