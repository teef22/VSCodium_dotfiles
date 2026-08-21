## Setup guide
Put this repo to `~/.config/VSCodium/User/` for VSCodium and to `~/.config/Code/User/` for VSCode. Remember to change paths in the `.../User/settings.json` (and probably other files) depending on wether you use VSCodium or VSCode.

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
