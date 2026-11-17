---
name: "coach-visuel-seance"
description: "Affichage des séances proposées par le kit coach et commandes de validation."
---

# Visuel des séances

Rend les séances au format séance (`coach-regles-entrainement`) lisibles sur téléphone, et validables séance par séance ou bloc par bloc.

## Le visuel

**Visuel interactif dans la conversation** quand l'outil est disponible ; sinon, les mêmes éléments en texte.

Pour la semaine :
- en tête : volume prévu (km, h), part en Z1-Z2, nombre de séances dures, et une ligne sur l'intention de la semaine ;
- une **carte par séance**, dans l'ordre des dates.

Pour chaque carte :
- jour et date, type, titre, durée, distance ;
- **profil de la séance** : une barre horizontale où chaque bloc a une largeur proportionnelle à sa durée et la couleur de sa zone (répétitions dépliées : effort et récup alternés) ;
- sous la barre, la liste des blocs avec leur id (`B1`…), durée, allure et FC ;
- le **pourquoi** ;
- le statut, et pour une séance `modifiee`, ce qui a changé.

Couleurs de zone, de froid à chaud : Z1 gris-bleu, Z2 bleu, Z3 vert, Z4 orange, Z5 rouge. Toujours doublées du libellé de zone : la couleur ne porte jamais seule l'information.

## Validation

Chaque carte porte trois boutons : ✅ accepter, ❌ refuser, ✏️ modifier ; chaque bloc, ❌ et ✏️. Un bouton envoie dans la conversation la commande correspondante ci-dessous ; ❌ et ✏️ demandent d'abord un motif en un champ libre.

Les mêmes commandes se tapent à la main, ce qui marche partout :

- `ok S1 S3` ou `tout ok`
- `non S2 : trop dur`
- `non S4.B2 : trop long`
- `modif S5 : 45 min au lieu de 60`

Sous le visuel, toujours rappeler ces commandes en une ligne.
