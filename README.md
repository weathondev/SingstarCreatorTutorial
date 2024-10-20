# Singstar Creator - Tutorial

I wanted to create custom PS2 Singstar DVDs for a long time, as i think that all the Ultrastar versions that are out there, Sing It, newer Singstar versions etc. are crap.
PS2s Singstar is the origin, the one and only.
Below there are the steps described on how to do it yourself - in theory it's not required to have any previous knowledge, but IT/PC knowledge itself will certainly help when running into errors.
The setup how custom games will run is the following:
 - **uLaunchELF/FreeDVDBoot** is booted by the burned DVD
 - **OPL** is started from the USB stick via **uLaunchELF**
 - **OPL** connects to your computer via the network cable, and accesses your shared network drive which contain the **.iso** game files (aka Singstar DVDs)

# Setup your PS2 to run CTurts FreeDVDBoot exploit

In case you don't have a modded PS2 lieing around, this is the easiest way to set it up to run custom games.
See [`FreeDVDBoots Github`](https://github.com/CTurt/FreeDVDBoot)
In case this github page will ever go down, i copied the parts i used here, if the github page is up, please refer to it as it contains troubleshooting tips, setup instructions for the fat PS2 etc.

## Easy setup for all PS2 Slim consoles

All you need is:

- A compatible console (all PS2 Slim / Sony Bravia TV units are supported),
- A DVD (not a CD), preferably a DVD-R as other types such as DVD+RW put more strain on the PS2 laser,
- A computer with a built-in disc burner / external USB disc burner,

### Step 1: Download the ISO
Download [`PREBUILT ISOs/All PS2 Slims - English language.iso`](https://github.com/weathondev/SingstarCreatorTutorial/raw/main/All%20PS2%20Slims%20-%20English%20language.iso)

### Step 2: Burn the ISO
Please check following to ensure a good burn which the PS2 will be able to read:

- Clean off any dust from the disc,
- Select lowest burning speed option,
- Select finalise disc option (down by default by ImgBurn e.g.),

### Step 3: Set console language to English
Your console must be set to **English language** for the exploit to work (other languages cause memory contents to change).

To do this, boot without a disc inserted, press **Circle** to enter **System Configuration** and set your system language to **English**.

### Step 4: Boot!
Insert the disc into your console, and wait. It should boot into **uLaunchELF** within a few seconds.
From **uLaunchELF**, you have the ability to run any homebrew you want over USB **mass** storage!
This leads us to the next step - running **OPL** via **uLaunchElf**

# Setup OPL on your PS2

See the [`ps2-home thread`](https://www.ps2-home.com/forum/viewtopic.php?f=50&t=3692) I used. The specific steps I took i describe below.
Download OPL from here: [`OPL Project - v1.1.0 [Official Release]`](https://www.ps2-home.com/forum/viewtopic.php?t=11576), alternatively you can use the [`version I used`](https://github.com/weathondev/SingstarCreatorTutorial/raw/main/OPNPS2LD-v1.1.0-ifcaro_all-1791-5db29c2-2021-09-09.zip).
Take the oldest, smallest and slowest USB drive you can find (PS2 has USB 1.1 so that limits the speed anyway), format it with FAT32 and copy the **OPNPS2LD.ELF** file on it.
Copy the three config files on it, make sure to adjust them to your own needs (specifically the network one):
[`conf_game.cfg`](https://github.com/weathondev/SingstarCreatorTutorial/blob/main/conf_game.cfg) global game settings to mainly disable pademu
[`conf_opl.cfg`](https://github.com/weathondev/SingstarCreatorTutorial/blob/main/conf_opl.cfg) mainly to view network games by default
[`conf_network.cfg`](https://github.com/weathondev/SingstarCreatorTutorial/blob/main/conf_network.cfg) IP settings for PS2 and to point to the PC with samba shared folder

# Setup Samba shared folder on your Computer

Why not just USB? While it might be slower, which probably would be unnoticable for Singstar (except for initial loading time, roughly 1/3 slower), it can't work for Singstar as OPL can only use one USB drive at once, which means that when you boot the game via network, it will work as it will switch from USB drive to microphones, but when you boot it via USB it needs the connection to the USB drive and can't connect to the microphones.
- Activate **SMB 1.0/CIFS File Sharing Support** via **activate/deactivate windows features dialog**.
- No need to do any IP changes, a typical router setup will just give your PC a reserved IP address which won't change, same for your PS2
- Create a folder on your C drive e.g. **PS2SMB** and put your Singstar.iso files (see below) there
- Create a local User account on your PC e.g. **guest** with password **guest**
- Share the **PS2SMB** folder via **advanced sharing**, make sure you give read & write rights to **guest**
- Make sure your PC is turned on when you want to play Singstar & make sure it's in the same network as your PS2

# Download Singstar Creator

Unfortunately all the links from the [`Official website`](https://singstar-creator.de.tl/) are down, therefore I uploaded a mirror [`here`](https://github.com/weathondev/SingstarCreatorTutorial/releases/download/SingstarCreatorV3/SC+3.0.zip).
The program is in german, but there are not many things that need to be done it in anyway. Nevertheless, dekkit from ps2-home created an images with the english texts:
[`Main`](https://github.com/weathondev/SingstarCreatorTutorial/raw/main/MainPage_english.png)
[`ContextMenu`](https://github.com/weathondev/SingstarCreatorTutorial/raw/main/ContextMenu_english.png)
The program expects as an input, an Ultrastar txt file (lyrics & mappings), a music file, a video file and a cover image. All of this is provided when you download songs from the [`spanish Ultrastar webpage`](https://ultrastar-es.org/en), if they don't have all the songs you want you can also check out the [`german one`](http://usdb.animux.de/) but they only provide the txt files. The easiest/quickest way to get the media files is by downloading from Youtube (Jdownloader2 is a really big help here, you can even set it up so it automatically converts the music file to mp3).
Flow is the following: 
- Start Singstar creator WITH administrator settings - if you don't do this the ESL patching will fail silently and while you can use the iso files via OPL you won't be able to burn them and use them directly.
- download some songs, add them via **Ordner hinzufügen**
- - Sometimes the program will show you an unhandled exception, that happens when txt files with an encoding different from UTF-8 are added (e.g. UTF8 with BOM). You can easily fix this by opening the txt files in Notepad++, change the encoding to UTF-8 and save the file again.
- go through each added song, right-click on it and click **Song überprüfen**, if it returns **TXT ist in Ordnung** the song is fine, sometimes it returns **...BPM ist zu schnell** which means you need to lower the BPM in the .txt file.
- - the problem with this is, that when you adjust the BPM, the lyrics/mappings will be off and it's a real hassle to correct them. While it's not a perfect solution, it's a quick and dirty one so i recommend halving the BPM with the original Ultrastar, see next chapter.
- Once all songs are fine you just click **DVD erstellen**, which will go a lot of stuff in the background (a lot of converting around etc.). You can watch this progress by checking the **Singstar1.log** file.
- - It took me quite long to figure this out: When you hit **DVD erstellen** the very first time it will try to install .net framework 3.5 if it's not installed yet (its quite old). If you can just install it, that's great, for me it took me a while to figure out how to do it. At first I had to do all Windows Updates, and then I was able to activate .net framework 3.5 via **activate/deactivate windows features dialog**. When you just skip the .net framework installation, it will look like it creates the .iso, but the PS2 will get stuck loading it.
- Once the program finishes it will have created a Singstar1.iso file. Copy it to your shared Samba drive and

## Common issues with Singstar Creator

- When adding multiple Songs in often gets confused with some files when converting which ends up in a mess. I can only recommend adding one song by one.
- After converting each folder must contain a .scv (video file), .sca (audio file), .txt (the beat map), .bmp (cover image).
- If you want to add a duett song, you need to use the option **Duett-Modus** where you need to choose which line who sings. Really bad UI unfortunately. This will create an .ini file. CAREFUL, once you click on **Duett-Modus** again, this file will always be overwritten, so make a backup before. You can NOT edit it with the tool, only recreate it from scratch, so be accurate when doing it. You could edit the .ini file manually afterwards but it's hard to guess which line is which.
- When you get an access violation exception, most likely the format of your txts is wrong - make sure they are UTF-8, not UTF-8 with BOM.

### When it gets stuck and the log files don't update
- Most likely something is wrong with your .txt song files. This will lead to the whole operation getting stuck with no feedback (You can kill singstar creator via the task manager).
- Known issues are:
  - Use of commas instead of dots
  - Lines starting with an R (this is an unknown annotation to singstar)
  - Sometimes negative timestamps for the beats are a problem


## Reducing BPM with the original Ultrastar (ingame editor)

- Install [`original Ultrastar`](https://github.com/weathondev/SingstarCreatorTutorial/raw/main/UltraStar-0.5.2.exe).
- Copy the songs that you want to check (too high BPM) to C:\Program Files (x86)\UltraStar\Songs
- Start up Ultrastar and go to the song selection
- Select the song and hit **E** to enter the edit mode
- Hit **D** to half the BPM
- Hit **S** to save the changes.

It will now create a .txt file with the same name in 
C:\Users\<User>\AppData\Local\VirtualStore\Program Files (x86)\UltraStar\Songs
replace your txt file with it, now you can check it again in **Singstar Creator**.

## Use the above mentioned editor to fix the start time to match the downloaded audio file

- Sometimes you just don't find a matching audio file on youtube, then you need to adjust the start time, which is called the GAP
- With the editor you can increase (hit **0**) the GAP by 10 or decrease (hit **9**) it by 10
- Hit **S** to save the changes afterwards

It will now create a .txt file with the same name in 
C:\Users\<User>\AppData\Local\VirtualStore\Program Files (x86)\UltraStar\Songs
replace your txt file with it, now you can check it again in **Singstar Creator**.

# Run the custom Singstar DVD

1. Insert the burned DVD into the PS2
2. Insert the USB drive into the PS2
3. Connect your network cable (PS2 same network as PC!)
4. Boot up PS2
5. Select Browse HDD (with O not X)
6. Select Mass (with O not X)
7. Select OPLs ELF file (with O not X)
8. Now OPL will be booted from USB stick, select the right ISO and start with (now with X)
9. Have fun!

# Support

If you need support with any step just create a Github issue - if I have time i'll try to help, please just concretely describe on what you did already and what doesn't work.
