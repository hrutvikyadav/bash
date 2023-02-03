# Bash

_Use `--help` flag with any command to see what it will do and the options you can provide along with it_
_Use `type <command_name>` to see the type of a command_

```bash
$ type echo
echo is a shell builtin

$ type bash
bash is /usr/bin/bash
```

___

For list of inbuilt __bash commands__, use
> Commands run in both _terminal_ and _script files_

```bash
$ help
GNU bash, version 5.0.17(1)-release (x86_64-pc-linux-gnu)
...
```

> For a list of commands that are not built in, use `ls /bin`\
> `/bin` directory in the root contains all binaries\

To find more about specific function, run `help <command>`

```bash
$ help if
if: if COMMANDS; then COMMANDS; [ elif COMMANDS; then COMMANDS; ]... [ else COMMANDS; ] fi
    Execute commands based on conditional.

    ...
```

> To execute _multiple commands_ in _one line_, use `;` to end statements

```bash
$ touch newfile.txt; echo $?
0
```

___

__exit status__ of _last command_ can be accessed with `$?`
> in terminal as well as script file

```bash
$ echo $?
0
```

| Exit status| Description |
|   :---:    |    :----:   |
| 0  | no errors       |
| 1  | error        |

__anything other than zero__ means there was an _error_
___

## Commands

1. echo

    prints out to terminal through _stdout_ or _stderr_[^op-types]

    U

    ```bash
    $ echo hello terminal
    hello terminal
    ```

    _redirect_ `echo`'s output to a file instead of printing to terminal by specifying the filename to
    > `>` or `1>` to _create or overwrite_ file with __stdout__'s content\
    > `2>` to do the same with __stderr__'s contents
    > `>>` to _append_ to existing file\
    If the _left side of `>` is __empty__,_ it will overwrite the file with empty contents
    Note:
    - stdout and stderr point to terminal by default, and stdin points to keyboard by default[^ip-types]
    - _redirect_ __stdin with `<` and stderr, stdin with `>`__\
    - redirecting will make std* point to filename instead

    ```bash
    # print output to file instead of default(terminal)
    echo "this will be written to existing README.md" >> README.md
    ```

    > use `-e` flag to insert _escape sequences_\
    > for this to work correctly, enclose entire value in quotes

    ```bash
    # read from file instead of default i.e. keyboard
    read NAME < examplefile.txt
    ```

2. pwd

    lists the current/present working directory

    U

    ```bash
    $ pwd
    home/example-directory/example-subdirectory
    ```

3. ls

    list contents of present dir

    U

    ```bash
    ls
    ```

    Use the `-l flag` for the _long list format_

    It will display the contents better

    ```bash
    $ ls -l
    total 468
    -rw-r--r--   1 hrutvik_ hrutvik_   3763 Dec 14 10:40 README.md
    -rw-r--r--   1 hrutvik_ hrutvik_  16958 Dec 15 16:58 favicon.ico
    -rw-r--r--   1 hrutvik_ hrutvik_   1748 Dec 30 12:23 index.html
    -rw-r--r--   1 hrutvik_ hrutvik_    492 Dec 14 10:40 manifest.json
    drwxr-xr-x 368 hrutvik_ hrutvik_  20480 Dec 30 11:41 node_modules
    -rw-r--r--   1 hrutvik_ hrutvik_ 401303 Dec 30 11:38 package-lock.json
    -rw-r--r--   1 hrutvik_ hrutvik_    912 Dec 30 11:36 package.json
    drwxr-xr-x   2 hrutvik_ hrutvik_   4096 Dec 30 12:00 public
    drwxr-xr-x   3 hrutvik_ hrutvik_   4096 Dec 30 11:40 src
    -rw-r--r--   1 hrutvik_ hrutvik_    161 Dec 30 12:20 vite.config.js
    ```

    use the `-a` or `-all` flag to display hidden files as well

    ```bash
    $ ls -a
    .   .git        .vscode    favicon.ico  manifest.json  package-lock.json  public      src
    ..  .gitignore  README.md  index.html   node_modules   package.json       robots.txt  vite.config.js
    ```

4. cd

    change dir by specifying _path or dir_name_

    the path `.` takes you to the folder you are in and `..` takes you one level up

    U

    ```bash
    cd ../..
    ```

    This will take us two levels up from pwd

5. more

    list contents of a specified file

    U

    ```bash
    $ more README.md
    # Bash!
    ```

6. clear

    clear the previous commands and their outputs from terminal

    U

    ```bash
    clear
    ```

7. mkdir

    make a new directory by specifying the _dir_name_

    ```bash
    mkdir new_directory
    ```

