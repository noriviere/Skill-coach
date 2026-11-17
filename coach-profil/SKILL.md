---
name: "coach-profil"
description: "Phase profil : créer ou modifier le profil de l'athlète dans le contexte."
---

# Phase profil

Rend un contexte dont la section **Profil** est complète et confirmée par l'athlète.

## Processus

1. **Partir de l'existant** : le contexte collé, sinon `contexte-coach.modele.md` du dépôt.
2. **Pré-remplir** depuis COROS (appliquer `coach-coros-donnees`, 8 dernières semaines) : volume hebdo moyen, sorties par semaine, FC max observée, FC repos, seuil et VMA si COROS les donne. Tout ce qui vient de là porte `(estimé)`.
3. **Interroger** l'athlète, une question à la fois, en proposant la valeur estimée quand il y en a une : objectif et date, disponibilités, contraintes et blessures, puis chaque repère `(estimé)` à confirmer. Fait quand chaque ligne du Profil est remplie ou marquée « inconnu » par l'athlète.
4. **Zones** : les calculer depuis les repères confirmés (règles dans `coach-regles-entrainement`), les montrer, les faire confirmer.
5. **Rendre** le contexte complet (règles communes), journal : « profil créé » ou « profil modifié : <quoi> ».
6. Proposer la suite : `/bilan`.
