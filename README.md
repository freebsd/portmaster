This script uses the existing ports infrastructure to track dependencies,
and keep them up to date.  It is written in /bin/sh so it has no dependencies.

Portmaster has the following features:
  * Updates and repairs (as needed) entries for dependencies in both +CONTENTS
    and +REQUIRED_BY files for both the port that is being updated, and any
    ports that depend on it
  * Runs make config recursively through all ports before starting build
  * Downloads distfiles in the background
  * Recursively checks and upgrades (or installs) all dependencies
  * User can force upgrades of all dependent ports
  * Offers the user the opportunity to delete stale distfiles
  * Supports ports/MOVED and non-default settings of PORTSDIR and PKG_DBDIR
  * Interactive update mode (prompts for each update)
  * Option to rebuild port, and ports that depend on it
  * Options to make packages out of installed, and new ports
  * Option to clean out stale port dependencies
  * Options to list installed ports by category, and those with new versions
  * Packages can be used for installation either exclusively, if available,
    or only for build dependencies

WWW: https://portmaster.github.io/

IRC: ircs://irc.libera.chat:6697/#portmaster
