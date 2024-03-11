# 0.5.2

## Performance Improvement
* `--list` command now runs ~5x times faster

# 0.5.1

## Bugfixes

* correct the syntax described by --help
* search for correct nhconf file

# 0.5.0

## Breaking Changes

no migration is provided; updating existing nh repos to be compatible with
0.5.0 needs to be done manually

* change format of pwd and tags indexes; this affects most functions.
* store pwds with ~ substitution for $HOME

## New Features

* index titles; commands that select existing notes like --edit and --cat can
  now select based on uuid or title

## Bugfixes

* shortcircuit commands --help and --version now bypass dependency checks
