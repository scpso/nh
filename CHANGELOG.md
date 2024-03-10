# 0.5.0

## breaking changes

no migration is provided; updating existing nh repos to be compatible with
0.5.0 needs to be done manually

* change format of pwd and tags indexes; this affects most functions.
* store pwds with ~ substitution for $HOME

## new features

* index titles; commands that select existing notes like --edit and --cat can
  now select based on uuid or title

## bugfixes

* shortcircuit commands --help and --version now bypass dependency checks
