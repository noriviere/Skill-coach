---
name: "coach-planifier"
description: "Phase planifier : proposer les prochaines séances, les afficher et les faire valider."
---

# Phase planifier

Rend un plan dont chaque séance est **acceptée**, **refusée** ou **modifiée** par l'athlète, et le contexte qui l'enregistre.

## Processus

1. **Contexte** : le lire (règles communes). Profil incomplet (objectif, disponibilités ou zones manquants) : proposer `/profil` et s'arrêter.
2. **Bilan express** : appliquer `coach-coros-donnees` sur les 2 dernières semaines, et la section Alertes de `coach-regles-entrainement`. Dernier bilan du journal vieux de plus de 7 jours : le dire et proposer `/bilan`, sans bloquer.
3. **Horizon** : la semaine à venir par défaut, ou ce que l'athlète demande (2 semaines maximum).
4. **Générer** avec `coach-regles-entrainement` : chaque séance au format séance, sur les jours disponibles, en respectant les préférences apprises. Fait quand chaque règle de la section Construction est vérifiée sur la semaine entière ; une règle qui ne peut pas l'être se dit dans la proposition.
5. **Afficher** avec `coach-visuel-seance`.
6. **Valider** : attendre la réponse de l'athlète (boutons ou commandes de validation). Pour chaque refus ou modification, appliquer `coach-ajuster` sur cette partie seulement, puis réafficher. Fait quand plus aucune séance n'est en attente.
7. **Rendre** le contexte complet : séances acceptées dans Plan en cours, une ligne par motif de refus dans Préférences apprises quand il dit quelque chose de durable (« pas de VMA le lundi »), journal « plan <dates> validé ».
