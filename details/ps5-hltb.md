# PS5 HowLongToBeat

Native HowLongToBeat completion estimates on the PS5 home screen.

## Features

- Main Story, Main + Extra, and Completionist estimates in one native panel
- Displays for games with or without played time, without focusing Play Game
- Persistent 30-day file cache; valid saved results need no network lookup
- Background lookups with bounded resources and cleanup when switching games

## Usage

1. Send `hltb.elf` to the console's ELF loader (port 9021).
2. Highlight a game on the home screen. Its completion metrics appear after the cache check or first lookup.
3. Restart ShellUI or reboot before loading over an older resident version.

Only firmware **12.20** has been tested. The original game title and played-time controls are preserved. Estimates depend on HowLongToBeat title matching; unavailable extra/completionist estimates display `N/A`.

## Source

[GitHub Repository](https://github.com/heydemoura/ps5-hltb) · [Releases](https://github.com/heydemoura/ps5-hltb/releases)
