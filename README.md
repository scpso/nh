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
