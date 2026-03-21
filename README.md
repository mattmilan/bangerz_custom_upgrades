# Custom Upgrades Testing

## Purpose

Changing the upgrades can be a tedious process, prone to errors.

Rather than have testers manage their own dev environments, which is itself another tedious error-prone process, one is being provided.

## Info

We get the default upgrades config file from one of the TF2 `.vpk` files using `VPKEdit`. We don't make any changes to the `.vpk` files.

After we edit the upgrades config, we send it to the server, in a folder where the RTU plugin can see it.

RTU checks that folder on every map load, or when we manually trigger it with the chat command `/rtu_rl`. If it finds a file, it sets the upgrades accordingly, otherwise it uses the default.

This should be the end of it, but for some reason, TF2 needs this file in two places: on the server, and on the client. This introduces two problems:

- If they differ, behavior gets wierd
- If the client already has a copy, they can't download a newer one (unless we play games with filenames)

## Instructions

> #### ENSURE you delete your local upgrades file before `retry` or you won't have the latest changes
> `C:\Program Files (x86)\Steam\steamapps\common\Team Fortress 2\tf\download\scripts\items\bangerz_upgrades.txt`
> `C:\Program Files (x86)\Steam\steamapps\common\Team Fortress 2 Classified\tf2classified\download\scripts\items\bangerz_upgrades.txt`

- <Github> [Update](https://github.com/mattmilan/bangerz_custom_upgrades/edit/master/bangerz_upgrades.txt) `bangerz_upgrades.txt` and commit
- <Github> Wait for the [github action](https://github.com/mattmilan/bangerz_custom_upgrades/actions) to complete (~10 seconds)
- <Client> Chat `/rtu_rl` to load the new changes to the server
- <Client> Delete your local `bangerz_upgrades.txt` if it exists
- <Client> Enter console command `retry` to load the new changes to the client
