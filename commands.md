# Commands

Notes on various CLI commands.

## Contents

- [Changing Directories](#changing-directories)
- [dig](#dig)
- [sed](#sed)

### Changing Directories

`cd` lets us change between directories. You can use a dash to jump back to your last directoy, like `cd -`.

### dig

The `dig` command queries domain name system (DNS) servers. It's useful for troubleshooting DNS problems. 

The `+trace` flag will run iterative queries to list the DNS lookup path. Such as `dig google.com +trace`.

The `+x` flag will run a reverse DNS lookup. Like `dig +noall +answer -x 8.8.8.8`.

- [dig command](https://www.ibm.com/docs/en/aix/7.3?topic=d-dig-command)
- [Linux and Unix dig Command Examples](https://www.cyberciti.biz/faq/linux-unix-dig-command-examples-usage-syntax/)
- [dig Command in Linux with Examples](https://www.geeksforgeeks.org/dig-command-in-linux-with-examples/)

### sed

The `sed` command can help you manipulate text from files. For example, it can be useful to use if you need to replace some text per a configuration or environment.

From the documentation below, here's an example which replaces instances of `hello` with `world` in the `input.txt` file and outputs the changes to `output.txt`.

```shell
sed 's/hello/world/' input.txt > output.txt

```

- [sed, a stream editor](https://www.gnu.org/software/sed/manual/sed.html)
