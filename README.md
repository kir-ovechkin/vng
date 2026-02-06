# vng
Visual Novell Game supply

## Presquisites

### MacOS

Install [Brew](https://brew.sh/)

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Install `rsync`

```bash
brew install rsync
```

### Windows

Install [choco](https://chocolatey.org/install)

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force;
[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072;
iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

Install `rsync` and `openssh`

```powershel
choco install rsync openssh -y
```

### Both – generate ssh-key

```
ssh-keygen -t ed25519 -a 100
cat ~/.ssh/id_ed25519.pub
```

## Release

Download current version (to Game folder on Desktop)

```bash
rsync -avz \
  roarstreet-quest.com:/var/www/roarstreet ~/Desktop/Game
```

Make a backup copy

```bash
ssh roarstreet-quest.com \
  "cp -a /var/www/roarstreet /var/www/roarstreet_$(date +%Y-%m-%d_%H-%M-%S)"
```

Release new version

```bash
rsync -avz --delete \
  ~/Desktop/Game/roarstreet/ \
  roarstreet-quest.com:/var/www/roarstreet/
```
