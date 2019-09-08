# bitwarden-ssh-auto-login
Auto ssh login with bitwarden saved password &amp; totp pin

# Features
1. Will auto prompt for bitwarden login/unlock (using `bw` of https://github.com/bitwarden/cli)
2. Get item from bitwarden with matching domain and auto fill password with `expect`
3. Auto fill TOTP pin with `oathtool` computed result if available
4. Decode bitwarden json result with `node`

# Note
1. Only tested on ubuntu & bash
2. Bitwarden session will be expired after current terminal session ended or any new `bw unlock` execution

# Requirements
1. `bw` of https://github.com/bitwarden/cli
2. `expect` of https://core.tcl-lang.org/expect/index
3. `oathtool` of https://www.nongnu.org/oath-toolkit/
4. `node` of https://nodejs.org/en/

# Installation
## Download
```shell
git clone https://github.com/lessmind/bitwarden-ssh-auto-login.git
ln -s bitwarden-ssh-auto-login/bwssh ~/bin/ # or any other dir in $PATH
```

## Alias
Add alias in .bashrc or other equivalent files
```shell
alias ssh='. bwssh ssh'
alias scp='. bwssh scp'
# or any other command requires ssh login
```
use `.` for exporting `BW_SESSION` to current shell

## Configuration
Vim `~/.bwssh`
```shell
# [ssh host] [bitwarden object id]
# comment starts with '#'
ssh1.example.com 00000000-0000-0000-0000-000000000001
ssh2.example.com 00000000-0000-0000-0000-000000000002
ssh3.example.com 00000000-0000-0000-0000-000000000003
```
`[bitwarden object id]` could be obtained from `bw list`, see `bw list --help`
