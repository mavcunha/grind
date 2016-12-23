# Grind

`grind` is a tool to help you configure and maintain your machine. I wrote a
[blog post](http://marcovaltas/com/2016/12/21/introducing-grind.html)
explaining why I created `grind`.

## How to use it (short)

1. [Download](https://github.com/mavcunha/grind/releases) or clone grind.
2. Check the `definitions` directory and write your own definition.
3. run `./grind update run`

## How to use it (long)

### Bootstrap

`grind` provides a `bootstrap` command for a pre-setup for grind itself:

```bash
grind bootstrap run
```

This is a special definition and it should set and install the requirements
from `grind` itself. On macOS it means installing [XCode CLI
Tools](https://developer.apple.com/xcode/features/) and
[Homebrew](http://brew.sh/).

### Update

`grind update run` is the daily command from `grind`, it will execute and run all
definitions for current machine.

### Definitions

All `grind` does is execute some functions in series defined in the `definitions` directory.
Here's an example of a definition on macOS:

### A simple definition

This definition will install `git` through *homebrew* if is not already installed.

```bash
use "brew"

brew_pkg "git"
```

### A more complex definition

This definition will install `vim` thorugh *homebrew* if is not already installed, and
configure some plugins and settings for `vim`.

```bash
use "brew"

brew_pkg "vim"

do_run "mkdir -p ${HOME}/.vim/bundle"
  unless_dir "${HOME}/.vim/bundle"

function install_bundles() {
  local bundles=("${!1}")
  for b in ${bundles[@]}; do
    local repo=${b}
    local target=${b#*/}

    do_run "git clone https://github.com/${repo}.git ${HOME}/.vim/bundle/${target}"
      unless_dir "${HOME}/.vim/bundle/${target}"
  done
}

vim_bundles=(
  'tpope/vim-pathogen'
  'tpope/vim-surround'
  'tpope/vim-unimpaired'
  'vim-ruby/vim-ruby')

install_bundles vim_bundles[@]
```

### Definitions directory organization

First `grind` will load and execute whatever is in the `global` directory,
these are assumed to be definitions to be applied to any machine.

After that `grind` will load scripts from the `machines` directory, where it will try
to find a subdirectory with the machine name and from there load the scripts. These
definitions are specific for each machine you want to maintain.

## Documentation

[Click here for more information.](https://github.com/mavcunha/grind/wiki)
