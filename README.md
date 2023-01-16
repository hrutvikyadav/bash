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

    prints out to terminal

    U

    ```bash
    $ echo hello terminal
    hello terminal
    ```

    print to a file instead of the terminal by specifying the filename

    ```bash
    echo this will be written to README.md >> README.md
    ```

    > use `-e` flag to insert _escape sequences_\
    > for this to work correctly, enclose entire value in quotes

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
