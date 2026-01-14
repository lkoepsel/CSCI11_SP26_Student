# Add your public key to Github

Adding your public key to github enables you to easily update your repository without a login. This step is mandatory and will be required for class.

# Steps

1. Start a terminal session in VS Code, *Terminal -> New Terminal*
2. Enter the following, ensuring each step is completed successfully before continuing:

## Step 1: 
```bash
ssh-keygen -t ed25519 -C "username@email.com"
```
This generates a new SSH key pair using the Ed25519 algorithm. [^4]

- **`ssh-keygen`**: The utility that creates SSH key pairs [^11]
- **`-t ed25519`**: Specifies the key type as Ed25519, which is more secure and performant than RSA [^12][^13]
- **`-C "username@email.com"`**: Adds a comment (label) to the key for identification purposes [^4]

The command prompts you to: (press return and accept the defaults)
- Choose a file location (defaults to `~/.ssh/id_ed25519`)
- Enter a passphrase for extra security (can be left empty)

This creates two files:
- `~/.ssh/id_ed25519` — your private key (keep this secret) [^7]
- `~/.ssh/id_ed25519.pub` — your public key (safe to share) [^7]

## Step 2: 
```bash
eval "$(ssh-agent -s)"
```

This starts the SSH agent and loads its environment variables into your current shell session. [^3][^6]

- **`ssh-agent -s`**: Starts the SSH agent and outputs shell commands that set environment variables [^6]
- **`$(...)` or backticks**: Command substitution that captures the output of `ssh-agent -s` [^3]
- **`eval`**: Executes the captured output, which sets `SSH_AUTH_SOCK` and `SSH_AGENT_PID` variables in your environment [^1]

Without `eval`, the variables would only be printed to the screen and not actually loaded into your shell. [^1] The SSH agent is a background process that securely holds your private key in memory.

## Step 3: 
```bash
ssh-add ~/.ssh/id_ed25519
```

This adds your private key to the running SSH agent. [^8][^9]

- **`ssh-add`**: Registers an SSH private key identity with the authentication agent [^8]
- **`~/.ssh/id_ed25519`**: The path to your private key file

Once added, the SSH agent handles authentication for you automatically. If your key has a passphrase, you'll be prompted to enter it once, and the agent caches it for the session. [^2][^9]

## Step 4: 
```bash
cat ~/.ssh/id_ed25519.pub
```

This displays your public key to the terminal. [^5][^10]

- **`cat`**: Reads and prints the file contents [^10]
- **`~/.ssh/id_ed25519.pub`**: Your public key file

The output is your public key, which you can copy and add to services like GitHub, GitLab, or remote servers to enable passwordless authentication. [^5]

## Step 5: 

Copy the line printed in Step 4. It will look similar to:
```bash
ssh-ed25519 AAc923NzaC1lZDI1NTE5A12b98zR9T/aH+Fqge+cSZuNBIDQBIENXcmGjgMSDKdMOuRf myemail@domain.com`
```

## Step 6: 
1. On your Github page, click on your image/avatar in the upper right-hand corner, to show a panel of entries, click on Settings:
    
    ![](avatar.png)

2. In Settings click on SSH and GPG keys
    
    ![](settings.png)

3. Click on New SSH Key

    ![](new.png)

4. Add a 1. Title, 2. Authentication Key, 3. paste the public key and 4. click Add SSH Key

    ![](addsshkey.png)


## Step 7:

Confirm *ssh* works by running `ssh -T git@github.com` in your terminal. If successful, it will reply with:
```bash
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

## Complete Workflow Summary

1. Generate a new Ed25519 key pair
2. Start the SSH agent to manage keys securely
3. Add your private key to the agent
4. Display your public key so you can copy it to remote services

This setup enables secure, passwordless SSH authentication without typing your passphrase repeatedly during a session. [^2]

[^1]: [shell - Why eval the output of ssh-agent? - Unix & Linux Stack...](https://unix.stackexchange.com/questions/351725/why-eval-the-output-of-ssh-agent) (14%)
[^2]: [Working With SSH Key Passphrases](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/working-with-ssh-key-passphrases) (14%)
[^3]: [bash - Running ssh-agent from a shell script - Server Fault](https://serverfault.com/questions/547923/running-ssh-agent-from-a-shell-script) (10%)
[^4]: [Generating a new SSH key and adding it to the ssh-agent - GitHub...](https://docs.github.com/en/enterprise-cloud@latest/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) (10%)
[^5]: [Adding a new SSH key to your GitHub account - GitHub Docs](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) (10%)
[^6]: [linux - ssh-agent needs to start each time on my server](https://serverfault.com/questions/593040/ssh-agent-needs-to-start-each-time-on-my-server) (8%)
[^7]: [Generating SSH key pairs - Reclaim Hosting](https://support.reclaimhosting.com/hc/en-us/articles/8421003621015-Generating-SSH-key-pairs) (7%)
[^8]: [ssh-add(1) - Linux man page](https://linux.die.net/man/1/ssh-add) (7%)
[^9]: [What exactly does ssh-add do? - Super User](https://superuser.com/questions/360686/what-exactly-does-ssh-add-do) (6%)
[^10]: [How do I access my SSH public key? - Stack Overflow](https://stackoverflow.com/questions/3828164/how-do-i-access-my-ssh-public-key) (4%)
[^11]: [Generating Your SSH Public Key - Git](https://git-scm.com/book/en/v2/Git-on-the-Server-Generating-Your-SSH-Public-Key) (4%)
[^12]: [Use SSH keys with GitLab](https://docs.gitlab.com/user/ssh/) (3%)
[^13]: [ed25519 vs other keys for SSH - Callgoose Docs](https://docs.callgoose.com/general/ed25519_vs_other_keys_for_ssh) (3%)
