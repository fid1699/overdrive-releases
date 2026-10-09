<p align="center">
  <img src=".github/banner.png" alt="Overdrive, a game store for the PS5" width="800">
</p>

<p align="center">
  <a href="https://github.com/half144/overdrive-releases/releases/latest"><img alt="Latest release" src="https://img.shields.io/github/v/release/half144/overdrive-releases?style=flat-square&label=latest&color=f2f2f3&labelColor=17171a"></a>
  <a href="https://github.com/half144/overdrive-releases/releases"><img alt="Downloads" src="https://img.shields.io/github/downloads/half144/overdrive-releases/total?style=flat-square&color=f2f2f3&labelColor=17171a"></a>
</p>

Overdrive is a game store that runs on a jailbroken PS5. Browse the catalog, download with up to 64
connections at once, extract archives and hand finished games to ShadowMountPlus, all from the
controller.

This repository holds its builds. Install it once by hand; after that, Overdrive updates itself.

## What you need

| | |
| --- | --- |
| **A jailbroken PS5** | Tested on firmware 13.60 |
| **[ShadowMountPlus](https://github.com/drakmor/ShadowMountPlus)** | Registers Overdrive and the games it downloads |
| **An ELF loader on port 9021** | For example John Törnblom's elfldr. Overdrive uses it to install packages and to reopen itself after an update |
| **A way to copy files to the console** | FTP, [PS5Upload](https://github.com/phantomptr/ps5upload) or a USB drive |

## Install

1. **Download** `Overdrive-PPSA99058.zip` from the [latest release](https://github.com/half144/overdrive-releases/releases/latest).
2. **Extract** it on your computer. You get a folder named `PPSA99058`.
3. **Copy** the whole `PPSA99058` folder to `/data/homebrew/` on the console, so you end up with
   `/data/homebrew/PPSA99058/eboot.bin`.
   - **FTP:** connect to the console's FTP server and upload the folder into `/data/homebrew/`.
   - **PS5Upload:** send the folder with `/data/homebrew/PPSA99058` as the destination.
   - **USB:** copy the folder to `homebrew/` at the root of an exFAT drive, plug it into the console
     and move it to `/data/homebrew/` with a file manager.
4. **Register** it: with ShadowMountPlus running, Overdrive appears on the home screen within a few
   seconds. If it does not, run ShadowMountPlus's scan again.
5. **Open** Overdrive from the home screen.

> Keep the folder name `PPSA99058`. It is the title ID, and the updater looks for that folder.

## Updates

Overdrive checks this repository a few seconds after it opens. When a newer release is out, it
asks first:

```
UPDATE AVAILABLE
v0.0.89
v0.0.88  →  v0.0.89
[ Update now ]  [ Later ]
```

**Update now** downloads the ZIP, checks it against the SHA-256 GitHub publishes for it, swaps the
new files into the install folder and reopens Overdrive on the new version. Your downloads,
favorites and settings stay where they are.

To update by hand instead, repeat the install steps over the existing folder.

## Troubleshooting

<details>
<summary><b>"Cannot start the game or app" after copying the folder</b></summary>

The console's launcher needs to read every file in the folder. Set the folder's permissions to
`777`, recursively (most FTP clients and PS5Upload can do it), then open Overdrive again.
</details>

<details>
<summary><b>Overdrive closes after an update but does not reopen</b></summary>

Reopening needs the ELF loader on port 9021. Without it the update still installs: open Overdrive
from the home screen and it runs the new version.
</details>

<details>
<summary><b>The update dialog never appears</b></summary>

The console needs internet access to reach GitHub, and Overdrive only offers a release newer than
the version shown next to its logo. GitHub allows 60 checks an hour per network; a busy shared
connection can run out, and the next launch tries again.
</details>

<details>
<summary><b>Overdrive does not show up on the home screen</b></summary>

Check that ShadowMountPlus is running and that the path is exactly
`/data/homebrew/PPSA99058/eboot.bin`, not one folder deeper.
</details>

## Releases

Each release is tagged `vX.Y.Z` and carries a single asset, `Overdrive-PPSA99058.zip`: the complete
`PPSA99058` app folder.
