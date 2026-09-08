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

#### Set VSCodium as default editor

Do not forget to set VSCodium as your editor of choice. To do this, in Unity Editor go to `Edit -> Preferences -> External Tools` and choose `External Script Editor` either in dropdown menu, or manually using explorer. Also set `External Script Editor Args` to `$(File)`.

#### Open C# project in VSCodium

The easy way to open your project in VSCodium from Unity is by `Assets -> Open C# Project`.

#### Regenerate project files (.sln / .csproj / etc.)

In case you got project files corrupted somehow or you didn't get them after cloning Unity project repo, try one of these to triger regeneration of those files:
- create new file in your Unity Editor to trigger domain reload;
- delete newly created file in your Unity Editor to trigger domain reload;
- save existing file with changes (like adding comment, etc.).

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
4. In case code suggestions, go-to actions and similar functions don't work in VSCodium, it may help to check your project files for [consistency](https://github.com/teef22/VSCodium_dotfiles/edit/main/README.md#regenerate-project-files-sln--csproj--etc).

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
