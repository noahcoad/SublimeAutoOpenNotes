# Auto Open Notes

A [Sublime Text](https://www.sublimetext.com/) Package

## Description

When a new window is opened with a single folder:
1. A `.sublime.autoopen` file is looked for in the folder.  If it exists, each file listed in the file is then opened.
2. Otherwise it'll look for a `notes.txt`, `notes.md`, `readme.md`, `readme.txt`, then `readme` files in that order in the root folder then a `wiki` folder and opens the first it finds.

## To Use
Try having a notes.txt or readme.md file in a folder and opening that folder in sublime.

    mkdir ~/tmp
    echo hello world > ~/tmp/notes.txt
    subl ~/tmp

OR

Put the files you want to be opened when this folder is opened into a `.sublime.autoopen` file, like:

    # .sublime.autoopen contents
    my_other_note_file.md


## The sweet flow...
Combined with the [Open URL](https://github.com/noahcoad/open-url) plugin ... create a projects.txt file that you put lines in for each project folder.  Then just open this projects.txt file, put the cursor over a line, ctrl+u to "open url" to that folder, and bamn, the folder is opened and the appropriate notes/readme file is opened automatically.

## Acknowledgments
Shout out to [@josiahcoad](https://github.com/josiahcoad) for code reviewing and improvement ideas!

## Also
Check out my other [Sublime Text packages](https://gist.github.com/noahcoad/712ba4e38467f5126eb8cedd9ecbc842)

Started 2018-10-11