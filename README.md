# AutomaticSQLiteDBOptimizer

Automatically optimizes SQLite databases on boot, on schedule, every X days

Just a quick and dirty adaptation of an old SQLite3 optimizer script from init.d days (i think from following a chain of zips that it originates with XDA member **mcbyte_it** [here](https://forum.xda-developers.com/t/script-run-init-d-scripts-once-every-n-days-zipalign-sqlite3-others.2084573/)) (who's zipalign is also on the todo list, another reason i was able to trace to him because i was working on that too) to a Magisk Module using a service.sh script instead, 
with an internal date offset mechanism to run the script every X days (default: 3 - which is plenty, and specifically to stop silliness).

The script will wait until boot is completed AND then until avg CPU usage is under 30%, to minimise the risk of possible corruption. 

**Disclaimer:** As always any use of any 3rd party script/software/advice is at the users discretion. All reasonable efforts have been made to make this as safe as possible, but the responsibility ultimately falls to the user whether to use and run the script. 



### What it does: ###

It:

- Reindexes
- Vacuums 
- Analyzes 

all .db files under /data. 

It runs a 1st run optimize after install (temp file optimsql_first_run on sdcard is used to enable this, and removed afetr first run), and then on schedule after that. 

By default it logs just script progress to /storage/emulated/0/autosqlite.log, but you can choose to enable more detail in the log if you wish


### User Configurable Options: ###

The schedule and loglevel can be changed by an external file on sdcard:

1. Create a file named **autosqlite_options** on **sdcard (/storage/emulated/0/)**

2. Inside create the following key=value pairs to suit your preference:

*interval=x*   (where x is the number of days between script runs, for the love of god do not put 1 (this goes out especially to the kind of people who put every app on their Magisk magiskhide/deny list) there is no benefit and you just heighten the possibility of corruption)

*loglevel=x*   (where x is either 1 (detailed logging) or 0 (basic logging - default))

### Requirements: ###

This module requires a working SQLite3 binary. If your ROM does not provide one (you can can check via typing *sqlite3* into a terminal), you can choose to use my SQLite3UniversalBinaries module located here:


https://github.com/stylemessiah/SQLite3UniversalBinaries


Dont forget you need to download a named SQLite3UniversalBinaries.vx.x.zip file from the Releases page under Assets. Do not try installing the source code with Magisk Manager, it will not go as you expect


**Please note:** the included LICENSE only covers the module components provided by the excellent work of Zack5tpg's Magisk Module Extended, which is available for here for module creators

https://github.com/Zackptg5/MMT-Extended/


All other work is credited above and **no one may fork or re-present this module as their own for the purposes of trying to monetize this module or its content without all parties permission. The module comes specifically without an overall license for this intent.**


### Project Stats ###

![GitHub release (latest by date)](https://img.shields.io/github/v/release/stylemessiah/AutomaticSQLiteDBOptimizer?label=Release&style=plastic) ![GitHub Release Date](https://img.shields.io/github/release-date/stylemessiah/AutomaticSQLiteDBOptimizer?label=Release%20Date&style=plastic) ![GitHub Releases](https://img.shields.io/github/downloads/stylemessiah/AutomaticSQLiteDBOptimizer/latest/total?label=Downloads%20%28Latest%20Release%29&style=plastic) ![GitHub All Releases](https://img.shields.io/github/downloads/stylemessiah/AutomaticSQLiteDBOptimizer/total?label=Total%20Downloads%20%28All%20Releases%29&style=plastic)

???
