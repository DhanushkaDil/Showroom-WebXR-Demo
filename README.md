# Walk-in WebAR

Places a GLB scene at real-world 1:1 scale so you can walk around and inside it. Built with three.js + WebXR (`immersive-ar`).

## Files
```
index.html
3DVW.glb      <- your Blender export (you add this)
README.md
```

## 1. Prepare the GLB in Blender
- **Scale**: 1 Blender unit = 1 meter (Scene Properties > Units). Check your hall's real size, since it will appear at exactly that size.
- **Floor at Z = 0**, so the floor lines up with the real floor.
- **Windows**: make glass materials transparent (Alpha / Blend). Solid white panes will block the camera view.
- **Spawn point**: in `index.html` set `SPAWN_BLENDER` to the Blender (x, y, z) where the visitor should start, such as the doorway. That point lands where you tap the floor.
- Export: File > Export > glTF 2.0 (.glb). Enable **Apply Modifiers**, **Compression (Draco)**, and keep textures at 2048px or smaller. Aim for under ~30 MB (GitHub's file limit is 100 MB).
- Name it `model.glb`.

## 2. Host on GitHub Pages
1. Create a repo, add the 3 files, and push.
2. Settings > Pages > Source: `main` branch, `/ (root)` > Save.
3. Open `https://<username>.github.io/<repo>/` on your phone (HTTPS is required for WebXR, and Pages provides it).

## 3. Use it
Tap **Start AR**, point at the floor where the entrance should be, tap to place, then walk. The buttons rotate, raise/lower, scale, or re-place the scene.

## Device support
- **Android + Chrome + ARCore phone**: works.
- **iPhone/iOS Safari**: does **not** support WebXR AR. For iOS you'd need a third-party engine such as 8th Wall or Zappar, or a native app.

## Local testing
`npx serve` in this folder, then on the Android phone use Chrome `chrome://inspect` port forwarding to `localhost:3000` (localhost counts as secure), or just push to GitHub Pages.
