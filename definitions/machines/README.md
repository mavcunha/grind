## Definitions specific to machines

This directory is definitions that will execute only for a specific machines.
Let's say that one of your machines is called 'bigblue', first create a
directory called 'bigblue':

```
# hostname -s returns the short machine name (without domain)
mkdir $(hostname -s)
```

Then add any definition for this machine inside this directory new directory.
`grind` will execute first the *global* definitions and after that will execute
definitions for the machine.
