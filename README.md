# elm-format-fast

This is a little script for running elm-format.

As a full-time Elm developer who works from the command-line, I often run `elm-format . --yes` in the root of a big Elm repository containing many hundreds of Elm files.

It takes several seconds, which is slow enough to be annoying, slow enough that I will get distracted and lose my train of thought.

This script shells out to elm-format, but it remembers which files were formatted last time, and doesn't re-format files that have not changed.

The first time you run it it will be quite a lot slower than elm-format, because it runs it file by file without multi-threading. But on subsequent runs where you only change a few files each time, it is much faster, perhaps by a factor of 50.

It requires Python3, but doesn't use anything outside the standard library.

Just download the script, put it somewhere on your path, and set it to have executable permissions.

It will create a file called `.elm-format-cache` in your home directory. This contains the hashes of all the formatted files.

It works because hashing algorithms are much faster than the formatter. Another approach would be to use the timestamps on files, but I don't know how reliable this would be.
