## Setup guide

### VSCodium
Put this repo to `~/.config/VSCodium/User/`.

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

### VSCode notes
1. Clone destination become ```~/.config/Code/User/```.
2. Consider changing paths in the `.../User/settings.json` and probably other files.
3. Also make sure to use ```code``` executable instead of ```codium``` when using shell snippets above.
