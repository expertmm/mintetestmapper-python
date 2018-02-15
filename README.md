# minetestmapper-python
Use python to make minetest maps from worlds.


## Goals:
* Conform syntax and features to the new official [https://github.com/minetest/minetestmapper](minetestmapper) which is in C++
* Add all features (especially standard output of geometry) from minetestmapper-numpy.py to minetestmapper.py
* Maintain minetestmapper-numpy.py (minetestmapper.py is considered low priority but seems to work better for sqlite worlds)
* Keep pace with changes to Python and minetest world format


## Reason for forking
* **minetestmapper.py**: The official python mapper util was discontinued by the minetest team because making maps using python is difficult to do efficiently considering the amount of data, and it was no longer considered necessary since they are now maintaining a C++ port at <https://github.com/minetest/minetestmapper> (the problem was eliminated by eliminating the python mappers from the repo, though spillz had significantly improved the performance using numpy in a fork).
* **minetestmapper-numpy.py**: Unfortunately, support requests directed to spillz have been on his [official thread](https://forum.minetest.net/viewtopic.php?f=14&t=8730) for a long time now, so I am placing that here. In addition, there is no reason to fork minetest to work on these mappers (spillz' version is in his fork of minetest), as the python mapper is no longer there. I suggest to spillz that if he continues his work on it, that he forks from here for that reason.
* **minetestmapper**: As for the C++ version of minetestmapper, for now it lacks some of the functionality of these mappers, and must be compiled from source in order to be installed. In addition, many steps are required in order to create a colors.txt file that covers all of your mods. Many authors have created some great colors.txt files, so all of that will be combined into this project's colors.txt (for reasons such as VenessaE's colors.txt makes prettier maps). This project can continue alongside the C++ version but hopefully the C++ version will integrate some important features so it can be used by web map projects.

### Replaces the following deprecated projects:
* minetestmapper.py (and related sectors2sqlite.py) formerly located at <https://github.com/minetest/minetest/tree/master/util>
* minetestmapper-numpy.py stranded as a pull request (in spillz' minetest fork) then apparently abandoned


## Requirements
* Python Imaging Library: http://www.pythonware.com/products/pil/
* The colors.txt should be generated by <https://github.com/expertmm/EnlivenMinetest/blob/master/mtanalyze/minetestinfo.py> for the most complete colors list (unless you use the more complicated [minetestmapper method]([https://github.com/minetest/minetestmapper])) and prettiest map until that code is moved from EnlivenMinetest to the minetestmapper-python project.

## Known Issues:
* has exception for unknown reason which may be related to why it doesn't draw higher than y=0 see `print("<Could not finish writing r error since r was not initialized>")`
* conform minetestmapper-numpy.py to official minetestmapper:
  * make input path to go after an `-i` param instead of being positional
  * make output path to go after an `-o` param instead of being positional
  * add `--geometry` param
  * add `--colors` param (see `load_colors()` which should be `load_colors(fname=x)` where x is a path specified by the user)
* conform minetestmapper.py to official minetestmapper:
  * add `--min-y` and `--max-y` params (see `for y in reversed(range(16)):`?)

## Changes
(2018-02-15)
* expertmm: clarified license notices in python files
* expertmm: (minetestmapper-numpy.py) changed minheight and maxheight to --min-y and --max-y to conform to official minetestmapper
(2018-02-14)
* expertmm: (minetestmapper-numpy.py) fixed exception while showing exception (see "Could not finish writing r error since r was not initialized")--the original exception occurs for unknown reason
(2017-04-12)
* expertmm: (minetestmapper.py) PEP8 compliance
(2017-03-17)
* expertmm: (minetestmapper.py) removed license from script (file should fall under the LICENSE included in the project)
(2016-03-08)
* expertmm: (minetestmapper.py) geometry and region params
(2011-07-30)
* WF: Support for content types extension, refactoring
* erlehmann: PEP 8 compliance.
(2011-06-04)
* celeron55: added #!/usr/bin/python2 and converted \r\n to \n to make it easily executable on Linux
(2011-06-02)
* j0gge: command line parameters, coordinates, players, ...
(2011-05-30)
* celeron55: simultaneous support for sectors/sectors2, removed
(2011-05-29)
* j0gge: initial release
