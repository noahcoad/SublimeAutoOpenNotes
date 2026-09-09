# AutoOpenReadme

A [Sublime Text](https://www.sublimetext.com/) package.

Open a folder, and its readme opens with it.

No commands, no key bindings, nothing to remember -- it just listens for new windows.

## What it opens

When you open a new window with a single folder, it looks for the first of these that exists and opens it:

`readme.md` → `readme.txt` → `readme` → `notes.md` → `notes.txt`

## Where it looks

The folder's **root** first, then a **`docs`** folder, then a **`wiki`** folder.

Folders are searched in order and each one is checked for *every* filename before moving on. So a
`notes.txt` in the root beats a `readme.md` in `docs/`:

```
myproject/
  docs/
    readme.md     <- 3rd choice
    notes.txt     <- 4th
  notes.txt       <- 2nd
  readme.md       <- 1st, this is what opens
```

Both the filenames and the folders are configurable -- see below.

## Config

*Preferences → Package Settings → AutoOpenReadme → Settings*, or from the command palette,
*Preferences: AutoOpenReadme Settings*. Defaults:

```json
{
	"files": ["readme.md", "readme.txt", "readme", "notes.md", "notes.txt"],
	"folders": [".", "docs", "wiki"],
	"auto_open_file": ".sublime.autoopen"
}
```

| Setting | What it does |
|---|---|
| `files` | Filenames to look for, in priority order.  First match wins. |
| `folders` | Folders to look in, in order, relative to the folder you opened.  `"."` is the root. |
| `auto_open_file` | Name of the per-folder override file.  See below. |

Matching is whatever your filesystem does, so `readme.md` already finds `README.md` on macOS and
Windows but not on a case-sensitive filesystem -- add `README.md` to the list explicitly if you work on
one. Prefer notes over readmes? Put them first:

```json
{
	"files": ["notes.md", "notes.txt", "readme.md", "readme.txt"]
}
```

## Per-folder override

To open something else -- or several things -- drop a `.sublime.autoopen` file in the folder listing
one file per line. When that file exists, `files` and `folders` are skipped entirely and everything
listed gets opened:

```
# .sublime.autoopen -- lines starting with # are ignored
notes.txt
docs/architecture.md
todo.md
```

Paths are relative to the folder holding the `.sublime.autoopen`. Files that don't exist are skipped
quietly. Unlike the defaults, this works in multi-folder windows -- every folder is checked for its own
`.sublime.autoopen`.

## Try it

    mkdir ~/tmp/demo
    echo "hello world" > ~/tmp/demo/readme.md
    subl ~/tmp/demo

## The sweet flow...

Combined with the [Open URL](https://github.com/noahcoad/open-url) plugin ... create a projects.txt
file that you put lines in for each project folder.  Then just open this projects.txt file, put the
cursor over a line, ctrl+u to "open url" to that folder, and bamn, the folder is opened and the
appropriate readme/notes file is opened automatically.

## Notes

Only fires on **new windows opened with a folder**, and only once per window, so it won't fight you if
you close the file. Windows that already have files open are left alone.

## Acknowledgments

Shout out to [@josiahcoad](https://github.com/josiahcoad) for code reviewing and improvement ideas!

## Also

Check out my other [Sublime Text packages](https://gist.github.com/noahcoad/712ba4e38467f5126eb8cedd9ecbc842)
