I always forget certain git commands so this is a compilation of those. 

# Delete local and remote branch

```
git push origin --delete <branch_name>
git branch -d <branch_name>
```

# Git aliases

**Create branch**

This git alias creates a new branch and publishes to origin

```newBranch = !git checkout -b $1 && git push -u origin```

Use it like `git newBranch myBranch` This will create a branch called `myBranch` and will be pushed to origin (so the remote branch will be created too)

**Delete branch**

`delBranch = !git push origin --delete $1 && git branch -d`


# Better Git Terminal

To use git autocomplete and have a better terminal **in macOS** do the following: 

**Install the tools** 

In the terminal do: 
```
brew install bash-git-prompt bash-completion
```

This will install autocomplete for git branches, files, etc and also a better git representation (like the name of the branch in the prompt).

**Configure Bash Profile**

Your bash profile (located in `~/.bash_profile` if it doesn't exist, create it) should look like this:
```
# terminal colors
export CLICOLOR=1
export TERM=xterm-color

[ -f /usr/local/share/git-completion.bash ] && . /usr/local/share/git-completion.bash

if [ -f /usr/local/share/gitprompt.sh ]; then
    # Use the next var if you want to get the prompt only in the repo directory
    GIT_PROMPT_ONLY_IN_REPO=1
    GIT_PROMPT_THEME=Default
    . /usr/local/share/gitprompt.sh
fi

# Git branch name in prompt
parse_git_branch() {
    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
export PS1="\u@\h \W\[\033[32m\]\$(parse_git_branch)\[\033[00m\] $ "
```


