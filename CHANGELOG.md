# Changelog

All notable changes to the LoL Gameplay Kit are documented here.
Format follows [Keep a Changelog](https://keepachangelog.com); versioning is semver.
0.x releases are internal; APIs may break between minors until 1.0.0.

## [Unreleased]

## [0.1.0] — 2026-07-09

### Added
- **Sample scenes**, fully self-contained inside the package (`Samples/Scenes/`): `KitShowcase`
  (service modules + calendar HUD), `InteractionDemo` (player/interactables/facing cone),
  `TooltipDemo` (uGUI TooltipPanel + hover item slots).  
- Package skeleton: embedded package at `Assets/GameplayKit`, asmdef-per-module topology
  (Core, Items, Flags, Calendar, Interaction, Contracts, Deduction, UI + Editor + Tests).
- The four integration contracts (save / RNG / events / config) as Core conventions,
  with the RNG contract enforced by an edit-mode source guard test.
- `GameplayKitConfig` (per-module enable toggles, loaded from `Resources`); per-module
  auto-discovered `IServiceRegistrar`s (the engine constructs registrars parameterlessly).
- **WorldFlags** (`LoLEngine-GameplayKit-Flags`): typed global variable store
  (bool/int/float/string), headless `WorldFlagStore` core, `IWorldFlagService`,
  save-integrated (`gameplaykit.flags`), pooled `WorldFlagChangedEvent`, live editor
  inspector window, sample, docs.
- **Calendar** (`LoLEngine-GameplayKit-Calendar`): day/phase counter with manual advance
  and save-safe id-keyed scheduled callbacks (`ICalendarService`, `CalendarConfig`,
  `gameplaykit.calendar` save domain), deterministic rollover event order, sample, docs.
- **Items** (`LoLEngine-GameplayKit-Items`): data-driven item definitions (`ItemDefinition`,
  `RarityDefinition`, typed custom-property bags), headless `ItemIndex` (id/tag/rarity
  queries), `IItemDatabaseService` + Resources-loaded `ItemDatabase`, edit-time validation
  with a menu command, sample, docs. Static content — deliberately no save domain or events.
- **Interaction** (`LoLEngine-GameplayKit-Interaction`): headless `InteractionResolver`
  (range/facing gates, nearest-wins, stable tie-break), `IInteractable`/`InteractableComponent`
  with LocString verbs, registry-based input-agnostic `InteractionDetectorComponent`
  (consumer calls `TryInteract()`), pooled focus/blur/interact events — including blur from a
  cached identity when the focused object is destroyed. Sample, docs.
- **Tooltip** (`LoLEngine-GameplayKit-UI`): headless `TooltipContent` model +
  `ITooltipService` (engine-free, UI-free logic), `ItemDefinition` binding with rarity-tinted
  titles, stock uGUI `TooltipViewComponent` (cursor-follow guarded for new-input-only
  projects) and hover `TooltipTriggerComponent`, sample, docs.
- **Contracts (Contracts-lite)** (`LoLEngine-GameplayKit-Contracts`): commissions with
  requirement predicates (has-item via a game-supplied `IContractItemCountProvider` adapter,
  flag checks via WorldFlags), calendar-day deadlines (inclusive deadline day, expiry on next
  day start), and rewards (flags applied, items emitted on `ContractCompletedEvent` for the
  game to grant).
- **Deduction (seed)** (`LoLEngine-GameplayKit-Deduction`): subject×property truth matrix
  (`DeductionMatrix`, `DeductionPropertyDefinition`), headless `KnowledgeBook` (reveal state +
  guess commitment with per-property `GuessReport`), `IKnowledgeService`,
  `gameplaykit.deduction` save domain, pooled reveal/guess events, sample, docs.
- Compatibility: LoL Engine 1.0.3, Unity 6000.0.
