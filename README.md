<div align="center">

# dev-setup

**The tools behind my 42 projects: what I use, and why.**

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
| Home | Windows with WSL, same shell and configs as at school |

One dotfile repo serves both, so a fresh login looks the same everywhere.

---

## Terminal

| Tool | Why |
|---|---|
| **fish** | Autosuggestions and syntax highlighting out of the box, no plugin setup |
| **tmux** | One session per project; prefix moved to `C-a`, splits on `\|` and `-`, `C-h/j/k/l` to move between panes |
| **zoxide** | Jump to any project by a fragment of its name instead of typing paths |
| **fzf** | Fuzzy picker for history, files and zoxide matches |
| **ripgrep / fd** | Fast search through code and files |
| **lazygit** | Staging hunks and reviewing a diff before committing |
| **gh** | GitHub from the terminal |

The aliases are plain POSIX `alias` lines, so one file works in fish, bash and zsh.

---

## Editor

| Tool | Why |
|---|---|
| **VS Code** | Main editor, also set as git's editor, diff tool and merge tool |
| **clangd** | Code completion and errors as I type. Adds `-Wall -Wextra -Werror -std=c++17` and the usual include folders to every project, so it works without a `compile_commands.json` |
| **clang-tidy** | `bugprone-*` and `performance-*` checks, shown inline through clangd |
| **clang-format** | My own style with no preset: tabs, Allman braces, 80 columns, close to the 42 Norm for C++ modules |

Small helpers open a zoxide match straight in VS Code, in a new or reused window.

---

## C / C++ quality

| Tool | Why |
|---|---|
| `cc -Wall -Wextra -Werror` | Same flags as the 42 grading, as a short alias (`ccw`, `c++w`) |
| **AddressSanitizer / UBSan** | Finds out-of-bounds access, use-after-free and undefined behaviour at runtime |
| **ThreadSanitizer** | Data races in threaded projects such as philosophers |
| **valgrind** | Leak checks and memory errors without recompiling |
| **gdb** | Stepping through code when printf isn't enough |

For threaded projects, one script rebuilds with TSan, runs, then rebuilds with ASan + UBSan and runs again.

---

## 42 tooling

| Tool | What it does |
|---|---|
| **norminette wrapper** | Groups Norm errors by file with colors and aligned line:column, so the output is readable at a glance |
| **forbidden-functions check** | Lists every external symbol a binary uses that is not on the subject's allowed list |
| **Makefile source list** | Prints all `src/**/*.c` files formatted for a Makefile `SRC` variable |
| **Header prototypes** | Collects all non-static function prototypes and regenerates the bottom of the project header |
| **Testers** | francinette, mini-moulinette and a minishell tester, each behind a short alias |
| **make aliases** | `m`, `mre`, `mb`, `md`, `mrun` for make, re, bonus, debug and run |

---

## Workflow

| Piece | How |
|---|---|
| **Dotfiles** | Managed with [chezmoi](https://www.chezmoi.io). Editing a config opens it in VS Code; closing the tab applies, commits and pushes it automatically |
| **git aliases** | `gst`, `gss`, `gdiff`, `gcm`, `gcap`, plus `gbaum` for a colored graph log with relative dates |
| **Pull then push** | One command does `git pull --rebase` and pushes only if there is something to push |
| **Docker** | Short aliases for `ps`, `exec`, `logs`, prune and `compose up/down` |
| **Session start** | One script opens the 42 intranet, VS Code and a tmux session with my pane layout |
| **Session end** | One script cleans up and logs out of the school PC |
| **Hotkeys** | Select text anywhere → search it on Google or in the 42 intranet, or copy it as a command to run |
| **Finding things** | `ag` searches my aliases, `hg` searches shell history |

---

<sub>Set up with help from <a href="https://claude.ai">Claude</a>. The tools and choices are my own.</sub>
