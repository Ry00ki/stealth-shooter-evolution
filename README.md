# Stealth Shooter Evolution

A browser-based stealth/shooter micro-game built iteratively with HTML5 canvas and React.  Each release introduces new mechanics and AI behaviours while keeping a stable core gameplay loop.

## Project Overview

**Goal:** Pick up chips without getting caught by guards.  Carry one chip at a time and deposit it in the safe zone to add time.  Clear all chips to advance levels.  The game scales with screen size and level: larger windows generate bigger arenas, more walls, more chips, and more enemies.

Over more than a dozen versions, the game evolved from a simple patrol-based stealth test (v3) into a rich arcade experience (v17) with dynamic enemy AI, procedurally generated maps, loot drops, power-ups, stamina-based dashing, snipers with laser sights, and screen-size-aware layouts.

## Getting Started

1. **Download the Repository:** Clone or download this repository.  The playable build ships as a single self-contained HTML file at the project root: `stealth_shooter_levels.html`.
2. **Run Locally:** Open `stealth_shooter_levels.html` in any modern browser.  The game does not require a build step or external assets.
3. **Adjust Screen Size:** At startup the game measures your window to set the arena size.  To replay with a different arena, reload the page after resizing your window.

## Controls

- **Move:** Arrow keys
- **Shoot:** Spacebar (fires bullets or power-up shots)
- **Sprint/Dash:** Double-tap an arrow and hold (consumes stamina)
- **Debug:** `D` (toggle vision & hearing cones)
- **Toggle Audio:** `A`
- **Restart Level:** `R`
- **Restart Game:** `G`

## Key Mechanics

- **Safe Zone:** A protective circle at spawn.  Guards and their bullets cannot enter, and you must return here to deposit chips.  Carrying a chip slows you down and disables your gun until deposited.
- **Enemies:**  AI-driven guards patrol, investigate, chase, and return.  Enemy catalogue includes patrols, gunners (ranged), sentries (slow, wide FOV), snipers (long sight + laser charge), and more.  Higher levels unlock more types and spawn mixtures.
- **Chips & Time:** Chips have varied values.  Picking up a chip instantly adds its value to the timer; depositing in the safe zone adds double its value.  Clearing all chips advances to the next level.
- **Lives & Hearts:** You start with three lives.  Lives persist through deaths until zero, when the game restarts.  Heart pickups spawn randomly and grant an extra life.
- **Power-Up Drops:** Killing an enemy drops its weapon for ~10 seconds.  Collecting it gives a temporary gun upgrade (e.g., omni-directional bursts).  Drop appearance, colour, bullets, and sound match the enemy type.  A countdown shows time remaining and pulses red in the last five seconds.
- **Stamina & Dash:** Double-tap to dash in a direction.  A stamina bar drains during dashes and refills when walking.  Map size sets max stamina so larger levels allow longer sprints.  Stamina bonuses randomly spawn, giving a brief "Super Sprint" with a bigger bar and faster regen.  A bar and labels above the HUD track current stamina and active boosts.
- **Dynamic Difficulty:** Each new level increases chip count, base enemy count, and roster variety.  Depositing chips spawns additional enemies scaled by chip value.  Timers scale by map area to keep travel distances fair.

## File Structure

- **stealth_shooter_levels.html** – The latest playable build containing the entire game.
- **README.md** – Project overview, controls, and contribution guidance.
- **LICENSE** – MIT license text.

## Contributing

This project is primarily for experimentation and education.  Pull requests adding new mechanics, enemy behaviours, or refactoring the enemy catalogue are welcome.  Please ensure that new versions remain playable and that existing stable behaviour (safe zone, timers, lives) remains intact.  Documentation updates in `docs/` are encouraged.

## License

This repository uses the MIT License.  See the `LICENSE` file for details.
