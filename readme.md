# WakaTime Plugin for Delphi

A plugin implementation for integrating [WakaTime](https://wakatime.com) to track your time activity programming with Delphi IDE's.

Any help is appreciated! Comments, suggestions, issues, PR's! Give us a star to help!

## Goals

The goal of this project is to provide a full integration with WakaTime with Delphi IDE's as other implementations for currently supported IDE's like Visual Studio Code, JetBrains Rider, Android Studio, etc.

## Currently supported and Tested IDE's

- Delphi 12.0
- Delphi 11.3
- Delphi 10.0
- Delphi 10.2
- Delphi XE2
- Delphi 7

> It should work with any other IDE version up from D7 but it should be tested. If you have any other version and want to collaborate just go to the section **Adding to new IDE**. 

## Support this plugin's author ([@diegomgarcia](https://github.com/diegomgarcia)) with Patreon

[![Patreon](https://c5.patreon.com/external/logo/become_a_patron_button.png)](https://www.patreon.com/dmgarcia)

Or make a single donation buying me a coffee:

[![Buy Me A Coffee](https://user-images.githubusercontent.com/835641/60540201-fcd7fa00-9ce4-11e9-87ec-1e98568e9f58.png)](https://www.buymeacoffee.com/dmgarcia)

You can also show support by showing on your repository that you use this lib on it with a direct link to it.

## How should I use it?

1- Clone this repository.

2- Open the project related to your IDE version: 

- WakaTimePlugin12_0.dproj - For Delphi 12.0 and Delphi 12.1
- WakaTimePlugin11_3.dproj - For Delphi 11.3
- WakaTimePlugin10.dproj   - For Delphi 10.0
- WakaTimePlugin10_2.dproj - For Delphi 10.2
- WakaTimePluginXE2.dproj  - For Delphi XE2 
- WakaTimePluginD7.dpr     - For Delphi 7

> Note: If your IDE is not listed here, don't be afraid, just go to the section **Adding to new IDE** and get back here after to continue.

3- Build and Install

4- Close the project

5- Go to the **Tools** menu and access the new **WakaTime Settings** menu.

6- Insert your WakaTime API key and hit OK.

**Tip** To get your WakaTime API Key, go to your WakaTime account, click on your avatar on settings and you will see a section named API Key with the text Secret API Key and a button to copy, just click on copy button and paste it on the settings of the plugin. You can also find it by going to [this link](https://wakatime.com/settings/api-key).

>If you use GetIt Package Manager, this package can be installed from there.

## Adding to new IDE

If your IDE does not have a package created for it yet, no worries just do the following steps:

Before start close all projects opened on your Delphi IDE.

1- On your Delphi IDE go to the File -> New -> Package. 

2- With the new Package created save the project inside the plugin directory with the name WakaTimePlugin{YourDelphiVersion}.

3- Right click on the project file and select the option Add... after that select all .pas files inside the plugin folder and hit the Open button. This will add all the files to this new package. 

4- Right click on the Requires section of the package and click on the option Add Reference, click on the Browse button, and go to the directory "C:\Program Files (x86)\Embarcadero\Studio\\**{YourDelphiVersion}**\lib\win32\release" and select the file designide.dcp then click on ok and ok again to add it to the package.

5- Now just save again and build your new plugin project, the IDE might ask to add a reference to RTL, just click on ok and continue the build.

6- Install the package on IDE and get back to step 3 of the section **How should I use?**

> Note: Don't forget, after you test the plugin with your new IDE you can make a PR here so we can update the supported IDE list.


## Know Issues

1- Before removing the package close all files on the editor, or you will get an invalid pointer operation. For some reason removing the reference on package removal with the files opened on the editor is trying to remove the reference more than one time, causing this error. I'm investigating the root cause.

2- On Delphi 7 sometimes after compiling and clicking on install the IDE hangs and closes, just open the IDE again and add the BPL using the menu -> component -> install packages -> add -> select the BPL's compiled inside the path: C:\Program Files\Borland\Projects\Bpl\WakatimeD7.bpl

3- If for some reason you note that your wakatime plugin is not working take a look at the logs of the auto installation at the .wakatime directory on your user's profile path, something like that: C:\Users\diego.garcia\.wakatime\install.log also certify that your windows have PowerShell installed on it as the auto-install/update relies on it.

## Manual installation 

1- Create a directory named **.wakatime** on your current user profile directory "C:\Users\diego.garcia\\.wakatime"

2- Download the wakatime-cli for Windows from the wakatime-cli github direct link [here](https://github.com/wakatime/wakatime-cli/releases/download/v1.73.1/wakatime-cli-windows-386.zip) 

3- Extract into the **.wakatime** directory and rename the file to **wakatime-cli.exe**

## Possible Improvements

1- Add support to IOTAFormNotifier and send the heartbeat on form save or changed. It doesn't affect anything now but I have to test it to see if it is worth implementing it.

2- Add an inno setup installer to simplify the process of installing. 

3- Add to some package manager?