8. touch

    Create new file with touch `filename`

    ```bash
    touch index.html
    ```

9. cp

    Copy files by giving source and destination

    ```bash
    cp background.jpg images
    ```

10. rm

    Remove a file by specifying the filename

    ```bash
    rm background.jpg
    ```

11. mv

    move or rename by providing filename and new/destination filename

    ```bash
    mv index.html src/index.js
    ```

12. find

    used to find a file or look at the present directory tree

    ```bash
    find
    ```

    Will list out file tree of current directory

    use `-name` flag to look for a file/folder in a different directory

    ```bash
    $ find -name index.html
    ./client/src/index.html

    $ find -name src
    ./client/src
    ```

13. if

    conditional execution of code
    > use `help <command>` to see syntax

    use `==` for string comparison

    ```bash
    if [[ $1 == arg1 ]]
    then
        echo true
    fi
    ```

    for comparing integers, use
    - `-eq` to check if equal
    - `-ne` to check if not equal
    - `-lt` to check if less than
    - `-le` to check if less than or equal
    - `-gt` to check if greater than
    - `-ge` to check if greater than or equal

    example: check if 1st argument is less than 5

    ```diff
    - if [[ $1 == arg1 ]]
    + if [[ $1 -lt 5 ]]
    then
        echo true
    fi   
    ```

14. `|` pipe character

    used to pipe _output of one command_ to _input of another command_\
    `<command1> | <command2>`
    i.e __1st command's stdout__ is __2nd command's stdin__

    ```bash
    $ echo "my_name" | read NAME
    ```

    > NAME will be set to "my_name" but this _mutation_ happens in a __subshell or subprocess__ and __not__ in the shell you are currently in\
    > So the __variables in current shell will not be affected__

15. cat

    read from stdin[^ip-types] and print to stdout[^op-types]
    > use redirection to specify ip/op\
    > provide filename or other input(eg. strings) as options

    ```bash
    $ cat filename.txt
    # contents of file
    ```

16. wc

    print word count information about file- newline, word, and byte counts for each file

    ```bash
    $ wc file.txt
    # shows the word line and character count
      588  1794 11726 README.md

    # print only lines in file
    $ wc file.txt -l
    592 README.md
    ```
    above output displays byte count inplace of character count
    > they are not the same, try `$ wc -m`\
    > some characters could be more than one byte
    __Input to a command can affect it's output__

17. grep

    _search_ for __patterns__ in text with `grep '<pattern>' <filename>`
    
    ```bash
    $ grep 'thisword' examplefile.txt
    # prints all lines that include _pattern_[^grep pattern]
    ```
    
    > useful flags: `--color`, `-n`, `-c`, `-o`
    
18. sed

    search a pattern and replace it with some other string with `sed 's/<search for pattern>/<replace with>/<regex flags>' <filename>`
    > this won't replace text by default, _prints to terminal instead_
    
    ```bash
    # using file to search
    $ sed 's/[0-9]/1/' numbers.txt
    # replaces digits 0-9 with 1 in file
    
    # use output from other commands
    $ grep -n 'hello[a-z]*' greetings.txt | sed 's/[0-9]+/1/' -E
    # grep will print "1:hello..." to stdout, this is piped to sed input, which will replace digits 0-9 with 1
    ```
    
    > flags `-E` to recognize all regex
