# Simple AR Viewer

Simple-AR-Viewer is a dead-simple, URL-based AR/3D viewer built on top of [`<model-viewer>`](https://modelviewer.dev/).  
You pass a model URL via the `?url=` query parameter and it renders full-screen, with optional AR on supported devices.

Example:

```text
https://your-domain.com/?url=https://your-cdn.com/models/my-model.glb
````

---

## Features

* **URL-based loading** – no UI, no menus, just `?url=...` and go.
* **Mobile-first full-screen view** – locks the page to 100% width/height.
* **AR support** via `<model-viewer>`:

  * `webxr`
  * `scene-viewer` (Android)
  * `quick-look` (iOS)
* **Orbit controls** – pinch/drag to inspect the model.
* **No backend required** – just static HTML + JS.

Implementation is a single `index.html` using Google’s hosted `model-viewer.min.js`. 

---

## How it Works

1. The page reads the `url` query parameter from `window.location.search`.
2. If `url` is present:

   * Shows a loading overlay.
   * Sets `<model-viewer id="viewer">.src` to that value.
   * Hides the overlay once the model fires the `load` event.
   * On error, replaces the overlay text with “Error loading model”.
3. If `url` is **missing**:

   * Shows the message: `Add ?url=YOUR_MODEL.glb to the URL`.

---

## Usage

### Basic URL format

```text
https://your-domain.com/?url=MODEL_URL
```

Where `MODEL_URL` is a direct link to your `.glb` (or other supported format) file.

#### Example

```text
https://your-domain.com/?url=https://example.com/models/chair.glb
```

If your URL has special characters, remember to URL-encode it:

```text
https://your-domain.com/?url=https%3A%2F%2Fexample.com%2Fmodels%2Fchair%20v2.glb
```

---

## Query Parameters

Currently only one parameter is used:

| Param | Required | Description                                     | Example                                     |
| ----- | -------- | ----------------------------------------------- | ------------------------------------------- |
| `url` | Yes      | Direct URL to the 3D model file to be rendered. | `?url=https://example.com/models/model.glb` |

If `url` is not provided, the page shows the hint:
`Add ?url=YOUR_MODEL.glb to the URL`.

---

## Supported Formats & AR

Support comes from `<model-viewer>`:

* Typical 3D format for web: **`.glb`** / **`.gltf`**
* For iOS Quick Look AR: **`.usdz`** (depending on your setup/hosting)
* AR modes configured:

```html
ar
ar-modes="webxr scene-viewer quick-look"
```

Notes:

* AR availability depends on the user’s device and browser.
* For AR:

  * Use **HTTPS**.
  * Make sure models are hosted on HTTPS as well.
  * Test on real mobile devices (Android/Chrome, iOS/Safari).

---

Copyleft (C) 2025 Nix

This program is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.
This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
You should have received a copy of the GNU General Public License along with this program. If not, see <https://www.gnu.org/licenses/>.

<p align="center">
  <a href="https://emoji.gg/emoji/5349-hellokittybyebye">
    <img src="https://cdn3.emoji.gg/emojis/5349-hellokittybyebye.png" width="128px" height="128px" alt="HelloKittyByeBye">
  </a>
</p>