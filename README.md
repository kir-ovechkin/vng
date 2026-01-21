# vng
Visual Novell Game supply

## Presquisites

Install [Brew](https://brew.sh/)

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Install `rsync`

```bash
brew install rsync
```

## Release

Download current version (to Game folder on Desktop)

```bash
rsync -avz --rsync-path="sudo rsync" roarstreet-quest.com:/var/www/roarstreet ~/Desktop/Game
```

```bash
ssh roarstreet-quest.com "sudo cp -a /var/www/roarstreet /var/www/roarstreet_$(date +%Y-%m-%d_%H-%M-%S)
```
