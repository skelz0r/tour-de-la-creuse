# Comment utiliser ce dossier

## Structure

```
seances/
├── _template_seance.md      # Copier pour chaque séance
├── _template_bilan_semaine.md
├── semaine-01/
│   ├── bilan.md
│   ├── 2026-01-27-endurance.md
│   ├── 2026-01-29-force.md
│   └── 2026-02-01-longue.md
├── semaine-02/
│   └── ...
```

## Workflow

### Après chaque séance

1. Copier `_template_seance.md` dans le dossier de la semaine
2. Renommer: `AAAA-MM-JJ-type.md` (ex: `2026-01-27-endurance.md`)
3. Remplir les questions

### En fin de semaine

1. Ouvrir `bilan.md` de la semaine
2. Remplir le tableau récapitulatif
3. Noter les auto-évaluations
4. Décider des ajustements

## Créer une nouvelle semaine

```bash
cp -r semaine-01 semaine-XX
```

Puis vider le contenu du bilan.
