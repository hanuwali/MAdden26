# Madden 26 – 3D Offline Ultra Simulation Edition

## Vision Statement

Deliver a fully offline, single-player, AAA American football simulation that prioritizes realism, authentic broadcast presentation, and deep football intelligence over arcade pacing or online-service monetization loops.

---

## 1) Core Engine Requirements

### 1.1 Rendering System

- **PBR pipeline** for player gear, turf, stadium materials, and weather interactions.
- **Real-time lighting + dynamic shadows** with cascaded shadow maps for field-wide consistency.
- **Volumetric stadium lighting** for night games, foggy weather, and high-intensity intros.
- **4K support** with dynamic resolution fallback for stable frame-time.
- **60 FPS baseline / 120 FPS performance mode** through quality presets and scalable post-processing.
- **HDR output** with calibrated luminance and contrast profiles for turf and uniforms.
- **Advanced camera framework** with cinematic rails, handheld emulation, and tactical zoom.
- **Animation blending system** synchronized with locomotion and ball-state transitions.

Optional premium features (hardware-dependent):
- Ray-traced reflections
- Selective global illumination path

### 1.2 Performance Targets

- Console target: 60 FPS quality mode, 120 FPS performance mode where available.
- PC target: scalable settings from 1080p medium to 4K ultra.
- Input latency budget: less than 80 ms end-to-end for gameplay camera modes.

---

## 2) Stadium System

### 2.1 Venue Fidelity

- Fully modeled architecture for all 32 NFL stadiums.
- Accurate field dimensions, hash spacing, sideline geometry, and team branding zones.
- Stadium-specific atmosphere profiles (chant cadence, crowd density, PA characteristics).

### 2.2 Dynamic Environment

- Time-of-day system with sun angle progression and shadow movement.
- Weather matrix:
  - Clear
  - Rain (wet-turf friction penalty, ball security modifier)
  - Snow (acceleration/cutting penalty, visibility shift)
  - Wind (kick arc, deep-ball drift, punt hang-time variance)

### 2.3 Crowd Simulation

- Multi-tier crowd LOD (skeletal near camera, shader-instanced distant sections).
- Excitement model driven by context events:
  - Third down
  - Red-zone snaps
  - Turnovers
  - Explosive plays
- Home-field modifier influences pre-snap audibles and composure checks.

---

## 3) Player Model System

- High-resolution player models with archetype-specific body composition.
- Height/weight scaling tied to collision capsule and locomotion acceleration curves.
- Jersey/cloth physics with constrained secondary motion.
- Helmet and visor reflection probes.
- Progressive sweat and dirt layers blended by play count, weather, and tackle intensity.
- Emotional states rendered through facial animation sets:
  - Celebration
  - Frustration
  - Fatigue
  - Focus intensity

---

## 4) Animation System

### 4.1 Motion Foundation

- Motion-captured base library per position group.
- Procedural overlays for contextual adaptation (reach, twist, stumble, foot recovery).
- Direction-aware run cycles for cuts, spins, and stutter steps.

### 4.2 Interaction Logic

- Context tackling: wrap, hit-stick, drag, gang tackle, ankle tackle.
- Momentum-driven transitions using velocity vectors and mass delta.
- Foot-plant validation to reduce skating on sudden change-of-direction.
- Fatigue transforms stride length, acceleration, and recovery windows.

### 4.3 Contact Quality

- Physics-informed collision impulse contributes to animation branch selection.
- Blend-to-ragdoll threshold for high-force edge cases.

---

## 5) Advanced Physics Engine

- Player mass and impact calculations for tackle outcomes.
- Ballistics model:
  - Launch angle
  - Velocity
  - Spin rate
  - Wind influence
- Turf friction coefficients per weather state.
- Momentum conservation in pile-ups and sideline hit interactions.
- Injury probability model based on force, angle, fatigue, and prior wear.

---

## 6) Offline AI System

### 6.1 Offensive AI

- Pre-snap defensive shell recognition.
- Protection adjustment against pressure indicators.
- Risk-aware throw decisions (coverage leverage, down/distance, game context).
- Pocket navigation with edge pressure weighting.
- Clock and score-aware aggression profile.
- Situation-triggered scramble/play-action behavior.

### 6.2 Defensive AI

- Coverage disguise system and post-snap rotation logic.
- Dynamic assignment switching to counter route combinations.
- Gap-integrity enforcement for run fits.
- Mobile-QB contain logic with spy and lane discipline.
- Play repetition detection and tendency exploitation.

### 6.3 Adaptive Learning (Local-Only)

- Tracks user tendencies by formation, concept family, down/distance, and field zone.
- Generates weighted counters (coverage shell shifts, pressure packages, alignment depth).
- Updates after each drive; persists in local save profile.
- No external telemetry, no cloud sync.

