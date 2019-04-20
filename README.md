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


This stuff is so simple I can just show you the whole patch right here. It's
also available in this repo as `quake.patch` so you can apply it to your own
version with `git apply quake.patch`


Here we just remove the code that subtracts ammo from the player, and that's
enough to give us infinite ammo. 

```diff

diff --git a/code/game/bg_pmove.c b/code/game/bg_pmove.c
index 5465c579..c981c954 100644
--- a/code/game/bg_pmove.c
+++ b/code/game/bg_pmove.c
@@ -1634,55 +1634,50 @@ static void PM_Weapon( void ) {
 		return;
 	}
 
-	// take an ammo away if not infinite
-	if ( pm->ps->ammo[ pm->ps->weapon ] != -1 ) {
-		pm->ps->ammo[ pm->ps->weapon ]--;
-	}
-
 	// fire weapon
 	PM_AddEvent( EV_FIRE_WEAPON );
```

And here we just change the delay between each shot (fire rate) to 0. Now every
weapon fires infinitely fast.

```diff 
 	switch( pm->ps->weapon ) {
 	default:
 	case WP_GAUNTLET:
-		addTime = 400;
+		addTime = 0;
 		break;
 	case WP_LIGHTNING:
-		addTime = 50;
+		addTime = 0;
 		break;
 	case WP_SHOTGUN:
-		addTime = 1000;
+		addTime = 0;
 		break;
 	case WP_MACHINEGUN:
-		addTime = 100;
+		addTime = 0;
 		break;
 	case WP_GRENADE_LAUNCHER:
-		addTime = 800;
+		addTime = 0;
 		break;
 	case WP_ROCKET_LAUNCHER:
-		addTime = 800;
+		addTime = 0;
 		break;
 	case WP_PLASMAGUN:
-		addTime = 100;
+		addTime = 0;
 		break;
 	case WP_RAILGUN:
-		addTime = 1500;
+		addTime = 0;
 		break;
 	case WP_BFG:
-		addTime = 200;
+		addTime = 0;
 		break;
 	case WP_GRAPPLING_HOOK:
-		addTime = 400;
+		addTime = 0;
 		break;
 #ifdef MISSIONPACK
 	case WP_NAILGUN:
-		addTime = 1000;
+		addTime = 0;
 		break;
 	case WP_PROX_LAUNCHER:
-		addTime = 800;
+		addTime = 0;
 		break;
 	case WP_CHAINGUN:
-		addTime = 30;
+		addTime = 0;
 		break;
 #endif
 	}
```
