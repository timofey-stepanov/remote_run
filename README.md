Remote Run (rr)
===============

Remote Run is designed to simplify developing process when
you should often perform some actions on remote server but want to edit files locally
using your preferable editor or IDE (QtCreator, Sublime, etc).

To execute command on your file tree on remote server simply prefix it with "rr ".
Tool will sync all changes from local file tree to server, execute the command,
and sync it's results back.

System requirements
===================

You should have python3 and rsync locally.
Your remote server should be accessible through rsync and ssh.

Tool is tested on OS X but should work on other Unix-like systems.

Quick start
===========

- **Install:**

    ```bash
    mkdir -p ~/bin
    git clone git://github.com/golovasteek/remote_run.git ~/bin/remote_run
    ln -s ~/bin/remote_run/rr.py ~/bin/rr
    ```
    If ~/bin is not in your $PATH you can add it:
    ```bash
    echo "export PATH+=\"~/bin:\$PATH\"" >> ~/.bashrc
    . ~/.bashrc
    ```

- **Configure:** Go to your project's root directory and configure remote run there:

    ```bash
    rr --init
    ```

    Editor will be opened. Set config variables with your server and a remote directory.
    Config will be saved into .remoterunrc in current directory.

- **Use:** Run your commands on server. Example:

    ```bash
    rr gcc hello.cpp -o hello
    rr ./hello
    ```
    Or launch shell:
    ```bash
    rr
    ```

Hints
=====

- To set environment variables place them between `rr` and your command:
    ```bash
    rr BUILD_VERBOSE=1 make
    ```

- For pipes use `bash -c`
    ```bash
    rr bash -c "cat file.txt | sort | uniq | wc -l"
    ```