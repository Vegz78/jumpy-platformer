## MakeCode Arcade games in RetroPie
![alt text](https://github.com/Vegz78/jumpy-platformer-ELF-test/blob/master/assets/MakeCode_Arcade_RetroPie.gif)
## Download natively executable MakeCode Arcade games on the Raspberry Pi
Dowload [the precompiled ELF game file above](https://github.com/Vegz78/jumpy-platformer-ELF-test/raw/master/arcade-jumpy-platformer.elf), or compile and download it yourself in your own browser here:
https://arcade.makecode.com/#pub:75452-06863-77183-79875?hw=rpi&compile=rawELF

Or, for any other MakeCode Arcade game that you have made or found, open it up in the online editor and add <nobr>```?hw=rpi&compile=rawELF```</nobr> to the end of the URL in the editor, so it looks like this:<BR>
```https://arcade.makecode.com/#editor?hw=rpi&compile=rawELF```<BR>
Press enter, let the page reload and then press the orange downlad button on the bottom left of the screen to download your game ELF executable file.

Execute from the Linux text console with command ```./arcade-jumpy-platformer.elf```, **not inside an X Window environment**. Make sure its's executable first(```chmod +x```).

## NB! MakeCode Arcade games ELF executables freeze on exit
This is a minor bug which prevents the running of the MakeCode Arcade games on the Raspberry Pi as ELF executables from being as smooth as it could be, with for instance full integration of MakeCode Arcade games in RetroPie, only using a gamepad etc. 

[Microsoft is currently looking for takers on trying to diagnose this](https://forum.makecode.com/t/how-to-launch-makecode-arcade-uf2s-in-raspbian-retropie/2725/22) and we can only hope that the skilled, but ever busy, MakeCode team will get a chance to address this issue some time in the future:
https://github.com/microsoft/pxt-arcade/issues/2435

**Any help on solving or speeding up the solution for this issue from the community is greatly appreciated!**

<BR>I just found a temporary work-around by pressing a combination of ```CTRL+C```, ```CTRL-D``` and ```CTRL-C``` on the keyboard to log out from and reset the console, and thereby killing the game and returning control of the screen and keyboard to a new console without having to reboot. 

<BR>**Error descriptions:**<BR>
From console (a little different with ```exec ./arcade-jumpy-platformer.elf```, but basically the same):<BR>
-Pressing ```BTN_EXIT``` OR ```CTRL-C``` freezes console keyboard and display in-game.<BR>
(Running game processes is orphaned during startup and hard to kill. You can ssh and kill parent bash process or using the ```CTRL+C```, ```CTRL-D``` and ```CTRL-C``` combination,  or run it like this: ```./gamefile.elf; killall -9 bash```)<BR><BR>
From RetroPie:<BR>
-Pressing ```BTN_EXIT```returns control to RetroPie, but game with frozen keyboard and display in-game in background.<BR>
-Pressing ```BTN_RESET``` OR ```CTRL-C``` returns control to RetroPie, with game still running in the background.<BR>

## Getting controller or keyboard to work
Make a folder and and file /sd/arcade.cfg with the following contents(for keyboard):
```
SCAN_CODES=/dev/input/event0
BTN_LEFT=105
BTN_RIGHT=106
BTN_UP=103
BTN_DOWN=108
BTN_A=30
BTN_B=44
BTN_RESET=16
BTN_EXIT=17
BTN_MENU=18
```

Double check by running ```evtest``` which /dev/input/event# number your keyboard is connected to. If not #0, edit the first line to the correct number.

For a game pad, it's the same procedure, where you have to have the game pad's event number in the first line and using the correct key codes from ```evtest``` for the controller buttons you want to bind in arcade.cfg.





## Blocks preview

This image shows the blocks code from the last commit in master.
This image may take a few minutes to refresh.

![A rendered view of the blocks](https://github.com/vegz78/jumpy-platformer/raw/master/.github/makecode/blocks.png)

#### Metadata (used for search, rendering)

* for PXT/arcade
<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
