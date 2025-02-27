---
layout: default
title: Windows Installation
parent: Installation
nav_order: 2
---

# Windows Installation Instructions

As of version 0.3.1, an URBANopt<sup>&trade;</sup> installer (64-bit Windows 7 – 10) is available to install the URBANopt CLI, Ruby, and OpenStudio SDK at the same time.  If you'd rather install the dependencies manually, view the [manual install](#manual-install) section below.

For CLI usage examples, see our [Getting Started page](../getting_started/getting_started.md)

We also have [tutorial videos](../resources/tutorials/tutorials.md) available to guide you through the installation steps.

## Install with the URBANopt installer

Follow the steps below or watch the [Windows Installer Video](https://urbanopt-tutorial.s3.amazonaws.com/videos/01_Windows_Installer.mp4).


1. Download the desired version of the [.exe installer](http://urbanopt-cli-installers.s3-website-us-west-2.amazonaws.com/).

1. Use the GUI installer and choose a directory to install. Once installed, open a  terminal and run the provided setup script for that shell (below are the setup scripts for each respective shell environment).

**Note: GitBash is recommended** If you are unfamiliar with git or GitBash, you can check out this [video tutorial](https://www.youtube.com/watch?v=iGutIN5t9Mo).

**GitBash**
```terminal
/c/urbanopt-cli-X.X.X/setup-env.sh
. ~/.env_uo.sh
```

**Powershell**
```terminal
c:\urbanopt-cli-X.X.X\setup-env.ps1
. ~\.env_uo.ps1
```

**Windows Command Prompt**
```terminal
c:\urbanopt-cli-X.X.X\setup-env.bat
%HOMEPATH%\.env_uo.bat
```



<span class="label label-red">Important Note</span> Each time you want to work on URBAnopt and you open a new terminal to do so, you will need to run the `env_uo` script to configure your terminal session environment:

**GitBash**
```terminal
. ~/.env_uo.sh
```

**Powershell**
```terminal
. ~\.env_uo.ps1
```

**Windows Command Prompt**
```terminal
%HOMEPATH%\.env_uo.bat
```

## Manual Install

Follow the steps below or watch the [Windows Manual Installation Video](https://urbanopt-tutorial.s3.amazonaws.com/videos/03_Windows_Manual_Install.mp4).

1. Install [Ruby 2.7.2 (x64) with DevKit](https://github.com/oneclick/rubyinstaller2/releases/download/RubyInstaller-2.7.2-1/rubyinstaller-devkit-2.7.2-1-x64.exe)

	Make sure that you select option 3: **MSYS2 and MINGW development toolchain** during the installation process:
	![installer options](../doc_files/ruby_windows.png)

1. Include path to Ruby by adding the following to your environment variables path:

	`C:\Ruby27-x64\bin`
1. Create a new environment variable `HOME` and set the variable value to the following:

	`C:\Users\<user_name>`

	Detailed instructions for [creating environment variables](https://helpdeskgeek.com/how-to/create-custom-environment-variables-in-windows/) can be found online.
1. Install Bundler version 2.1:

	```terminal
	gem install bundler -v 2.1
	```

1. Install [OpenStudio 3.4.0](https://github.com/NREL/OpenStudio/releases/tag/v3.4.0)

1. Create file `C:\ruby-2.7.2-1-x64-mingw32\lib\ruby\site_ruby\openstudio.rb` and edit it to contain the path to your installed OpenStudio (where X.X.X is the OpenStudio version installed):

	```ruby
	require 'C:\openstudio-X.X.X\Ruby\openstudio.rb'
	```

1. Verify your OpenStudio and Ruby configuration:

	```terminal
	ruby -e "require 'openstudio'" -e "puts OpenStudio::Model::Model.new"
	```

	Expected output:

	```terminal
	OS:Version,
	 {<long-uuid>},                          !- Handle
	 3.1.0;                                  !- Version Identifier`
	 ```

1. Install the URBANopt Command Line Interface (CLI). This should not take longer than a few minutes. Visit the [known issues](../developer_resources/known_issues.md) page if the installation stalls.

    ```terminal
    gem install urbanopt-cli
    ```

## URBANopt CLI Usage

1. View available CLI commands with:

    ```terminal
    uo --help
    ```

1. For detailed instructions, see the [Getting Started page](../getting_started/getting_started.md).

## OpenDSS and DiTTo Reader Installation

As of version 0.4.0, the URBANopt CLI includes DiTTo/OpenDSS support.  Since this functionality is implemented in Python, a different set of dependencies must be installed in order to use it.

If you'd like to use this functionality, follow the [OpenDSS installation](./ditto_reader.md) instructions.

Note that Windows users may experience some difficulty during the install (particularly with the environment variable setup).  If you are not able to access the opendss command via the CLI, you can always access it manually by following the general [OpenDSS instructions](../workflows/opendss/opendss.md#converting-and-running-opendss).

## DES Installation

As of version 0.5.2, the URBANopt CLI includes DES support.  This functionality is implemented in Python and Modelica requires that various dependencies be installed before use.

Follow the [DES Installation Instructions](./des_installation.md) to install these dependencies.
