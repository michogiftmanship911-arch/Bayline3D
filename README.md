# Bayline3D
Private 3D model viewer built with Three.js. Drag-and-drop .glb/.gltf, studio lighting, material and wireframe controls, password-gated access, and a built-in usage guide. threejs, webgl, 3d-viewer, gltf, glb, model-viewer, javascript, static-site
# Bayline 3D

A private 3D model viewer for engineering and automotive assets, built with Three.js. Load a `.glb` or `.gltf` file, light it with a studio rig, strip it back to wireframe, and tune its materials in real time. Access to the viewer is gated by a password that visitors request by email.

**Live site:** [your-site-link-here]

## Features

- **Model loading:** drag and drop or pick `.glb` / `.gltf` files. Models are centred, scaled to fit, and rested on the floor automatically.
- **Studio lighting:** a shadow-casting key light, cyan and blue rim lights, an environment for reflections, and a shadow softness control.
- **Material controls:** metalness, roughness, clearcoat, transmission, emissive glow, and colour, with an option to override the materials in a loaded file.
- **Display modes:** wireframe, auto-rotate, floor grid, and three background themes.
- **Camera tools:** orbit, zoom, pan, front, side, top and 3/4 views, and reset.
- **Model readouts:** mesh count, triangle count, material count, bounds, and live FPS.
- **Procedural fallback:** a generated mechanical sculpture appears when no model can be loaded.
- **Usage guide:** a page that explains what every control does and what it means.
- **Password gate:** a landing page with a contact list and an unlock box.

## Pages

| File | Purpose |
|---|---|
| `index.html` | Landing page with the unlock box and contact list |
| `viewer.html` | The 3D viewer, locked until the password is entered |
| `guide.html` | Guide to every button, slider and readout |
| `404.html` | Not-found page |
| `site-config.js` | Contact details, contact list, and the password hash |
| `gate.js` | Front-end password check |
| `set-password.js` | Node script that updates the password hash |
| `model.glb` | Sample model |

## Run locally

The viewer loads files with `fetch` and ES modules, so it needs a local web server (opening the files directly will not work).

```bash
git clone https://github.com/[your-username]/[your-repo].git
cd [your-repo]
python3 -m http.server 8000
```

Then open http://localhost:8000.

## Deploy

This is a static site with no build step. Upload the folder to any static host:

- **Netlify:** drag the folder onto https://app.netlify.com/drop
- **Cloudflare Pages:** create a Pages project and upload the folder
- **GitHub Pages:** publish from the `main` branch in Settings, then Pages

## Change the password

```bash
node set-password.js "your new password"
```

This rewrites the hash in `site-config.js`. Commit and redeploy afterwards. The password itself is never stored in the repository.

## Customise

- Edit your name, email and contact list in `site-config.js`.
- Replace `model.glb` with your own default model, and update the model name in `viewer.html`.

## Security note

The password gate is a front-end check. It keeps casual visitors out of the viewer page, but the hash and the model file are public files on the host. Anyone who knows the model's URL can download it. If the model must stay private, use host-side access control such as Cloudflare Access, and do not publish the model in a public repository.

## Built with

- [Three.js](https://threejs.org/) (loaded from the jsDelivr CDN)
- HTML, CSS and vanilla JavaScript

## Contact

Michael: michaelayen001@gmail.com

## Credits

Sample model: [model name, author, and source link]. Used under [model's licence]. The model is not covered by this project's licence.

## License

The source code is released under the MIT License. See [LICENSE](LICENSE).

MIT License

Copyright (c) 2026 [Your Full Name]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