(See detailed model in `docs/ai/adaptive_ai_local_model.md`.)

---

## 7) Game Modes (Offline Only)

### 7.1 Exhibition

Quick-play with full broadcast package and configurable simulation settings.

### 7.2 Franchise Mode

- 30+ year simulation support.
- Player progression, morale, fatigue, injury, and recovery pipelines.
- Contract negotiation with cap-aware AI behavior.
- Trade market logic with team-needs modeling.
- Coaching staff and scouting department management.
- Draft pipeline: scouting, combine metrics, class generation, AI war rooms.
- Retirement, records, and Hall of Fame logic.
- Optional team relocation (offline ecosystem only).

### 7.3 Career Mode (Superstar)

- Create-a-player with position-specific archetypes.
- Skill tree progression and training drills.
- Media/reputation and locker-room chemistry systems.
- Performance grading and milestone tracking.
- Offline endorsement simulation (no real-money economy).

### 7.4 Season Mode

Single-season flow with standings, playoffs, and postseason records.

---

## 8) Playbook System

- Full offensive and defensive playbook libraries.
- Custom play creator with route/node editing.
- Formation editor and defensive assignment editor.
- Local-only playbook save/load profiles.
- AI counter-adaptation against overused concepts.

---

## 9) Broadcast Presentation System

- Cinematic open package tied to teams/stadium/time/weather.
- TV-style camera cuts for pre-snap, post-play, and replays.
- Dynamic replay director with event scoring (big hit, touchdown, turnover, clutch conversion).
- On-screen stat overlays, drive summaries, and halftime recap package.
- Commentary state machine with context-aware lines and reduced repetition logic.

---

## 10) Audio System

- Layered crowd bed + event-driven hype stingers.
- Stadium chants and PA identity per venue.
- Player callouts and line-audible mix priorities.
- Weather-dependent Foley and ambience.
- Referee announcement pipeline.
- Spatial audio mix buses for field-level realism.

---

## 11) UI / UX System

- Next-gen visual design language with fast transitions.
- Franchise dashboard with cap, roster health, and weekly objectives.
- Player card and comparison views.
- Depth chart, injury report, and analytics pages.
- Input-optimized navigation for controller and mouse/keyboard.

---

## 12) Statistics & Analytics

- Full season/career/franchise record books.
- Advanced metrics:
  - QB rating
  - Completion percentage
  - Yards after contact
  - Pressure rate allowed/created
  - Coverage rating
  - Sack rate
  - Turnover differential
- Graph-based trends over week, season, and multi-year franchise windows.

---

## 13) Full Team Implementation (32 NFL Teams)

All teams included with branding and metadata. Source of truth: `data/nfl_teams.json`.

---

## 14) Customization System

- Custom teams and uniforms.
- Custom stadium templates.
- Logo editor.
- Attribute and roster editing.
- League rule tuning and gameplay sliders.
- Quarter length and simulation profile presets.

---

## 15) Realism Settings

Exposed sliders and presets:
- Injury frequency
- Penalty frequency
- AI difficulty/adaptation intensity
- Fatigue realism
- Speed scaling
- Fumble frequency
- Pass accuracy realism

---

## 16) Performance Optimization

- LOD scaling across players/crowd/stadium assets.
- Dynamic resolution scaling.
- CPU/GPU workload balancing with frame pacing telemetry.
- Memory budgets by mode (gameplay, replay, franchise hub).
- Fast local loading and deterministic save writes.

---

## 17) Suggested Technical Stack

- Unreal Engine 5 runtime and toolchain.
- C++ for simulation systems and performance-critical gameplay loops.
- Blueprint for content assembly and cinematic scripting.
- Local save/telemetry architecture only.

---

## Offline Compliance Gates (Hard Requirements)

1. No online multiplayer subsystems compiled into shipping profile.
2. No login/account gating for any mode.
3. No microtransaction storefront code paths.
4. No cloud-only save dependency.
5. All adaptation and analytics remain local to the player’s machine.

---

## Milestone-Oriented Build Plan

### Milestone A — Vertical Slice (Core Football Loop)

- One stadium, two teams, full gameplay loop.
- Core tackle/physics/ballistics systems.
- Baseline offensive and defensive AI.
- Minimal broadcast package.

### Milestone B — Full Gameplay Foundation

- All weather states and traction model.
- Expanded animation/contact library.
- Advanced playbooks and custom play editor MVP.
- Initial adaptive AI profile persistence.

### Milestone C — Franchise & Career Foundations

- Franchise year-loop, contract engine, scouting prototype.
- Career mode progression and grading loops.
- Analytics and record books.

### Milestone D — Content Completion

- All 32 teams, stadium identity layers, commentary content expansion.
- Polish pass for UI/UX and presentation.
- Optimization and compliance lock for offline-only shipping.
