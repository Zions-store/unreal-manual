Copyright (C) 2026 ZionXiaoxiSuOGLocGo
SPDX-License-Identifier: GPL-3.0-or-later
# unreal-manual Changelog

## [2.4.0] - 2026-09-25 — Official-Documentation Gap Analysis Round
**Source**: full comparison against the official UE 5.8 documentation (chapter-tree scan + 13 deep-read pages via subagents)

### Added
- **Materials & Material Instances** chapter — editor shortcuts, master/instance workflow, constant vs
  dynamic instances, Static Switch compile-explosion and unwired-expression pitfalls
- **Lighting** chapter — light types × mobility table, Lumen enablement and its UE4-upgrade / Static-light /
  update-latency pitfalls, Lightmass legacy route, **Post Process Volume** section
- **Landscape & Foliage** chapter — Shift+2 entry, section-size guidance, Sculpt/Paint/Edit Layers/Spline,
  automatic collision, foliage-as-ISM, **Water System** pointer
- **Modeling Mode** chapter — Shift+5, PolyGroups, Accept model, output types, harvest-to-ISM
- **Level Blueprint** section (per-level orchestration, instance events, reusability pitfall) and
  **Blueprint Debugger** (breakpoints/watch pins)
- World Partition: **Data Layers** expanded — Asset (Editor vs Runtime), Data Layer Outliner,
  SetDataLayerInstanceRuntimeState, server-authority pitfall
- Animation: **Control Rig** section — Forwards/Backwards Solve, runtime integration paths, FK Control Rig
- **Paper 2D** chapter (sprite/flipbook/tile map, when-2D-makes-sense guidance) and
  **Mass Entity** chapter (crowd-scale awareness, when-not-to-use)
- Performance: **ISM/HISM** section (component-level sharing, Nanite→ISM, per-instance custom data) and
  **Unreal Insights** section (Trace → .utrace → Timing view, channel pitfall)
- GAS: **Newer Gameplay Systems (5.5+)** awareness table (Gameplay Camera / Targeting / Mover)
- **Production & Automation Extras** chapter — Source Control editor integration, Editor Python scripting
  (with MCP supersession note), Pixel Streaming, Motion Design / NNE / LWC adjacency table
- Symptom Router +4 rows; frontmatter keywords +18 (Lighting, Material, Landscape, Modeling Mode,
  Level Blueprint, Control Rig, Mass Entity, Paper 2D, ISM, Unreal Insights, ...)

## [2.3.0] - 2026-09-24 — Usability Audit Round
**Source**: usage-driven audit — retrieval tests (4 questions), gap tests (12 domains), subagent blind tests

### Fixed
- Restore CHANGELOG body to pristine v2.2.1 content: the 2026-06-30 security pass re-encoded the file and corrupted
  every non-ASCII character (em-dashes, arrows) into U+FFFD mojibake. Body is now byte-identical to the initial
  baseline; copyright header re-applied.
- C++ Delegates: added the missing `UPROPERTY(BlueprintAssignable)` pattern — without it dynamic multicast
  delegates never appear in Blueprint's Events list (previous answer was un-executable); noted the 4th
  DECLARE_MULTICAST_DELEGATE combination
- ANY_PACKAGE removal version unified to UE 5.5 (MCP compatibility table claimed 5.8)
- StateTree retitled "(UE 5.4+ Templates)" with 5.0–5.2 experimental note; Behavior Trees no longer
  dismissed as legacy — documented as still widespread (new chapter)
- Enhanced Input: version gate noted (plugin enabled by default since 5.1)
- Terminology: "custom inspectors" → property editors; Unity-coroutine aside now defers to the Appendix

### Added
- **Symptom Router** table (15 symptom → section rows) at the top
- **Navigation & AI Movement** chapter — NavMeshBoundsVolume setup, P-key visualization, AI MoveTo /
  AAIController::MoveTo, MOVE_NavWalking, reachability pitfalls
- **Behavior Trees** chapter — Blackboard, composites, tasks/decorators/services, EQS, BT vs StateTree guidance
- Character Movement: RotationRate, bOrientRotationToMovement, GroundFriction, BrakingFrictionFactor rows
  - feel-tuning cheat sheet (floaty / icy / sluggish-turn fixes)
- **UMG Responsive Layout** — anchors table, DPI Scale Rule, safe zones, absolute-Canvas pitfall
- **Packaged Build Crashes (Crash Reporter)** — Saved/Crashes, -log, PDB symbols, editor-only culprits
- **Blueprint Function Library** section (BP library + UBlueprintFunctionLibrary C++ pattern)
- **Physics Constraints** section — Actor/component/handle forms, constraint types table, pitfalls
- **Dedicated Servers** section — Server.Target.cs, packaging, client connect, listen-server alternative
- **Sequencer (Cinematics)** chapter — vs Blueprint Timeline, Event track, camera cuts
- Touch Input note (Enhanced Input) and Editor Utility Widgets note (UMG)
- MCP configuration section rewritten: global opencode.json (current practice) vs per-project .mcp.json
- Frontmatter keywords +13 (NavMesh, pathfinding, Behavior Tree, Blackboard, StateTree, Sequencer,
  dedicated server, crash report, touch input, anchors, DPI scale, physics constraint, function library)

## [2.2.1] - 2026-06-30 — Audit Bug Fixes
  baseline; copyright header re-applied.

## [2.2.1] - 2026-06-30 — Audit Bug Fixes
**Source**: project-ledger quality audit

