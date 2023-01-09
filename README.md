# Bash

_Use `--help` flag with any command to see what it will do and the options you can provide along with it_

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

13.
