# Divert Diplomat

A single-file, offline **diplomatic-relations & aircraft-diversion checker** for aircrew — a
situational-awareness planning aid for "does country X hate country Y?" questions when planning
routes and diversions.

> ⚠️ **Not an operational source.** Curated mid-2026 snapshot for situational awareness only.
> Relations, airspace and entry rules change fast — always verify against current NOTAMs, company
> Ops/Dispatch, State AIP and overflight/landing permits. If it disagrees with an official source,
> the official source wins.

## Features

**Relations check** — pick two countries, get a green / amber / red verdict with three detail levels:

| Level | Shows |
|-------|-------|
| **Cockpit** | one-line verdict, terse enough to use mid-diversion |
| **Brief** | + the working relationship and each country's own airspace/instability/recognition status |
| **Full** | + full historical background and passenger/crew implications |

**Diversion checker** — build a scenario and get a combined assessment:

- Type an **ICAO code** (`LTFE`, `EGKK`, `BKPR`…) or a **registration mark** (`G`, `N`, `4X`, `TC`…),
  or pick a country. Codes resolve to airport + country automatically.
- Flags: diversion-field conflict/airspace status · **non-recognised entities** (N. Cyprus, Kosovo,
  Taiwan) · **aircraft-state hostility** (e.g. an Israel- or Western-registered aircraft into a
  hostile/sanctioned state) · **passenger restrictions** (e.g. Gibraltar→Spain) · **crew passport
  bars** · **crew nightstop / visa** issues (e.g. US C-1/D).

Other: light / dark (day / night) theme toggle, works fully offline, opens on an iPad / EFB.

## Usage

Open `index.html` in any browser. No install, no dependencies, no network required.

## How it works

All data is a curated static dataset baked into `index.html`:

- `C` — per-country flags (`status`, `conflict`, `airspace`, `entity`, `passportBar`, `crewVisa`)
- `REL` — bilateral relationships keyed `"A|B"` (sorted), each with `l1`/`l2`/`l3` detail and optional `pax`/`crew`
- `ICAO2` / `ICAO1` / `ICAO_EXACT` — ICAO location-indicator prefixes → country
- `AIRPORTS` — named airports for display
- `REG` — aircraft registration marks → country

To add a bilateral case, add a `REL` entry. To flag a country, add fields to its `C` entry.
Passenger restrictions only appear when the `REL` pair has an explicit `pax` field.

## Coverage & caveats

Data is a **mid-2026 snapshot** and reflects general historical patterns. ~150 countries/territories
resolve; notable disputes are written up in detail, others default to "stable — verify". This is a
planning aid, **not** a legal, operational or navigational source.

## Licence

MIT — see [LICENSE](LICENSE).
