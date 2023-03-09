## MIRV Missiles AKA Fragmentation Mod
![GitHub tag (latest by date)](https://img.shields.io/github/v/tag/miketanJp/PB_fragmentMod?color=red&label=latest) ![GitHub release (latest by date and asset)](https://img.shields.io/github/downloads/miketanJp/PB_fragmentMod/v1.0.0/PB_FragmentMod.7z?color=red&label=Download) ![GitHub](https://img.shields.io/github/license/miketanJp/PB_fragmentMod)

A library mod for [Phantom Brigade](https://braceyourselfgames.com/phantom-brigade/), a Hybrid turn-based strategy game by [Brace Yourself Games](https://braceyourselfgames.com). The mod is developed in C-Sharp programming language with the use of [Harmony Framework](https://harmony.pardeike.net/).

The main purpose of this mod is to introduce [MIRV Missiles](https://en.wikipedia.org/wiki/Multiple_independently_targetable_reentry_vehicle) and and a delayed fragmentation mode. It can be crafted into the workshop as well, provided you have the necessary workshop charge (and resource) to make it.

## Installation / Editing
- Go to PhantomBrigade folder (located in C:\Users\[USER]\AppData\Local\PhantomBrigade) and create a folder named 'Mods' inside of it, if not present;
- Create a YAML file named 'mods.yaml' (including the file extension name) if not present;
- Open Notepad++ / Sublime Text and insert the following properties as shown below:
<br>![mods_config_02](https://user-images.githubusercontent.com/88181255/188758336-726faaca-9031-47d2-8ec4-07fa2e98f845.png)
- Save the changes into AppData\Local\PhantomBrigade\Settings;
- In the PB_fragmentMod.7z file, copy and paste the whole mod folder (fragmentMod) into Mods folder;
- Start the game, go to Mods menu and enable the mod (you have to reboot the game as the game doesn't support hot-plug mod loading);
- Find the Missile Launcher "MRV/01 Vanguard" and Enjoy!

More information about Phantom Brigade's Modding System can be found [here](https://wiki.braceyourselfgames.com/en/PhantomBrigade/Modding/ModSystem).

## Basic introduction
The main idea to develop the mod came when I tried, through weapon config files, to apply the same fragmentation properties used by shotguns as a similar system doesn't officially exists for missile launchers. It made me realize that approach wasn't technically possible as I needed to split the projectile after a set time. The system used in shotguns works in order to apply instant fragmentation only for that kind of weapons.

The mod uses custom properties in the weapon's YAML file, each one of them can be customized with desired values. Fragmented projectiles created in that istant will then inherit the properties of the original one (guidance data, projectile speed, lifetime, etc.).

<b>Custom values used in this mod</b>
- fragment_count (ints) → The number of fragments created from the original warhead while splitted;
- fragment_delay (floats) → The interval of the missile before splitting into several fragments from the moment it has been fired;
- fragment_scatter_angle (floats) → Scatter angle of the splitting missiles. It relies on wpn_scatter_angle property;
- fragment_key (strings) → The subsystem (actual weapon) where the injection should happen.
- fragment_hardpoint (strings) → The weapon hardpoint where the fragmentation will be performed;
- fragment_fanout (strings) → Fanout pattern to perform the desired splitting mode;
- fragment_scale (vectors) → New projectiles scale express in Vector3 coordinates (X,Y,Z);

<b>Custom properties (Missile Launcher YAML file)</b>
<br>![properties_example](https://user-images.githubusercontent.com/88181255/188760147-1e2c772f-ae3e-4c79-88d1-2fef853b4b59.png)


<b>WARNING:</b> in order to avoid issues, it is strongly adviced to set an amount between 18 and 23. For some strange reasons, if the set amount of child missiles is huge, results are that some of them are either gone or causing visual issues.

## Images
![starbust](https://user-images.githubusercontent.com/88181255/188744853-dbecbb07-64be-403b-95ce-61c9e719f7cf.png)
"Starburst" Pattern

![circular](https://user-images.githubusercontent.com/88181255/188744872-4971d4ce-05b7-419c-ae5d-b48cb301d5f8.png)
"Circular" pattern

## Mod live demo
https://user-images.githubusercontent.com/88181255/188748556-9b0dc88f-db61-4542-816c-647e1e9dcfc7.mp4
