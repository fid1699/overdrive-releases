# Overdrive releases

Builds of Overdrive, the PS5 game store, published for its in-app updater.

Each release is tagged `vX.Y.Z` and carries `Overdrive-PPSA99058.zip`: the
complete `PPSA99058` app folder. Overdrive reads the latest release from this
repository, checks the ZIP against the SHA-256 GitHub publishes for it, swaps
the files into its install folder and reopens on the new version.

To install by hand, extract the ZIP and copy the `PPSA99058` folder to
`/data/homebrew/` on the console; ShadowMountPlus registers it.
