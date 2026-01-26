# Skill: Planification

Proposer des créneaux pour la semaine: vélo (selon météo) et renfo (Lafay).

## Étapes

1. Calculer la semaine en cours (semaine 1 = 26 janvier 2026)
2. Lire `suivi.md` pour les séances prévues cette semaine
3. Exécuter `./bin/meteo` pour récupérer la météo 7 jours
4. Identifier les créneaux ✅ ou 🤷 compatibles avec les durées des séances
5. Proposer un planning avec liens Google Calendar

## Format de sortie

Tableau récapitulatif:
| Jour | Séance | Durée | Créneau proposé | Notes |
|------|--------|-------|-----------------|-------|

Puis pour chaque créneau validé par l'utilisateur, générer le lien Google Calendar:
```
https://calendar.google.com/calendar/render?action=TEMPLATE&text=TITRE&dates=YYYYMMDDTHHMMSS/YYYYMMDDTHHMMSS&details=Semaine%20X%20-%20DESCRIPTION&location=Bordeaux
```

## Règles vélo

- Prioriser les créneaux ✅ sur les 🤷
- Éviter les ❌
- Sortie longue = week-end de préférence

## Règles renfo (Lafay)

- 2 séances par semaine, 15-20min
- Pas le même jour qu'une sortie vélo intense (force ou longue)
- Idéal: jours de repos vélo ou après sortie endurance
- Pas de contrainte météo (intérieur)

## Workflow

1. Demander les disponibilités de la semaine
2. Proposer un planning complet (vélo + renfo)
3. Demander confirmation
4. Générer les liens calendrier
