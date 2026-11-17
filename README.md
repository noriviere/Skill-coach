# Skill-coach

Kit de skills Claude qui analyse l'historique COROS, propose des séances de course à pied et les fait valider séance par séance ou bloc par bloc.

## Principe

- **Un seul skill installé** : `coach/`, le chargeur. Il lit les autres skills ici, à l'étiquette `Stable`. On fait évoluer le kit sans rien réinstaller.
- **Une conversation = une phase.** Le contexte vit hors de la conversation : un fichier `contexte-coach.md` que l'athlète colle au début et que Claude rend mis à jour à la fin.
- **COROS** est lu par son connecteur officiel (`https://mcp.coros.com/mcp`).

## Phases

| Commande | Rôle |
|---|---|
| `/coach profil` | Créer ou modifier le profil (objectif, dispos, zones) |
| `/coach bilan` | Analyser l'état de forme récent |
| `/coach planifier` | Proposer les prochaines séances, à valider |
| `/coach ajuster` | Refaire la partie refusée, ou adapter le plan |

## Structure

```
coach/                      chargeur, seul skill à installer
coach-regles-communes/      contexte, sources de vérité, ton, sécurité
coach-profil/               phase profil
coach-bilan/                phase bilan
coach-planifier/            phase planifier
coach-ajuster/              phase ajuster
coach-coros-donnees/        lecture COROS → résumé standard
coach-regles-entrainement/  zones, séances, construction, charge, alertes, format séance
coach-visuel-seance/        affichage et commandes de validation
contexte-coach.modele.md    modèle du contexte
VERSION
```

## Installation (athlète)

1. Claude → Paramètres → Capacités : activer l'exécution de code et la création de fichiers.
2. Paramètres → Connecteurs → Ajouter un connecteur personnalisé : `https://mcp.coros.com/mcp`, se connecter à COROS.
3. Compresser le dossier `coach/` en ZIP, puis l'importer dans Personnaliser → Skills.
4. Nouvelle conversation : `/coach profil`. Garder le contexte rendu à la fin dans un fichier `contexte-coach.md`.

## Publier une version (mainteneur)

Modifier, incrémenter `VERSION`, puis déplacer l'étiquette :

```
git tag -f Stable && git push -f origin Stable
```
