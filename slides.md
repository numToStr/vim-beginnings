---
title: Vim Beginnings - Vikas Rajbanshi
favicon: https://upload.wikimedia.org/wikipedia/commons/9/9f/Vimlogo.svg
layout: center
fonts:
  sans: 'Fira Code'
  serif: 'Fira Code'
  mono: 'Fira Code'
---

<img style="width:400px" src="https://upload.wikimedia.org/wikipedia/commons/9/9f/Vimlogo.svg" alt="vim" />

---

# Introduction

### What?

- Vim is a modal text editor
- Fast, efficient and highly configurable
- Mouse is Dead, Long Live Keyboard
- Vi -> Vim -> Neovim

### Why?

- Vim is (almost) everywhere
- To be fast and more efficient
- If you hate your mouse
- Want to edit some text on a remote server
- Want to flex your vim magic
- And don't want your pc to be a heater

**Myself**: I am using Neovim for >3 years after trying and failing multiple times.

---

# Installation

You can find the installation instruction for your operating system from the following repositories:

- Vim - https://github.com/vim/vim

- Neovim - https://github.com/neovim/neovim

### Emulators

- VSCode - https://github.com/VSCodeVim/Vim

- IntelliJ - https://github.com/JetBrains/ideavim

- XCode - https://github.com/XVimProject/XVim2

---

# Modes

- NORMAL - For navigation and going to other modes (default)

- COMMAND - For running ex-commands | <kbd>:</kbd>

- INSERT - For typing text | <kbd>i</kbd> <kbd>I</kbd>

- VISUAL - For selecting text | <kbd>v</kbd> <kbd>V</kbd> <kbd>CTRL-v</kbd>

- REPLACE - For replacing text, not that useful | <kbd>r</kbd> <kbd>R</kbd>

<small>For more about modes</small>

```bash
:h index
:h inserting
:h visual-start
:h replacing
:h vim-modes
:h mode-switching
```

---

# Getting Help

Using and reading help doc

```bash
:h <anything_you_want>
```

_or_

```bash
:help <anything_you_want>
```

---

# Navigation

- Basic - <kbd>h</kbd> <kbd>j</kbd> <kbd>k</kbd> <kbd>l</kbd>

- Line - <kbd>w</kbd> <kbd>W</kbd> <kbd>b</kbd> <kbd>B</kbd> <kbd>f{char}</kbd> <kbd>F{char}</kbd> <kbd>0</kbd> <kbd>^</kbd> <kbd>$</kbd> and Press <kbd>;</kbd> (ahead) or <kbd>,</kbd> (back) if you want to repeat the last <kbd>f</kbd> motion

- Block - <kbd>%</kbd> <kbd>{</kbd> <kbd>}</kbd>

- Page - <kbd>gg</kbd> <kbd>G</kbd> <kbd>CTRL-U</kbd> <kbd>CTRL-D</kbd> <kbd>CTRL-F</kbd> <kbd>CTRL-B</kbd>

- Jump List - <kbd>CTRL-o</kbd> <kbd>CTRL-i</kbd>

<small>For more about navigation</small>

```bash
:h navigation
```

---

# Editing

- Inserting (write) - To write something, first enter the `INSERT` mode by pressing <kbd>i</kbd> <kbd>I</kbd> <kbd>a</kbd> <kbd>A</kbd> <kbd>s</kbd> <kbd>S</kbd> <kbd>o</kbd> <kbd>O</kbd>

- Deleting (cut) - Text can be deleted by pressing <kbd>dd</kbd> <kbd>D</kbd> <kbd>[count]d{motion}</kbd> <kbd>cc</kbd> <kbd>C</kbd> <kbd>[count]c{motion}</kbd> <kbd>cgn</kbd> <kbd>cgN</kbd> <kbd>x</kbd> <kbd>X</kbd> etc.

- Yanking (copy) - Text can be copied by pressing <kbd>yy</kbd> <kbd>Y</kbd> <kbd>[count]y{motion}</kbd>

- Putting (paste) - Text can be pasted by pressing <kbd>p</kbd> <kbd>P</kbd>

