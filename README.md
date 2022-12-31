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
See https://github.com/CTurt/FreeDVDBoot
In case this github page will ever go down, i copy the parts i used here:

## Easy setup for all PS2 Slim consoles

All you need is:

- A compatible console (all PS2 Slim / Sony Bravia TV units are supported),
- A DVD (not a CD), preferably a DVD-R as other types such as DVD+RW put more strain on the PS2 laser,
- A computer with a built-in disc burner / external USB disc burner,

### Step 1: Download the ISO
Download [`PREBUILT ISOs/All PS2 Slims - English language.iso`](https://github.com/CTurt/FreeDVDBoot/raw/master/PREBUILT%20ISOs/All%20PS2%20Slims%20-%20English%20language.iso)

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

