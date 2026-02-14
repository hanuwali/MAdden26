# Offline Adaptive AI Model (Local-Only)

## Purpose

Enable CPU teams to counter repetitive player behavior while preserving fairness, readability, and entirely offline execution.

## Data Collection (Per User Profile)

Stored in local save data only:

- Formation call frequency by down/distance.
- Play concept families (inside zone, flood, mesh, cover-3 beater, etc.).
- Pass depth distribution (short/intermediate/deep).
- Directional rushing tendencies.
- Blitz pickup success rates.
- Red-zone call preferences.
- 2-minute drill aggression profile.

## Adaptation Cycle

1. **Observe** each snap and classify concept tags.
2. **Aggregate** over rolling windows (last drive, half, game, season).
3. **Score predictability** using entropy + success-rate weighting.
4. **Respond** with weighted counter packages.
5. **Decay old data** so stale patterns lose influence.

## Defensive Counter Examples

- Frequent quick-game concepts → tighter underneath zones + simulated pressure.
- Repeated stretch/outside run right → set edge hard, shift front strong side, increase run blitz probability.
- Heavy play-action on early downs → discipline linebackers and raise zone-drop depth.

## Offensive CPU Counter Examples

- User overcommits to blitz → increase hot routes, max protect shots, RB screen frequency.
- User sits in two-high shells → raise run rate + seam stress concepts.
- User repeatedly spies QB → handoff and option pitch weighting increases.

## Safeguards

- Adaptation intensity slider (Conservative / Standard / Aggressive).
- Never force impossible psychic reactions; counters must be assignment-legal.
- Randomized counter selection within valid tactical buckets to avoid deterministic AI.

## Storage & Privacy

- File location: local profile save path.
- No network transmission.
- No account-linked telemetry.
- User can reset adaptation history at any time from settings.