17. ps

    Used to see running processes in current shell\
    __Works differently based on what preceeds the options(`-e` and `e` or `--e` is diff)__

    Use with options for useful info
    > Common: `-aux`, `-efjH`\
    > `grep` the output of these flags to find more details about specific commands or similar things

    ```bash
    $ ps
    PID TTY          TIME CMD
        9 pts/0    00:00:00 bash
    144 pts/0    00:00:00 ps

    # use `-x` to see processes from current and other shells,
    # `-u` to show associated user, CPU and memory consumption(VSZ=total_alloted_mem, RSS=currently_consumed_mem_in_RAM) etc
    # `-a` to processes for all users
    $ ps -aux
    USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
    root         1  0.0  0.0   1804  1184 ?        Sl   09:35   0:00 /init
    root         7  0.0  0.0   1812    84 ?        Ss   09:35   0:00 /init
    root         8  0.0  0.0   1812    92 ?        R    09:35   0:00 /init
    hrutvik_     9  0.0  0.0  10188  5056 pts/0    Ss   09:35   0:00 -bash
    hrutvik_   147  0.0  0.0  10856  3320 pts/0    R+   09:45   0:00 ps -aux

    # an alternative to this is `-e`
    # combine with `-f` to get full listing of commands,
    # `-H` to get a tree view with parent and child processes
    $ ps -efH
    UID        PID  PPID  C STIME TTY          TIME CMD
    root         1     0  0 09:35 ?        00:00:00 /init
    root         7     1  0 09:35 ?        00:00:00   /init
    root         8     7  0 09:35 ?        00:00:00     /init
    hrutvik_     9     8  0 09:35 pts/0    00:00:00       -bash
    hrutvik_  2484     9  0 10:31 pts/0    00:00:00         ps -efH
    root       149     1  0 09:59 ?        00:00:00   /init
    root       150   149  0 09:59 ?        00:00:00     /init
    hrutvik_   151   150  0 09:59 pts/1    00:00:00       -bash
    hrutvik_   688   151  0 10:16 pts/1    00:00:00         git show
    hrutvik_   689   688  0 10:16 pts/1    00:00:00           /usr/bin/pager

    # `-j` also shows PGID and SID
    ```

    > `grep` the output- search and find specific processes

    - See processes run by `user`

        ```bash
        $ ps -U root
        PID TTY          TIME CMD
            1 ?        00:00:00 init
            7 ?        00:00:00 init
            8 ?        00:00:00 init
        149 ?        00:00:00 init
        150 ?        00:00:00 init
        297 ?        00:00:00 init
        ```

    - Or `group`_group-name or id_

        ```bash
        $ ps -G 0
        PID TTY          TIME CMD
            1 ?        00:00:00 init
            7 ?        00:00:00 init
            8 ?        00:00:00 init
        149 ?        00:00:00 init
        150 ?        00:00:00 init
        297 ?        00:00:00 init
        298 ?        00:00:00 init
        ```

    Get `occurences` and `PID`'s of a __program__ i.e. _process that is run by executing a command like `apt`_
    Usually to kill a program, find it's PID and run `kill` command

    ```bash
    $ ps -C bash
    PID TTY          TIME CMD
        9 pts/0    00:00:00 bash
    151 pts/1    00:00:00 bash
    2095 pts/9    00:00:00 bash

    ```

    Find information about a process `PID` with `ps -p PID1,PID2,PID3`\
    _when using a list as parameters, don't use spaces_
    use `-o comm=` to output the `command` associated with the `PID`

    ```bash
    $ ps -p 151
    PID TTY          TIME CMD
    151 pts/1    00:00:00 bash
    
    $ ps -p 151 -o comm=
    bash

    $ ps -p 151,1999 -o comm=
    bash
    node
    ```

18. nproc

    See processesing units available to __system__/__current process__

    ```bash
    $ nproc
    16
    ```

19. ulimit

    Used to display, allocate, and limit resources
    Limits can be enforced at _**global**, **group**, and **user** levels_

    Ulimit is linked to security config file[^sc] and allows us to edit this file quickly

    User can edit their own limits within allowed tresholds(`soft-limit` to `hard limit`)

```bash
# dislay limits for user
# defaults to current user if no user specified
$ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 63442
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 63442
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

# associated flag for changing limits is also pronited above
# use `-H` or `-S` to display hard and soft limits
# or use in combination with above output to get specific limits

$ ulimit -Ss
8192
# prints soft limit for stack size

$ ulimit -s 8190
# change temporarily for current shell instance
```

> To make changes permanent, change the security config file as root
> add 4 fields to the file- `domain`, `type`, `item`, `value`
> Ex> Set hard limit for processors for user_name_X
> `user_name_X hard nproc 4`

```bash
user_name_X@PC:~$ su
Password:

root@PC:/home/user_name_X# nano /etc/security/limits.conf
root@PC:/home/user_name_X# exit
user_name_X@PC:~$ ulimit -u
3xxx
```

_Reference for possible items to change:_

| item | changes it will make |
| :---: | :---:|
core | limits core file size(KB)
data | set max data size(KB)

___

## Scripts

Instead of _running commands in terminal,_ we can _put commands in a file_ to run as a `script`

- scripts are created with `.sh` extension

    ```bash
    $ touch new-script.sh
    $
    ```

    add commands to the script

    ```bash
    # new-script.sh

    echo hello from new-script
    ```

- run the script with `sh <filename>` to run it _using `shell` interpreter_

    ```bash
    $ sh new-script.sh
    hello from new-script
    ```

    > to run using _bash interpreter,_ use `bash <filename>`\
    > `bash` stands for _bourne-again-shell_

    __many interpreters may not give the output you expect__

- _add comments to file with_ `: ''`

    ```bash
    : '
        This is a comment
        this is another line    
    '
    ```

___

