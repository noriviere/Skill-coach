---
name: "coach-bilan"
description: "Phase bilan : analyser l'état de forme récent à partir de COROS et du contexte."
---

# Phase bilan

Rend un diagnostic de forme. N'écrit aucun plan.

## Processus

1. **Contexte** : le lire (règles communes).
2. **Données** : appliquer `coach-coros-donnees`, 4 dernières semaines (8 si le journal est vide).
3. **Confronter au plan en cours** : pour chaque séance prévue passée, la marquer `fait`, `sauté` ou `modifié` d'après COROS.
4. **Analyser** avec `coach-regles-entrainement` (sections Charge et Alertes). Fait quand chacun de ces points a une réponse chiffrée :
   - volume et charge des 4 dernières semaines, et la tendance ;
   - répartition de l'intensité (part du temps en zones 1-2) ;
   - séances clés réussies ou ratées, avec le ressenti ;
   - **alertes** déclenchées, ou « aucune ».
5. **Rendre** le bilan en 5 à 8 lignes : un état en une phrase (« en progression », « fatigue qui s'accumule », « reprise »), les chiffres, les alertes, puis **ce que ça implique** pour la suite.
6. **Rendre** le contexte complet : statuts du plan à jour, journal « bilan : <état> ».
7. Proposer la suite : `/planifier`.
