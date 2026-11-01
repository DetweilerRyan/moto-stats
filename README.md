# moto-stats

A small hobby web app that turns [Calimoto](https://calimoto.com) GPX exports from one or more riders into a combined trip recap: tracks on a map, per-rider stats, and head-to-head comparisons on the roads riders have in common.

## Jobs To Be Done

**Primary job performer:** a motorcycle trip organizer or a rider in a friend group.

**Main job statement:**
> When a group of us has finished riding together (or separately on the same roads), I want to combine everyone's recorded rides in one place, so I can relive the trip and see how each rider did, without manually stitching files or spreadsheets together.

**Related jobs**
| Type | Job |
|------|-----|
| Functional | Combine multiple rides from multiple riders into one trip view |
| Functional | See my own and others' stats for the trip |
| Functional | Compare riders on the same stretches of road |
| Functional | See all tracks rendered on a map |
| Emotional | Feel part of a shared experience; friendly bragging rights |
| Social | Share a recap with the group with a single link |

## Outcome-Driven Innovation (desired outcomes)

Format: *Minimize the time / likelihood / effort to...* Importance is the expected priority for v0.1 (H/M/L).

| # | Desired outcome | Priority |
|---|-----------------|----------|
| 1 | Minimize the time it takes to get multiple riders' GPX files into one trip | H |
| 2 | Minimize the effort to identify which rider each ride belongs to | H |
| 3 | Minimize the time to see all tracks on a single map | H |
| 4 | Minimize the time to see each rider's totals (distance, moving time, avg/max speed, elevation) | H |
| 5 | Minimize the effort to see lean angle stats (max/avg left and right) when present in the data | M |
| 6 | Minimize the effort to find which roads riders have in common | H |
| 7 | Minimize the time to see who was fastest on a shared road segment | H |
| 8 | Minimize the effort to share the recap with the group | H |
| 9 | Minimize the likelihood that private locations (e.g. home) are exposed | M (undecided) |
| 10 | Minimize the likelihood of losing or duplicating uploaded rides | M |

## v0.1 Scope

**In**
- Create a trip; access is by unlisted link only (no accounts). Visitors choose a display name.
- Each rider can upload their own GPX files, or an organizer can upload on behalf of others (assign rides to a rider).
- Parse Calimoto GPX, including extension data (e.g. lean angle) when present.
- Map rendering of all tracks (MapLibre + OSM tiles), colored per rider.
- Per-rider stats: distance, moving time, avg/max speed, elevation gain, lean angle when available.
- Whole-ride comparison between riders.
- Shared road segment matching and per-segment comparison (time/speed).

**Out (later)**
- Liveblocks realtime collaboration (presence, cursors, shared viewport, annotations).
- Accounts/OAuth.
- Privacy zones (start/end trimming): undecided, to be revisited.

## Tech stack
- Next.js + TypeScript on Vercel
- Vercel Postgres with Drizzle ORM
- MapLibre GL with OpenStreetMap tiles
- Liveblocks (post v0.1)

## Open questions
- Exact extension fields in Calimoto GPX exports (a sanitized sample will be added to the repo).
- Segment matching approach (map-matching to OSM vs. geometric proximity of tracks).
- Privacy handling of start/end locations.
- Handling of large files and many rides per trip.
