# 0.5.5

## New Features

* new commands `--data-dir` and `--repo-dir` to print the currently-configured
  dirs to stdout

# 0.5.4

## New Features

* `--list` colorisation of last 30 days turns out to be noisy in use, have
  changed to 7 days to make it more useful for quickly finding recent notes. So
  now color scheme is today=green, last 7 days=white, all other dates=grey

# 0.5.3

## New Features

* `--list` will colorise dates on recency; today=green, last 30 days=white,
  all other dates=grey

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
