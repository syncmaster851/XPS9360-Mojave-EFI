# XPS9360-Mojave-EFI

NOTE: For High Sierra, it's in https://github.com/syncmaster851/XPS9360-EFI

Hardware
XPS 9360, i7 7500U, 16G Memory, 512 Toshiba SSD, QHD+ Touch Screen, BIOS 2.6.2 Replaced the Wifi Card with DW1560 (BCM94352z)

Clover Version
4813

DUAL OS
Windows 10 Mojave 10.14.2 Boot loader - Clover

NOTE FOR SOUND:

Compare to https://github.com/the-darkvoid/XPS9360-macOS, the sound part was changed a little bit as I have a layout b.
Also the headphone inject work only with ALCPlugfix, so merged some code from https://github.com/the-darkvoid/XPS9360-macOS/pull/76

Steps to apply this:
1. Pull the latest from https://github.com/the-darkvoid/XPS9360-macOS
2. Copy audio/DSDT/XPS9360.sh to the-darkvoid's XPS9360-macOS
3. $sudo ./XPS9360.sh --compile-dsdt
4. $sudo ./XPS9360.sh --patch-hda
5. Rebuild cache
   $sudo chmod -Rf 755 /S*/L*/E*
   $sudo chown -Rf 0:0 /S*/L*/E*
   $sudo chmod -Rf 755 /L*/E*
   $sudo chown -Rf 0:0 /L*/E*
   $sudo rm -Rf /S*/L*/PrelinkedKernels/*
   $sudo rm -Rf /S*/L*/Caches/com.apple.kext.caches/*
   $sudo touch -f /S*/L*/E*
   $sudo touch -f /L*/E*
   $sudo kextcache -Boot -U /
