### Doom for PocketPC
The resources referenced from https://elephantflea.pw/2024/04/doom-for-pocket-pc

#### Deletable Lumps
`Deletable Lumps.txt` has a list of lumps that can be removed from `doom1.wad` to save space.
I recommend using [SLADE](https://slade.mancubus.net/) for this. I have also provided `doom1.wad.vcdiff`
in case you would like to patch `doom1.wad` instead, reducing the filesize by a couple of megabytes.

#### HELP2
`HELP2.lmp` is the missing lump that the game tries to load after playing an internal demo. 
This can be added to `doom1.wad` if you would like to stop the crashing but without editing
`Doom.exe`.

#### Doom.exe Patches
These `VCDIFF` patches remove the copy protection from `Doom.exe` along with fixing the `HELP2` crash.
They can be applied using `xdelta3` or similar software. Two patches are provided:

* `doom_internal.exe.vcdiff`
    * Files must be in `\Program Files\DoomPDA\*`
    * Use this if running from main memory
    
* `doom_sdcard.exe.vcdiff`
    * Files must be in `\Storage Card\DoomPDA\*`
    * Use this if running from SD card
    
Both remove the copy protection and fix the `HELP2` crash. Using xdelta3 `Doom.exe` can be
patch with the following command:

```shell script
xdelta3 -d -s Doom.exe <diff file> Doom_patched.exe
```

If the files you are patching are copied from an existing install rather than pulled from the
game's installer/cab on the CD the above patch command will fail as the game's copy protection will
have added some bytes to the end of the files to patch. With `xdelta3` you can force the patch
to be applied with the `-n` argument.

```shell script
xdelta3 -n -d -s Doom.exe <diff file> Doom_patched.exe
```

By default, the game installs `Doom.exe` to `\Windows\Start Menu\Doom.exe`. It can be moved
you `DoomPDA` directory, and a shortcut can be placed elsewhere instead (eg in the `Games` folder).