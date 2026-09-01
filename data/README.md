# Data

This folder contains the datasets used in the March Madness betting analytics project.

## Files

### `KenPom_Barttorvik.csv`

Team-level NCAA basketball statistics compiled from KenPom and BartTorvik-style metrics across multiple seasons.

The dataset includes variables related to:

- offensive and defensive efficiency
- shooting performance
- rebounding
- turnover rates
- free-throw rates
- strength of schedule
- team talent and ranking metrics

These team-level statistics are joined to tournament matchups and converted into Team A minus Team B differences for modeling.

### `Tournament_Matchups.csv`

NCAA tournament matchup data used to construct historical game-level observations.

The file contains team, seed, round, score, and season information. Historical games are paired into Team A / Team B matchups, while the supplied 2026 rows are treated as future matchup candidates.

## Usage

The analysis expects both files to be stored in this directory:

```text
data/
├── KenPom_Barttorvik.csv
└── Tournament_Matchups.csv
