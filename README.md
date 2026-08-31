## Setup guide

### VSCodium
Put this repo to `~/.config/VSCodium/User/`. Remember to change paths in the `.../User/settings.json` (and probably other files) depending on wether you use VSCodium or VSCode.

To install extensions from `extensions.txt` run:
```zsh
while read extension; do
    codium --install-extension "$extension"
done < extensions.txt
```
After adding / removing new extension, you can save updated list by running:
```zsh
codium --list-extensions > extensions.txt
```

### VSCode
Put this repo to `~/.config/Code/User/` for VSCode. Paths used in `.../User/settings.json` must be changed depending on wether you use VSCodium or VSCode.

To install extensions from `extensions.txt` run:
```zsh
while read extension; do
    code --install-extension "$extension"
done < extensions.txt
```
After adding / removing new extension, you can save updated list by running:
```zsh
code --list-extensions > extensions.txt
```
