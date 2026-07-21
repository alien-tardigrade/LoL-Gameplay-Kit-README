# LoL Gameplay Kit — Data-Driven Gameplay Systems for Unity

[![Unity Version](https://img.shields.io/badge/Unity-6000.0%2B-blue.svg)]()
[![Version](https://img.shields.io/badge/Version-0.1.0-orange.svg)](CHANGELOG.md)
[![Docs](https://img.shields.io/badge/Docs-lol--kit.moomoo.games-brightgreen.svg)](https://lol-kit.moomoo.games/)

> LoL Engine is the plumbing. The Gameplay Kit is the grammar.

Data-driven gameplay systems for simulation / management / narrative-economy games, built on
the [LoL Engine](https://lol-engine.moomoo.games/). Every module obeys four contracts the engine
makes possible: **versioned save state**, **deterministic named-stream RNG**, **typed pooled
events**, and **ScriptableObject config with LocString-native text**.

## Documentation

**Full documentation site: https://lol-kit.moomoo.games/**

| Guide | |
|---|---|
| [Home](https://lol-kit.moomoo.games/) | Overview, the four contracts, getting started |
| [Cheatsheet](https://lol-kit.moomoo.games/CHEATSHEET/) | Quick reference for every module |
| [World Flags](https://lol-kit.moomoo.games/worldflags/) | Typed global variable store |
| [Calendar](https://lol-kit.moomoo.games/calendar/) | Semantic days/phases + persistent scheduling |
| [Items](https://lol-kit.moomoo.games/items/) | Item definitions + database |
| [Tooltip (UI)](https://lol-kit.moomoo.games/tooltip/) | Tooltip service + widgets |
| [Interaction](https://lol-kit.moomoo.games/interaction/) | Interactables, verbs, focus |
| [Contracts](https://lol-kit.moomoo.games/contracts/) | Commissions with deadlines and rewards |
| [Deduction](https://lol-kit.moomoo.games/deduction/) | Hidden-property knowledge matrices |

## Modules (v0.1.0 — Tier 1)

| Module | What it does |
|---|---|
| **Core** | Shared primitives, config, contracts |
| **WorldFlags** | Typed global variable store |
| **Calendar** | Semantic days/phases + persistent scheduling |
| **Items** | Item definitions + database |
| **Tooltip (UI)** | Tooltip service + widgets |
| **Interaction** | Interactables, verbs, focus |
| **Contracts** | Commissions with deadlines and rewards |
| **Deduction** | Hidden-property knowledge matrices |

Enable only what you use via the `GameplayKitConfig` asset; each module's service registrar is
auto-discovered by the engine. Games reference module assemblies, never the reverse.

## The four contracts

1. **Save** — every stateful module ships a versioned save domain (`gameplaykit.<module>`), migration-ready from v1.
2. **RNG** — no `UnityEngine.Random`, ever (enforced by an edit-mode guard test); draws come from `IRngService` named streams.
3. **Events** — modules communicate outward via typed pooled `GameEvents`; no hard sibling references where an event suffices.
4. **Config** — tuning lives in ScriptableObjects; player-facing strings are LocStrings, never raw strings.

## Requirements

- **Unity** 6000.0 or later
- **LoL Engine** (`games.moomoo.lol-engine`) ≥ 1.0.3

## License & Support

- **Changelog** — see [CHANGELOG.md](CHANGELOG.md)
- **Support** — unitysupport@moomoo.games
- **Documentation** — https://lol-kit.moomoo.games/

---

*This repository is the public documentation host for the LoL Gameplay Kit. The site under
[lol-kit.moomoo.games](https://lol-kit.moomoo.games/) is published to this repo's `gh-pages`
branch from the Kit's source repository — this default branch intentionally holds only the
README, changelog, and license.*
