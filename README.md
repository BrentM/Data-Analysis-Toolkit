# Data-Analysis-Toolkit
Tools and guides for working with CSV, JSON, XML, and SQLite for simple data analysis.

This guide is intended for people who will kill someone if they have to nest one more VLOOKUP in excel and for people who have very useful data stuck inside an XML or JSON file and don't know how to get it out. 

##If you are on Windows set up a Virtual Linux machine
The Linux command line lets you do some very powerful things. It is usually easier to set up a Virtual Machine than it is to use Cygwin or try to make things work on Windows.

It is actually a lot easier than it sounds. When you are done you will have a complete Linux system that lives inside your Windows system in a separate window. 

###Download and Install Virual Box
https://www.virtualbox.org/wiki/Downloads
You want to get the Windows Binary

You start the executable and then click yes a lot.

###Download Ubuntu
Ubuntu is a popular and well supported Linux Distribution.

http://www.ubuntu.com/download

You want the desktop version. And probably the 64 bit version. 

This will download a .iso file that is an exact copy of what would be boot CD if you were installing Linux on a blank system.

###Set up your new virtual Machine
Open Virtualbox and select "New".

Give your machine a name and select "Linux" for the type and "Ubuntu (64 bit)" for the version.

You can get away with 512MB of RAM but 1024 or 2048 will give you a better experience if you have enough RAM on your system. While your Virtual Machine is running it will grab this amount of ram for itself and so it won't be available to you main system.

You want to create a new virtual drive. I usually set the size to 50GB and use the default file type. You want to use a dynamically allocated storage. This will only use the actual amount of space that your system needs up to the setting you provided (50GB). 

Now that you have a virtual Hard Drive you need to tell the virtual system that you want to use the Ubuntu .iso file as a virtual CD drive. Click the "Storage" setting when you have your virtual machine selected in the list. Then select the CD picture under "Controller: IDE". You can then click on the CD button next to the select box that appears. Select your Ubuntu .iso file - you don't have to put this any specific place because you won't need it after you boot your system the first time.

Now we are ready to boot up your system. Slect you system and click the "Start" arrow.

You then have to click the default a lot. Don't worry about some of the prompts that warn you about deleting drives - this system can only edit its virtual drive and can't touch your Windows data.

When you reboot the system you will see a shiny new Linux System in an tiny window.

###Installing VirtualBox Guest Additions
You will quickly get tired of using the tiny window. VirtualBox Guest Additions fix this problem and provide a couple other tool's that can be nice.

Before you start it is a good idea to update you new system with the latest software. Click on the circle Ubuntu symbol on the sidebar. This opens something that is similar to Windows start menu. Type "Terminal" into the search bar and then select the terminal icon (Black box with > and underscore).

(Optional) Starting the terminal this way is annoying. You can make is stick to the sidebar by right clicking and choosing "Lock to Launcher".

In your open terminal type:
    sudo apt-get update

This tell your system to get the latest version of all your software - the apt-get update part - and do it as the root (the most powerful user who can do everything) - the sudo part.

Side Note: sudo is a very useful command. Linux makes you do most things a a normal user so you can't accidentally do bad or dumb things. Sudo is a command that tells the system that you really know what you're doing and it is okay that the command that is after sudo might need to do potentially dangerous things.


Now you are ready to install the Guest Additions. You just click on the "Devices" tab at the top of your window and select "Insert Guest Additions CD image". This will put a new virtual CD into the fake CD drive that your virtual machine has. Ubuntu will detect the CD and automatically run the right file - you just have to click run and then wait. You just hit enter when it is done.

Now you have to restart you system for the Guest Additions to start working.

When your system boots again you should be able to change the window size and the desktop should resize to match. Pressing Control - F will make you virtual machine fill the full screen. Pressing Control - F will make it go back to a window again.

Now you are ready for the good data analysis stuff.

##Install Data Analysis Tools
We can now install a couple tools for working with various data sets. This requires some more command line work but should be simple and give you a chance to learn the basics of the command line. 

To Be Continued... {exciting and slightly ominous music}
