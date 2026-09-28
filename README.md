# Trajectory Studio

Interactive visualizer for interplanetary spaceflight trajectories. Ships with Project Lyra, Voyager 2, New Horizons, Parker Solar Probe, 1I/'Oumuamua, and a stock Earth→Mars Hohmann. Paste your own JSON to add missions.

**Live:** https://braxtonmccormack.github.io/trajectory-studio/

## What's in the box

- **Real orbital mechanics** — planets propagated from J2000 mean elements; trajectories built from patched Kepler arcs and Lambert-solved gravity-assist legs.
- **6 preset missions**, each rendered from real launch and flyby dates where they exist.
- **3D toggle** with drag-to-rotate — see 'Oumuamua's inclined retrograde arc dive through the ecliptic, or New Horizons drop below the plane to meet Pluto.
- **Custom missions** via JSON paste.

Single self-contained `index.html`. No build step, no dependencies (only IBM Plex from Google Fonts).

## Adding your own mission

Paste JSON into the sidebar. Each row is `[days_from_epoch, x_AU, y_AU]` or `[days_from_epoch, x_AU, y_AU, z_AU]` in the heliocentric ecliptic frame:

```json
{
  "name": "My Mission",
  "epoch": "2030-01-01",
  "target": "Alpha Centauri",
  "trajectory": [
    [0,    1.00,  0.00,  0.00],
    [30,   1.05,  0.15,  0.01],
    [60,   1.11,  0.29,  0.02]
  ]
}
```

Real vectors can come from [JPL Horizons](https://ssd.jpl.nasa.gov/horizons/) — request a vector table in ecliptic coordinates and reformat the X, Y, Z columns.

The "Export current" button dumps the active mission in the same format, so you can seed a file from a preset and tweak.

## Caveats

- Preset trajectories are qualitatively correct but not sub-day-accurate ephemerides. For publication-grade accuracy, feed in real Horizons vectors.
- Parker Solar Probe uses concentric shrinking-perihelion orbits — Lambert doesn't handle its multi-year Venus-flyby pattern well.
- The Lyra escape direction is approximate; there's no single published Lyra trajectory to lock onto.

## Hosting your own copy

Fork, then enable GitHub Pages on `main` / root. That's the whole build step.

## License

MIT
