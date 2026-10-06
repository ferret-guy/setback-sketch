# Setback Sketch

Freehand-draw a line or outline on satellite imagery and see one-sided setback distances from it.
Everything (map view, imagery layer, drawing, distances, side, units, smoothing, shading) is stored
in the URL hash, so any link reopens the exact sketch.

## Use
- **Go**: search an address or paste `lat, lng`
- **✏️ Draw**: press and drag on the map; release to finish
- **Side**: Left/Right of draw direction (open line) or Outside/Inside (closed outline)
- **Setbacks**: comma-separated list, ft or m (default 20, 60, 100 ft)
- **🔗**: copy a shareable link

## Host on GitHub Pages
It's a single static `index.html` with no build step.

1. Create a new GitHub repo and push these files to the `main` branch.
2. In the repo, go to **Settings → Pages**, set **Source** to *Deploy from a branch*, and pick `main` / `(root)`.
3. The site appears at `https://<user>.github.io/<repo>/`.

## URL format
`#map=<zoom>/<lat>/<lng>&l=<hybrid|sat|esri>&d=20,60,100&u=<ft|m>&s=<a|b>&c=1&sm=1&b=0&p=<encoded polyline>`

`p` is the raw sketch as a Google encoded polyline (1e-6 precision). Parameters at their default values are left out.

## Notes
- Libraries load from unpkg (Leaflet 1.9.4, Turf 7). Address search uses OpenStreetMap Nominatim.
- Google imagery uses Google's tile servers directly, without an API key. Esri imagery is available as a fallback.
