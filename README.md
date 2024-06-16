# Paper server on Android device!

This guide will show you how you can run a Minecraft Paper server on an Android device.

----------------

### DISCLAIMER: 
You really shouldn't do this. It's not going to run as well as a real machine with more powerful hardware. You do you though. I did it for the fun of it. You don't want to do this. Just don't. Seriously, why am I even writing this? This is crazy!

# BIGGER DISCLAIMER: 
THIS IS NOT SUPPORTED BY PAPER. Don't do this and expect the brilliant Paper devs to help you. You're the crazy one doing this, not them. They won't have any desire to assist you in your descent into the abyss of instanity.

----------------

### Step one: Question your ambitions in life, and install Termux from the Google play store.

To embark on this adventure that will likely end up with you needing a trip to a psychologist, we're going to need to install the Termux terminal emulator from Google play. You can also install Termux using the F-Droid app if you wish. Just get the app somehow, we can't really do anything without it.

![image](https://github.com/Jadan1213/paper_on_android/assets/68805162/d51d4c7c-bc65-44d3-ab78-6074541c2ed8)

Once you have Termux installed, Open the app. (If you didn't realize this was obvious, just turn back now, it's too much for you).

![Screenshot_2](https://github.com/Jadan1213/paper_on_android/assets/68805162/9d1691d6-4e3c-4a99-a6b3-aae5bd46ae0d)

You will be greeted with the Termux terminal screen.

### Step two: Ok, so we're doin this. Update the Termux package repository

Before we can really have a party, you'll need to update your package repository. You can do this by running ```pkg update``` on the terminal. Once that process completes, it may ask you to upgrade (type Y and hit enter) if it doesn't then run ```pkg upgrade -y``` in order to bring your install up to date. There may be several confirmations asking if you want to overwrite files or leave the current ones, you can just hit enter on these.

If you get an warning that a package repository isn't selected, you can ignore it. Termux will parse the mirror list and perform the updates anyways.

### Step three: Install a linux distribution and fall down the rabbit hole that is superior operating systems.

In order to facilitate this delusion, we need to install linux. We're going to use Proot to run Debian (If you want to run ARCH btw, you can, but you're on your own).

On the Termux terminal, run ```pkg install -y proot```
