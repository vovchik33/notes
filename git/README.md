# GIT

### Support few ssh keys on the same machine
switch to vovchik33
```
eval "$(ssh-agent -s)" && ssh-add ~/.ssh/id_ed25519
```

switch to other
```
eval "$(ssh-agent -s)" && ssh-add ~/.ssh/id_rsa
```

or configure all them together in ~/.ssh/config
```
Host gitlab.com
  HostName gitlab.com
  HostkeyAlgorithms +ssh-rsa
  PubkeyAcceptedAlgorithms +ssh-rsa
  User git
  IdentityFile ~/.ssh/id_rsa_gitlab

Host github.com
  HostName github.com
  HostkeyAlgorithms +ssh-rsa
  PubkeyAcceptedAlgorithms +ssh-rsa
  User git
  IdentityFile ~/.ssh/id_rsa_github

Host stash.cmpn.corp
  HostName stash.cmpn.corp
  HostkeyAlgorithms +ssh-rsa
  PubkeyAcceptedAlgorithms +ssh-rsa
  User git
  IdentityFile ~/.ssh/id_rsa_cmpn
```

### Change commits date

More info: [link](https://stackoverflow.com/questions/454734/how-can-one-change-the-timestamp-of-an-old-commit-in-git)

To change the dates of the last 4 commits:

```
git rebase -i HEAD~4

```
Edit the rebase as follows, inserting exec lines to modify dates as needed:

```
pick 4ca564e Do something
exec git commit --amend --no-edit --date "1 Oct 2019 12:00:00 PDT"
pick 1670583 Add another thing
exec git commit --amend --no-edit --date "2 Oct 2019 12:00:00 PDT"
pick b54021c Add some tests
exec git commit --amend --no-edit --date "3 Oct 2019 12:00:00 PDT"
pick e8f6653 Fix the broken thing
exec git commit --amend --no-edit --date "4 Oct 2019 12:00:00 PDT"
```

If you want to see the original commit date in the rebase instruction list (Git 2.6+):
```
git config --add rebase.instructionFormat "[%ai] %s"
```