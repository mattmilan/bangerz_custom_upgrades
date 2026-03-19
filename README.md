# Custom Upgrades Testing
## Purpose

Changing the upgrades can be a tedious process, prone to errors.

Rather than have testers manage their own dev environments, which is itself another tedious error-prone process, one is being provided.

## Info
The upgrades in TF2 are defined in a file that one can access by using VPKEdit to browse the game's `.vpk` files.

We can extract this file, make changes, and then tell the server to use it instead of the default.

One caveat is that both the server and the client need a copy of this file, and they need to be the same, or there will be problems.

This becomes a problem down the road, when the server upgrades file has been changed again, after a client has already downloaded it; sourcemod cannot overwrite this file, and the user must manually delete it, or they will not get the new file.

## Instructions

DEFAULT client file: `C:\Program Files (x86)\Steam\steamapps\common\Team Fortress 2\tf\download\scripts\items\bangerz_upgrades.txt`

- Delete current client file if exists
- Update `bangerz_upgrades.txt` in github and commit.
- Github will send the changed file to the game server.
- Download client file
- Refresh the upgrades in game with `/rtu_rl`
