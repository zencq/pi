# Every Item Procedural

![Maintained](https://img.shields.io/maintenance/no/2026)
![GitHub Release](https://img.shields.io/github/v/release/zencq/pi?display_name=release)
![GitHub Repo Size](https://img.shields.io/github/repo-size/zencq/pi)
[![Supported by the No Man's Sky Community Developers & Designers](https://raw.githubusercontent.com/NMSCD/About/master/badge/purple.svg)](https://nmscd.com/)

This repository contains a collection of files with values of stats for every
**P**rocedural **I**tem in [No Man's Sky](https://www.nomanssky.com/). This includes
mainly technology upgrades but also the products (treasures/artifacts in-game).

## Usage

Each item has two files, one easier for humans to read (`.csv`) and one better for
programmatic processing (`.parquet`). Each file includes the seed, its weighted
perfection in percent, the actual stats, and the procedural name in different languages.
The files itself and the stats are named with the game internal names but you can
use them without any developer knowledge.

All values are shown without rounding and without regard to its sign as it does
not matter for the purpose of this. Most, but not all, stats are shown in a in-game
like form. If not, the raw value is used (e.g. `UP_RAIL1` always showed `+2%` but
actually had a range from `30` to `40`).

There is also the `Pi.xlsx` file which is a user friendly collection of best and
most desirable seeds. It is categorized by inventory type and contains the best
values for each stat per item in addition to those already mentioned. The file is
automatically generated and not curated by hand.

## Known Issues

The following items are currently *outdated* or *not available* due to changes in
a newer yet unsupported game version. All supported versions can be can be seen
below and the latest item update in the [releases here on GitHub](https://github.com/zencq/pi/releases).

* All Corvette parts from **Voyagers 6.00** and up are not available.

## How it works 2.3

The current implementation utilizes [NMS.py](https://github.com/monkeyman192/NMS.py)
by [monkeyman192](https://github.com/monkeyman192). NMS.py (and its backend [pyMHF](https://github.com/monkeyman192/pyMHF))
is included in this repository as submodules to ensure best compatibility.

Currently it is designed to only work with the following GOG.com versions which
cover all changes/additions since the first one listed.
* 4.13
* 5.20
* 5.61
* 6.02

After cloning you must execute `git submodule update --init` in the newly created
directory to initialize the NMS.py and pyMHF submodules. Then install both in your
Python environment with the command `pip install .` by changing into the respective
directories, starting with pyMHF and followed by NMS.py. Finally adapt the inline
[config](https://github.com/monkeyman192/pyMHF/blob/master/docs/settings.md) at the
top of the mod file to your needs and you are ready to go.

To run it, simply execute the command `pymhf run .\NMSpy_mods\Pi.py`. When NMS.py
runs, a distinct terminal window opens where some information are logged. All output
is marked with `pi`.

As soon as the menu appears in the game, you can start generating via the GUI window
that opens short after the terminal. Both, technology and products, are enabled
by default but and can be toggled separately. The generation will run a couple of
minutes (depending on your machine) in the background with some progress logging.
It is also possible to set custom values for each category to only generate those
specific items (comma separated).

You can also extend the records with the generated names for multiple languages
by running it multiple times with different language settings. After a generation
is done, you can change the in-game language and immediately start it again without
restarting. This will not overwrite existing names of other languages. The
selected/new language will be shown in the log mentioned above.

## License

The tooling in this repository (e.g. `NMSpy_mods`, `generate_xlsx.py`) is licensed
under the [Mozilla Public License 2.0](LICENSE).

The collected data (the `.csv` and `.parquet` files in the item folders and `Pi.xlsx`)
is licensed under [CC BY 4.0](LICENSE-DATA). You are free to share and adapt it as
long as you give appropriate credit, e.g. "Data from [Pi](https://github.com/zencq/pi) by zencq".

The submodules `NMS.py` and `pyMHF` are separate projects with their own licenses.

No Man's Sky and all related game content are the property of Hello Games. This
project is not affiliated with Hello Games.

## Contributors

The main developers are:

* **zencq**
  * [GitHub/cengelha](https://github.com/cengelha) - [GitHub/zencq](https://github.com/zencq)

Thanks to all other contributors! You can find them in the sidebar or in detail in the [contributors graph](https://github.com/zencq/pi/graphs/contributors?all=1).

## Credits

* **monkeyman192** - Biggest thanks goes to him for creating NMS.py and the continuous support
* **DHarhan** - Giving feedback about the desirability of certain stats and combinations
* **ICE** and **DarkWalker** - Previously used scripts based on those shared by
  them in the Discord [Creative & Sharing Hub](https://discord.gg/RSGQFQv2pP)
