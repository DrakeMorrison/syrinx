# micvis

A full-screen microphone visualizer that looks like [cliamp](https://github.com/bjarneo/cliamp)'s
terminal visualizer. Single `index.html`, no dependencies, no build.

## Run

Open `index.html` in Chrome or Firefox and click **start microphone**. If the browser
refuses mic access from a `file://` URL, serve it instead:

    python3 -m http.server 8765 --bind 127.0.0.1

and open <http://127.0.0.1:8765/>. The **demo signal** button (or `?demo` in the URL) runs a built-in synthetic beat without a mic.

## Modes

Columns (default), Bars, Ascii, ClassicPeak, ClassicLED, Wave, Mirror.

The spectrum pipeline is a port of cliamp's: 2048-point Hann-windowed FFT at ~30 Hz,
ten log-spaced bands between 20 Hz and 20 kHz, its dB-to-level mapping, fast-attack /
slow-decay band smoothing, per-frame easing, and the green / yellow / red row zoning.
Block characters are drawn as eighth-height rects on a terminal cell grid.

## Keys

| key | action |
|---|---|
| ← → or `v` | change mode |
| `t` | cycle theme |
| `-` `=` | gain down / up (turns auto gain off) |
| `[` `]` | cell size |
| `f` | fullscreen |
| `h` | pin / hide the control panel |

Settings persist in localStorage.
