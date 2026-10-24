<div align="center">

#The tools behind my 42 projects: what I use, and why.

![OS](https://img.shields.io/badge/OS-WSL%20%2B%2042%20Linux-0078D6?style=flat-square)
![Shell](https://img.shields.io/badge/Shell-fish-4AAE46?style=flat-square)
![Editor](https://img.shields.io/badge/Editor-VS%20Code-007ACC?style=flat-square)
![Lang](https://img.shields.io/badge/C%20%2F%20C%2B%2B-17-00599C?style=flat-square)

</div>

This is a showcase, not an installer. It describes how my environment is built so you can
take ideas from it. The actual dotfiles are kept private.

<!-- Screenshot: put a picture of terminal + editor at assets/setup.png and uncomment -->
<!-- ![My setup](assets/setup.png) -->

---

## Machines

| Where | What runs there |
|---|---|
| 42 school PCs | Linux without root: everything lives in `$HOME` |
| Home | Windows with [WSL](https://learn.microsoft.com/windows/wsl/), same shell and configs as at school |

---

## Top 5

| Tool | Why it matters |
|---|---|
| [fish](https://fishshell.com) | Autosuggestions and syntax highlighting out of the box, no plugin setup |
| [zoxide](https://github.com/ajeetdsouza/zoxide) | Jump to any project by a fragment of its name instead of typing paths |
| [chezmoi](https://www.chezmoi.io) | One dotfile repo for the school PCs and WSL, so a fresh login looks the same everywhere. Editing a config opens it in VS Code; closing the tab applies, commits and pushes it |
| `-fsanitize` ([ASan](https://clang.llvm.org/docs/AddressSanitizer.html), [UBSan](https://clang.llvm.org/docs/UndefinedBehaviorSanitizer.html), [TSan](https://clang.llvm.org/docs/ThreadSanitizer.html)) | Catch out-of-bounds access, use-after-free, undefined behaviour and data races exactly where they happen |
| [clangd](https://clangd.llvm.org) | Errors and completion as I type. Adds `-Wall -Wextra -Werror -std=c++17` and the usual include folders to every project, so it works without a `compile_commands.json` |

---

## More tools I use at 42

| Tool | Why |
|---|---|
| [norminette](https://github.com/42School/norminette) | The official Norm checker, run in watch mode while coding so style errors never pile up |
| [42_minishell_tester](https://github.com/zstenger93/42_minishell_tester) | Hundreds of shell cases compared against bash |
| [valgrind](https://valgrind.org) | Finds leaks and invalid reads without recompiling |
| [lldb](https://lldb.llvm.org) | Stepping through code when printf isn't enough |
| [make](https://www.gnu.org/software/make/manual/make.html) | Every project is built with a Makefile, so make targets are what I type most |
| [VS Code](https://code.visualstudio.com) | Main editor, also set as git's editor, diff tool and merge tool |
| [lazydocker](https://github.com/jesseduffield/lazydocker) | Containers, logs and volumes in one terminal view while building Inception |
| [clang-tidy](https://clang.llvm.org/extra/clang-tidy/) | `bugprone-*` and `performance-*` checks, shown inline through clangd |
| [clang-format](https://clang.llvm.org/docs/ClangFormat.html) | My own style with no preset: tabs, Allman braces, 80 columns, for the C++ modules |
| [fzf](https://github.com/junegunn/fzf) | Fuzzy picker for history, files and zoxide matches |
| [ripgrep](https://github.com/BurntSushi/ripgrep) / [fd](https://github.com/sharkdp/fd) | Fast search through code and files |
| [gh](https://cli.github.com) | GitHub from the terminal |

On top of that I keep a few small custom helper scripts for repetitive 42 tasks.

---

## VS Code extensions

Sorted by how much they help me day to day.

| Extension | Why |
|---|---|
| [clangd](https://marketplace.visualstudio.com/items?itemName=llvm-vs-code-extensions.vscode-clangd) | Brings clangd into the editor: errors, completion, go-to-definition |
| [42 Header (Long)](https://marketplace.visualstudio.com/items?itemName=secondfry.42header-long) | Inserts and updates the 42 file header that the Norm requires |
| [Claude Code](https://marketplace.visualstudio.com/items?itemName=anthropic.claude-code) | AI pair programmer right next to the code |
| [Toggle Semicolon](https://marketplace.visualstudio.com/items?itemName=awesomektvn.toggle-semicolon) | Adds or removes the semicolon at the end of the line with one shortcut, without moving the cursor |
| [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) | Catches typos in names, comments and READMEs |
| [vscode-pdf](https://marketplace.visualstudio.com/items?itemName=tomoki1207.pdf) | Opens the subject PDF in a tab beside the code |
| [Material Icon Theme](https://marketplace.visualstudio.com/items?itemName=PKief.material-icon-theme) | File icons that make large project trees easier to scan |

---

## Aliases

One file of plain `alias` lines, shared by fish, bash and zsh. Five examples:

```bash
alias gst='git status'                # what changed?
alias m='make'                        # build
alias q='exit'                        # close the shell
alias ccw='cc -Wall -Wextra -Werror'  # compile with the 42 grading flags
alias la='ls -Al'                     # list everything, hidden files included
```

---

## About this repo

This README was written with [Claude](https://claude.ai), and I reviewed all of it myself.
It is mostly a public summary of my private chezmoi config.

If you want to know more, get in touch through my [GitHub profile](https://github.com/RoboFB).
I'm more than happy to help you set something up or explain how a part of it works.
