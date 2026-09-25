# cs2-practice-routine

I wrote this tool to track my daily CS2 practice routines (aim_botz, recoil patterns, etc.) and save my stats locally. It runs a lightweight local HTTP server that listens to CS2 Game State Integration (GSI) payloads, tracks your progress through a configurable routine in real time, and logs kills, headshot ratios, and kills-per-minute (KPM) to a SQLite database.

It runs entirely on Windows, requires no external dependencies (just standard Python), and integrates directly with the game.

## Installation

1. Clone this repository or download `practice.py` directly.
2. Run the setup command to automatically find your Steam installation and write the GSI configuration file:

```cmd
python practice.py setup
```

If you have Steam installed in a non-standard directory, you can specify the path manually:

```cmd
python practice.py setup --steam-path "D:\Games\Steam"
```

## How it Works & Usage

To start a practice session, run:

```cmd
python practice.py start
```

This starts the local GSI listener on port 3000. Launch CS2 and join your practice map (e.g., aim_botz). The tool will automatically detect your kills and track your progress through the default routine:

- **Warmup**: 100 kills with any weapon
- **AK Spray**: 100 kills with AK-47
- **Flick Shots**: 50 headshots with Deagle or USP-S

As you get kills, the console will update in place showing your current progress, headshot percentage, and kills-per-minute (KPM). Once a stage is finished, a sound plays and the next stage begins. All completed stages are saved to a local `practice.db` file.

### Viewing Stats

To see your progress over time, run:

```cmd
python practice.py stats
```

This reads the SQLite database and prints a table of your historic sessions, showing your average KPM and headshot percentage per drill.

<!-- last-checked: 2026-09-25 -->
