# syrinx

A full-screen microphone visualizer, named for the Greek pan flute whose graduated pipes look like a spectrum, that looks like [cliamp](https://github.com/bjarneo/cliamp)'s
terminal visualizer. Single `index.html`, no dependencies, no build.

## Run

Live at <https://drakemorrison.github.io/syrinx/>, or run it locally:

Open `index.html` in Chrome or Firefox and click **start microphone**. If the browser
refuses mic access from a `file://` URL, serve it instead:

    python3 -m http.server 8765 --bind 127.0.0.1

and open <http://127.0.0.1:8765/>. The **demo signal** button (or `?demo` in the URL) runs a built-in synthetic beat without a mic.

## Modes

Columns (default), Bars, Ascii, ClassicPeak, ClassicLED, Wave, Mirror.

Ferrofluid isn't from cliamp. It's a matte, smoky ink creature in the spirit of the mimics
from Prey (2017): a lumpy body with a few long, curling tendrils that shed smoke. Bass drives
the bottom tendrils and treble the top, mirrored left and right. Each tendril is springy, so
loud hits make it lash out and twitch. It's drawn smooth instead of on the cell grid.

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
