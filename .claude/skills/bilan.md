# Skill: Bilan de la semaine

Fait le bilan hebdomadaire de l'entraînement.

## Déclencheurs

- `/bilan`
- "faire le bilan"
- "bilan de la semaine"

## Instructions

1. Déterminer la semaine en cours (ou demander si ambiguë)

2. Lire les séances enregistrées dans `seances/semaine-XX/`

3. Lire le fichier `bilan.md` de la semaine pour voir les objectifs

4. Afficher un récap:
   - Séances prévues vs réalisées
   - Volume total (heures, km, D+)
   - Taux de complétion

5. Poser les questions d'auto-évaluation:
   - Régularité (1-5): "J'ai fait ce qui était prévu?"
   - Qualité (1-5): "Les séances étaient bonnes?"
   - Récupération (1-5): "Je récupère bien?"
   - Nutrition (1-5): "J'ai bien mangé/bu pendant les sorties?"
   - Motivation (1-5): "J'ai envie de continuer?"

6. Demander:
   - Ce qui a bien marché
   - Ce qui a été difficile
   - Ajustements pour la semaine prochaine

7. Si fin de phase (semaines 4, 9, 14), poser les questions de bilan de phase

8. Mettre à jour le fichier `seances/semaine-XX/bilan.md`

9. Afficher un message d'encouragement adapté au contexte

## Calcul des semaines

| Semaine | Dates | Phase |
|---------|-------|-------|
| 1 | 26 jan - 1 fév | Base |
| 2 | 2-8 fév | Base |
| 3 | 9-15 fév | Base |
| 4 | 16-22 fév | Base (fin) |
| 5 | 23 fév - 1 mar | Force |
| 6 | 2-8 mar | Force |
| 7 | 9-15 mar | Force |
| 8 | 16-22 mar | Force |
| 9 | 23-29 mar | Force (fin) |
| 10 | 30 mar - 5 avr | Spécifique |
| 11 | 6-12 avr | Spécifique |
| 12 | 13-19 avr | Spécifique |
| 13 | 20-26 avr | Spécifique |
| 14 | 27 avr - 3 mai | Spécifique (fin) |
| 15 | 4-10 mai | Affûtage |
| 16 | 11-17 mai | Affûtage |
| 17 | 18-24 mai | Course |

## Exemple d'interaction

```
User: /bilan
Claude: Bilan semaine 1 (26 jan - 1 fév)

Séances enregistrées:
- 27/01: Endurance 1h20 ✓
- 29/01: Force 1h05 ✓
- C (longue): non enregistrée

Objectifs: A ✓ | B ✓ | C ✗ | Renfo1 ✗ | Renfo2 ✗
Taux: 2/5 (40%)

Questions:
- Régularité (1-5)?
User: 3
- Qualité (1-5)?
User: 4
...
Claude: Bilan mis à jour.
Semaine 2: objectif sortie longue 2h15!
```

## Notes

- Être bienveillant mais honnête
- Si taux < 50%, demander ce qui a bloqué
- Rappeler l'objectif global: finir le tour, pas performer
