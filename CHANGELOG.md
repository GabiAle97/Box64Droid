# V1

CHANGELOG:
- FIRST RELEASE (From now on: v1)
- Added Wine 8.16 by Kron4ek (testing)
- Added Wine-GE 8.15 by Glorious Eggroll (testing)
- Native instance already has Turnip 23.1.7
- Added Turnip versions from Termux-box 
  (some of them are buggy, so there is 
  an option to return the default one)
- Modified Updater (option 4):
  - Now you can update the current system 
    or switch to Ubuntu Kinetic, Lunar or Mantic,
    aiming to more updated libraries
  - Now every fresh install will update the system
    (letting you choose between the 
    previously mentionated distributions) and 
    box64/box86 by default
  - Now the updater installs GStreamer libs 
    (fixes RE7/RE3 Cutscenes)
- Changed the way Wine is running (Switch from 
  "box64 wine" to "box64 wine64")
- Now every Box64Droid run will check for updates
  and ask if you want to install them

# V1.0.1

CHANGELOG:
- Added Wine-GE 8.16 by Glorious Eggroll (testing)
- Native instance already has Turnip 23.1.8
- Now every Box64Droid run will check for updates
  only if there are modified scripts, so if something
  like CHANGELOG.md is modified, it won't ask for
  an update.
- Some libs have been copied to system32 when they're
  for syswow64, and viceversa. Now they're being copied
  on the corresponding folder (will see how it behaves)
