# Data-Analysis-Toolkit
Tools and guides for working with CSV, JSON, XML, and SQLite for simple data analysis.

This guide is intended for people who will kill someone if they have to nest one more VLOOKUP in excel and for people who have very useful data stuck inside an XML or JSON file and don't know how to get it out. 

##If you are on Windows set up a Virtual Linux machine
The Linux command line lets you do some very powerful things. It is usually easier to set up a Virtual Machine than it is to use Cygwin or try to make things work on Windows.

It is actually a lot easier than it sounds. When you are done you will have a complete Linux system that lives inside your Windows system in a separate window. 

###Download and Install Virtual Box
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

You can get away with 512MB of RAM but 1024 or 2048 will give you a better experience if you have enough RAM on your system. While your Virtual Machine is running it will grab this amount of ram for itself and so it won't be available to your main system.

You want to create a new virtual drive. I usually set the size to 50GB and use the default file type. You want to use a dynamically allocated storage. This will only use the actual amount of space that your system needs up to the setting you provided (50GB). 

Now that you have a virtual Hard Drive you need to tell the virtual system that you want to use the Ubuntu .iso file as a virtual CD drive. Click the "Storage" setting when you have your virtual machine selected in the list. Then select the CD picture under "Controller: IDE". You can then click on the CD button next to the select box that appears. Select your Ubuntu .iso file - you don't have to put this any specific place because you won't need it after you boot your system the first time.

Now we are ready to boot up your system. Select you system and click the "Start" arrow.

You then have to click the default a lot. Don't worry about some of the prompts that warn you about deleting drives - this system can only edit its virtual drive and can't touch your Windows data.

When you reboot the system you will see a shiny new Linux System in a tiny window.

###Installing VirtualBox Guest Additions
You will quickly get tired of using the tiny window. VirtualBox Guest Additions fixes this problem and provide a couple other tool's that can be nice.

Before you start it is a good idea to update your new system with the latest software. Click on the circle Ubuntu symbol on the sidebar. This opens something that is similar to Windows start menu. Type "Terminal" into the search bar and then select the terminal icon (Black box with > and underscore).

(Optional) Starting the terminal this way is annoying. You can make it stick to the sidebar by right clicking and choosing "Lock to Launcher".

In your open terminal type:
    sudo apt-get update

This tells your system to get the latest version of all your software - the apt-get update part - and do it as the root (the most powerful user who can do everything) - the sudo part.

Side Note: sudo is a very useful command. Linux makes you do most things a a normal user so you can't accidentally do bad or dumb things. Sudo is a command that tells the system that you really know what you're doing and it is okay that the command that is after sudo might need to do potentially dangerous things.


Now you are ready to install the Guest Additions. You just click on the "Devices" tab at the top of your window and select "Insert Guest Additions CD image". This will put a new virtual CD into the fake CD drive that your virtual machine has. Ubuntu will detect the CD and automatically run the right file - you just have to click run and then wait. You just hit enter when it is done.

Now you have to restart you system for the Guest Additions to start working.

When your system boots again you should be able to change the window size and the desktop should resize to match. Pressing Control - F will make your virtual machine fill the full screen. Pressing Control - F will make it go back to a window again.

Now you are ready for the good data analysis stuff.

##Install Data Analysis Tools
We can now install a couple tools for working with various data sets. This requires some more command line work but should be simple and give you a chance to learn the basics of the command line. 

###Install SQLite
SQLite is a simple database that is easy to setup and share. When you create a new SQLite database the whole database just lives in a single file. It is easy to share or email this file to other people as a simple way to share your dataset. It is also convenient because if you mess something up you can just delete the database and start over. 

For doing anything more than the simplest data analysis it is far easier to use a database instead of Excel. It takes a bit more time to learn but you will save many hours of pushing data around. When you find yourself needing a VLOOKUP call in excel that is probably the time to start looking at using a database. Additionaly, you can make complicated pivot tables in a database that would be a pain to do in Excel. Once you have your analysis complete it is simple to export you data to excel for reporting.

It is simple to install SQLite. You just do:

    sudo apt-get install sqlite3

You can check that it worked by running:

    sqlite3 --version

This command will output the current version of SQLite. This happens to be version 3.xx which is why we use the sqlite3 command.

###Install Python
It happens that a lot of helpful data analysis tools are written in Python (a popular programming language). You don't need to know Python to make use of all the great tools that are available. You will need to install some Python components so you virtual machine will know how to run Python programs.

Run this command to get the Python tool for installing new Python software:

    sudo apt-get install python-pip

Enter "y" when it asks you if you want to install new things. This will install pip the Python package manager. Pip will be used in later steps to install Python tools.

Check that it worked:

    python --version

And then:

    pip --version

Both of these commands should output the current version of the tool as the response. You might have noticed a pattern - if you put --version at the end of commands they will tell you their current version. This is a common input for command line tools. It is an easy way to check that the tool is set up right at a basic level.

###Install csvkit
Csvkit is a great tool for working with .csv files. .csv files are just a giant list of information with each item separated from the next item with a "," and each line separated by a linebreak. You can open these file in Excel which makes them very convenient.

Csvkit allows you to work on .csv files on the command line, including converting to and from different formats and importing them into databases like SQLite. 

Documentation for csvkit is online here:
https://csvkit.readthedocs.org/en/0.9.1/index.html

Install it now!

    sudo pip install csvkit

You'll notice that we had to use sudo here. I usually try to install things without sudo first because it is safer. In this case the install fails with a "permission denied" error. This is a very common occurence on Linux. It usually means that the install wanted to write to a directory that is not writeable for security reasons. The directory that hold commands for the system is write protected like this to prevent evil programs from replacing your normal commands with evil versions. This is why you often need to use sudo to install new commands.

Check that it worked right using one of the commands from the package:

    in2csv --version

You'll notice that --version did not work this time but we still got a very helpful message telling us how to use in2csv. This also tells us that the command is being recognised by the system properly.

###Install xmllint
XMLLint will let you work with XML data before you import it into a database. Sometimes you only care about some information in an XML file and don't want to clog your database up with useless data. 

Install it:

    sudo apt-get install libxml2-utils

You now know how to check if it worked.

###Install xmlutils

    sudo pip install xmlutils

This package will let you convert to JSON and csv, and import to a database.

###Install JQ
You are almost done. This utility lets you work with JSON in a way that is similar to the XML utilities abobe but JSON instead of XML.

    sudo apt-get install jq

### Done installing
It was a bit of work but now you know how to install Ubuntu packages (apt-get) and Python tools (pip). When you find something new that you want to try it is worth checking if it can be installed through one of these instead of trying manually.

You now have tools to work with the 3 most common data formats used right now - XML, JSON, and CSV - and a database to put that data in for analysis.
