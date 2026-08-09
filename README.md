# ACSE Mod Template
This repository is a template for an ACSE Cobra Engine mod. This repository should be located within the `GAME_NAME\Win64\ovldata\` folder.

## First Setup
### Renames
There are two find and replace operations you must complete on this repository:
- The text `INSERT_MODNAME_HERE` must be changed to your mods name across every file in the repository. 
  - Additionally, the root folder directory should be named like `GAME_NAME\Win64\ovldata\INSERT_MODNAME_HERE\`, with the `INSERT_MODNAME_HERE` being changed. 
  - Additionally, the file `INSERT_MODNAME_HEREluadatabase.lua` must also be renamed.
- The text `INSERT_UUID_HERE` must be changed to a 128-bit UUID. You can generate such a UUID here: https://www.uuidgenerator.net/.

### Cobra Tools setup
This repository is set up to work with the "flatten lua subfolders" setting in Cobra Tools. Please turn it on if it isn't. If you do not want to use this setting, simply add `database.` to the start of the luadatabase file, and move it directly under the Main folder.

### Packaging
In the OVL tool `ovl_tool_gui.py`, navigate in the top bar to `File > New`. Then select the Main folder within this folder. You will note any lua or file errors in the console. Then, navigate to `File > Save`, this will save the OVL, and you should see the toplevel directory contains three files:
- Main (folder)
- Main.ovl
- Manifest.xml

You should then, if running ACSEDebug, see the printout in the log: `INSERT_MODNAME_HERE called Init()!`. If you do not see this, something has gone wrong. Recheck all renames, and make sure your Manifest has a UUID.

## VSCode build setup
This repository automatically includes my own developed and battle-tested build scripts which automatically build, launch or package the mod for release!

Note, massive credit to Inaki from the Cobra Tools team for contributing the code for packaging `*.PPUIPKG` files.

There are just a few things to do:
- Set an Environment Variable in your Operating System called `COBRATOOLS` to be the path to your installation of Cobra Tools. This is mine for example: `D:\Git\cobra-tools`. 
- Make sure you have an `.ovlpaths` file in this directory. It should contain a list of relative folders which will be packed into OVLs.
- If doing UI, also include a `.uipackages` file in your main directory. This should contain a list of relative folders which will be converted into `.ppuipkg` files when their parent OVL is built.

If you have done this, you should now be able to navigate to the Run and Debug menu in VSCode and select one of the three options at the top next to the green arrow:
- Run Build (builds the entire mod).
- Run Build and Launch (builds the mod and starts up Planet Coaster 2).
- Package Build (packages the existing build artifacts [ovls, aux files, etc] into a .zip for easy distribution).