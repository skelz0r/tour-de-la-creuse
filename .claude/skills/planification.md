# Skill: Planification vélo

Proposer des créneaux vélo pour la semaine selon météo et plan d'entraînement.

## Étapes

1. Calculer la semaine en cours (semaine 1 = 26 janvier 2026)
2. Lire `suivi.md` pour les séances prévues cette semaine
3. Exécuter `./bin/meteo` pour récupérer la météo 7 jours
4. Identifier les créneaux ✅ ou 🤷 compatibles avec les durées des séances
5. Proposer un planning avec liens Google Calendar

## Format de sortie

Tableau récapitulatif:
| Jour | Séance | Durée | Créneau proposé | Météo |
|------|--------|-------|-----------------|-------|

Puis pour chaque créneau validé par l'utilisateur, générer le lien Google Calendar:
```
https://calendar.google.com/calendar/render?action=TEMPLATE&text=Sortie%20vélo%20-%20TYPE&dates=YYYYMMDDTHHMMSS/YYYYMMDDTHHMMSS&details=Semaine%20X%20-%20DESCRIPTION&location=Bordeaux
```

## Règles

- Prioriser les créneaux ✅ sur les 🤷
- Éviter les ❌
- Sortie longue = week-end de préférence
- Demander confirmation avant de générer les liens calendrier
