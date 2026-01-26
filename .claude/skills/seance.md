# Skill: Enregistrer une séance

Enregistre les résultats d'une séance d'entraînement vélo ou renforcement.

## Déclencheurs

- `/seance`
- "j'ai fait une séance"
- "enregistrer ma sortie"

## Instructions

1. Demander le type de séance:
   - A (endurance)
   - B (force)
   - C (longue)
   - Renfo (renforcement)

2. Demander la date (proposer aujourd'hui par défaut)

3. Calculer la semaine correspondante (semaine 1 = 26 jan - 1 fév)

4. Poser les questions selon le type:

### Pour séances vélo (A, B, C)

**Avant:**
- Forme au réveil (1-5)
- Fatigue jambes (1-5)

**Pendant:**
- Durée réelle
- Distance
- D+ (si connu)
- Lien Strava (optionnel)
- RPE global (1-10)
- Nutrition: bidons bus, solide mangé
- Fringale? Coup de chaud/froid?

**Si séance B (force):**
- Nb de blocs faits
- Cadence tenue?

**Après:**
- Sensation générale: cramé / fatigué / ok / frais
- Douleurs éventuelles

### Pour Renfo

- Exercices faits (squats, fentes, gainage...)
- Durée
- Sensation: tonique / neutre / rincé

5. Créer le fichier dans `seances/semaine-XX/YYYY-MM-DD-type.md`

6. Mettre à jour la case correspondante dans `seances/semaine-XX/bilan.md` (cocher la séance)

## Format du fichier

```markdown
# Séance du JJ/MM

## Infos
- **Type**: X
- **Semaine**: X/17
- **Durée**: Xh
- **Distance**: X km
- **D+**: X m

## Ressenti
- **Forme avant**: X/5
- **RPE**: X/10
- **Sensation après**: X

## Nutrition
- Bidons: X
- Solide: X
- Fringale: non

## Notes
[notes libres si mentionnées]
```

## Exemple d'interaction

```
User: /seance
Claude: Quel type de séance?
- A (endurance)
- B (force)
- C (longue)
- Renfo

User: B
Claude: Date? (défaut: aujourd'hui 26/01)
User: aujourd'hui
Claude: Durée réelle?
User: 1h10
Claude: Distance?
User: 28km
...
Claude: Séance enregistrée dans seances/semaine-01/2026-01-26-force.md
```
