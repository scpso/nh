# 0.6.1

## Bugfixes

* `--data-dir`, `--repo-dir` and `--git` commands all bypass repo consistency
  check and can thus be used to help repair underlying repo errors
* Empty `QUERY` when required now causes a fatal error instead of a malestrom
  of ouput iterating over all files in the repo
* When hunting for a config file in `XDG_CONFIG_DIRS`, will now break on first
  found file

# 0.6.0

## Breaking Changes

* Versions prior to `0.6.0` were mistakenly passing non-option arguments
  appearing before a `--` through to the external commands `cat` and `grep`
  when nh was run with the `--cat` and `--grep` commands respectively. This
  perhaps didn't matter much as these versions of nh had no meaningful
  non-option arguments anyway but it was incorrect and unintended behaviour.
  For `0.6.0` onwards, the `--` is explicitly required to pass through options
  or arguments to `cat`, `grep` and now also `git`.
* The existing commands `--cat`, `--delete`, `--edit`, and `--move` all
  operate similarly on an existing note that needs to be identified with a
  fragment of its uuid or title. Previosly this was specified with a required
  argument to the option, but now these commands all read from the trailing
  arguments, named `QUERY` in the `--help`. The significance of this is:
  1.    Option order is now less finnicky when using these commands.
  2.    Titles containing spaces can be queried without quotes - i.e. the
        command:

            nh -e my existing note

        will concatenate the arguments `my`, `existing` and `note` into the
        title query `my existing note` and search for a note with a matching
        title accordingly. This saves keystrokes but in particular is ergonomic
        when an initial query isn't specific enough, say:

            nh -e my

        matches notes with titles `my existing note` and `my previous note` -
        `nh` will notify the user of the multiple matches and the user need
        only re-run their prior command and append an extra argument:

            nh -e my existing

        to open the intended note; it is no longer necessary to cursor over the
        the prior command in order to wrap the entire argument in quotes:

            nh -e 'my existing'

        As such the workaround of only using `-` or `_` characters to separate
        words in titles instead of spaces is longer beneficial in this way -
        though it's certainly still acceptable and not discouraged if the user
        chooses to do so for their own reasons.
  3.    Be aware that even when extra arguments are split around options, they
        will still be concatenated into a single query string, i.e. the
        command:

            nh my -e existing

        will still resolve to a title query of `my existing` - this behaviour
        is considered technically correct in terms of command parsing and we
        don't question a user's choice to express their command however they
        see fit (and, importantly, using whatever tool they see fit to generate
        such commands), and nor do we otherwise assume that technically correct
        and usable input expressed in a non-conventional order is problematic.
* Note that, as with prior versions, `nh` will silently ignore options or
  arguments that aren't meaningful and will only complain if a command is
  explicitly incorrect. It would perhaps be beneficial to warn users in such
  circumstances to help educate and avoid the user building mistaken beliefs
  about various option combinations - such a warning may be added to a future
  version, but currently there is no logic in the codebase to explicitly
  identify extranneous input, only logic to ensure required input is present
  and not conflicting.

## New Features

* New command `--git` to run git commands directly on the notes repo. As with
  `--cat` and `--grep`, arguments after `--` are passed through to `git`.

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
