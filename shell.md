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

### Multiline Commands

Terminals can be configured to handle multiline commands. Typically adding a backslash at the end of a line will allow the terminal to process these. In some cases you may need to use a caret, backtick or pipe.

Simple `echo` example:
```shell
echo "This spans \
multiple lines \
testing, 123"
```

### Output Notes

In Linux/Unix command-line shell scripting, 2>&1 is an idiom used to redirect standard error (stderr) to standard output (stdout). It allows you to combine error messages and normal output into a single stream, which can then be displayed together or saved to a file.

### vi

`vi` is a powerful text editor you can use from the terminal. You can perform commands on a file or edit a file's contents. Here are some helpful commands.

- `vi` - opens a file
- `i` - starts insert mode
- `esc` - exits insert mode
- `:wq` - saves your changes while in insert mode and exits `vi`

Here are some examples of the commands which would create a new file named `vi.test`, open it, start insert mode, enter the text "Hello world", exit insert mode and then save the changes and exit `vi`. Finally it prints the contents of your new file using `cat` to confirm the changes were made:

```shell
touch vi.test # create a file named vi.test
vi vi.test # open the vi.test file with vi
i # enter insert mode
Hello world # type the text Hello world
esc # exit insert mode
:wq # save the changes and quit vi
cat vi.test # print the contents of vi.test to confirm the changes
```

- [Basic vi Commands](https://www.cs.colostate.edu/helpdocs/vi.html)

## Resources
 
- [Bash Reference Manual](https://www.gnu.org/software/bash/manual/bash.html)
- [RC Config files](https://medium.com/@aadishazzam/rc-files-403a2b7c80a9)
- [What is .bashrc file in Linux?](https://www.digitalocean.com/community/tutorials/bashrc-file-in-linux)
- [Bashrc: How To Use It To Improve Your Linux Experience](https://www.namehero.com/blog/bashrc-how-to-use-it-to-improve-your-linux-experience/)
- [How to use Bash file test operators in Linux](https://www.howtoforge.com/bash-if-e-and-s-and-other-file-test-operators-in-linux)
- [Advanced Bash-Scripting Guide: Chapter 7. Tests](https://tldp.org/LDP/abs/html/tests.html)
- [Oh My Zsh](https://ohmyz.sh/)
- [Z shell](https://en.wikipedia.org/wiki/Z_shell)
