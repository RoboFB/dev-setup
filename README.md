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
| Home | Windows with [WSL](https://learn.microsoft.com/windows/wsl/), same shell and configs as at school |

One dotfile repo serves both, so a fresh login looks the same everywhere.

---

## The tools that helped most at 42

| Tool | Why it matters |
|---|---|
| [norminette](https://github.com/42School/norminette) | The official Norm checker. I run it in watch mode while coding, so style errors never pile up |
| [francinette](https://github.com/xicodomingues/francinette) | Tests libft, get_next_line, ft_printf and more before an evaluation |
| [mini-moulinette](https://github.com/k11q/mini-moulinette) | Quick checks for the Piscine-style C exercises |
| [42_minishell_tester](https://github.com/zstenger93/42_minishell_tester) | Hundreds of shell cases compared against bash |
| [valgrind](https://valgrind.org) | Finds leaks and invalid reads without recompiling |
| [AddressSanitizer](https://clang.llvm.org/docs/AddressSanitizer.html) + [UBSan](https://clang.llvm.org/docs/UndefinedBehaviorSanitizer.html) | Catch out-of-bounds access, use-after-free and undefined behaviour exactly where they happen |
| [ThreadSanitizer](https://clang.llvm.org/docs/ThreadSanitizer.html) | Data races in philosophers and other threaded projects |
| [gdb](https://www.sourceware.org/gdb/) | Stepping through code when printf isn't enough |
| [make](https://www.gnu.org/software/make/) | Every project is built with a Makefile, so make targets are what I type most |
| [VS Code](https://code.visualstudio.com) + [clangd](https://clangd.llvm.org) | Errors and completion as I type. clangd adds `-Wall -Wextra -Werror -std=c++17` and the usual include folders to every project, so it works without a `compile_commands.json` |
| [tmux](https://github.com/tmux/tmux) | One session per project: editor, build and tests side by side, and the session survives a closed terminal |
| [zoxide](https://github.com/ajeetdsouza/zoxide) | Jump to any project by a fragment of its name instead of typing paths |
| [lazygit](https://github.com/jesseduffield/lazygit) | Staging hunks and reviewing the diff before every push |

---

## The rest of the stack

| Tool | Why |
|---|---|
| [fish](https://fishshell.com) | Autosuggestions and syntax highlighting out of the box, no plugin setup |
| [fzf](https://github.com/junegunn/fzf) | Fuzzy picker for history, files and zoxide matches |
| [ripgrep](https://github.com/BurntSushi/ripgrep) / [fd](https://github.com/sharkdp/fd) | Fast search through code and files |
| [clang-tidy](https://clang.llvm.org/extra/clang-tidy/) | `bugprone-*` and `performance-*` checks, shown inline through clangd |
| [clang-format](https://clang.llvm.org/docs/ClangFormat.html) | My own style with no preset: tabs, Allman braces, 80 columns, for the C++ modules |
| [Docker Compose](https://docs.docker.com/compose/) | Containers for the projects that need them |
| [gh](https://cli.github.com) | GitHub from the terminal |
| [chezmoi](https://www.chezmoi.io) | Manages the dotfiles. Editing a config opens it in VS Code; closing the tab applies, commits and pushes it |

---

## My own helper scripts

| Helper | What it does |
|---|---|
| **norminette wrapper** | Groups Norm errors by file with colors and aligned line:column, readable at a glance |
| **forbidden-functions check** | Lists every external symbol a binary uses that is not on the subject's allowed list |
| **Makefile source list** | Prints all `src/**/*.c` files formatted for a Makefile `SRC` variable |
| **Header prototypes** | Collects all non-static function prototypes and regenerates the bottom of the project header |
| **Sanitizer rerun** | Rebuilds with TSan and runs, then rebuilds with ASan + UBSan and runs again |
| **Pull then push** | `git pull --rebase`, then pushes only if there is something to push |
| **Session start / end** | Opens the 42 intranet, VS Code and my tmux layout; at the end cleans up and logs out |
| **Selection hotkeys** | Select text anywhere → search it on Google or in the 42 intranet, or copy it as a command |
| **Open in VS Code** | Picks a project with zoxide and opens it in a new or reused VS Code window |
| **Search helpers** | Search my aliases or my shell history by keyword |

---

## Aliases

One file of plain `alias` lines, shared by fish, bash and zsh.

| Alias | What it does |
|---|---|
| `c` / `q` | clear / exit |
| `la` / `ll` / `ld` | ls with hidden files / long list / sorted by change time |
| `aptuu` / `aptse` | update + upgrade / search packages |
| `ccw` / `c++w` | compile with `-Wall -Wextra -Werror`, the 42 grading flags |
| `m` / `mre` / `mb` / `md` / `mrun` | make / re / bonus / debug / run |
| `norm-watch` | norminette re-run live on every change |
| `mini` / `francinette` / `paco` / `mstest` | start a tester |
| `gst` / `gss` / `gdiff` | git status / short status / compact diff summary |
| `ga` / `ga.` | git add / add everything |
| `gc` / `gcm` / `gcam` | commit / commit with message / commit all with message |
| `gp` / `gcp` / `gcap` | push / commit + push / commit all + push |
| `gpull` / `gclone` | pull / clone |
| `glog` / `glogs` | log / one-line log |
| `gbaum` / `gbaums` | colored graph log with relative dates, with and without file stats |
| `gls` | list tracked files |
| `vsc` / `vscn` / `vscr` | VS Code / new window / reuse window |
| `ta` | attach to the last tmux session |
| `dps` / `dpsa` / `dexe` / `dlogs` | docker ps / all / exec -it / logs |
| `dc` / `dcup` / `dcdown` | docker compose / up -d / down |
| `drm` / `dri` / `dspa` | prune containers / images / everything |
| `chez` / `chez-e` / `chez-cd` / `chez-code` | chezmoi / edit a config / go to source / open source in VS Code |
| `copy` / `past` | copy to / paste from the clipboard |
| `bash-clean` | bash with no config and an empty environment, for testing minishell against it |

---

<sub>Set up with help from <a href="https://claude.ai">Claude</a>. The tools and choices are my own.</sub>
