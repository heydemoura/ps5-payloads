# PS5 Memcard

A memory card for the PS5. The payload watches every save on the console (PS5 and PS4 titles, all profiles) and keeps a copy on USB drives under `/memcard`. Its web page shows what is on each card and imports any save back into any profile.

## Features

- Automatic backup: a save is copied once it has been unchanged for 15 seconds, at most every 5 minutes while its game runs, and again when the game closes
- Several memory cards at once: every drive with a `/memcard` folder gets every save, and a card that was unplugged catches up when it returns
- Import a card save into any profile on the console, or back up one save, one game or everything on demand
- The previous copy of each save is kept and can be imported too
- A **PS5 Memcard** shortcut on the Media tab opens the page in the console's browser, and a notification reports how many memory cards were found
- Cards can be named; the name is stored on the card

## Usage

1. Plug a USB drive (exFAT or FAT32) into the PS5.
2. Download `ps5-memcard.elf` from the [latest release](https://github.com/heydemoura/ps5-memcard/releases/latest) and send it to a running PS5 ELF loader on port 9021:

   ```sh
   nc -q0 <ps5-ip> 9021 < ps5-memcard.elf
   ```

3. Open `http://<ps5-ip>:8083/` in a browser, or use the **PS5 Memcard** shortcut on the Media tab.

With no card connected, the first USB drive becomes one by itself. Any other drive is left alone until you press **Use as card** on its tile.

Tested on firmware 12.20 with one USB drive. Not yet tried on a console: a real game's save (the tests used a synthetic PS5 save), PS4 saves, and two drives at once. Importing the save of a game that is running is refused. See the [project README](https://github.com/heydemoura/ps5-memcard#readme) for the card layout, settings and API.

Save handling is built on [Garlic SaveMgr](https://github.com/earthonion/garlic-savemgr) by earthonion.

## Source

[GitHub repository](https://github.com/heydemoura/ps5-memcard)
