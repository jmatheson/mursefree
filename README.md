This is an implementation of OpenAPS soup to nuts once you have your hardware set up.

These instructions can help you get setup assuming you want to do the following:
* You want the current dev version of OpenAPS. This means the bleeding edge, probably buggy, version of the software. If you don't want that they you should probably follow the regular instructions at [https://github.com/openaps/docs]

Initial Setup (one time only)
* Get all your hardware. I suggest the Pi, Dexcom G5, Carelink Stick and battery for starters. Full instructions and options @ [https://github.com/openaps/docs/blob/master/docs/getting-started/hardware.md]
* Create a github.com account. If you are willing to have your info public then do the free version, otherwise do paid and create the repository as private.
* Go here [https://github.com/nightscout/cgm-remote-monitor]. Press fork in the upper right. This will give you a copy of Nightscout.
* Set up Nightscout using Heroku [ http://www.nightscout.info/wiki/labs/how-to-heroku]. We want Heroku, not Azure.
* Connect your Dexcom G5 to your Nightscout instance [http://www.nightscout.info/wiki/welcome/nightscout-with-ios-and-dexcom-share/nightscout-bridge-for-dexcom-g5]

Format SD Card (Mac instructions, Each time you start with a new Micro SD card or one that had been get corrupted)
* Format/Reformat your Micro SD card with SDFormatter [https://www.sdcard.org/downloads/formatter_4/]. Select Overrite. It will take 20-30 minutes.
* Install NOOBS from  [https://www.raspberrypi.org/downloads/noobs/].
* Unzip NOOBS. Open the NOOBS directory. Copy all the files to your Micro SD Card. Don't simply copy the NOOBS directory itself. That will not work.
* Plug in your pi with a network cable, mouse and hdmi to a monitor (no keyboard needed). Insert the Micro SD card, then plug the pi into a battery or wall.
* Finish installing the OS on your pi from there using on screen instructions.

Setup openaps (Every time you start with a new Micro SD card)
* Log in to your pi ```ssh pi@raspberrypi.local``` from your laptop/desktop computer using the Terminal program (assuming it is on the same network as your Pi). The password by defailt is ```raspberry```
* Set timezone by typing in```sudo raspi-config``` and then follow the menu's to set your Timezone. Save when done.
* Run ```curl -s https://gist.githubusercontent.com/jmatheson/755891b12ce051bde10c/raw/9b059c2a748813c7af44ecaeeeccd1c3177ee5ce/.profile | bash -```. This will grab a sample .profile for setting up your environment variables.
* Now edit the file and update with all of your information per the instructions ```nano .profile```. Save the file when done. 
* Run ```curl -s https://gist.githubusercontent.com/jmatheson/f47bf446450598e714a8/raw/9863e425a7dd7a0848f9714a79236c29e3a50ac2/setup.sh | bash -``` which will install everything else we need in one fell swoop!
* You are now looping!

NOTE: If you make edits to any files on github.com in your repository, be sure to pull them down to your local pi so there are no conflicts for backing up your pi. Use something like: ```git pull http://github.com/jmatheson/openaps```
