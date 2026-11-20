# Real FPS

**Is that clip really 60 fps?** Drop a video and see how many frames are actually new.

Live: https://cranefomo.github.io/realfps

A lot of "60 fps" gameplay clips are 30 fps games exported into a 60 fps file. Every other frame is a copy. This page finds the copies and tells you the real number.

## What it does

- Counts real (unique) frames vs frames in the file
- Shows real FPS, 1% low and how many frames are copies
- Draws a per-second chart and a frame strip of the first 2 seconds
- Checks your graphics card and suggests a Veyra preset
- Gives you a Claude Code prompt that installs Veyra from the official repo only and checks the SHA-256 hash

## Privacy

Everything runs in your browser (WebCodecs + mp4box.js). The video is never uploaded. No accounts, no tracking.

## How it works

Each frame is shrunk to 384x216 grayscale and compared with the last unique frame in 8x8 blocks. A frame counts as new if any block changed a lot, or if more than a third of blocks changed a little. Same idea as ffmpeg's mpdecimate filter.

Works best with H.264, VP9 and AV1 (mp4, mov, webm). HEVC (H.265) needs a browser with hardware support. Analysis covers the first 90 seconds.

## Limits

- Compression noise can make a copied frame look new, so real FPS may read slightly high on very noisy clips.
- A static scene (menu, paused game) has no new frames by nature. Test on motion.
- Phone recordings of a TV measure the phone, not the game.

## No guarantee

This is a free hobby tool, provided "as is". Results are estimates, not proof. Nothing here is affiliated with or endorsed by Rockstar Games, Take-Two, Sony, Microsoft, NVIDIA, AMD, Anthropic or the Veyra project. Install third-party software at your own risk.

## Credits

- [Veyra](https://github.com/Likely7/Veyra-NRVideo) by Likely7, GPL-3.0. This repo does not include or redistribute Veyra. The "DLSS 5" name used in some posts is not an official NVIDIA feature of Veyra.
- [mp4box.js](https://github.com/gpac/mp4box.js) 0.5.3, BSD-3-Clause, inlined in `index.html` (license in `LICENSE-mp4box.txt`).
- Frame-duplicate idea in the spirit of ffmpeg mpdecimate and phosphenq's truefps script.

Made by [@Cranefomo](https://x.com/Cranefomo). Also: [qrcheck](https://cranefomo.github.io/qrcheck), a QR code scam checker.

## License

MIT for this page's own code.