### Fixed
- H1: Fix `GetActorOfClass` return type mismatch (added `Cast<>`)
- H2: Fix `OnJump()` undeclared `Character` variable (use inherited `Jump()`)
- H3: Version range contradiction resolved (body references frontmatter)
- H4/H5: Duplicate content blocks replaced with cross-references (BlueprintPure, Compatible Skeleton)
- H6: Substrate version corrected to UE 5.5+
- M1/M2: CHANGELOG semver standardized
- M4: Typo `Unpaus` → `Unpause`
- M9: RootComponent contradiction resolved

### Added
- C++ Delegates section (`DECLARE_DELEGATE`, `DECLARE_DYNAMIC_MULTICAST_DELEGATE`)
- Smart Pointers section (`TSharedPtr`, `TUniquePtr`, `TWeakPtr`, `TSharedRef`)
- Async Loading section (`FStreamableManager::RequestAsyncLoad` with examples)

---

## [2.2.0] - 2026-06-30 — Advanced Gameplay Patterns + Substrate + Tool Ecosystem
**Source**: ThirdPersonTest project-ledger development session

### Added
- **Advanced Gameplay Patterns** (new standalone chapter):
  - Compatible Skeleton retargeting workflow (IK Rig fallback for Mixamo in UE5.8)
  - C++ BlueprintPure expanded example for multi-state AnimBP access
  - Checkpoint/Respawn system: Controller-stored Transform, respawn position restoration, full state reset
  - Combo attack input cache pattern: CachedInputTime + AttackCooldown + Tolerance + AnimNotify chain
- **Animation → Compatible Skeleton Retargeting**: When IK Rig fails, use Manage Compatible Skeletons for lightweight runtime retargeting
- **Substrate Material System**: UE5.5+ next-gen material basics, BSDF graph, MakeSubstrateMaterialAttributes migration
- **Tool Ecosystem**: Understand-Anything knowledge graph integration, opencode MCP launch prerequisite (must start from project directory)
- Copyright notice + SPDX identifier added to SKILL.md
- Version metadata (2.3.0) added to SKILL.md frontmatter

### Changed
- Compatibility updated to include UE5.8

---

## [2.1.0] - 2026-06-25 — MCP + ABP + Project Knowledge Board
**Source**: ThirdPersonTest UE 5.8 project (crouch animation + MCP integration session)

### Added
- **MCP Integration** (new standalone chapter): Official vs community MCP comparison, deployment workflow (plugin copy
  → build → Python venv → opencode config), UE5.8 compatibility fixes (`ANY_PACKAGE`→`nullptr`, `BufferSize` shadow
  warning), MCP limitations (no AnimBP support, no asset deletion, static mesh assignment restrictions).
- **Animation → ABP Creation & Troubleshooting**: Proper AnimBP creation (Animation Blueprint from context menu, not
  generic `create_blueprint`), AnimGraph verification, copy-paste between ABPs, Event Graph variable update chain
  pattern, C++ `BlueprintPure` getter for AnimBP access.
- **Troubleshooting**: Live Coding active blocking builds; `ANY_PACKAGE` undeclared fix for UE5.5+; ABP variable name whitespace sensitivity diagnostics.
- **Project Knowledge Board**: New section at end of manual — per-project memory entries with key paths, class names, engine version, fix history. Enables session-to-session continuity without polluting global knowledge sections.

### Principles
- Global reusable knowledge → insert into matching core chapter (Animation, MCP, Troubleshooting).
- Project-specific memory → Project Knowledge Board with date + project name header.
- Variable names in ABP are whitespace-sensitive (`MovementComponent` ≠ `Movement Component`) — always verify exact spelling in source My Blueprint.
- ABP copy-paste across skeletons works only if both ABPs share the same target skeleton.

---

## [2.0.0] - 2026-06-24 — Major Update
**Source**: ThirdPersonTest UE 5.8 project hands-on summary

### Added
- **Lifecycle**: CDO Constructor asset loading (FObjectFinder failure under World Partition OFPA, 3 alternatives), hot-reload vs full-rebuild decision matrix, Blueprint CDO rebuild overwrite warnings.
- **Enhanced Input**: Multi-IMC simultaneous loading with BeginPlay fallback, ETriggerEvent full event table, interface calling conventions (UINTERFACE MinimalAPI+NotBlueprintable → no `Execute_` generation).
- **Animation**: AnimNotify architecture (UAnimNotify → Cast interface → drive game logic).
- **Character Movement**: Crouch settings (SetCrouchedHalfHeight replaces deprecated member), state bitfield packing, wall-jump pattern.
- **Collision**: SweepMultiByObjectType vs SweepMultiByChannel selection guide, Actor Tag system for AI target identification.
- **StateTree AI** (new standalone section): UE5 default NPC behavior system, StateTreeComponent + AAIController bridging, NavMesh debugging.
- **UMG**: WidgetComponent Screen vs World rendering space, RequestRedraw trigger conditions, GetWidgetFromName bypass for BP events.
- **Level Management**: World Partition OFPA activation detection (`__ExternalActors__/` + `__ExternalObjects__/`) and development implications.
- **Troubleshooting**: Output Log search quick-reference, benign PIE log identification, UE_LOG debugging template.

### Principles
- Additions inserted into matching sections, not appended at end.
- Keep original heading hierarchy and code style consistent with the base manual.
- No project-specific class names or paths.

---

## [1.0.0] - 2026-06-20 — Initial Release
**Source**: openSkills project launch (created via skill-creator)

### Added
- Unreal Engine core concepts: Actor/Pawn/Character, GameMode/GameState/PlayerController framework, Blueprint vs C++,
  rendering, physics, animation, UMG UI, Enhanced Input, network replication, UPROPERTY/UFUNCTION macros, GameInstance
  lifecycle, C++ vs Blueprint tradeoffs.
- 62.2KB SKILL.md.
