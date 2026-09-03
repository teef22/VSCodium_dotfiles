# Setup guide

## VSCodium
Put this repo to `~/.config/VSCodium/User/`.

### Extensions
Extensions are managed via [VSIX Manager](https://github.com/zokugun/vscode-vsix-manager). Any changes to entries should be written to `vsix.extensions` array in a `settings.json` file, then `VSIX Manager: Synchronize extensions` command should be run in VSCodium.

Alternative way to fast saving / installing the list of used extensions is by using shell snippets below:
- for saving the extension list to `extensions.txt`:
```zsh
codium --list-extensions > extensions.txt
```

- for installing extensions from the list in `extensions.txt`:
```zsh
while read extension; do
    codium --install-extension "$extension"
done < extensions.txt
```

## VSCode notes
1. Clone destination become ```~/.config/Code/User/```.
2. Consider changing paths in the `.../User/settings.json` and probably other files.
3. Also make sure to use ```code``` executable instead of ```codium``` when using shell snippets above.
