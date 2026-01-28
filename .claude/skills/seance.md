# Skill: Enregistrer une séance

Enregistre les résultats d'une séance d'entraînement vélo ou renforcement.

## Déclencheurs

- `/seance`
- "j'ai fait une séance"
- "enregistrer ma sortie"

## Instructions

### Pour séances vélo (A, B, C)

1. Lancer `./bin/strava seance` pour récupérer la dernière activité
2. Afficher les données récupérées et demander confirmation
3. Déduire le type automatiquement selon ces règles:
   - ~31km + ~250m D+ → "Côtes court" → B (force)
   - ~55km + ~400m D+ → "Côtes long" → C (longue)
   - >60km ou >3h → C (longue)
   - <150m D+ sur <50km → A (endurance)
   - En cas de doute, demander confirmation
4. Poser uniquement les questions subjectives:
   - RPE global (1-10) - ressenti d'effort
   - Sensation après: cramé / fatigué / ok / frais
   - Nutrition: bidons bus, solide mangé, fringale?
   - Douleurs éventuelles
   - Notes libres (optionnel)
5. Si séance B (force): nb de blocs faits, cadence tenue?
6. Calculer la semaine (semaine 1 = 26 jan)
7. Créer le fichier `seances/semaine-XX/YYYY-MM-DD-type.md`
8. Ajouter au CSV: `./bin/strava csv <id> <semaine> <type> <rpe> <sensation> >> data/seances.csv`
9. Cocher la séance dans `seances/semaine-XX/bilan.md`

### Pour Renfo

1. Demander:
   - Exercices faits (squats, fentes, gainage...)
   - Durée
   - Sensation: tonique / neutre / rincé
2. Créer le fichier et cocher le bilan

## Format du fichier vélo

```markdown
# Séance du JJ/MM

## Infos

- **Type**: A (endurance) / B (force) / C (longue)
- **Semaine**: X/17

## Données Strava

- **Distance**: X km
- **D+**: X m
- **Durée**: X min
- **Vitesse moy**: X km/h
- **Vitesse max**: X km/h
- **Puissance moy**: X W (si dispo)
- **Calories**: X
- **Effort relatif**: X
- **PRs**: X (si > 0)
- **FC moy/max**: X bpm (si dispo)
- **Strava**: https://...

## Ressenti

- **RPE**: X/10
- **Sensation après**: X

## Nutrition

- **Bidons**: X
- **Solide**: X
- **Fringale**: non

## Notes

[notes libres]
```

## Exemple d'interaction

```
User: /seance
Claude: [lance ./bin/strava seance]
Claude: Dernière activité: "Sortie endurance" du 26/01
- 25 km, 52 m D+, 62 min
- 24.2 km/h moy, 92 W
- 3 PRs

C'est bien celle-ci? Type A (endurance)?

User: oui
Claude: RPE (1-10)?
User: 3
Claude: Sensation après? (cramé/fatigué/ok/frais)
User: frais
Claude: Nutrition - bidons bus?
User: 2/3
Claude: Solide mangé?
User: 1 barre
Claude: Fringale?
User: non
Claude: Notes à ajouter?
User: bonne reprise
Claude: ✓ Séance enregistrée: seances/semaine-01/2026-01-26-endurance.md
```
