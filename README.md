# Paper server on Android device!

This guide will show you how you can run a Minecraft Paper server on an Android device. BE SURE TO BE ON WIFI.

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

Before we can really have a party, you'll need to update your package repository. You can do this by running ```pkg update``` on the terminal. Once that process completes, it may ask you to upgrade (type Y and hit enter), if it doesn't, then run ```pkg upgrade -y``` in order to bring your install up to date. There may be several confirmations asking if you want to overwrite files or leave the current ones, you can just hit enter on these.

If you get an warning that a package repository isn't selected, you can ignore it. Termux will parse the mirror list and perform the updates anyways.

### Step three: Install a linux distribution and fall down the rabbit hole that is superior operating systems.

In order to facilitate this delusion, we need to install linux. We're going to use Proot to run Debian (If you want to run ARCH btw, you can, but you're on your own).

On the Termux terminal, run ```pkg install -y proot-distro```

Once the package has been installed, we're going to install Debian.

type ``` pd install debian```. It will take a little time to install all the required files, so take this time to take a break, go outside, touch some grass, take your meds, whatever you want I guess. Once finished, you can enter the Debian OS by typing ```pd login debian```. You should be greeted with the Debian command line.

![image](https://github.com/Jadan1213/paper_on_android/assets/68805162/b62f8370-8c2b-47bb-935b-7baf266a9685)

### Step four: Now the really fun part, we ARE having fun right? Installing Java.

I'm not really a coffee guy, but Java is kinda important here, so we'll need to install it. We're going to use the Eclipse adoptium (Temurin) release of Java. You can view the instructions [Here](https://adoptium.net/installation/linux/) if you want, or follow along with me. Your choice, I won't be offended.

First we need to make sure we have the required packages to install Temurin. Make sure you type everything exact, or it won't work. It's going to be annoying on a phone touchscreen, but hey, you asked for this.

Run ```apt update``` to update your Debian package repositories\
Run ```apt upgrade -y``` to bring all your current packages up to date\
Run ```apt install -y wget apt-transport-https gpg``` These may already be present, but we're doing this just to be sure.

Now we need to add the GPG key for our Temurin repository. Keep in mind, that is a capital `O` not a zero after `-q`

Run ```wget -qO - https://packages.adoptium.net/artifactory/api/gpg/key/public | gpg --dearmor | tee /etc/apt/trusted.gpg.d/adoptium.gpg > /dev/null```

Now we need to add the Temurin repository to our local repository listing. This is going to be a pain typing on a touch screen, so if you have a way to copy/paste it (like from your phone's browser), it will be less of a headache. Don't chicken out now though, I told you this was insane to do.

Run ```echo "deb https://packages.adoptium.net/artifactory/deb $(awk -F= '/^VERSION_CODENAME/{print$2}' /etc/os-release) main" | tee /etc/apt/sources.list.d/adoptium.list```

Now we can actually install Java. We're going to use Java 21 so we can run Paper 1.20.6 in this example.

Run ```apt update``` to update your repository with the new packages available. If you entered anything wrong above, you'll likely get an error at this part of the process. 
Run ```apt install -y temurin-21-jdk``` to install the Java 21 release.
Run ```java -version``` to verify that the installation succeeded and Java 21 is available.

You should see\
![image](https://github.com/Jadan1213/paper_on_android/assets/68805162/cbd3251a-f9e1-4949-ac5d-857c31b6f84e)

### Step five: The main event, installing PAPER!

Now we need to make a directory to store our server files.

Run ```mkdir -p ./minecraft/paper-1.20.6``` to create the directories.\
Run ```cd minecraft/paper-1.20.6/``` to switch to your new directory.\
Run ```wget https://api.papermc.io/v2/projects/paper/versions/1.20.6/builds/145/downloads/paper-1.20.6-145.jar``` to download the latest (as of this writing) version of PaperMC. You can find the link for the latest version on [Papermc.io](https://papermc.io/downloads/paper).\
Run ```echo "eula=true" > eula.txt``` to pre-write the eula file, setting it to true.

Now assuming you crazies have followed along correctly, and haven't given up by this point, lets run our Paper server!

Run ```java -Xmx2G -jar paper-1.20.6-145.jar nogui``` to start the server. If you're using a different version of paper, make sure you use the Jar name of the version you've downloaded! make sure your console shows that you're in the ```~/minecraft/paper1.20.6/``` directory, or the command won't work (this will be different depending on what you named your directory).

You can change the `-Xmx2G` value to allocate a max amount of RAM of your choosing. You'll want to make sure you don't set this too high. Be sure to find out how much RAM your phone has, and make sure you leave plenty available for your phone and java to do their fancy thing. If you allocate too much, you'll end up crashing.

The first start of the server will take considerably longer since files will need to download. Subsequent startups should be faster.

Don't worry about this warning, you should still be able to connect to the server just fine as long as you're on the same Wi-Fi network as your phone. You ARE on Wi-Fi right?.\
![image](https://github.com/Jadan1213/paper_on_android/assets/68805162/e0cd4edc-fbde-4327-8b3e-3441e5eb6dd0)

### CONGRATULATIONS, your phone is now running Paper!

Now, open Minecraft Java 1.20.6 on your PC and go to multiplayer

![image](https://github.com/Jadan1213/paper_on_android/assets/68805162/b2626977-4814-440d-b7cb-7ffd8524a900)

Select `Direct connection`

![image](https://github.com/Jadan1213/paper_on_android/assets/68805162/f15f1fef-d2c0-480d-a644-eb4527eb8cdd)

Enter your phone's Wi-Fi IP address. You can find this in your android Wi-Fi settings (Google it, this is a minecraft tutorial not a phone settings tutorial). In my case, it's `192.168.30.9`

![image](https://github.com/Jadan1213/paper_on_android/assets/68805162/b91de7dc-649a-4543-ac52-e16b527b651e)


Assuming everything was followed correctly, and there were no errors, you should be logged in!

![image](https://github.com/Jadan1213/paper_on_android/assets/68805162/3f7d883f-6c88-4f53-acba-f5994c1e94dc)


### PLUGINS

Paper supports many wonderful plugins by amazing devs. to install them, go into your plugins directory using ```cd ./plugins``` (your full path, assuming you followed this guide exactly, should be `~/minecraft/paper1.20.6/plugins`)

You can install plugins by downloading them directly using `wget` followed by the URL of the plugin. This will be the download URL for the plugin jar for whichever plugin you're trying to download. For example, to install the Chunky plugin from Modrinth, you would run:

```wget https://cdn.modrinth.com/data/fALzjamp/versions/6ENKPUbu/Chunky-1.4.10.jar```

You will need to `stop` and then launch your server again for the plugins to load.

### WAKELOCK and RUN IN BACKROUND

Since android has many power saving features, you'll want to acquire a wakelock and allow the application to run in the background. The notification bar should show an `Acquire wakelock` button/toggle for Termux.

![image](https://github.com/Jadan1213/paper_on_android/assets/68805162/943ba626-3da8-47af-a629-833ee23b1b11)

For Battery optimization, you'll want to set the Termux app to `Not optimized`. Getting here will be dependent on your version of android. Google this.

![image](https://github.com/Jadan1213/paper_on_android/assets/68805162/cc265cf3-8f81-4783-a4db-8650a49ad52e)

## FINAL STEP
Be sure to call your parents and tell them you love them, and how crazy you are for doing something completely whacko like this. Although I'm sure they already know you're crazy. They can probably recommend you a good pshycologist to see.

Have fun!
