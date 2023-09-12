Interactive Shell

Upgrading to a fully interactive TTY using Python

# Enter while in reverse shell
$ python -c 'import pty; pty.spawn("/bin/bash")'

Ctrl-Z

# In Kali
$ stty -a
$ stty raw -echo
$ fg

# In reverse shell
$ reset
$ export SHELL=bash
$ export TERM=xterm-256color
$ stty rows <num> columns <cols>

--------------------------------------------


The reason why it doesn't work in Kali Linux is because the latest Kali uses the zsh shell by default, not bash. To get it to work, you just have to make sure you're using the bash shell.

To temporarily switch to a bash shell, run the following command in your terminal:

exec bash --login

You can confirm if you're using bash by running:

ps -p $$

In the terminal which uses bash, run the listener and run the commands to upgrade the shell:

python -c 'import pty; pty.spawn("/bin/bash")'
CTRL + Z
stty raw -echo
fg
export TERM=xterm

As long as you're using bash and not zsh, it will work.

