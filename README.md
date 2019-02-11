# Re-enable_rc6 (optimized for Manjaro)

*Confirmed working with kernel __4.20.5__*

**current version does NOT work with kernels <4.20**

Since linux 4.16 the i915.enable_rc6 parameter has been disabled. This patch re-enables it so your computer won't crash. See https://bugs.freedesktop.org/show_bug.cgi?id=105962 for some background and information (although, if you're here you probably already know all that!). This patch is basically just the output of git revert on [this](https://github.com/torvalds/linux/commit/fb6db0f5bf1d4d3a4af6242e287fa795221ec5b8) commit of the master [linux](https://github.com/torvalds/linux/) branch. Slight modifications were done by hand to try to minimally affect all progress since 4.15.16.

## Instructions (for Manjaro)
1. `git clone https://gitlab.manjaro.org/packages/core/linux420.git`
2. `cd linux420/`
3. put re-enable_rc6.patch in this folder and replace the PKGBUILD
4. `makepkg -s`[note: if getting checksums errors, do `makepkg -g` and then copy the hashes into the PKGBUILD file]
5. copy all the files from the pkg directory into the respective root directories
6. `sudo mkinitcpio -p linux420`
7. `sudo update-grub`

## Questions/Contributions

Please direct non-Manjaro related questions and contributions to the original patch. 

## Author

Arthur Eigenbrot - aeigenbrot at nso.edu [original patch]

Filip Fila [Manjaro modifications]
