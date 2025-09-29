# Stealth Shooter v17.2 Review

## Modularize presentation and logic assets
- The latest build keeps all CSS in a `<style>` block and all gameplay code in a monolithic `<script>` tag inside `stealth_shooter_levels_v17_2.html`. Splitting these concerns into external files would make iteration easier, enable editor tooling/linters, and reduce download churn when only assets or logic change.【F:stealth_shooter_levels_v17_2.html†L8-L146】【F:stealth_shooter_levels_v17_2.html†L312-L973】

## Consolidate pickup spawning utilities
- `spawnHeart` and `spawnStam` duplicate the same placement loop with only the payload differing. Extracting a shared helper (e.g., `spawnPickup(kind, radius, life)`) would cut maintenance overhead and ensure future tweaks (spawn bounds, retry count) stay in sync.【F:stealth_shooter_levels_v17_2.html†L595-L616】

## Provide deterministic randomization hooks
- Level layout, enemy composition, and pickups rely on direct `Math.random()` calls. Surfacing a seeded RNG or exposing level seeds would allow consistent reproduction of runs, simplify debugging, and open the door to sharing daily challenges.【F:stealth_shooter_levels_v17_2.html†L321-L377】【F:stealth_shooter_levels_v17_2.html†L595-L616】

## Isolate runtime assertions from production loop
- The bottom-of-file `setTimeout` installs intervals that repeatedly mutate state and call `console.assert` while the game runs. Gate these checks behind a debug flag or move them into a dedicated test harness so they do not consume cycles or risk leaking timers during normal play.【F:stealth_shooter_levels_v17_2.html†L948-L964】
