# Commands

Notes on various CLI commands.

## Contents

- [cd](#cd)
- [cat](#cat)
- [df](#df)
- [dig](#dig)
- [grep](#grep)
- [ifconfig](#ifconfig)
- [ipconfig](#ipconfig)
- [ls](#ls)
- [Multiline Commands](#multiline-commands)
- [ping](#ping)
- [sed](#sed)
- [tree](#tree)

### cd

`cd` lets us change between directories. You can use a dash to jump back to your last directoy, like `cd -`.

### cat

The `cat` command can print the contents of a file to standard output. It can do other things like concatenating file contents together as well.

This example will print the contents of `filename` to the terminal.

```bash
cat filename
```

- [cat (Unix)](https://en.wikipedia.org/wiki/Cat_(Unix))

### df

The `df` command displays information about the total space on a file system. The `-h` flag will print out the size of each disk in a human-readable format. `-k` will display the blocks in kilobytes.

- [df Command](https://www.ibm.com/docs/en/aix/7.3?topic=d-df-command)
- [df (Unix)](https://en.wikipedia.org/wiki/Df_(Unix))

### dig

The `dig` command queries domain name system (DNS) servers. It's useful for troubleshooting DNS problems. 

The `+trace` flag will run iterative queries to list the DNS lookup path. Such as `dig google.com +trace`.

The `+x` flag will run a reverse DNS lookup. Like `dig +noall +answer -x 8.8.8.8`.

- [dig command](https://www.ibm.com/docs/en/aix/7.3?topic=d-dig-command)
- [Linux and Unix dig Command Examples](https://www.cyberciti.biz/faq/linux-unix-dig-command-examples-usage-syntax/)
- [dig Command in Linux with Examples](https://www.geeksforgeeks.org/dig-command-in-linux-with-examples/)

### grep

`grep` can be used to find instances of a given pattern within a file. It will print each line that includes a match. Note from the documentation, "since newline is also a separator for the list of patterns, there is no way to match newline characters in a text."

- [grep](https://www.gnu.org/software/grep/manual/grep.html)
- [Finding text strings within files (grep command)](https://www.ibm.com/docs/en/aix/7.3?topic=files-finding-text-strings-within-grep-command)

### ifconfig

`ifconfig` can be run on Unix-like systems, such as macOS, to configure or query network interface parameters.

- [ifconfig](https://en.wikipedia.org/wiki/Ifconfig)

### ipconfig

From Microsoft's documentation, `ipconfig` in Windows "displays all current TCP/IP network configuration values and refreshes Dynamic Host Configuration Protocol (DHCP) and Domain Name System (DNS) settings. Used without parameters, `ipconfig` displays Internet Protocol version 4 (IPv4) and IPv6 addresses, subnet mask, and default gateway for all adapters."

- [ipconfig](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ipconfig)

### ls

The `ls` command lists the contents of a directory. Using the `-a` flag will include hidden files (like `ls -a`). The `-l` flag will display additional information about the files (such as ownership and last modified date).
 
- [ls](https://en.wikipedia.org/wiki/Ls)

### Multiline Commands

Terminals can be configured to handle multiline commands. Typically adding a backslash at the end of a line will allow the terminal to process these. In some cases you may need to use a caret, backtick or pipe.

Simple `echo` example:
```shell
echo "This spans \
multiple lines \
testing, 123"
```

### ping

The `ping` command tests if a device on a network is reachable.

- [Ping command basics for testing and troubleshooting](https://www.redhat.com/en/blog/ping-usage-basics)

### sed

The `sed` command can help you manipulate text from files. For example, it can be useful to use if you need to replace some text per a configuration or environment.

From the documentation below, here's an example which replaces instances of `hello` with `world` in the `input.txt` file and outputs the changes to `output.txt`.

```shell
sed 's/hello/world/' input.txt > output.txt
```

- [sed, a stream editor](https://www.gnu.org/software/sed/manual/sed.html)

### tree

The `tree` command prints the directory structure from the folder where you run the command.

- [tree (command)](https://en.wikipedia.org/wiki/Tree_(command))
