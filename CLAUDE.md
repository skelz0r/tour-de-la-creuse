# Instructions Claude - Tour de la Creuse

## Contexte

Préparation pour le Grand Tour de la Creuse (22-24 mai 2026).
Cycliste: 36 ans, 67kg, basé à Bordeaux, objectif = finir le tour.

## Fichiers importants

- `stats.md` - **Stats Strava de référence** (vitesses, records, estimations)
- `bilan.md` - Synthèse du profil et de la stratégie
- `suivi.md` - Check-list globale des 17 semaines
- `seances/` - Dossier avec le suivi détaillé
- `fiches/` - Guides techniques (sorties, nutrition, Lafay, peloton)
- `data/seances.csv` - Données séances pour export web
- `webapp/` - Dashboard de suivi (timeline, stats, liens Strava)
- `bin/meteo` - Script météo 7 jours avec indicateurs vélo
- `bin/strava` - Récupérer les dernières activités Strava
- `bin/strava-auth` - Flow OAuth pour générer le refresh_token
- `.env` - Credentials Strava (crypté via git-crypt)

## Commandes disponibles

### `/seance`
Enregistrer une séance. Poser les questions du template et créer le fichier.
Pour les séances vélo: toujours demander le lien Strava.

### `/bilan`
Faire le bilan de la semaine. Calculer le taux de complétion et poser les questions d'auto-évaluation.

### `/planification`
Proposer des créneaux vélo pour la semaine selon la météo et le plan d'entraînement.

## Calcul des semaines

Semaine 1 = 26 janvier 2026. Course = semaine 17.

```
Phase 1 (Base): semaines 1-4
Phase 2 (Force): semaines 5-9
Phase 3 (Spécifique): semaines 10-14
Phase 4 (Affûtage): semaines 15-16
Course: semaine 17
```

## Stats clés (voir stats.md pour détails)

- Moyenne générale: ~23 km/h
- Endurance: 20-22 km/h → 1h15 = ~25 km, 1h30 = ~30 km
- Sortie la plus longue: 76.5 km
- Point de départ: très bas (quasi rien depuis octobre 2025)

## Parcours Bordeaux

| Parcours | Distance | D+ | Durée estimée | Usage | Strava |
|----------|----------|-----|---------------|-------|--------|
| Côtes court | 31km | 256m | 1h20-1h30 | Force (B), semaine | [lien](https://www.strava.com/activities/10659306067) |
| Côtes long | 55km | 402m | 2h-2h15 | Longue (C) avec D+ | [lien](https://www.strava.com/activities/14731308903) |

Proposer selon forme et phase:
- Phase 1-2: "Côtes court" pour habituer aux montées
- Phase 2+: "Côtes long" quand 31km bien digéré

## Ton

- Concis, direct
- Bienveillant mais pas complaisant
- Rappeler l'objectif: finir, pas performer
- Français

## Outils

### Script météo (`bin/meteo`)
```bash
./bin/meteo [jours] [lieu]  # défaut: 7, Bordeaux
./bin/meteo 3               # 3 prochains jours à Bordeaux
./bin/meteo 5 Paris         # 5 jours à Paris
```
Affiche météo horaire (7h-20h) avec jour de la semaine et indicateurs:
- ✅ = OK (pluie < 30%)
- 🤷 = ça peut le faire (pluie 30-50%)
- ❌ = mort (pluie > 50% ou préc. > 0.5mm)

Requiert: `jq`

### Scripts Strava (`bin/strava`, `bin/strava-auth`)

**Setup initial:**
1. Créer une app sur https://www.strava.com/settings/api
2. Mettre `localhost` comme Authorization Callback Domain
3. Créer `.env` avec `strava_client_id` et `strava_client_secret`
4. Lancer `./bin/strava-auth` pour générer le `strava_refresh_token`
5. Ajouter le token au `.env`

**Usage:**
```bash
./bin/strava              # 5 dernières activités
./bin/strava list 10      # 10 dernières
./bin/strava last         # JSON dernière activité
./bin/strava get <id>     # JSON activité spécifique
./bin/strava seance       # Données formatées pour /seance
./bin/strava seance <id>  # Idem pour une activité spécifique
./bin/strava csv <id> <sem> <type> <rpe> <sens>  # Ligne CSV
```

Requiert: `curl`, `jq`, `python3` (auth uniquement)

### Webapp (`bin/webapp`)
```bash
./bin/webapp        # Lance sur port 8080
./bin/webapp 3000   # Port custom
```
Ouvre automatiquement le navigateur.

**Structure:**
- `webapp/index.html` - Single page app (HTML + JS inline)
- `data/seances.csv` - Données source
- `_site/` - Build généré (gitignored)

**Déploiement:**
- GitHub Pages via `.github/workflows/deploy.yml`
- Push sur main → build automatique → deploy
- Le workflow copie `index.html` + `seances.csv` dans `_site/`

**Format CSV (`data/seances.csv`):**
```
date,semaine,type,nom,distance_km,denivele_m,duree_min,vitesse_moy,vitesse_max,puissance_moy,calories,effort_relatif,prs,fc_moy,fc_max,rpe,sensation,strava_id,embed_token
```

**Affichage par séance:**
- Badge type (A/B/C) avec couleur
- Nom, date
- Stats: distance, D+, durée (min), vitesse moy, puissance, PRs
- Lien Strava
- Sensation avec emoji

**Totaux en haut:**
- Nb séances, km total, D+ total, temps total

### Liens Google Calendar
Format pour créer un événement:
```
https://calendar.google.com/calendar/render?action=TEMPLATE&text=TITRE&dates=YYYYMMDDTHHMMSS/YYYYMMDDTHHMMSS&details=DESCRIPTION&location=LIEU
```

## Quand l'utilisateur revient

1. Calculer la semaine en cours
2. Vérifier les séances enregistrées cette semaine
3. Proposer soit `/seance` soit `/bilan` soit `/planification` selon le contexte
