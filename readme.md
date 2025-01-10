# MarkDown Shortcut

In this repository I attempt to reproduce what I think is a GitHub feature of
treating a MarkDown file as a shortcut.

I've seen this in the Mermaid repository https://github.com/mermaid-js/mermaid
where the `CONTRIBUTING.MD` file is "redirecting" to a nested MarkDown file
whose relative path is in the main file's content, and GitHub treats this file
in a special way as it has a dedicated "shortcut" icon.

Let's see if all it takes is for a file to have a relative path of another file
in its body or there is more magic to this that I am not privy to at the moment.

I created two shortcut files, `shortcut.md` and `shortcut2.md`, one before the
destination file existed and another after it did, however neither of them got a
special icon.

I am starting to think this might be a Unix thing with the file having special
attributes that GitHub renders the special icon for but no other special
handling.
This is supported by the fact that the Mermaid MarkDown shortcut file just opens
its raw content like any other MarkDown file without doing any sort of
redirecting or linkifying the content path.

The hypothesis turned out to be correct, after creating a shortcut using `ln`,
like so: `ln -s destination.md shortcut3.md`, and pushing the resulting file to
the repository, it now shows up with the special icon and its content is the
destination file as expected and as seen in the case of the Mermaid repository
file.
