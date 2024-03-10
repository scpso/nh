# nh - Note Here

This project is licensed under the terms of the MIT License.

I am a compulsive note-taker. In my work I often find I want to take notes that
are contextual to a project or other shared directory, but I don't want to
pollute the shared environment with my private thoughts. Thus I'm in the
habbit of recording notes elsewhere with sloppy/inconsistent/unsearchable
references to the original directories they're relevant to.

nh is a simple utility - a single bash script - that simply provides a wrapper
around my text editor to record bits of metadata including the PWD where the
note was authored and a simple tagging feature. But both the note content and
the metadata are stored in their own directory structure which, additionally,
can be automatically synced to a private github repo for use across different
devices.

Notes are presented in `.md` format just for nice syntax highlighting - I've
been storing my notes as `.md` for years so this feels natural to me. This too
is the reason for the metadata key/value formatting.

It also served as a good project to nudge my bash scripting forward with a
few patterns I intend to repeat elsewhere.

It's not exactly feature-complete, and any weird shenanigans with the
underlying git repo will likely require some manual intervention, but from my
perspective this is acceptable.

This is entirely a personal project and I may extend or change or otherwise
break it…

## Install

The file nh in the root of the repo is the only required file for full
operation. As such the easiest way to install the latest version is:

    cd ~/somewhere/in/your/path # e.g. ~/bin
    curl https://raw.githubusercontent.com/scpso/nh/main/nh >nh
    chmod 744 nh

You can verify it's working correctly with:

    nh --version

Before you can start storing notes you'll need to initialise a repo. For just
trying nh out a local repo is best:

    nh --new-lrepo

nh will read the $EDITOR environment variable to choose a text editor to run,
falling back to nano if $EDITOR is not set. It's not required, but if you want
to you can set this permanently (with, for example, vim as your preferred
editor):

    printf 'EDITOR=vim\nexport EDITOR\n' >>~/.bashrc

To write a new note, just run nh with no other commands:

    nh

To list existing notes:

    nh --list --all

to edit an existing note, you can specify it with the first few characters of
the note's id or its title (both of which are displayed by the --list command:

    nh --edit mynote

Check the help for more commands:

    nh --help
