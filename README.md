## PB_fragmentMod
A library mod for [Phantom Brigade](https://braceyourselfgames.com/phantom-brigade/), a Early-Access game under development by [Brace Yourself Games](https://braceyourselfgames.com). It is programmed in C-Sharp with code-injection through [Harmony Framework](https://harmony.pardeike.net/).

The main purpose of this mod is to introduce [MIRV Missiles](https://en.wikipedia.org/wiki/Multiple_independently_targetable_reentry_vehicle) with different splitting patterns to choose from.

<b>NOTE:</b> as the mod is still a WIP and game updates may brick the mod out, is way to be perfect and fully operational without any future-proof fixes. This is my very first attempt to manipulate projectiles at runtime through code-injection level, without the need to modify projectiles' input curve contained in each weapon's YAML file config.

Since the mod is mainly tested on the Experimental version of the game, it may be broken in case of conflict with new game updates.

## Installation and required tools
- Go to PhantomBrigade folder (located in Documents/My Games) and create a folder named 'Mods' if not present;
- Create a YAML file named 'mods.yaml' (including the file extension name) if not present;
- Open mods.yaml with Notepad++ / Sublime Text (either one of them is mandatory) and insert the following properties as shown below:
- ![mods_config_02](https://user-images.githubusercontent.com/88181255/188758336-726faaca-9031-47d2-8ec4-07fa2e98f845.png)
- Save the changes;
- In the PB_fragmentMod.7z file, copy and paste the whole mod folder (fragmentMod) into Mods folder;
- Start the game, go to Mods menu and enable the mod (you have to reboot the game as it doesn't support hot plug mod support);
- Find the Missile Launcher "Sling" model and enjoy!

More information about Phantom Brigade's modding system can be found [here](https://wiki.braceyourselfgames.com/en/PhantomBrigade/Modding/ModSystem).

## Basic introduction
The main idea to develop this kind of mod came when I tried, through weapon config files, to apply the same fragmentation properties used by shotguns as a similar system weren't available to Missile Launchers. This made me realized that approach wasn't technically possible as I needed to split the projectile after a set time. The system used in shotguns works in order to apply instant fragmentation (immediately after the projectiles are fired) and the fragmentation delay algorithm works specifically for that kind of weapons, which is why I decided to develop a fragmentation system specifically for missiles.

The mod uses custom properties in the weapon's YAML file, each one of them can be customized with desired values.
New projectiles created in that istant will then inherit the properties of the original warhead (guidance data, projectile speed, lifetime, etc.), since the child projectiles will either cause conflicts or empty assets with no properties attached ( = mere game props with no "soul").

Since the game is built around Unity Game Engine, missiles (as well as ballistic projectiles) use a good amount of rotation functions to obtain facing, rotations and custom calls to perform more or less the same operations with lesser code.

<b>Custom values used</b>
- fragment_count (ints) → The number of fragments created from the original warhead while splitted;
- fragment_delay (floats) → The interval of the missile before splitting into several fragments from the moment it has been fired;
- fragment_scatter_angle (floats) → Scatter angle of the splitting missiles. It relies on wpn_scatter_angle property;
- fragment_key (strings) → The subsystem (actual weapon) where the injection should happen.
- fragment_hardpoint (strings) → The weapon hardpoint where the fragmentation will be performed;
- fragment_fanout (strings) → Fanout pattern to perform the desired splitting mode;
- fragment_scale (vectors) → New projectiles scale express in Vector3 coordinates (X,Y,Z)

<b>WARNING:</b> in order to avoid issues, it is strongly adviced to set an amount between 18 and 23. There's no way a real MIRV missile can hold such a high number of independent wareheads (i.e. 30).

## Images
![starbust](https://user-images.githubusercontent.com/88181255/188744853-dbecbb07-64be-403b-95ce-61c9e719f7cf.png)
"Starburst" Pattern

![circular](https://user-images.githubusercontent.com/88181255/188744872-4971d4ce-05b7-419c-ae5d-b48cb301d5f8.png)
"Circular" pattern

## Live Demo
https://user-images.githubusercontent.com/88181255/188748556-9b0dc88f-db61-4542-816c-647e1e9dcfc7.mp4
