# SMAPI Example Mod

An extremely simple Stardew Valley SMAPI Mod written on Arch Linux from the CLI\
This mod is the same source as from the [Developer Tutorial](https://stardewvalleywiki.com/Modding:Modder_Guide/Get_Started)

I noticed that the SMAPI tutorial was pretty insufficient for Arch users so leaving a basic starting point with some instructions might help others.

ALWAYS default back to the SMAPI documentation. The instructions I've provided are a vague overview of what they provided with less GUI/IDE crap.

## Reproducing

1. install the pre-reqs as documented by the SMAPI guide
   1. Install openssl1.1
   2. install SMAPI into your Stardew install
   3. You don't need an IDE, the IDE is a lie. You can use the CLI and a text editor
   4. dotnet 5.0, there's an AUR package that I used for it called "[dotnet-sdk-5.0-bin](https://aur.archlinux.org/packages/dotnet-sdk-5.0-bin)"
      1. For non-arch users or if the AUR goes down, you should be able to download dotnet 5.0 as a tar, create a folder on your system, and export the DOTNET_ROOT variable as well as updating your path to use that folder. Basic OG linux /opt/ style installs will work.
2. setup development environment, run the following commands to setup a folder\
```sh
mkdir -p ~/Projects/ExampleMod
cd ~/Projects/ExampleMod
```
1. create the project template: `dotnet new classlib --framework net5.0`
2. install SMAPI nuget package into your project `dotnet add package Pathoschild.Stardew.ModBuildConfig --version 4.1.1` NOTE: you probably need a different version check [here](https://www.nuget.org/packages/Pathoschild.Stardew.ModBuildConfig)
3. copy template source from SMAPI Mod guide
4. add a manifest.json structured like so:
```json
{
  "Name": "<your project name>",
  "Author": "<your name>",
  "Version": "1.0.0",
  "Description": "<One or two sentences about the mod>",
  "UniqueID": "<your name>.<your project name>",
  "EntryDll": "<your project name>.dll",
  "MinimumApiVersion": "3.0.0",
  "UpdateKeys": []
}
```
1. build the project `dotnet build`

For me this built the project.\
I can modify files from text editors, and build from CLI, and builds are automatically installed in my local stardew valley Mod/ folder.

I hope this helps someone.
