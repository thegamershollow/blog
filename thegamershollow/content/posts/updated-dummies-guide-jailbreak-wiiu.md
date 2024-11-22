---
title: "Dummies Guide Jailbreak The Wii U"
date: 2023-05-03T16:38:59Z
draft: true
tags: [Homebrew, Wii U, Guide, Tutorial, Python, Advanced, Walkthrough, Aroma, Wii U Homebrew, Wii Homebrew, vWii Homebrew, Development, Video Game, Jailbreak]
author: "TheGamersHollow"
---

## What You Need

- A Wii U with the latest firmware installed (**The Wii U can be from any region**)
- An SD card or microSD card with an adapter
- A computer to copy files to the SD card
- Python Development environment installed on your computer (Download URLS can be found [**HERE**](https://https://www.python.org/downloads/))
- The WiiU SD card setup tool downloaded on your computer (The latest version can be downloaded [**HERE**](https://github.com/thegamershollow/Wii-U-SD-Card-Setup-Tool/releases/latest))
- An internet connection setup on your Wii U

## Setting up The SD Card

Plug the SD card into your computer and format it to FAT-32 a guide on how to do that can be found [**HERE**](https://www.pcguide.com/how-to/format-sd-card-fat32/). After formatting the SD card rename it to something **other than wiiu** as it will not allow you to jailbreak your console if it is named wiiu.

## Getting The Files For The SD Card

To make the process of jailbreaking your console easier we have programmed a tool that is based in python.

navigate to where you downloaded the Wii U SD Card Setup Tool

### For Windows

If you are on Windows you will need to have Python (3.0 or above) installed and the required Python modules installed. To install the modules open Terminal/Command Prompt/Powershell navigate to the directory that the files are downloaded in and type the following

```console
C:\Users\dummy\> pip install -r requirements.txt
```

The Terminal/Command Prompt/Powershell should spit out something like this

```console
Collecting requests (from -r requirements.txt (line 1))
  Using cached requests-2.30.0-py3-none-any.whl (62 kB)
Collecting colorama (from -r requirements.txt (line 2))
  Using cached colorama-0.4.6-py2.py3-none-any.whl (25 kB)
Collecting pandas (from -r requirements.txt (line 3))
  Using cached pandas-2.0.1-cp311-cp311-macosx_11_0_arm64.whl (10.7 MB)
Collecting charset-normalizer<4,>=2 (from requests->-r requirements.txt (line 1))
  Using cached charset_normalizer-3.1.0-cp311-cp311-macosx_11_0_arm64.whl (121 kB)
Collecting idna<4,>=2.5 (from requests->-r requirements.txt (line 1))
  Using cached idna-3.4-py3-none-any.whl (61 kB)
Collecting urllib3<3,>=1.21.1 (from requests->-r requirements.txt (line 1))
  Downloading urllib3-2.0.2-py3-none-any.whl (123 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 123.2/123.2 kB 1.6 MB/s eta 0:00:00
Collecting certifi>=2017.4.17 (from requests->-r requirements.txt (line 1))
  Using cached certifi-2022.12.7-py3-none-any.whl (155 kB)
Collecting python-dateutil>=2.8.2 (from pandas->-r requirements.txt (line 3))
  Using cached python_dateutil-2.8.2-py2.py3-none-any.whl (247 kB)
Collecting pytz>=2020.1 (from pandas->-r requirements.txt (line 3))
  Using cached pytz-2023.3-py2.py3-none-any.whl (502 kB)
Collecting tzdata>=2022.1 (from pandas->-r requirements.txt (line 3))
  Using cached tzdata-2023.3-py2.py3-none-any.whl (341 kB)
Collecting numpy>=1.21.0 (from pandas->-r requirements.txt (line 3))
  Using cached numpy-1.24.3-cp311-cp311-macosx_11_0_arm64.whl (13.8 MB)
Collecting six>=1.5 (from python-dateutil>=2.8.2->pandas->-r requirements.txt (line 3))
  Using cached six-1.16.0-py2.py3-none-any.whl (11 kB)
Installing collected packages: pytz, urllib3, tzdata, six, numpy, idna, colorama, charset-normalizer, certifi, requests, python-dateutil, pandas
Successfully installed certifi-2022.12.7 charset-normalizer-3.1.0 colorama-0.4.6 idna-3.4 numpy-1.24.3 pandas-2.0.1 python-dateutil-2.8.2 pytz-2023.3 requests-2.30.0 six-1.16.0 tzdata-2023.3 urllib3-2.0.2
```

After you are done intalling the Python modules run the Python file by doing the following

```console
C:\Users\dummy\> python wiiu.py
```

When run in the Terminal/Command Prompt/Powershell should return this

```console
Please specify the path of your Wii U SD Card:
```

To specify the path of you Wii U's SD card drag the icon of the SD card from File Explorer into the Termina/Command Prompt/Powershell and hit ENTER. It should then show the selection screen for the tool. To move onto the next step click [HERE](/posts/updated-dummies-guide-jailbreak-wiiu/#using-the-tool)

### For UNIX/ MAC OS/ LINUX

For UNIX based systems (e.g: Mac OS, and Linux) the procces of setting up the tool is much easier. It does not require you to install any Python modules as they are already packaged into the executable of `wiiu`. **NOTE** *if you are running Mac OS it might make you enter the Admin password due to the executable being unsigned/unverifiable by the operating system.*

To open the program navigate to the folder it is located in with the Terminal/Shell, once located run this

```console
[user@computer]$ ./wiiu
```

You should now see a prompt

```console
Please specify the path of your Wii U SD Card:
```

To specify the path of you Wii U's SD card drag the icon of the SD card from File Explorer into the Terminal/Shell and hit ENTER. It should then show the selection screen for the tool. To move onto the next step click [HERE](/posts/updated-dummies-guide-jailbreak-wiiu/#starting-the-jailbreak)

## Starting the Jailbreak

After setting up the tool you should be greeted with a screen that looks like this

```console
Wii U SD Card Setup Tool
Type the number corrasponding to the option that you want to select.
1. Download/Update base SD Card files
2. Download/Update Wii U Homebrew Apps
3. Download/Update Files needed for vWii mod
4. Download/Update Wii Homebrew Apps
5. Remove all files from the Wii U SD Card
6. Use a Diffrent SD Card
7. Exit

Option: 
```

You are going to want to select option 1 for the base SD card files. Now you are going to want to make sure that all the files listed below are on you Wii U's SD card.

{{< collapse-menu menu="SD Card Layout" item="🗂️ wiiu<br>┣ 📂 apps<br>┃ ┣ 📂 Bloopair_pair_menu<br>┃ ┃ ┗ 📄 Bloopair_pair_menu.wuhb<br>┃ ┣ 📂 appstore<br>┃ ┃ ┣ 📂 .get<br>┃ ┃ ┃ ┣ 📂 packages<br>┃ ┃ ┃ ┃ ┗ 📁 appstore<br>┃ ┃ ┃ ┃ ┣ 📄 info.json<br>┃ ┃ ┃ ┃ ┗ 📄 manifest.install<br>┃ ┃ ┃ ┗ 📄 repos.json<br>┃ ┃ ┣ 📄 appstore.rpx<br>┃ ┃ ┣ 📄 appstore.wuhb<br>┃ ┃ ┣ 📄 background.mp3<br>┃ ┃ ┣ 📄 icon.png<br>┃ ┃ ┗ 📄 meta.xml<br>┃ ┣ 📂 nuspli<br>┃ ┃ ┗ 📄 NUSspli.wuhb<br>┃ ┗ 📄 AromaUpdater.wuhb<br>┣ 📂 environments<br>┃ ┗ 📁 aroma<br>┃ ┣ 📂 modules<br>┃ ┃ ┃ ┣ 📂 setup<br>┃ ┃ ┃ ┃ ┣ 📄 00_mocha.rpx<br>┃ ┃ ┃ ┃ ┣ 📄 10_wums_loader.rpx<br>┃ ┃ ┃ ┃ ┣ 📄 30_bloopair.rpx<br>┃ ┃ ┃ ┃ ┗ 📄 99_autoboot.rpx<br>┃ ┃ ┃ ┣ 📄 AromaBaseModule.wms<br>┃ ┃ ┃ ┣ 📄 CURLWrapperModule.wms<br>┃ ┃ ┃ ┣ 📄 ContentRedirectionModule.wms<br>┃ ┃ ┃ ┣ 📄 FunctionPatcherModule.wms<br>┃ ┃ ┃ ┣ 📄 KernelModule.wms<br>┃ ┃ ┃ ┣ 📄 MemoryMappingModule.wms<br>┃ ┃ ┃ ┣ 📄 NotificationModule.wms<br>┃ ┃ ┃ ┣ 📄 PatchMemoryRelocationsModule.wms<br>┃ ┃ ┃ ┣ 📄 PluginBackend.wms<br>┃ ┃ ┃ ┣ 📄 RPXLoadingModule.wms<br>┃ ┃ ┃ ┣ 📄 SDHotSwapModule.wms<br>┃ ┃ ┃ ┗ 📄 WUHBUtilsModule.wms<br>┃ ┣ 📂 plugins<br>┃ ┃ ┃ ┣ 📄 AromaBasePlugin.wps<br>┃ ┃ ┃ ┣ 📄 drc_region_free.wps<br>┃ ┃ ┃ ┣ 📄 ftpiiu.wps<br>┃ ┃ ┃ ┣ 📄 homebrew_on_menu.wps<br>┃ ┃ ┃ ┣ 📄 regionfree.wps<br>┃ ┃ ┃ ┣ 📄 screenshot.wps<br>┃ ┃ ┃ ┣ 📄 sdcafiine.wps<br>┃ ┃ ┃ ┣ 📄 swipswapme.wps<br>┃ ┃ ┃ ┗ 📄 wiiload.wps<br>┃ ┗ 📄 root.rpx<br>┣ 📂 payloads<br>┃ ┣ 📂 default<br>┃ ┃ ┗ 📄 payload.elf<br>┃ ┣ 📁 nanddumper<br>┃ ┃ ┗ 📄 payload.elf<br>┣ 📄 payload.elf<br>┗ 📄 payload.rpx<br>">}}

After verifying that the files are on the SD card eject the SD card from your computer and insert the SD card into the Wii U’s SD card slot. Now turn on your Wii U and open the internet browser and go to wiiuexploit.xyz then once on the page click `run homebrew launcher` and hold the `X` button until a screen says `Environment Loader` at the top. **If your Wii U freezes in the process, turn it off and delete your internet browser save data then try again.** Once on the `Environment Loader` screen, navigate to where it says `Installer` and press `A`. Then press `A` on `check`, and press `A` again on `Install/Update`. Your Wii U console will shutdown, turn it back on and open the `Health and Safety Guide` while holding X. This will open the `Environment Loader` press `A` on `Installer` again and press `A` on `check`, then press `A` on `Boot Options`. Now press `A` on `Switch to PayloadLoader`. This will allow you to automatically boot into the jailbreak whenever you turn on your Wii U. Your console will have to shutdown again, turn it back on. It will then boot into the `Environment Loader` menu, with the `d-pad` scroll down to `Aroma` and press `Y`, this will autoboot the `Aroma Environment` whenever you turn on your console or restart it. Now Press `A` on `Aroma` to launch into the environment.You will the be greeted with a menu titled `Boot Selector` press `Y` then `A`, you will now be redirected to the Wii U Menu, and have now succesfully jailbroken your Wii U and installed the Aroma Environment on it, you can now use Homebrew apps and install dumped discs/software onto your console.

If you would like to jailbreak the Virtual Wii to play WiiWare/Wii/Gamcube game backups follow this guide [**HERE**](/posts/dummies-guide-jailbreak-vwii)
