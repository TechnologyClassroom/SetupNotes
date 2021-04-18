# Minetest notes

Michael McMahon

[Minetest](https://www.minetest.net/) is an open source game engine similar to
Minecraft or other voxel games.  This engine can run a variety of games called
[subgames](https://wiki.minetest.net/Subgames).

Note: Minecraft 4 and Minecraft 5 are incompatible.  If using multiplayer, the
client version must match the server version.

## Teaching computer science

The engine is written in C++, but knowing C++ is not necessary to mod the game.
All subgames are created with
[the LUA programming language](https://www.lua.org/).  Lua is a beginner,
interpreted language.  You can modify most things in the game without
recompiling for instant gratification.  If you place the entire game in the
documents folder, anyone can mod the game without admin rights.

## Tweaks to make the game safer for educational environments

- Delete the TNT mod from all subgames.  It is a folder in nearly every subgame
  called /tnt/ and you can remove it.  Search for it and delete it.  Someone can
  spend weeks creating a voxel masterpiece.  Someone else can destroy everything
  in under a minute.  Tears follow.  Regular backup plans help mitigate this,
  but deleting tnt is easiest.  The benefits of having tnt are heavily shadowed
  by the drawbacks.
- Consider removing lava for a similar reason.  Not as simple to do.
- Multiplayer servers include chatting with strangers.  Block the public
  servers.  I include this functionality in the
  https://github.com/technologyclassroom/hosts project.  It can also be modified
  through the minetest/builtin/ lua files.  I do not remember what I changed to
  make that happen, sorry.
- The main menus can be modified to remove the delete world button.  This saves
  tears laters.
- Rename `/killme` command to `/spawn`.
- Disable PvP.

The file minetest/builtin/mainmenu/tab_singleplayer.lua is the menu for
singleplayer.

Change this line:

```
			"button[4,4.15;2.6,0.5;world_delete;".. fgettext("Delete") .. "]" ..
```

to this:

```
--			"button[4,4.15;2.6,0.5;world_delete;".. fgettext("Delete") .. "]" ..
```

The file minetest/builtin/mainmenu/tab_server.lua is the menu for starting a
server.

Change this line:

```
		"button[4,4.15;2.6,0.5;world_delete;" .. fgettext("Delete") .. "]" ..
```

to this:

```
--		"button[4,4.15;2.6,0.5;world_delete;" .. fgettext("Delete") .. "]" ..
```

And this line:

```
		"checkbox[0.25,1.15;cb_server_announce;" .. fgettext("Public") .. ";" ..
```

to this:

```
--		"checkbox[0.25,1.15;cb_server_announce;" .. fgettext("Public") .. ";" ..
```

## Project ideas

- Try building your room/building/yard to scale.
- Change a mod.
- Build a mod.
- Create a subgame.

## Subgames to start with:

- [MineClone 2](https://git.minetest.land/MineClone2/MineClone2) - An addictive attempt at recreating a popular proprietary game that is similar to Minetest.  Includes achievements, mobs, experience, etc.
- [Minetest game](https://content.minetest.net/packages/Minetest/minetest_game/) - The default barebones game.  This is not very exciting, but a great starting point if you are building your own subgame.
- [Dreambuilder](https://content.minetest.net/packages/VanessaE/dreambuilder_game/) - Comes packed with lots of building materials

Older subgames:

- Carbone - Comes action packed with monsters and excellent mods
- Moontest - Start on the moon!  Warning You will suffocate without a spacesuit.

## Mods to look for:

- [Blockly Minetest](https://devel.trisquel.info/ruben/blockly-minetest) - adds
  a python and blockly api to build blocks with code.
- Technic - Adds tools that greatly enhance single player such as drills,
  chainsaws, and drilling lazers.  Add machines that must be powered by coal,
  solar, etc.
- [protector](https://forum.minetest.net/viewtopic.php?id=4212) - adds
  protection blocks.  This prevents your house from being destroyed or looted.
  Kids can be mean and this helps curb this.  Protection blocks can be added to
  your initial inventory as well by changing the mod
  /give_initial_stuff/init.lua with this line:

```
player:get_inventory():add_item("main", "protector:protect 1")
```

- craft_guide - With 5 sticks, you can build a craft guide.  This guide can be
  placed anywhere and shows all of the ways to craft any item available.  This
  allows you to stay immersed in the game without searching through code or
  forums to find crafting recipes.  Must be placed in the minetest/mods folder
  and manually added to each world.
- streets - adds roads to the game
- bags - Allows you to carry LOTS of items with you.  This helps mining
  expeditions greatly.  Warning: requires inventory_plus mod.
- sethome - Allows you to use commands to warp back to your house.
- pyramids - adds pyramids with treasure and traps
- ufos - adds spaceships
- worldedit - adds a world manipulation tool.  This is great for building large
  structures.

## Troubleshooting

Read the errors from the terminal and look them up on
http://wiki.minetest.net/Troubleshooting

The most common one I have run into is ```ServerEnvironment::loadMeta():
EnvArgsEnd not found``` and the solution is to delete the env_meta.txt in the
world's folder.
