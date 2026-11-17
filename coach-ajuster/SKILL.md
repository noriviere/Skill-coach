---
name: "coach-ajuster"
description: "Phase ajuster : refaire seulement la partie refusée ou à adapter d'un plan."
---

# Phase ajuster

Change le strict nécessaire. Tout ce qui est accepté reste identique, à la virgule près.

Appelée de deux façons : depuis `planifier`, sur un refus ; ou seule (`/ajuster`) dans une nouvelle conversation, quand la vie s'en mêle (malade, déplacement, séance ratée). Seule, elle lit d'abord le contexte (règles communes) et cible le Plan en cours.

## Processus

1. **Cible** : les séances ou blocs visés (`S2`, `S4.B3`) et le **motif**. Sans motif : le demander une fois, en proposant les plus courants (trop dur, trop long, pas dispo ce jour, douleur, envie d'autre chose).
2. **Lire le motif** :
   - *pas dispo* : déplacer sur un autre jour disponible, sinon raccourcir ;
   - *trop dur / trop long* : baisser l'intensité ou le volume du bloc visé, garder l'objectif de la séance ;
   - *douleur / malade* : règles de la section Alertes de `coach-regles-entrainement` ;
   - *envie d'autre chose* : remplacer par une séance de même rôle dans la semaine.
3. **Revérifier** la section Construction de `coach-regles-entrainement` sur la semaine entière : un changement peut en casser une autre (deux jours durs collés).
4. **Réafficher** avec `coach-visuel-seance` : seulement ce qui a changé, marqué « modifié », avec son pourquoi.
5. **Valider** comme dans `planifier`, étape 6.
6. Seule (`/ajuster`) : **rendre** le contexte complet, journal « ajusté : <quoi, pourquoi> ».
