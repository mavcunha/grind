# Grind

`grind` is a set of bash scripts to configure macOS machines. It provides an
easier API for configuration tasks.

## How to use it (short)

1. Download or clone grind.
2. Check the `definitions` directory and write your own definition.
3. run `./grind update run`

## How to use it (long)

### Bootstrap

`grind` provides a `bootstrap` command for a pre-setup for grind itself:

```bash
grind bootstrap run
```

This is a special definition and it should set and install what we understand
as dependencies for the other definitions, like 'homebrew' which itself depends
on 'XCode CLI Tools', so the bootstrap will install 'XCode CLI Tools' followed
by 'homebrew'.

### Update

`grind update run` is the daily command from `grind`, it will execute and run all
definitions for current machine.

### Definitions

All `grind` does is execute some functions in series defined in the `definitions` directory.
Here's an example of a definition:

```bash
do_run "brew install httpie"
  unless_file "/usr/local/bin/http"

do_run "brew install jq"
  unless_file "/usr/local/bin/jq"

do_run "brew install leiningen"
  unless_file "/usr/local/bin/lein"
```

See [Grind Definition API](https://github.com/mavcunha/grind/wiki/Grind-Definition-API)

### Definitions directory organization

First `grind` will load and execute whatever is in the `global` directory,
these are assumed to be definitions to be applied to any machine.

After that `grind` will load scripts from the `machines` directory, where it will try
to find a subdirectory with the machine name and from there load the scripts. These
definitions are specific for each machine you want to maintain.

## Documentation

[Click here for more information.](https://github.com/mavcunha/grind/wiki)
