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