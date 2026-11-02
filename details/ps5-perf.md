# PS5 Perf

A `perf(1)`-style sampling profiler for the PlayStation 5. It profiles any running process (games, system apps, other payloads) and reports where CPU time goes, live on the console or as files for the usual perf tooling on your computer.

## Features

- `stat`: CPU time, context switches and page faults, per process or per thread
- `record`, `report`, `top`, `script`: cpu-clock sampling with call stacks
- Function names for Sony system libraries (NIDs resolved), `sub_<offset>` functions for stripped games, and full symbols for your own payloads from their ELF
- Output in `perf script` format (speedscope, Firefox Profiler, FlameGraph), folded stacks and SVG flame graphs
- Low overhead: a game is paused only for tens of microseconds per sample, and never while it is idle

Hardware counters (cycles, cache misses) are not available on the PS5.

## Usage

1. Download `ps5-perf.elf` from the [latest release](https://github.com/heydemoura/ps5-perf/releases/latest).
2. Send it to a running PS5 ELF loader on port 9021:

   ```sh
   nc -q0 <ps5-ip> 9021 < ps5-perf.elf
   ```

3. Connect to port 9077 and type `help`, e.g. `nc <ps5-ip> 9077`, then `report -p eboot.bin -g -d 10`.

For recordings, flame graphs and offline reports, use the host client `ps5perf.py` from the same release:

```sh
python3 ps5perf.py -H <ps5-ip> record -p eboot.bin -g -o game   # Ctrl-C to stop
```

Tested on firmware 12.20. See the [project README](https://github.com/heydemoura/ps5-perf#readme) for all commands and options.

## Source

[GitHub repository](https://github.com/heydemoura/ps5-perf)
