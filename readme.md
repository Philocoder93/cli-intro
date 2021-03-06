# The CLI (Command Line Interface)

## Learning Objectives

### Concepts

- Compare and contrast CLIs with GUIs.
- Explain how command line usage can increase efficiency.
- Describe the anatomy of a command: statements, flags and arguments.
- Explain what a path is and why the 'current path' is important in the CLI.
- Explain the difference between absolute and relative paths.

### Mechanics

- Setup your working directory / environment for WDI.
- List common commands to...
  - View the path of the current directory.
  - View the contents of a directory.
  - Navigate to different directories.
  - Manage files and directories.
- Open files and directories with Atom.
- List unsafe commands.

## Framing (5 minutes / 0:05)

As developers, we need a tool to communicate with our computers. Operating systems like Windows or OSX generally provide a graphical user interface (GUI) so that we can do this. They also, however, provide an interface that is strictly text-based: the Command Line (CLI).

**Turn & Talk:** Given your exposure to the Command Line in the pre-work and Installfest, spend **2 minutes** discussing and writing down some answers for the following questions with a partner...

* How is the CLI different from the GUI?
* What do you like / dislike about using it?
* Compared to a GUI, in what ways might using the CLI be better or worse for developers?

---------------------------------------------------------------------------

### Why The CLI? (10 minutes / 0:15)

Simply put: **if you want to learn to code, you must know your way around the CLI.** Programming languages are an advanced means of controlling your computer. Learning the CLI teaches you to control the computer purely using language. Once you get past that, you can then move on to writing code and make the hunk of metal in front of you do what you want.

#### Benefits of the CLI

**Speed.** Developers can execute common tasks much faster using the CLI. Features such as tab completion,
command history, piping and more all contribute to this.

> Try a `.txt` file on your computer, first via the GUI, then the CLI using the `touch` command. Which way is quicker?

**Precision.** We can look at the commands we're about to enter and understand exactly what they will do. This allows for...

**Repeatability / Scriptability.** We can easily save commands and re-use them, or even share them with others.

> What you did during Installfest was run a set of scripts that we shared with you!  

**Tools.** There are tons of tools we can use in the CLI to achieve a vast number of tasks. Most of them are built in, but we can also download external ones using services like Homebrew (OSX) and `apt-get` (Linux).

