# quake3-hacks

Collection of goofy hacks for Quake III Arena, specifically the version being
actively supported and developed by [ioquake3](https://github.com/ioquake/ioq3).

Since Quake III Arena was open-sourced under the GPL license by id Software,
'hacking' the game is as simple as getting familiar with the codebase and just
changing it.

## Examples: 
![example1](example1.gif)
The rocket launcher in Quake III Arena is supposed to have a slow fire rate and
a limited amount of ammo, but here it has neither.

![example2](example2.gif)
The grenade launcher by default is also slow and requires reloading. 

## Compiling Quake III:
- Make sure you have SDL2 installed
- Clone the [ioquake3](https://github.com/ioquake/ioq3) repo
- [Compile](http://wiki.ioquake3.org/Building_ioquake3)
- Obtain `.pak` files for Quake III, and put them into `ioq3/build/release-your-release/baseq3`
- Apply the patch file after checking that Quake built successfully.

## Running them:
Use `git apply patchname.patch` to apply the patchs. You can apply them all at
the same time as there's no merge conflicts.