- Undo/Redo - <kbd>u</kbd> and <kbd>CTRL-R</kbd>

- Write/Exit - <kbd>:w</kbd> and <kbd>:q</kbd>

For more info

```bash
:h Insert-mode
:h deleting
:h copy-move
:h usr_{1,45}.txt
:h undo-commands
```

---

# Buffers & Windows

**Buffer** is a file loaded into memory for editing. Think of it as a tab.

**Window** is a viewport onto a buffer. You can use multiple windows on one
buffer, or several windows on different buffers. Think of this is as splits.

### Navigating buffers/windows

- `:bnext` - Go to next buffer

- `:bprev` - Go to previous buffer

- `:b {bufname}` - Go to a specific buffer

- <kbd>CTRL-w {h,j,k,l}</kbd> - Go to left/down/up/right window

<small>For more about buffers/windows</small>

```bash
:h windows
```

---

# Registers

Registers are spaces in memory that Vim uses to store some text or operation details. Each of these spaces has an identifier so that it can be accessed later. Most of the time you won't be interacting with the registers directly but it is important to know about it.

#### Types

- Unnamed - Used by Vim for storing the recent yanked text.
- Named - For us to use it

**Using** - Press <kbd>"{char}{command}</kbd>

- <kbd>"ayy</kbd> - Copy current line and put it in `a` register
- <kbd>"zdd</kbd> - Delete current line and put it in `z` register
- <kbd>"zp</kbd> - Paste whatever is in `z` register

For more about registers

```bash
:h registers
```

---

# Transforming & Substituting

- Dot Repeat - Press <kbd>.</kbd> to repeat the last text change

- Search/Find - <kbd>/</kbd> <kbd>?</kbd> <kbd>\*</kbd> <kbd>#</kbd> and <small>Press <kbd>n</kbd> or <kbd>N</kbd> to find the next pattern</small>

- Replace - <kbd>s/{pattern}/{substitute}/[g]</kbd> <kbd>%s/{pattern}/{substitute}/[g]</kbd>

- Change Case - <kbd>~</kbd> <kbd>g~{motion}</kbd> <kbd>gu{motion}</kbd> <kbd>gU{motion}</kbd>

#### Global Command

```bash
:[range]g[lobal]/{pattern}/[cmd]

:[range]g![lobal]/{pattern}/[cmd]
:[range]v[global]/{pattern}/[cmd]
```

<small>For more info</small>

```bash
:h case
:h search-commands
:h :global
```

---

# Text Objects

Text object is a vim way of transcending beyond the individual character to allow the user to think in words, sentences, blocks, paragraphs, etc. It includes constructs for plain text or any programming language. And, It can be paired with any other motion.

#### Examples

- <kbd>ciw</kbd> - Delete the current word and go to insert mode
- <kbd>viw</kbd> <kbd>diw</kbd> <kbd>yiw</kbd> - Select/Delete/Yank the current word under the cursor
- <kbd>di'</kbd> <kbd>di"</kbd> - Delete text inside single or double quotes
- <kbd>di(</kbd> <kbd>di{`{`}</kbd> - Delete text inside normal or curly brackets
- <kbd>yi'</kbd> <kbd>yi"</kbd> - Yank text inside single or double quotes
- <kbd>ya(</kbd> <kbd>ya{`{`}</kbd> - Yank text around normal or curly brackets

<small>For more about text objects</small>

```bash
:h text-objects
:h objects
```

---

# Macros

Macros are kind of a record and replay mechanism but for text. You can record a sequence of simple or complex commands which can be executed at later point of time in the same or different file.

#### Record

- To start recording the macro press <kbd>q{register}</kbd>. Here `register` should be a alphanumeric character.
- To stop recording the macro press <kbd>q</kbd> again.

#### Play

Press <kbd>@{register}</kbd> to play the macro stored at that particular `register`

**Example**: <kbd>qa</kbd> (Recording at `a`) and <kbd>@a</kbd> (Play macro at `a`)

<p><small>For more about macros</small></p>

```bash
:h complex-repeat
```

---

# Bonus

- Configuration
- Plugins
- LSP