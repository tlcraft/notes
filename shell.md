# Shell Notes

`bash` is one version of a shell program. Shells sit at the outer layer of the operating system and allow users to interact with the OS directly.

Here are several important configuration files:

- `.bashrc` – typically for functions and aliases (interactive, non-login)
- `.bash_profile` – typically for environment variables (login)
- `.bash_login` – used if a profile file doesn’t exist (login)
- `.profile` – environment setup common to all users (login)

Here are notes on the configuration types from above:

- Login – shell that’s run upon start to load env vars and settings
- Non-login – shells invoked without logging into anything
- Interactive – scripts that include some input and/or output
- Non-interactive – init or startup files (no human interaction)

The rc file gets run when a terminal starts up and makes available any commands that are defined. This can be useful for setting environment variables or common functions.

Aliases are typically for commands which don't have arguments, but they don't have to be. Consider adding aliases for common tasks to simplify them. The spacing in files is syntactically important so keep that in mind.
