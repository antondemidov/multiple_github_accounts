# multiple_github_accounts
just a note how to handle multiple github accounts

# Steps
1. Generate multiple ssh keys
```
ssh-keygen -t rsa -C "email@personal_mail.com" -f "id_rsa"
ssh-keygen -t rsa -C "email@work_mail.com" -f "id_rsa_work"
```
2. Add public key to github accounts
3. Add something like this to ssh config:

```
#github personal
host github.com
 HostName github.com
 IdentityFile /Users/Username/.ssh/id_rsa
 User git

##github work
host github.com-work
 HostName github.com
 IdentityFile /Users/Username/.ssh/id_rsa_work
 User git
```
4. Add to `~/.zshrc` few aliases:
```
alias github-work='ssh-add -D && ssh-add /Users/Username/.ssh/id_rsa_work'
alias github-personal='ssh-add -D && ssh-add /Users/Username/.ssh/id_rsa'
```
5. `source ~/.zshrc` and choose what account you need to use