- find the _location path of the bash shell_,

    ```bash
    $ which bash
    /usr/bin/bash
    ```

    > returns the path

- to tell the script file to use _path of the bash interpretor_, add a __shebang__ `#!<bash_path>`

    adding a `shebang` tells the script to _use bash __interpretor by default__._
    > i.e. bash or whatever is present at the path specified

    ```bash
    # new-script.sh
    # add path from above command
    #!/bin/bash

    echo shebang added to script
    ```

    now we can execute the script with just the filename/path

    ```bash
    $ ./new-script.sh
    shebang added to script
    ```

    _if user does not have permission to run the script, it won't execute and a message will be shown_

    ```bash
    $ ./new-script.sh
    bash: ./new-script.sh: Permission denied
    ```

    in this case, list out the directory contents and check permissions for the script

    ```bash
    $ ls -l
    total 8
    -rw-r--r-- 1 hrutvik_ hrutvik_ 4643 Jan 16 12:05 new-script.sh
    ```

    the first column for the script file: `-rw-r--r--` shows permissions
    > the shorthands represent permissions, where r: read, w: write, x: execute

    to change permissions, i.e. add execute permission, run `chmod +x <filename>`

    ```bash
    $ chmod +x new-script.sh
    $
    ```

    this will add `x` permission for each user. list the dir again to verify if x was added for users\
    now the file should run

___

## Variables

> View all variables in the shell using `declare -p`\
> here -p stands for print\
> _use `declare -p VAR_NAME`_ to view specific vars

- create variables with `VARIABLE_NAME=VALUE`, _without spaces_
    > to add a value with spaces, use `""`

    ```bash
    # new-script.sh

    MY_VAR=1

    MY_STR="new string"
    ```

- use _variable name with `$` to use it_

    ```diff
    ...

    + echo $MY_STR 
    ```

- to read user input and store it in new variable use `read VAR_NAME`

    ```diff
    ...
     
    + read NEW_VAR
    + echo entered value is $NEW_VAR
    ```

    this will read user input and print it

## Arguments

programs/scripts can accept `arguments`
access the args in program with $

- one way to access all passed args is with `$*`

    ```bash
    #!/bin/bash
    # script.sh
    echo $*
    ```

    executing the script will print out all passed args

    ```bash
    $ ./script.sh arg1 arg2
    arg1 arg2
    ```

- another way to access args is with `$index`, begining with 1\
    in `script.sh`

    ```diff
    ...

    - echo $*
    + echo $1
    ```

    will print only the first argument

## Env variables

Every shell has env variables, use `printenv` to view the list\
Use `$env_var_name` to access them

```bash
$ printenv
SHELL=/bin/bash
COLORTERM=truecolor
TERM_PROGRAM_VERSION=1.74.3
...

$ $SHELL
/bin/bash
```

## Calculations

Bash sees everything as a string

- to perform operations, enclose calculations inside `(( ))`\
    __`$` is not needed inside `(( ))`__
    > run `help let` to see more

    ```bash
    $ I=0; (( I+2 )); echo $I
    2
    ```

    > Above code will only perform calculation\
    > To do something with the result of calculation, use `$(( ))`
    >
    > ```bash
    > $ I=0; echo $(( I+2 ))
    > 2
    > ```

- another option is to use `[[ ]]`\
    __`$` is needed inside `[[ ]]`__
    > run `help [[` and `help test` to see more

## Arrays

Arrays are zero indexed
Create array with variable

```bash
$ ARR=("first_elem" "a" "c")
$
```

access using index

```bash
$ echo ${ARR[1]}
a
```

print all elements in array

```bash
$ echo ${ARR[*]}
first_elem a c
```

> also possible to use `@` in place of `*`

we can also use `declare` to view the variable

```bash
$ declare -p ARR
declare -a ARR=([0]="first_elem" [1]="a" [2]="c")
```

> `-a` in above returned value stands for array

## Functions

Declare functions using
> run `help function` to view more help

```bash
# declare a function
NEW_FN() {
    echo this is a new fn
}

# call it
NEW_FN
```

Functions can accept args just like scripts\
access them based on index(starting from 1)

```bash
# declare fn and access args
ANOTHER_FN() {
    echo first arg is $1
}

# call with args
ANOTHER_FN 9
```

above function will print out 9

___

## Footnotes

[^ip-types]: stdin-by-default-*readsfrom*keyboard
[^op-types]: there are 2 types of outputs- stdout and stderr, both *print to* terminal by default. Valid/successful commands will print to stdout, whereas invalid/unsuccessful commands will print to stderr
[^grep pattern]: string or RegExp
