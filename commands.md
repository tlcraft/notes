# Commands

Notes on various CLI commands.

## Contents

- [awk](#awk)
- [cd](#cd)
- [cat](#cat)
- [df](#df)
- [dig](#dig)
- [find](#find)
- [grep](#grep)
- [head](#head)
- [ifconfig](#ifconfig)
- [ipconfig](#ipconfig)
- [jq](#jq)
- [ls](#ls)
- [mkdir](#mkdir)
- [nl](#nl)
- [ping](#ping)
- [realpath](#realpath)
- [rm](#rm)
- [sed](#sed)
- [touch](#touch)
- [tree](#tree)
- [uname](#uname)
- [which](#which)

### awk

The `awk` command can be used for pattern matching and text processing. It's named after the creators (Alfred **A**ho, Peter **W**einberger, and Brian **K**ernighan).

The following example prints each line that includes the characters `###` in this file. It also incldues the line number for each one.

```shell
awk '/###/ {print NR,$0}' commands.md
```

You can set a field separator and then reference the fields using the pattern `$1`, `$2`, `$3` and so on. `$0` represent the entire line and `$NF` represents the last field.

This script sets the field separator to a space and prints the first and last fields of each line along with the line number.

```shell
awk -F' ' '{print NR, $1, $NF}' commands.md
```

This script prints out the length of the longest line of this file (as well as the line itself).

```shell
awk '{ if (length($0) > max) max = length($0); line = $0 } END { print max, line }' commands.md
```

You can also create `.awk` files with saved patterns and actions and reference them with the `-f` flag. 

- [AWK command in Linux](https://www.geeksforgeeks.org/linux-unix/awk-command-unixlinux-examples/)
- [AWK](https://en.wikipedia.org/wiki/AWK)

### cd

`cd` lets us change between directories. You can use a dash to jump back to your last directoy, like `cd -`.

### cat

The `cat` command can print the contents of a file to standard output. It can do other things like concatenating file contents together as well.

This example will print the contents of `filename` to the terminal.

```shell
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

### find

The `find` command searches for files or directories based on a set of criteria. The following command will search for all files within the given directory.

```shell
find /path -type f
```

- [Find Command in Linux](https://www.geeksforgeeks.org/linux-unix/find-command-in-linux-with-examples/)

### grep

`grep` can be used to find instances of a given pattern within a file. It will print each line that includes a match. Note from the documentation, "since newline is also a separator for the list of patterns, there is no way to match newline characters in a text."

- [grep](https://www.gnu.org/software/grep/manual/grep.html)
- [Finding text strings within files (grep command)](https://www.ibm.com/docs/en/aix/7.3?topic=files-finding-text-strings-within-grep-command)

### head

The `head` command can be used to print out a number of lines from a file. By default it prints the first 10 lines. You can also print data based on bytes.

- [Head Command in Linux With Examples](https://www.geeksforgeeks.org/linux-unix/head-command-linux-examples/)

### ifconfig

`ifconfig` can be run on Unix-like systems, such as macOS, to configure or query network interface parameters.

- [ifconfig](https://en.wikipedia.org/wiki/Ifconfig)

### ipconfig

From Microsoft's documentation, `ipconfig` in Windows "displays all current TCP/IP network configuration values and refreshes Dynamic Host Configuration Protocol (DHCP) and Domain Name System (DNS) settings. Used without parameters, `ipconfig` displays Internet Protocol version 4 (IPv4) and IPv6 addresses, subnet mask, and default gateway for all adapters."

- [ipconfig](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ipconfig)

### jq

`jq` is a cli utility like `sed` for `JSON`. "You can use it to slice and filter and map and transform structured data."

- [jqlang.org](https://jqlang.org/)

### ls

The `ls` command lists the contents of a directory. Using the `-a` flag will include hidden files (like `ls -a`). The `-l` flag will display additional information about the files (such as ownership and last modified date).

You can combine commands, such as the `which` command to get information about executables. Below the command lists information about the aws executable and its file permissions. Sorting the output by modification time (`t`), in reverse order (`r`) and including hidden files (`a`) and then printing the results in the long format (`l`). These extra options aren't necessary for a single file but are common habits for directory listings.

```shell
ls -ltra $(which aws)
```

- [ls](https://en.wikipedia.org/wiki/Ls)

### mkdir

The `mkdir` command will create folders and directories. If you use the `-p` flag any parent directories that don't exist will be created. Using that flag and brace expansion you can create complex directory structures. For example:

```shell
mkdir -p dir/{module/{ses, s3}, functions/email}
```

Would create the following structure:

```
dir/
├── module/
│   ├── ses/
│   └── s3/
└── functions/
    └── email/
```

- [Brace Expansion](https://www.gnu.org/software/bash/manual/html_node/Brace-Expansion.html)

### nl

The `nl` command numbers lines of a file. It will print out the line number along with the line itself. Some options include using a pattern matcher and including blank lines.

```shell
nl commands.md
```

- [nl (Unix)](https://en.wikipedia.org/wiki/Nl_(Unix))

### ping

The `ping` command tests if a device on a network is reachable.

- [Ping command basics for testing and troubleshooting](https://www.redhat.com/en/blog/ping-usage-basics)

### realpath

The `realpath` command prints the resolved, absolute pathname of a file or directory. It automatically expands all symbolic links and clears out relative path elements like . (current directory) and .. (parent directory). It can be useful to use the `cd` command with it in order to change to a given directory.

```shell
cd $(realpath name)
```

- [Linux realpath](https://dustinpfister.github.io/2022/03/18/linux-realpath/)

### rm

The remove command will remove files and folders from your hard drive. You can use the `-f` flag to force items to be removed and to suppress confirmation messages. The `-r` flag will recursively delete items in order to delete directories.

Here's an example: `rm -rf directory_name`

- [rm man page](https://linuxcommand.org/lc3_man_pages/rm1.html)

### sed

The `sed` command can help you manipulate text from files. For example, it can be useful to use if you need to replace some text per a configuration or environment.

From the documentation below, here's an example which replaces instances of `hello` with `world` in the `input.txt` file and outputs the changes to `output.txt`.

```shell
sed 's/hello/world/' input.txt > output.txt
```

- [sed, a stream editor](https://www.gnu.org/software/sed/manual/sed.html)

### test

You can check for files using the `test` command. For example, the following command will print a message describing if a file exists or not. Replace `file/path` with your test case.

```shell
test -e file/path && echo exist || echo not exist
```

### touch

The `touch` command can create files for you. Such as `touch filename`.

- [Creating an Empty File in Linux](https://www.geeksforgeeks.org/linux-unix/touch-command-in-linux-with-examples/)

### tree

The `tree` command prints the directory structure from the folder where you run the command.

- [tree (command)](https://en.wikipedia.org/wiki/Tree_(command))

### uname

`uname` can be used to list system information. Such as the kernel name or machine hardware name.

Here are two examples, one that prints all system information and one that prints the machine name:
```shell
uname -a
uname -m
```

- [uname](https://man7.org/linux/man-pages/man1/uname.1.html)

### which

The `which` command locates the executable file that runs when you type a command in your terminal. For example, `which aws` or `which code` will print the file path to the executable that runs those commands.

- [which (command)](https://en.wikipedia.org/wiki/Which_(command))
