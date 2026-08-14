## Setup guide
Put this repo to `~/.config/VSCodium/User`.

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
