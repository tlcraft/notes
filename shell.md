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
