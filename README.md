# FindConfig

FindConfig is a Python package which implements the simple task
of looking for a configuration file in a series of locations.

## Usage

```
from findconfig import findconfig

config = findconfig("my.config.yaml")
```

The command above returns the Pathlib path of the first file found in the
locations indicated below (in the order), which has the given filename,
with or without a prepended dot (e.g. ``.my.config.yaml`` in the example above).

## Config file locations

The locations which are searched are, in order of priority:
- the directories indicated in the XDG specification:
  - XDG config home
  - XDG config dirs
- the home directory of the user
- the source code directory of the calling program:
  - the directory of the calling module
  - any ancestor directory, stopping at (and including) the first one
    which does not contain a ``__init__.py`` file
- directories listed in the ``more_path`` keyword argument

### Options

The following keyword options can be used:
```
more_path (list of strings or Path, default: []): directory names to be searched
  into, in the order, _after_ the default locations stated above

allow_dot (boolean, default: True): also look for the filename with a prepended
  dot, if the filename does not start with a dot

use_xdg (boolean, default: True): enable searching in the XDG specification paths
use_home (boolean, default: True): enable searching in the user home directory
use_src (boolean, default: True): enable searching in the source code directory
                              of the program
```