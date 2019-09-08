# bitwarden-ssh-auto-login
Auto ssh login with bitwarden saved password &amp; totp pin

# Requirements
1. `bw` from https://github.com/bitwarden/cli
2. `expect` from https://core.tcl-lang.org/expect/index
3. `oathtool` from https://www.nongnu.org/oath-toolkit/

# Installation
```shell
git clone https://github.com/lessmind/bitwarden-ssh-auto-login.git
ln -s bitwarden-ssh-auto-login/bwssh ~/bin/ # or any other dir in $PATH
```

# Alias
Add alias in .bashrc or other equivalent files
```shell
alias ssh='. bwssh ssh'
alias scp='. bwssh scp'
# or any other command requires ssh login
```

# Configuration
Vim `~/.bwssh`
```shell
# [ssh host] [bitwarden object id]
ssh1.example.com 00000000-0000-0000-0000-000000000001
ssh2.example.com 00000000-0000-0000-0000-000000000002
ssh3.example.com 00000000-0000-0000-0000-000000000003
```
`[bitwarden object id]` could be obtained from `bw list`, see `bw list --help`
