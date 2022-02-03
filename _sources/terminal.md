# Introduction to the Terminal

The terminal interface can be challenging at first glance since most of us are familiar with the
graphical user interface provided by our operating system. We like to point and click with the mouse,
so the keyboard-only terminal is difficult to navigate.

The basic idea of the terminal is that you are 'somewhere' in the file system. That 'somewhere' is a
*directory*, and directories contain *subdirectories* and *files*. A directory is equivalent to a folder.

*Commands* are used to navigate the file system, rearrange files, create and edit files, run executable
files, etc.

## Paths

The usage of most terminal commands mentioned on this page is the same:
`<command> <PATH>`

Therefore, it is imperative that you have an understanding of paths. A *path* is a string that tells the 
operating system where you want to go. On Linux, paths are separated by forward slashes.

On Lambda, your data is held at `/data/aneurysm/<your-username>`. The breakdown of this path is simple:
- `/` is called the *root directory*. It is the starting point of the entire file system.
- After the root directory, forward slashes (`/`) delimit subdirectories. Within the directory `/`, there
is a directory called `data`. Likewise, `aneurysm` is contained within `data`, and the directory with your
username is contained within `aneurysm`.

It's important to note that paths don't necessarily lead to directories. Individual files are also associated
with a path. For example, a file called "file.txt" in the aneurysm directory has the path `/data/aneurysm/file.txt`.

### Absolute and Relative Paths

A path that starts with the root directory is called an *absolute path*. This sort of path leads to the 
same place no matter where in the file system you are. If you want to access a file in your code, it's
often wise to use the absolute path to that file since it won't change even if you run your code from
a different place.

A path that starts with any character other than `/` is called a *relative path*. This sort of path leads
to a different place depending where you are in you code. For example, if you're in the directory `/data/`,
the absolute path to `/data/aneurysm/<your-username>/` leads to the same place as the relative path 
`aneurysm/<your-username>/`.

There are two special relative paths: `.` and `..`
- `.` refers to *the current directory*. `./aneurysm/<your-username>/` and `aneurysm/<your-username/` lead to 
the same place.
- `..` refers to *the current directory's parent*. `/data/aneurysm/../` refers simply to `/data/`.

## Navigation - The `cd` command

`cd` means *change directory*, and it allows you to move around in the file system.

The usage of `cd` is as previously mentioned:
`cd <PATH>`, with <PATH> being replaced with the path you want to go to.

Examples:
- `cd .` will do nothing, since it just brings you to where you currently are.
- `cd ..` will bring you to the parent directory.
- `cd ../..` will bring you two levels higher than your current directory - i.e. the parent directory of your 
parent directory.
- `cd /data/aneurysm` will bring you to the directory called `aneurysm`, located in the directory called `data`.
- `cd data/aneurysm` will fail if the current directory does not have a folder called `data` (which must then
have a folder called `aneurysm`) since it's a relative path.

## Listing - The `ls` command

`ls` (probably) means *list*. It lists all the files in the directory.

The usage of `ls` is as expected:
`ls <PATH>`, with <PATH> being replaced with the path to the directory you want.

`ls` without anything else is interpreted as `ls .`, i.e. it lists the files in the current directory.

## File Copying - The `cp` command

`cp` means *copy*. It allows you to copy files to a different place in the file system.

The usage of `cp` is as follows:
`cp <SOURCE> <DESTINATION>`

`<SOURCE>` is the path to the *file you want to copy*.
`<DESTINATION> is the path to the *location you want to copy the file to*.

If you want to copy a directory, you must add the `-r` flag:
`cp -r <SOURCE> <DESTINATION>` 

## File Moving - The `mv` command

`mv` means *move*. However, in many cases it is used to rename files or directories.

The usage of `mv` is as follows:
`mv <SOURCE> <DESTINATION>`

If <DESTINATION> is not an existing path, <SOURCE> will simply have its name changed to
<DESTINATION>.

If <DESTINATION> is an existing **file** and <SOURCE> is a **directory**, the command will error out.

If <DESTINATION> is an existing **file** and <SOURCE> is a **file**, the contents of <DESTINATION> will
be overwritten by the contents of <SOURCE>.

If <DESTINATION> is an existing **directory**, <SOURCE> will be moved into <DESTINATION>.

## File Creation - The `touch` and `mkdir` commands

Linux has dedicated commands for creating empty files and directories. The usage is very simple.

`touch <FILENAME>` will create an empty file called <FILENAME> *in the current directory*. If you want to
create a file in a different place than your current directory, you have to adjust the path you give.

Likewise, `mkdir <DIRNAME>` will create an empty directory called <DIRNAME> in the current directory.

## File Editing - The `nano` editor

Obviously, you'll need to edit files. In the terminal, there's no Notepad or VSCode for you to open up -
if you want to edit a file, you have to do it in the terminal window. Linux provides several editors, but
the most appropriate one for a new user is probably nano.

The usage of nano is very simple:
`nano <FILENAME>`

If there is no file called <FILENAME>, *nano will automatically create one*. 

All the nano commands are found at the bottom of the screen once you enter the editor.

## Package Installation - The `pip3` command

Sometimes when running your code, you might encounter an error that says something like "Package not found: xyz".

When this happens, it's a sign that you need to install a package that you're lacking. This can be done
with the `pip3` command:

`pip3 install xyz`

This will download the requested package to your Python environment.

**Note: Some sites might tell you to install a package with pip. On Lambda, *you MUST use pip3*!!!**
