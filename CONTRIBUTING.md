# Contributing with grind

First off, thanks for considering helping.

`grind` is a quite simple software in theory you should be able to understand
the code and *create a pull request with your change*. And that's the preferred
way of contributing.

## Things to keep in mind when contributing

* Be mindful of everyone's machine
* Use admin privileges with utmost care
* Keep it simple but idiomatic

## Be mindful of everyone's machine

`grind` is mostly a configuration tool, it helps to set up your machine without
having to remember all the steps or software you usually need. This is very
personal, each user will have different sets of configurations and
applications.

So keep `grind` unopinionated as most as you can, do not force conventions that
are not already conventions from the OS or other tools you interact with.

### Use admin privileges with utmost care

It is possible to call for admin privileges through `grind` functions. But for
each instance that this is needed it is important that the user is informed and
consent to the admin use.

Never require to run `grind` as root. Never ask for admin privileges without
informing the user what you're trying to do. Never do more with admin
privileges than what you asked for, if you need to do two unrelated things just
ask for admin again.

### Keep it simple but idiomatic

Regarding the code itself, keep it simple. Do not write long functions or over
complicated code. 

With this said, `grind` is a zsh script and shell scripting has it's common
idioms. Like ternary such as `[[ test ]] && if_pass || if_fails` and that's
Okay.
