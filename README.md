# Git-Commands
List of git commands


Git is a set of command line utility programs that are designed to execute on a Unix style command-line environment. Modern operating systems like Linux and macOS both include built-in Unix command line terminals. Git for Windows comes with its own command prompt (Git Bash) that, besides git commands, has some useful Unix commands (and it looks better than the Windows default prompt).

======
Git generic commands
git init								: Initializing new git repository
git config –global user.name "[name]"  	: Sets the author name
git config –global user.email "[email]" : Sets the author email
git clone URL							: For cloning the repository from existing url
git commit -m "Message"					: Commit all the files with message in local repo
git add *								: Adding all the files to git repository
git add [file]							: Add a particular file to git repository
git diff								: shows the file differences which are not staged
git diff -staged						: differences between files in staging area and latest version present
git diff [first branch] [second branch]	: difference between two branches
git reset [file]						: unstages the file, but preseves the content
git reset [commit]						: undoes all commits after specified commit and preserves the changes locally
git reset -hard [commit]				: discards all history and goes back to specified commit
git status								: lists all the files that have to be committed
git rm [file]							: command deletes file from working directory and stages deletion
git rm --cached -r 						: remove all the files from staging area(basically undo the git add . command)
git log									: list the version history for current branch
git log -follow[file]					: list version history for a file, including the renaming of files also
git show [commit]						: show metadata and content changes of specified commit
git tag [coomitId] 						: command used to give tags to specified commit
git branch								: list all the branches in current repository
git branch [branch name]  				: command create a new branch
git branch -d [branch name]  			: command delete the branch
git checkout [branch name]				: used to switch from one branch to another 
git checkout -b [branch name] 			: creates a new branch and switched to it
git merge [branch name]					: merge specified branch's history into current branch
git remote add [variable] [remoteUrl]	: connect your local repo to remote server (variable is the name of the remote, by default used origin)
git push [variableName] master			: sends commited changes of master branch to remote repository
git push [variableName] [branch]		: sends branch commits to remote repository
git push -all [variableName]			: pushes all branches to your remote repository
git push [variableName] :[branchName]	: deletes a branch on your remote repository
git push -u origin master				: pushes your local repository to remote repository
git pull [repoLink]						: fetches and merges changes from remote server to working directory 
git stash save							: temporarily stores all modified tracked files
git stash pop							: restores the most recently stashed files
git stash list							: lists all stashed changesets
git stash drop							: discards the most recently stashed changeset

======
There are three regions in git: 
1) Working directory =>git add=> Staging directory 
2) git commit
3) Local repository

===================
SSH Key for Github
===================
When working with a GitHub repository, you'll often need to identify yourself to GitHub using your username and password. An SSH key is an alternate way to identify yourself that doesn't require you to enter you username and password every time. SSH keys come in pairs, a public key that gets shared with services like GitHub, and a private key that is stored only on your computer. If the keys match, you're granted access. The cryptography behind SSH keys ensures that no one can reverse engineer your private key from the public one

======
The first step in using SSH authorization with GitHub is to generate your own key pair. You might already have an SSH key pair on your machine. You can check to see if one exists by moving to your .ssh directory and listing the contents.
$ cd ~/.ssh
$ ls
Check the directory listing to see if you already have a public SSH key.

======
By default, the filenames of the public keys are one of the following:
id_dsa.pub
id_ecdsa.pub
id_ed25519.pub
id_rsa.pub

======
If you see id_rsa.pub, you already have a key pair and don't need to create a new one. If you don't see id_rsa.pub, use the following command to generate a new key pair. Make sure to replace your@email.com with your own email address.
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
When asked where to save the new key, hit enter to accept the default location.
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/username/.ssh/id_rsa):
You will then be asked to provide an optional passphrase. This can be used to make your key even more secure, but for this lesson you can skip it by hitting enter twice.

Enter passphrase (empty for no passphrase):
Enter same passphrase again:
When the key generation is complete, you should see the following confirmation:

Your identification has been saved in /Users/username/.ssh/id_rsa.
Your public key has been saved in /Users/username/.ssh/id_rsa.pub.
The key fingerprint is:
01:0f:f4:3b:ca:85:d6:17:a1:7d:f0:68:9d:f0:a2:db your@email.com
The key's randomart image is:
+--[ RSA 2048]----+
|                 |
|                 |
|        . E +    |
|       . o = .   |
|      . S =   o  |
|       o.O . o   |
|       o .+ .    |
|      . o+..     |
|       .+=o      |
+-----------------+
The random art image is an alternate way to match keys but we won't be needing this.

======
Add public key to GitHub
We now need to tell GitHub about your public key. Display the contents of your new public key file with cat:
$ cat ~/.ssh/id_rsa.pub
The output should look something like this:
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEA879BJGYlPTLIuc9/R5MYiN4yc/YiCLcdBpSdzgK9Dt0Bkfe3rSz5cPm4wmehdE7GkVFXrBJ2YHqPLuM1yx1AUxIebpwlIl9f/aUHOts9eVnVh4NztPy0iSU/Sv0b2ODQQvcy2vYcujlorscl8JjAgfWsO3W4iGEe6QwBpVomcME8IU35v5VbylM9ORQa6wvZMVrPECBvwItTY8cPWH3MGZiK/74eHbSLKA4PY3gM4GHI450Nie16yggEg2aTQfWA1rry9JYWEoHS9pJ1dnLqZU3k/8OWgqJrilwSoC5rGjgp93iu0H8T6+mEHGRQe84Nk1y5lESSWIbn6P636Bl3uQ== your@email.com

======
Deleing SSH key
Delete the id_rsa Files
The Bash command for deleting files is rm -f, so I needed to do this:
rm -f ~/.ssh/id_rsa* // it will delete both the public and private keys

======
Setting configuration for git
Creating a config file inside .ssh folder
touch config
nano config : We are opening config file in nano
#default office account
Host github.com
	HostName github.com
	User git
	IdentifyFile ~/.ssh/id_rsa
#default personal account - DevAnuragGarg
Host devanuraggarg
	HostName github.com
	User git
	IdentifyFile ~/.ssh/id_rsa_dev_anurag_garg
	
======
git@github.com:DevAnuragGarg/FilmiReview-MVVM-Android-Architecture.git
github.com								: host name
git										: command line tool
DevAnuragGarg							: Username
FilmiReview-MVVM-Android-Architecture	: Repository name
