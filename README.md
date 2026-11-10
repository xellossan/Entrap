# Moraff's Entrap VR & Desktop Remake (WebXR + P2P Multiplayer + Voice Chat)

A first-person 3D browser and Oculus Quest WebXR remake of Steve Moraff's classic DOS turn-based tactical puzzle game **[Moraff's Entrap (1990/1991)](http://www.classicdosgames.com/game/Moraff's_Entrap.html)** published by **[MoraffWare](https://dosgames.com/author/moraffware/)**.

## Included Files for Web Server Deployment
- `index.html` — Main entry point and UI overlay (Start Lobby, VR/Desktop Mode Selector, P2P Room Configuration, Radar Minimap, and HUD).
- `styles.css` — Responsive HUD styling, cyber-grid theme, and first-person reticle indicators.
- `game.js` — Complete 3D Three.js + WebXR engine, Oculus Quest controller locomotion & triggers, Desktop WASD + Mouse PointerLock controls, PeerJS WebRTC P2P data synchronization, direct WebRTC voice chat, and turn-based *Moraff's Entrap* monster AI.
- `manifest.json` — Web App Manifest for standalone browser and Quest installation.

## Deploying to Your Web Server
1. Extract all files from `moraffs_entrap_vr.zip` into any static web server folder (Nginx, Apache, GitHub Pages, Cloudflare Pages, Vercel, Netlify, or `npx serve .`).
2. **Important for Oculus Quest WebXR & Microphone Voice Chat**: Browsers require **HTTPS** (or `http://localhost` during local testing) to enable `navigator.xr` (WebXR immersive VR sessions) and `navigator.mediaDevices.getUserMedia` (WebRTC direct voice chat).

## Controls Summary

| Action | Oculus Quest VR Controller | Desktop Browser |
| :--- | :--- | :--- |
| **Move (1 Grid Square)** | **Left Thumbstick** (Fwd / Back / Left / Right) | **WASD** or Arrow Keys (or On-Screen Pad) |
| **Rotate Character** | **Right Thumbstick** (Left / Right Snap Turn) | **Mouse Movement** (Click canvas to lock) or **Q / E** |
| **Delete Floor Square** | **Left Controller Trigger** (aim laser at floor) | **Left Mouse Click** (aim crosshair at floor) |
| **Create Floor Square** | **Right Controller Trigger** (aim laser at empty space) | **Right Mouse Click** (aim crosshair at empty space) |

## Game Modes & Rules
- **Turn-Based Grid Action**: Every time a player moves 1 square, creates 1 floor square, or deletes 1 floor square, all monsters on the map move 1 square.
- **Single Player**: Start at the South end (`z = 17`) and reach the North Goal Row (`z = 0`) across 10 progressive difficulty levels without letting a monster touch you.
- **2-Player P2P Multiplayer & Direct Audio Chat**:
  - Defaults to room name **`Xellossan`**.
  - **Host (Player 1)** starts on the South end (`z = 17`) and races to the North Goal (`z = 0`).
  - **Joiner (Player 2)** starts on the opposite North end (`z = 1`) and races to the South Goal (`z = 18`).
  - **Closest-Player Monster AI**: On every turn, each monster calculates which living player it is closer to and moves 1 square toward that player.
