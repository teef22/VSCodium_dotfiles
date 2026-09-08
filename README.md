# Setup guide

## VSCodium
Put this repo to `~/.config/VSCodium/User/`.

### Extensions
Extensions are managed via [VSIX Manager](https://github.com/zokugun/vscode-vsix-manager). Any changes to entries should be written to `vsix.extensions` array in a `settings.json` file, then `VSIX Manager: Synchronize extensions` command should be run in VSCodium.

#### First time setup
When clean-installing VSCodium on your system:
1. Install [VSIX Manager](https://open-vsx.org/extension/zokugun/vsix-manager) extension from default marketplace of VSCodium ([Open VSIX Registry](https://open-vsx.org)).
    1. (for ArchLinux-based distros) Install [vscodium-bin-marketplace](https://aur.archlinux.org/packages/vscodium-bin-marketplace) package from AUR, which allows access to [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/vscode) from VSCodium. Though VSIX Manager allows equal access to all extensions from any defined marketplaces, repos, etc., MS Marketplace on VSCodium works more reliable than its web service.
2. Check wether all needed extensions are defined in `vsix.extensions` array in `settings.json` file.
3. Run `VSIX Manager: Synchronize extensions` command in VSCodium to sync your extensions.

### Unity development

Here are a few tips for Unity development with VSCodium.

#### Set default editor

Do not set VSCodium as your default editor directly, otherwise you lose Unity Editor's ability to [regenerate project files](https://github.com/teef22/VSCodium_dotfiles/edit/main/README.md#regenerate-project-files). On the contrary, create symlink named `code` to your VSCodium executable by running this in your terminal:
```zsh
sudo ln -s $(which codium) /usr/local/bin/code
```
Then choose `/usr/local/bin/code` as your editor of choice in the `Preferences -> External tools -> External Script Editor`.

#### Open C# project in VSCodium

The easy way to open your project in VSCodium from Unity is by `Assets -> Open C# Project`.

#### Regenerate project files

Sometimes you got your project files corrupted somehow or you don't get them after cloning Unity project repo. To fix that follow these steps:
1. Using your terminal create symlink named `code` to your VSCodium executable (`codium`) by running this:
    ```zsh
    sudo ln -s $(which codium) /usr/local/bin/code
    ```
    Do this to [trick](https://discussions.unity.com/t/missing-generate-all-csproj-files-in-unity-2020-3/247892/7) Unity Editor into thinking you are using an officially [supported distribution](https://docs.unity3d.com/Manual/preferences-external-tools.html#:~:text=Unity%20has%20built%2Din%20support%20for%20Visual%20Studio%20Community%2C%20Visual%20Studio%20Code%20%28VSCode%29%20and%20JetBrains%20Rider%2E) of VSCode.
2. Inside Unity Editor go to `Preferences -> External tools`. For `External Script Editor` choose your newly created symlink `/usr/local/bin/code` using internal explorer. Section `Generate .csproj files` should appear now.
3. Ensure you have checked `Embedded packages` and `Local packages` inside section `Generate .csproj files`.
4. Press `Regenerate project files` button.

#### `dotnet-sdk` package

Make sure you have your `dotnet-sdk` package of optimal supported version (LTS or latest) installed systemwide. Here is [pacman dotnet-sdk package](archlinux.org/packages/extra/x86_64/dotnet-sdk/) for reference.

#### Setting up Unity development environment with VSCodium

Because of the licensing terms, default VSCode extensions for development on C# / Unity can't be used anymore. But there are ways to continue development with telemetry-free VSCodium. My extensions of choice are these:
- full C# support, including Unity debugger, through [DotRush](https://github.com/JaneySprings/DotRush/tree/main);
- useful Unity code snippets with [Unity Code Snippets](https://marketplace.visualstudio.com/items?itemName=kleber-swf.unity-code-snippets) extension.

Below are list of steps to perform before starting development:
1. Install DotRush extension (already defined in VSIX Manager).
2. Install Unity Code Snippets extension (already defined in VSIX Manager).
3. Make sure VSCodium is set as your [default script editor](#set-vscodium-as-default-editor).
4. In case code suggestions, go-to actions and similar functions don't work in VSCodium, it may help to check your project files for [consistency](https://github.com/teef22/VSCodium_dotfiles/edit/main/README.md#regenerate-project-files).

#### Unity debugger

DotRush extension provides Unity debugger functionality through [integrated Mono Debugger](https://github.com/JaneySprings/DotRush/tree/main#debugging-unity-projects). Works out of the box.

Quick reminders on Unity debugging:
1. Make sure the opened folder in VSCodium is the root one of your Unity project (contains `Assets/` directory and others).
2. Don't forget to create [`launch.json`](https://code.visualstudio.com/docs/debugtest/debugging-configuration) file (e.g. by using functionality of Debug sidebar `create launch.json file`).
3. Ensure Unity Editor is in Play Mode.

### .NET development

Besides [DotRush](https://github.com/JaneySprings/DotRush/tree/main) extension, there are a few worth checking for general .NET development:
1. [C#](https://github.com/muhammadsammy/free-vscode-csharp) - popular extension on Open VSIX with solid C# support.
2. [C# Dev Tools](https://github.com/jakubkozera/vsc-csharp-dev-tools) - promising extension featuring full C# support.

## VSCode notes
1. Clone destination becomes ```~/.config/Code/User/```.
2. Consider changing paths in the `.../User/settings.json` and probably other files.
3. To develop with Unity, packages like [.NET Install Tool](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.vscode-dotnet-runtime), [C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp), [C# Dev Kit](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csdevkit), [Unity](https://marketplace.visualstudio.com/items?itemName=VisualStudioToolsForUnity.vstuc) are more than enough to begin.
