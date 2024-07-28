# Shell Notes

A zero dependency POSIX compliant shell script that makes it really simple to
manage your text notes.

Instead of trying to impose a whole bunch of rules and syntax requirements,
this tool does its best to get out of your way.

It tries to do everything possible so that if you're working in a terminal, you
can save whatever text you want into a file. This could come from typing a
sentence out, pasting something from your clipboard or saving the output of a
program.

Original Author: [Nick Janetakis](https://github.com/nickjj/notes)

## Design Goals and Philosophy

Low friction note taking without worrying about specific file types, formatting, tagging,
check boxes, syntax rules and a bunch of other things that delay you from
getting something out of your head and into a document.

### Text is amazing for notes because:

- You can use `grep` and friends to search through it later
- Very low disk space used.
- It's really easy to back up and sync to other devices using Drop Box or similar tools

Since it's unstructured text you can use this tool for whatever type of note
taking you want. You can keep track of general thoughts, create a diary etc.

There's other things you can do such as piping input to it, or running the
script without any arguments to open the file in your configured `EDITOR`.

### What is this script not good for?

Depending on how you work, it's probably not ideal for grouping up a bunch of
extended thoughts about a specific topic.

For example, if you were planning to write a book then you would end up with a
bunch of isolated date formatted files that was mixed in with everything else.

## Installation

Copy / paste the line below, or if you don't like this pattern of installing
scripts then feel free to run things manually.

### 1 liner to get `notes` downloaded to `/usr/local/bin`:

```sh
sudo curl \
  -L https://raw.githubusercontent.com/da5atar/notes/master/shell-notes \
  -o /usr/local/bin/notes && sudo chmod +x /usr/local/bin/notes
```

You can also choose to replace `master` with a specific [release
tag](https://github.com/da5atar/shell-notes/tags) if you want to grab a specific
version.

There's no fancy `git clone` instructions because you may end up modifying at
least 1 line of the script. Plus since the script is so simple, this repo is
likely not going to change and if it does you will be able to `diff` it without
any issues.

### Configuration

By default it will use `${HOME}/notes` as your notes directory and if that
directory doesn't exist beforehand, this script will allow you to create it
with a `y/n` prompt when you first run the program.

You can also customize your notes path in 1 of 2 ways:

1. Put `export NOTES_DIRECTORY="/tmp/foo"` in your `~/.profile` or equivalent
file (`/tmp/foo` would be your notes path)
2. Directly edit the `notes` script and replace `${HOME}/notes` with `/tmp/foo`
in the `NOTES_DIRECTORY` variable

Also, if you want this script to open your notes in your code editor you'll
want to make sure you have your `EDITOR` defined in your `~/.profile` too. This
is a Unix standard. For example, mine looks like `export EDITOR="micro"`.

*If you change your `~/.profile`, don't forget to log out / login.*

## Usage Examples

There's 3 ways of using this script:

- `notes something you want to jot down`
  - Appends whatever arguments you add as text into the dated file

- `xclip -o | notes`
  - Pipes and appends anything (in this case your clipboard's contents) into the dated file

- `notes`
  - Opens the dated file in your configured `EDITOR`

That's really all there is to it. With the above 3 ways of adding notes you'll
find yourself adding all sorts of different types of notes with very little
friction.

If you wanted to go all out, you could even create custom key binds in your
code editor that would take the selected text and append it to your notes by
running one of the above commands. Since everything is text you have a lot of
flexibility!

Also, you have the power of the command line at your finger tips to manipulate
these files however you see fit. For example you can run `cat 2019-*-*.txt >
2019.txt` to create a yearly file.
