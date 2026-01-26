# Préparation Grand Tour de la Creuse

**Objectif**: Finir le tour (22-24 mai 2026)

## La course

- 5 étapes / 300 km / 4000 m D+
- Groupe < 28 km/h
- Lac de Vassivière (Creuse)

## Structure du dossier

```
tour-de-la-creuse/
├── bilan.md          # Synthèse profil + stratégie
├── suivi.md          # Check-list 17 semaines
├── seances/          # Suivi détaillé par semaine
├── data/
│   └── seances.csv   # Données pour la webapp
├── webapp/           # Dashboard de suivi
├── bin/
│   ├── meteo         # Météo 7j avec indicateurs vélo
│   ├── strava        # Récupérer activités Strava
│   ├── strava-auth   # Auth OAuth Strava
│   └── webapp        # Lancer le dashboard local
└── .claude/skills/   # Skills Claude (/seance, /bilan, /planification)
```

## Webapp

Dashboard local pour visualiser la progression.

```bash
./bin/webapp
```

Affiche : totaux (séances, km, D+, temps), timeline par semaine, stats par séance avec lien Strava.

## Intégration Strava

Les séances vélo sont automatiquement importées depuis Strava.

```bash
./bin/strava              # Liste les 5 dernières activités
./bin/strava seance       # Données formatées pour /seance
./bin/strava csv ...      # Export CSV pour la webapp
```

Setup initial : voir `CLAUDE.md` section Outils.

## Utilisation avec Claude

### Enregistrer une séance
```
/seance
```

### Faire le bilan de la semaine
```
/bilan
```

## Planning

| Phase | Semaines | Focus |
|-------|----------|-------|
| Base | 1-4 (jan-fév) | Régularité, endurance |
| Force | 5-9 (fév-mar) | Gros braquet, volume ↑ |
| Spécifique | 10-14 (avr) | Enchaînements WE |
| Affûtage | 15-16 (mai) | Volume ↓, fraîcheur |
| Course | 17 | 22-24 mai |

## Semaine type

- **A**: Endurance 1h15-1h30
- **B**: Force 1h-1h15 (blocs gros braquet)
- **C**: Longue (2h → 4h progressif)
- **Renfo**: Lafay 2x/semaine
