# Regions and Societies: Districts

An Expansion Pack for [Regions and Societies](https://github.com/Regions-and-societies/Core-MMF). It simulates **the inside of a world tile**.

Core divides the planet into regions and gives each one a population. This adds the layer underneath: a settlement is a cluster of **districts**, one district is one local map of ground, and each district is a place with its own people and its own job.

## Why this is separate from Core

Core works at world scale: regions, ownership, population, the economy over a whole planet. Districts work at **sub-tile** scale, and they need per-settlement state that Core deliberately does not carry — Core stays cheap at worldgen and keeps districts as closed-form maths, never as objects.

So the line is drawn at **geometry versus life**:

| Core supplies | This expansion adds |
|---|---|
| `WorldScaleRules` — a tile is ~374 local maps, 23.4 km² | District demographics, and enclaves |
| `DistrictRules` — hex rings, occupancy, build time | The build-and-ruin lifecycle |
| `SettlementTier` — homestead through city | One economic sector per district, and its output |
| `EconomicSectorDef` — the sector vocabulary | Special structures |
| The region population and pressure model | District unrest |
| | A district management and inspection tool |

Everything in the left column is public API, documented in Core's Developer's Guide. Nothing here reaches into Core's internals.

## Scale, in short

A world tile is about 6 km across and 23.4 km² of ground, derived from RimWorld’s own travel clock: 3300 ticks to cross a tile at 2500 ticks an hour is 1.32 hours of marching. A district is one **fixed** piece of that ground, 0.0625 km² — the area a 250x250 map covers — which makes **374 districts to a tile**. It is deliberately not tied to the map size a player runs: doing that made the settlement ladder mean different things for different people, and put a city on two thirds of its tile at 500x500.

Settlements occupy a hex cluster of those maps:

| Tier | Districts | Nominal population | Supporting settlements |
|---|---|---|---|
| Homestead | 1 | 100 | 1 |
| Hamlet | 7 | 700 | 3 |
| Village | 19 | 1,900 | 6 |
| Town | 37 | 3,700 | 10 |
| City | 61 | 6,100 | 15 |

Even a city uses about a sixth of its tile, which is what leaves room for suburbs and farmland to be real rather than a fudge.

## Status

Design and backlog only. Nothing is built yet.

## Licence

See Core.
