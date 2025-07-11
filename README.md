# Oh My Posh configuration

## Table of Contents

- [Installation](#installation)
- [Fonts](#fonts)
- [PowerShell configuration file](#powershell-configuration-file)
- [Using prepared themes and configuration](#using-prepared-themes-and-configuration)
- [Miscellaneous](#miscellaneous)
    - [Terminal Icons](#terminal-icons)
    - [PSReadLine Module](#psreadline-module)
    - [Console history file](#console-history-file)
    - ["Z" - replacement of standard 'cd' command](#z---replacement-of-standard-cd-command)

For a complete guide, visit https://ohmyposh.dev/
You can also visit Scott Hanselman's blog and read about his setup:
https://www.hanselman.com/blog/my-ultimate-powershell-prompt-with-oh-my-posh-and-the-windows-terminal
or view introductory tutorial on YouTube, when he walks you through the process
https://www.youtube.com/watch?v=VT2L1SXFq9U&list=WL&index=26&t=2722s&ab_channel=ScottHanselman

## Installation

```pwsh
winget install JanDeDobbeleer.OhMyPosh -s winget
```

After installing, the oh-my-posh path should be added to the environment variables

With the installation, some base themes will already be available. However, I prefer to use my own theme available in the '/themes' folder called 'jyk.omp.json'

## Fonts

There are some special fonts prepared for use with oh-my-posh. They contain additional glyphs and icons that are used by it. You can find them on the Nerd Fonts page: https://www.nerdfonts.com/
My recommendations are:
- [JetBrainsMono Nerd Font](https://github.com/ryanoasis/nerd-fonts/releases/download/v3.4.0/JetBrainsMono.zip)
- [CaskaydiaCove Nerd Font](https://github.com/ryanoasis/nerd-fonts/releases/download/v3.4.0/CascadiaCode.zip)
- [CaskaydiaMono Nerd Font](https://github.com/ryanoasis/nerd-fonts/releases/download/v3.4.0/CascadiaMono.zip)

You need to extract them and copy them to Windows 'font' folder, or right click and select 'install font'.

## PowersShell configuration file

```pwsh
New-Item -Path $PROFILE -Type File -Force
```

To open just created PowerShell configuration file, use

```pwsh
notepad $PROFILE
```

Each time this configuration is edited you should reload it by using

```pwsh
. $PROFILE
```

## Using prepared themes and configuration.

In 'PowerShthe ell_config' folder, there is already a prepared PowerShell configuration file that I prefer (and recommend) to use:

```
Microsoft.PowerShell_profile_jyk_v2.ps1
```

It not only will start oh-my-posh each time PowerShell is opened, but also contains some useful scripts, allowing e.g. see history of 10 recent commands.
Some of those scripts might need the installation of additional modules. More on that in [**Miscellaneos**](#miscellaneous) section below.

## Miscellaneous

### Terminal Icons

Extending the look of files and folders when listing files and directories (dir, ls commands).

First, we need to install 'Terminal Icons'

```pwsh
Install-Module -Name Terminal-Icons -Repository PSGallery
```

Then we need to add this line to the PowerShell configuration file

```pwsh
Import-Module -Name Terminal-Icons
```

**IMPORTANT**: The configuration file mentioned before has this already included.

More information about 'Terminal Icons' and setup can be found here:
https://www.hanselman.com/blog/take-your-windows-terminal-and-powershell-to-the-next-level-with-terminal-icons

### PSReadLine Module

This module is needed if you want to use some scripts provided in the attached PowerShell configuration files.
To install, run this command:

```pwsh
Install-Module PSReadLine -Repository PSGallery
```

### Console history file

All commands run in the PowerShell console are stored in the file 'ConsoleHost_history.txt' located in

```pwsh
cd $ENV:USERPROFILE\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadline
```

### "Z" - replacement of standard 'cd' command

You can read more about this on Scott Hanselman's blog post here:
https://www.hanselman.com/blog/spend-less-time-cding-around-directories-with-the-powershell-z-shortcut

This powerful command for PowerShell lets you speed up moving around the directories.

You can install "Z" by running this command:

```pwsh
Install-Module z -AllowClobber
```

After that, you will need to add an import to the PowerShell configuration file:

```pwsh
Import-Module z
```