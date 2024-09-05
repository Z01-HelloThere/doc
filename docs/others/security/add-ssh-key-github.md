# Connect to Github with a SSH key

## Quick step-by-step guide:

### Generate a new SSH key:

```sh
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Note: you can use your github email address

### Add the key to the ssh-agent:

```sh
eval "$(ssh-agent -s)"; ssh-add ~/.ssh/id_ed25519
```

option | desc.
---|---
`-t` | **type**<br>Specifies the type of key to create.
`-C` | add a **comment** (usualy the email address)  
`-f` | **filename**<br>Specifies the filename of the key file. 

### Configure Git and Github

* Copy the public key:

```sh
cat ~/.ssh/id_ed25519.pub
```

* Set git key format

```sh
git config --global --unset gpg.format
git config --global gpg.format ssh
```

* Add the public key to your [GitHub](https://github.com/settings/keys) account (Settings > SSH and GPG keys > New SSH key)

* Configure Git to use the SSH key: 

```sh
git config --global user.signingkey ~/.ssh/id_ed25519
```

(Note: this step is not necessary if you're using SSH keys, but rather GPG keys. For SSH keys, you can simply use `git commit -S` to sign your commits)

### Test your newly created key on the github server

```sh
ssh -T git@github.com
```

You should receive this answer:

```txt
Hi <username>! You've successfully authenticated, but GitHub does not provide shell access.
```

### How to sign a commit?

```sh
git commit -S -m "Your commit message"
```

## Optional

### Start your SSH-agent automatically

Add this script to a ~/.ssh/ssh-agent-start.sh file.

```sh file=~/.ssh/ssh-agent-start.sh
SSH_ENV="$HOME/.ssh/agent-environment"

function start_agent {
    echo "Initialising new SSH agent..."
    /usr/bin/ssh-agent | sed 's/^echo/#echo/' >"$SSH_ENV"
    echo succeeded
    chmod 600 "$SSH_ENV"
    . "$SSH_ENV" >/dev/null
    /usr/bin/ssh-add;
}

# Source SSH settings, if applicable

if [ -f "$SSH_ENV" ]; then
    . "$SSH_ENV" >/dev/null
    #ps $SSH_AGENT_PID doesn't work under Cygwin
    ps -ef | grep $SSH_AGENT_PID | grep ssh-agent$ >/dev/null || {
        start_agent
    }
else
    start_agent
fi
```

Execute:

```sh
chmod +x ~/.ssh/ssh-agent-start.sh
```

Add to your `~/.bashrc` file

```sh
. ~/.ssh/ssh-agent-start.sh
```
