# Takbeer
Prayer timing stand alone project based on qt on Raspberry pi. Uses Gebetszeiten.de as source for monthly database query , which updates the database for the complete month. 

Install:
1. Connect to your Raspberry Pi using ssh (ssh pi@raspberrypi) or directly using HDMI
2. Install Apache (sudo apt-get install apache2 apache2-utils)
3. Install PHP (sudo apt-get install php) php7 installed
- The permissions aren’t set correctly just yet, so for the time being, we’ll create a index file as sudo:
    --  sudo echo "<?php phpinfo(); ?>" | sudo tee index.php
4. Install MySQL Server:(sudo apt-get install mysql-server); Client:(sudo apt-get install mysql-client)
5. Clone the repository : git clone https://github.com/aquibrash87/Takbeer.git
6. Build and Run (a) mkdir build && cd build (b) cmake .. (c) make -j

to work with QtWebkit Library you should have not older then 5.0.0 of QtCreator
 Updating Qtceartor Version from 4 to 5  
1- after you clean the old version from Qtcreator or uninstall with all libraries
2- with this instrucation 
sudo apt-get install qt5-default
sudo apt-get install qtcreator 
 also you can follow this video 

https://www.youtube.com/watch?v=C_uOybXbDYI&feature=youtu.be

if you have some problems with the libraries you can install a specific libraries through this command
sudo apt-get install qt5-default libqt5webkit5-dev gstreamer1.0-plugins-base gstreamer1.0-tools gstreamer1.0-x

somtimes , it happend some problems with .pro files you can recreate this file
by this command 

-firstly go the directory of the project
make clean 
-after that
make

-also sometimes you need to update the libraries and packages 
throught this steps

building Qt5 with bugfixes from source.

go here, install dependencies via apt-get (the -dev packages)
as root do apt-get build-dep qt5-default
as root do apt-get install libxcb-xinerama0-dev flex bison gperf libicu-dev libxslt-dev ruby libssl-dev libxcursor-dev libxcomposite-dev libxdamage-dev libxrandr-dev libdbus-1-dev libfontconfig1-dev libcap-dev libxtst-dev libpulse-dev libudev-dev libpci-dev libnss3-dev libasound2-dev libxss-dev libegl1-mesa-dev gperf bison libasound2-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev, after that apt-get install '^libxcb.*-dev' libx11-xcb-dev libglu1-mesa-dev libxrender-dev libxi-dev
after that do this:

 # git clone https://code.qt.io/qt/qt5.git
 # cd qt5
 # git submodule update --init
after that link ./configure --help output for your case and we will continue

FINAL UPDATE: source build did the trick, the problem was with an outdated Qt in packages. The configuration string :

# mkdir qt-build
 # cd qt-build
 # ../configure -opensource -static -confirm-license -release -nomake examples -openssl-runtime -prefix /usr

reference for this 

https://raspberrypi.stackexchange.com/questions/61078/qt-applications-dont-work-due-to-libegl/61086

