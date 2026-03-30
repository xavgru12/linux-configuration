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

Gemini hat gesagt
This EACCES error is a direct result of trying to install or link a global package into /usr/lib/node_modules/, which is owned by the root user, while you are logged in as xaver.

Since we just updated your Node.js using the NodeSource (APT) method, your global folder is restricted. You have two ways to fix this: the "Quick Fix" (using sudo) or the "Pro Fix" (fixing permissions permanently).

Option 1: The Quick Fix (sudo)
If you are just trying to get nemoclaw installed right now, simply prefix your command with sudo:

Bash
sudo npm link
# OR
sudo npm install -g <package-name>
Note: Using sudo with npm is generally discouraged for long-term development because it can lead to further permission headaches down the line, but it will solve the immediate error.

Option 2: The "Proper" Fix (Change NPM's Default Directory)
To avoid ever needing sudo for npm again, you can tell npm to store global packages in your home directory instead of the system folders.

Create a directory for global installations:

Bash
mkdir ~/.npm-global
Configure npm to use the new directory path:

Bash
npm config set prefix '~/.npm-global'
Open (or create) your ~/.profile or ~/.bashrc file:

Bash
nano ~/.bashrc
Add this line to the very end of the file:

Bash
export PATH=~/.npm-global/bin:$PATH
Update your current terminal session:

Bash
source ~/.bashrc
