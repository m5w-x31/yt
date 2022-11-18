(2022.11.19)

# Ubuntu Server connect from Vscode Remote SSH

## Environment

### Server

- Ubutntu 22.04 Server
  - local IP: 192.168.0.100
  - user: m5w

### Client

- Visual Studio Code (macOS Ventura)

---

## Console SSH connect

- vscode terminal (zsh)

```
% ssh m5w@192.168.0.100
```

## setup SSH key

- secret key: "u22_rsa"
- public key: "u22_rsa.pub"

```
% ssh-keygen

% ssh-copy-id -i ~/.ssh/u22_rsa.pub" m5w@192.168.0.100
```

## setup SSH config

```
% vi ~/.ssh/config
---
Host u22
  Hostname 192.168.0.100
  User m5w
  IdentityFile ~/.ssh/u22_rsa
  TCPKeepAlive yes
```

- ssh connect test

```
% ssh u22
```

## Vscode Remote SSH connect

- extension: Remote - SSH : https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh

