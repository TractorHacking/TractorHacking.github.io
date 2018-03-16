---
layout: page
title: Processing Script
---
The processing script used to process raw CAN data from the scope CSV output
can be [found here](https://github.com/TractorHacking/Scripts/tree/master/tractordata_parse).

# Contents

# Releases

There are two releases at the time of writing this page:

[v1.0](https://github.com/TractorHacking/Scripts/tree/v1.0/tractordata_parse): Single-file script without setuptools integration. The more "stable" version.
[v1.1](https://github.com/TractorHacking/Scripts/tree/v1.1/tractordata_parse): Modularized version of the above script, with some unfinished features. This is more bleeding-edge version.

# Examples

(note that the program name may very depending on your execution environment - either a local script `./tractordata_parse.py`, or a script in your path, `tractordata_parse`.)

To list all packets with the PGN 0xF004, while also showing the source address:

`tractordata_parse id-info --sortby-pgn --target-info 0xf004 --show-src`

To list all unique PGN values:

`tractordata_parse dump-ids --sortby-pgn`

To list all unique sources:

`tractordata_parse dump-ids --sortby-src`


