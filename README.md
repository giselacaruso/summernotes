# Summer Notes

Write in the sand (or snow) with your finger. It fades in a minute.

**Live:** https://summernotes.vercel.app

![Hello! written in the sand](og.jpg)

A small browser experiment by [Gisela Caruso](https://giselacaruso.com). One HTML file, no build step, no dependencies.

## What it does

- **Sand or snow.** Each material has its own look: wet sand with shells and pebbles, or snow with drifts, twigs, leaves and bird tracks.
- **Finger or stick.** Two stroke widths. Every stroke digs a groove, piles the displaced material on the edges and drops a few crumbs.
- **Things move.** Shells, pebbles and leaves get pushed along when your stroke runs into them.
- **Erase or clear.** Smudge parts away with the hand tool, or clear everything with the broom.
- **It fades.** About a minute after you write, the strokes start to erode. Some patches vanish completely, others leave a faint trace.

## How it works

- The surface is a **height map** (a grid of floats) updated in JavaScript on every stroke.
- A **WebGL2 fragment shader** lights it with a low sun: surface normals, ray-marched shadows, cavity darkening and grain.
- Wet sand under the groove is darker; snow shadows go blue.
- Shells and pebbles are drawn to two canvases (color and height) that the shader reads, so they cast shadows like the sand does.
- A small "angle of repose" relaxation step keeps groove walls from being too perfect.

## Run it locally

Open `index.html` in a browser with WebGL2 support, or serve the folder:

```
npx serve .
```

Keyboard: `1` sand, `2` snow, `D` finger, `P` stick, `M` erase, `R` clear.

## License

MIT
