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
- create new file in your Unity Editor / VSCodium and switch between them to trigger domain reload;
- save existing file with changes (like adding comment, etc.).

#### `dotnet-sdk` package

Make sure you have your `dotnet-sdk` package of optimal supported version (LTS or latest) installed systemwide. Here is [pacman dotnet-sdk package](archlinux.org/packages/extra/x86_64/dotnet-sdk/) for reference.

#### Setting up Unity development environment with VSCodium

Because of the licensing terms, default VSCode extensions for development on C# / Unity can't be used anymore. But there are ways to continue development with telemetry-free VSCodium. My extensions of choice are these:
- full C# support through [DotRush](https://github.com/JaneySprings/DotRush/tree/main);
- complete integration with Unity with [Antigravity Unity](https://github.com/billythekidz/UnityAntigravityIDE).

Below are list of steps to perform before starting development:
1. Install DotRush extension (already defined in VSIX Manager).
2. Install Antigravity Unity extension (already defined in VSIX Manager).
3. For <b>each</b> Unity project add next package form git (`Window -> Package Manager -> |+| -> Install package from git URL...`):
```zsh
https://github.com/billythekidz/UnityAntigravityIDE.git
```
4. Make sure VSCodium is set as your [default script editor](#set-vscodium-as-default-editor).
5. In case code suggestions, go-to actions and others don't work in VSCodium:
   1. Check your project files for [consistency](https://github.com/teef22/VSCodium_dotfiles/edit/main/README.md#regenerate-project-files-sln--csproj--etc).
   2. See Unity Antigravity's [troubleshooting section](https://github.com/billythekidz/UnityAntigravityIDE#intellisense-not-working--no-autocomplete-or-suggestions).

#### Setting up Unity Debugger
TODO: ...

## VSCode notes
1. Clone destination become ```~/.config/Code/User/```.
2. Consider changing paths in the `.../User/settings.json` and probably other files.
3. To develop with Unity, packages like [.NET Install Tool](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.vscode-dotnet-runtime), [C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp), [C# Dev Kit](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csdevkit), [Unity](https://marketplace.visualstudio.com/items?itemName=VisualStudioToolsForUnity.vstuc) are more than enough to begin.
