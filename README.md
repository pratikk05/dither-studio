# Dither Studio

A local-first browser app for uploading 3D models, previewing a real-time ordered Bayer dithering shader, adjusting parameters, and exporting a PNG or a GLB geometry preview.

## Run locally

Requires Node.js 18+.

```bash
npm install
npm run dev
```

Open the local URL printed by Vite. To build for deployment:

```bash
npm run build
npm run preview
```

## Features

- Bundled Napoleon bust sample with local loading for `.glb`, `.gltf`, `.obj`, and `.stl`
- Interactive orbit and zoom
- Live GLSL Bayer ordered dithering, pixel size, resolution, contrast, exposure, grayscale, inversion, ink/background colors and a bloom-accent control
- PNG export of the rendered viewport
- GLB export of the normalized model geometry for reuse in a 3D editor
- Standalone website HTML export with the current model and shader settings embedded
- Responsive dark UI with neon accents

### Export note

The dithering is a **screen-space post-processing effect**. PNG export captures the visual effect. GLB export includes the model geometry and materials, but does not bake the screen-space shader into model geometry or textures. OBJ/GLTF texture references can be external; GLB is the recommended upload format.

## Shader attribution and license

The ordered Bayer dithering approach in this project is based on the technique demonstrated in [niccolofanton/dithering-shader](https://github.com/niccolofanton/dithering-shader), by Niccolò Fanton, released under the MIT License. The reference credits the original dithering pattern to Klems on Shadertoy. This app is an independent implementation of the Bayer threshold pass and UI, rather than a copy of the original repository's full source. See `THIRD_PARTY_NOTICES.md` for attribution and license details.

The original repository's MIT license permits reuse, modification, distribution, sublicensing, and sale provided the copyright and permission notice are retained. This project does not bundle the original repository's 3D model asset.

## Notes

- Model files are parsed in your browser; this app does not upload them to a server.
- Complex scenes and very large models can use substantial GPU memory.
- OBJ material and texture files may need to be supplied separately; GLB is generally the easiest format.
- The bundled Napoleon model is licensed under CC BY 4.0. Its attribution and license are included in `public/models/napoleon/license.txt`.
- Website HTML exports load Three.js from jsDelivr, so the hosted page needs internet access unless you change the import map to use a local Three.js installation.
