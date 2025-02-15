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

The rc file gets run when a terminal starts up and makes available any commands that are defined (technically it's called by other files that run automatically). This can be useful for setting environment variables or common functions.

Aliases are typically for commands which don't have arguments, but they don't have to be. Consider adding aliases for common tasks to simplify them. The spacing in files is syntactically important so keep that in mind. Commands can include operators like `-z` which checks if the length of a string is zero and `-gt` which is the greater than comparison operator. These can be used in what are known as test commands.

Resources
 
- [Bash Reference Manual](https://www.gnu.org/software/bash/manual/bash.html)
- [RC Config files](https://medium.com/@aadishazzam/rc-files-403a2b7c80a9)
- [What is .bashrc file in Linux?](https://www.digitalocean.com/community/tutorials/bashrc-file-in-linux)
- [Bashrc: How To Use It To Improve Your Linux Experience](https://www.namehero.com/blog/bashrc-how-to-use-it-to-improve-your-linux-experience/)
- [How to use Bash file test operators in Linux](https://www.howtoforge.com/bash-if-e-and-s-and-other-file-test-operators-in-linux)
- [Advanced Bash-Scripting Guide: Chapter 7. Tests](https://tldp.org/LDP/abs/html/tests.html)
- [Oh My Zsh](https://ohmyz.sh/)
- [Z shell](https://en.wikipedia.org/wiki/Z_shell)
