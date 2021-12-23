### Nodejs setup in Kali Linux Machine


## Install nvm


NVM stands for Node.js Version Manager. The nvm command is a POSIX-compliant bash script that makes it easier to manage multiple Node.js versions on a single environment. To use it, you need to first install the bash script, and add it to your shell's $PATH.

Learn more about why we recommend using NVM in Overview: Manage Node.js Locally.

Note: We do not recommend using nvm to install Node.js for production environments. If you're installing Node.js on your production environment you should consider using your OS's package manager, or your server tooling of choice, to install and lock the environment to a specific version of Node.js.

The official documentation for how to install nvm, and some common trouble shooting tips, is in the project's README.

Windows users: The process for installing nvm on Windows is different than what's shown below. If you're using Windows check out this Windows-specific version of nvm.

The basic process is as follows:

## Download the install script

Using curl, or wget, download the installation script. In the URL below make sure you replace v0.35.0 with the latest version of nvm.

```
 curl -sL https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.0/install.sh -o install_nvm.sh
```

It's not a bad idea to open the install script and inspect its contents given that you just downloaded it from the Internet.

## Run the install script

Run the install script with bash.

```
bash install_nvm.sh
```

This script clones the nvm repository into ~/.nvm. Then it updates your profile (~/.bash_profile, ~/.zshrc, ~/.profile, or ~/.bashrc) to source the nvm.sh it contains.

You can confirm that your profile is updated by looking at the install script's output to determine which file it used. Look for something like the following in that file:

```
export NVM_DIR="$HOME/.nvm"
  [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
  [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```
  
## Restart your terminal
In order to pick up the changes to your profile either close and reopen the terminal, or manually source your respective ~/.profile.

Example:

```
source ~/.bash_profile
```

## Verify it worked
Finally, you can verify that it's installed with the command command:

```
command -v nvm
```

Should return nvm. Note: You can't use the which command with nvm since it's a shell function and not an actual application.

## See what it does

Finally, run the nvm command to get a list of all the available sub-commands and to further verify that installation worked.

# Use nvm to install the latest LTS release of Node.js
Now that you've got nvm installed let's use it to install, and use, the current LTS version of Node.js.

```
nvm install --lts
```

# Output
Installing latest LTS version.
Downloading and installing node v16.x...
Downloading https://nodejs.org/dist/v10.16.3/node-v16.x-darwin-x64.tar.xz...
######################################################################## 100.0%
Computing checksum with sha256sum
Checksums matched!
Now using node v16.x (npm v8.9.0)
Creating default alias: default -> lts/* (-> v16.x)
<br>

Verify it worked, and that the version is correct:

```
node --version
```

# => v16.x
which node
# => /Users/joe/.nvm/versions/node/v16.x/bin/node