> Tree is an example of a nifty third-party tool. It's useful in visualizing directory structure. Try downloading it by running this in the CLI: `$ brew install tree`.
>
> Tools built for the command line usually follow something called
the ['Unix philosophy'](http://catb.org/esr/writings/taoup/html/#id2807216), meaning each tool should do one thing and do it
well. Complex tasks can be achieved by chaining tools together.  

**Debugging.** Whenever we get an error in the CLI, it will often come with a lot of information that we can use to then debug it. As developers, this preferable to what can often be unhelpful GUI errors, like this...

![](http://coding-journal.com/wp-content/uploads/2013/10/Screen-Shot-2013-10-30-at-12.02.14.png)

> All these benefits aren't necessarily exclusive to the CLI (compared to a traditional GUI), but they tend to be more consistent.

--------------------------------------------------------------------------------

## DEMO: Hello.txt using GUI vs CLI

> Note: There's nothing wrong with combining the powers of both the CLI and a GUI! We generally won't be writing files in the terminal. We'll be using the Atom GUI. This just highlights that there are efficiencies that can be garnered from knowledge of CLI.

We might be thinking to ourselves, "These differences are negligible! Which in this contrived example, it's a difference of MAYBE 5 seconds. But in the span of our careers as developers, becoming proficient with the command line is extremely important. It will end up saving us lots of time.

## CLI Basics (30 minutes / 0:45)


### Everything is a Command

Everything we enter into the command line is a **command**. When we hit enter, the command is executed.  

In this and future lesson plans, we will indicate a line of code is a CLI command by prefacing it with the `$` symbol.

### Output and Side Effects

Some commands have **output**, which is displayed on the screen for us to see. Examples of commands that have output are...

* `pwd`
* `ls`
* `telnet towel.blinkenlights.nl`

> Don't worry about `telnet`. Chances are you won't see it again in WDI. It's just a means of connecting to a remote computer via the Terminal.

Other commands' primary purpose is to execute some **side-effect**, or in other words, to make some change that isn't necessarily printed in the Terminal after hitting enter.
* For example, `touch`. This creates a file in an indicated location. We do not, however, get a confirmation it did this immediately after hitting enter.

> Often times, a command whose main job is a side effect may not provide any output if it succeeds. If there is an error, it will provide output.
>
> Some commands may provide both an output and side effects.

### Command Syntax (Flags and Arguments)

Commands generally consist of three parts...
  1. Command
  2. Flags
  3. Arguments

The **Command** is the first word you type into the CLI (e.g. `ls`, `cd`, or `touch`). Think of it as the "verb" which indicates what we want to do.

Next come the **Flags**. Think of these as "options" that tell the command how to do what it's about to do. There may be zero or more options.
* Sometimes you won't be using any options. Other times just one or maybe even more!
* Options usually start with one or two dashes. If the option is a letter, then one dash (e.g., `-a`). If it's a whole word, then two dashes (e.g., `--all`).

> [Here's a list](http://catb.org/esr/writings/taoup/html/ch10s05.html#id2948149) of some single-letter flags you might encounter. This is not an exhaustive list.

Finally come the **Arguments**. These are "targets", or what you want to do the action to. These could be file names, URLs, etc.

#### Common Patterns

The commands entered into the CLI are often in one of the following forms..

- `doSomething --how toFiles`
- `doSomething --how sourceFile destinationFile`

Where **doSomething** is, in effect, a verb, **how** an adverb (for example, should the command be executed "verbosely" or "quietly") and **toFiles** an object or objects (typically one or more files) on which the command should act.

> Not all commands follow this pattern, but many do.

Let's take a look at something we did for installfest.

```
$ brew install git
```

> When we type this command and hit enter , we're saying, "Computer, we're about to do something with homebrew. The thing were going to do is install something. What we want to install is git.


**Q:** Spend 2 minutes writing down the commands, flags and arguments for each of the below commands.
  1. `$ touch index.html`
  2. `$ ls -al`
  3. `$ cp index.html index2.html`
  4. `$ brew install git`

> Remember, not all of these have flags and/or arguments.

--------------------------------------------------------------------------------

## BREAK (10 minutes / 0:55)

--------------------------------------------------------------------------------

## Paths (30 minutes / 1:25)

### What is a Path?

A path is a description that tells us where a file or folder is located on our computer.

Our terminal is always working from a single path at a time. Commands that are run will take action in the current path (directory) unless we tell them to do otherwise.

Before we get too deep into paths. Let's review a couple of important commands that we'll be using frequently throughout this lesson.

* `pwd`:  outputs the current working directory ("print working directory").
* `cd`:  changes directories ("change directory").
* `ls`:  lists folders and files ("list").

### Relative vs. Absolute Paths

All paths point to a single file or folder. They can, however, be written in two different formats: **relative** or **absolute**.

#### Absolute Paths

An absolute path tells us exactly where the file or folder is located based on a root starting point. An example in the real world would be a (meticulous) mailing address for General Assembly...

```
Classroom 6
GA
8th Floor
1133 15th St NW
Washington, DC 20003
USA
Earth
Solar System
Milky Way
```

Absolute paths start with a `/` and go from the top down...

```bash
# General Assembly in path form...
/Milky_Way/Solar_System/Earth/USA/Washington_DC/1133_15th_St_NW/8th_Floor/GA

# ...but here's a more realistic example...
/Users/adrianmaseda/wdi/lessons/cli-intro
```

The first slash essentially means "start at the root of the computer's file system."

Some absolute paths instead start with a `~`. This is a shortcut to the absolute path of our home directory. So the above absolute path could also be written as

```bash
~/wdi/lessons/cli-intro
```

> On Macs, `~` corresponds to your user directory - `/users/your-mac-username`.

#### Relative Paths

Relative paths are interpreted as starting from the current working directory. They start with anything but a `/` or `~`.

So if we were in our home directory, the path to this lesson's directory could be written in the following ways...

```bash
wdi/lessons/cli-intro                                   # relative
~/wdi/lessons/cli-intro                                 # absolute
/Users/adrianmaseda/wdi/lessons/cli-intro               # absolute
```

If we were in a different folder, then the relative path would point to an entirely different folder/file.

Periods have special meaning when used in relative paths..
* `.`: one dot means "relative to the current directory"
* `..`: two dots means "go up to the parent directory"

So if we're in `~/wdi/lessons`, then the relative path `../projects` means "go up one level to the wdi folder, then down into my `projects` directory.

We can use more than one `..` to go up multiple levels. For example...

This time, if we're in `~/wdi/lessons/cli-intro`, entering `cd ../../projects` would go up two levels to `wdi`, and then down one level into `projects`.

**Q:** Spend two minutes writing out what the following commands are doing in English...
  1. `$ cd ./lessons`
  2. `$ ls ..`
  3. `$ mv ../index.html .`

### Compare Images in HTML

Turns out paths are really important in HTML too. If we look at the image tags in the `index.html` file in this repo we'll see this...

```html
<img src="../heeler.jpg">
<img src="firehydrant.jpg">
<img src="images/troll.png">
<img src="/Users/andrewkim/wdi/lessons/cli-intro/demo_html/images/troll.png">
```

Of these four paths, which are relative vs. absolute?

> We can see here that the `troll.png` photo is linked in two different ways. Which way is better? Does it matter?

## You do

https://github.com/ga-wdi-exercises/dc_directory_tree

--------------------------------------------------------------------------------

## Common Commands

### Getting Help (5 minutes / 1:30)

There are three general ways to get help with a command.

* Add `--help` or `-h` to the end of the command (e.g., `brew --help`).
* Use the manual -- or `man` -- tool (e.g., `man brew`).
* Google!

The first two options will display text using a program called `less`. Use the arrow keys to navigate. Type `q` to quit.

--------------------------------------------------------------------------------

## BREAK (10 minutes / 2:05)

--------------------------------------------------------------------------------

## Unsafe Commands (10 minutes / 2:15)

### `sudo`

`sudo` -- or "super user do" -- runs the command that follows as the super user (i.e., 'root' or 'admin'). That means your computer will not prevent you from running the command and may not even confirm if this is what you actually want to do. This is of particular concern when the command may have destructive effects.

> Generally, you shouldn't need to run commands with `sudo` in this course. If you're not sure, ask an instructor.

### `rm`

`rm` -- or "remove" -- deletes files with no confirmation. There is no `trash` to recover removed files
from.  So use `rm` with caution.

You should especially use `rm -rf` with caution.

> Based on your knowledge of flags, what does `rm -rf` do?

## WDI Environment (10 minutes / 2:25)

### Directory Structure

Here's the suggested structure for your WDI folder. Please create the following folders if they do not exist.

  * ~/wdi
    * sandbox
    * exercises
    * lessons
    * projects

---


## Ultimate Time Savers

The next three points are reasons not to hold down the arrow or delete keys.

### `ctrl-c`

Cancel whatever you were typing before. Abort!

### `ctrl-e`

Move cursor to the **e**nd of the line.

### `ctrl-a`

Move cursor to the beginning of the line

> a is the beginning of the English alphabet

### The up and down arrows

Cycle through previous commands

### Tab completion

When typing a command that has a file as an argument, like `cd`,
type only the first few letters and hit the TAB key.

### Clear the screen

- ctrl-l
- command-k
- `clear`

## You do: Speed Rounds

Copy and paste each of the following commands into the terminal without
pressing enter. 

### 1. Cancel the really long line of text

```
$ kjahlkjhsadlkjfhlaksjdhf asdjkfhlsadjhflkjashdf lasjkhdfjhasd sdjhfjhsgajhgf
```

### 2. Fix the typo at the beginning of the command

```
$ cdd ~/Documents && pwd && ls && ccd -
```

### 3. Fix the typo at the end of the command

```
Same as the previous command
```

## Own your terminal

1. [Color your prompt](http://www.cyberciti.biz/faq/bash-shell-change-the-color-of-my-shell-prompt-under-linux-or-unix/)
  - It will be WAY easier to read
2. [Choose a theme](http://apple.stackexchange.com/a/92769)
  - Pick something you like to look at

## [iTerm2](https://www.iterm2.com/features.html)

Most of the instructors use iTerm2 as a terminal replacement.

My favorite features include:

- A better, more readable font
- Hotkey support (full screen and tabs)
- Unlimited Scroll Back history

--------------------------------------------------------------------------------

## Bash Profile Aliases (If Time Allows)

You may have noticed during Installfest that the instructors messed with this file: `~/.bash_profile`.

<details>
  <summary>**Q:** Based on the path, where is this file located?</summary>
  In the home directory (i.e., Users/your-name-here).
</details>

Essentially, we changed the `~/.bash_profile` to make your prompt into a better one!

There will be commands you will find yourself doing frequently. It might become a pain to type out these commands in full all the time. It would be really nice if we could shorten some of these commands... enter aliasing. Aliasing is really quite simple!

Let's open our  `~/.bash_profile` in atom and type in the following...

```
alias greeting="echo 'hello world'"
alias gs='git status'
```

> At this point you may be wondering what exactly "bash" is. Bash is a language we can use to interact with our computer via the shell (via Terminal or some other text-based interface).

### You Do: Make An Alias

Take the next five minutes to create your own alias and test it. If possible, alias something you think you'll find yourself doing frequently!

--------------------------------------------------------------------------------

## Homework: To Oz

[To Oz](https://github.com/ga-wdi-exercises/to_oz)

#### Submission Instructions

1. Go to the assignment's [issues page](https://github.com/ga-wdi-exercises/to_oz/issues).
2. Click 'New Issue’.
3. Give it a title of `CLI HW (Your Name Here)`. Replace "Your Name Here" with your actual name.
4. For the description, copy paste the CLI commands you used to complete the assignment.

## Additional Practice

- [Command Line Fu](https://github.com/ga-wdi-exercises/command_line_fu)
- [Kitchen Organizer](https://github.com/ga-wdi-exercises/kitchen_organizer)

--------------------------------------------------------------------------------

## Sample Quiz Questions

* Why would a developer prefer the command line over a GUI?
* Where can we find help for shell commands?
* Describe 4 bash commands for managing folders and files.
* Describe 2 unsafe commands.
* You are currently in the "code" folder in the below file tree. How would you get to the folder that contains "beach.png" using the command line?

```
home
├── documents
│   └── code
├── photos
│   ├── headshot.jpg
│   └── summer_vacation_2014
│       └── beach.png
└── videos
```

* **BONUS:** Write a command to list only files beginning with your first name. Label the parts of the command.

## Hungry for More?

* `grep`
* `cat`
* `less`
* `find`
* `cal`
* `vim` and `vimtutor`

## Feeling Adventurous?

Bash isn't the only option. Check out zsh (http://code.joejag.com/2014/why-zsh.html) or fish (http://fishshell.com/)

## Glossary

*  **Prompt** — is a sequence of (one or more) characters used in a command-line interface to indicate readiness to accept commands. Its intent is to literally prompt the user to take action. A prompt usually ends with one of the characters `$`, `%`, `#`, `:`, `>` and often includes other information, such as the path of the current working directory.

*  **Arguments(Parameters)** — are items of information provided to a program or command when it is started. A program can have many command-line arguments that identify sources or destinations of information, or that alter the operation of the program.

*  **Flags(Options)** — modify the operation of a command; the effect is determined by the command's program. Options follow the command name on the command line, separated by spaces. 

*  **Path** - is the description that tells us (or a computer) where a file or folder is on our computer.
