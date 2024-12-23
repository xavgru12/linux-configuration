setup nvim with chad and custom plugins (mason, pyright etc)

save in bash profile(create own custom .sh and append to bash profile (.bashrc))
history | tail -2 | head -1 |  cut -c 8- | tr -d '\n' | xclip -selection clipboard

history prints history of commands, tail takes last two commands, head takes one of the commands(which is last command), cut -c 8- removes the number which is in front of command, tr removes new empty line
 
name the command: last (bash alias)



One way is to pipe it to tee -a /dev/tty >> file like so:

echo "This is some text" | tee -a /dev/tty >> file

Another way is to pipe it to tee -a file with no redirects like so:

echo "This is some text" | tee -a file

check how big a folder is:
du -hs /path/to/directory

