# PS5 Web Stream

Stream PlayStation 5 video and stereo audio over your local network to a browser or OBS. Includes a dashboard and a fullscreen player with capture controls.

## Features

- H.264 video and stereo AAC audio over HTTP-FLV
- 720p, 1080p, 1440p and 4K capture at 60 fps
- Fullscreen Video.js player, dashboard and OBS browser source support
- URL options for hiding controls, choosing mute state and capture resolution

## Usage

1. Download `ps5-web-stream.elf` from the [0.1.0 release](https://github.com/heydemoura/ps5-web-stream/releases/tag/0.1.0).
2. Send it to a running PS5 ELF loader on port 9021:

   ```sh
   nc -q0 <ps5-ip> 9021 < ps5-web-stream.elf
   ```

3. Open `http://<ps5-ip>:8080/` for the dashboard or `http://<ps5-ip>:8080/player` for the player.

The player accepts `controls=0` to hide its controls, `mute=0` or `mute=1`, and `resolution=1` through `4` for 720p, 1080p, 1440p and 4K. Example: `/player?controls=0&mute=0&resolution=4`. Resolution changes affect all connected viewers.

For OBS, add a Browser source using the fullscreen player URL. See the [project README](https://github.com/heydemoura/ps5-web-stream#use-the-fullscreen-player-in-obs) for source sizing and audio routing.

## Source

[GitHub repository](https://github.com/heydemoura/ps5-web-stream)
