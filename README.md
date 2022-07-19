# Algorithm-for-Install-ROS2-in-Jetson-Nano-with-windows

## Table of contents
* [Introduction](#Introduction)
* [Components required](#Components-required)
* [setup algrithem](#setup-algrithem)


## Introduction
     The jetson nano is one of series of embedded computing boards from Nvidia , 
     Jetson is a low-power system and is designed for accelerating machine learning applications ,
     building practical AI applications, cool AI robots, and more.

![jetson-nano-dev-kit-top-r6-HR-B01](https://user-images.githubusercontent.com/64277741/179639970-f0d995bf-f667-403c-b02d-a2940fda9243.png)
  Figure (1): Jetson nano kit 
  
 ### Ports & Interfaces
    1. microSD card slot for main storage
    2. 40-pin expansion header
    3. Micro-USB port for 5V power input, or for Device Mode
    4. Gigabit Ethernet port
    5. USB 3.0 ports (x4)
    6. HDMI output port
    7. DisplayPort connector
    8. DC Barrel jack for 5V power input
    9. MIPI CSI-2 camera connectors
  
  
## Components required

    1- Nvidia jetson nano

    2- microSD card (32GB UHS-1 minimum recommended)

    3- USB keyboard and mouse 

    4- Computer display (HDMI or DP)

    5- Micro-USB power supply deliver 5V⎓2A EX:  Adafruit’s 5V 2.5A Switching Power Supply with 20AWG MicroUSB Cable (GEO151UB-6025)
    
    6-  computer with Internet connection  
    
    7- ability to flash your microSD card 
    

## setup algrithem
First step :
### Write Image to the microSD Card

      To prepare your microSD card, you’ll need a computer with Internet connection and the ability to read and write SD cards,
      either via a built-in SD card slot or adapter

 step 1: Download the [Jetson Nano Developer Kit SD Card Image](https://developer.nvidia.com/jetson-nano-sd-card-image), 
  and note where it was saved on the computer.
 
 step 2: INSTRUCTIONS FOR WINDOWS :
 
  Format your microSD card using SD Memory Card Formatter from the SD Association.
  

  1- Download, install, and launch  [SD Memory Card Formatter for Windows](https://www.sdcard.org/downloads/formatter/sd-memory-card-formatter-for-windows-download/) .
 
 ![Jetson_Nano-Getting_Started-Windows-SD_Card_Formatter](https://user-images.githubusercontent.com/64277741/179655546-a65398a0-6129-425b-9868-a0616bcc9f05.png)

  2- Select card drive .
  
  3- Select “Quick format”
  
  4- Leave “Volume label” blank
  
  5- Click “Format” to start formatting, and “Yes” on the warning dialog
  
 Use Etcher to write the Jetson Nano Developer Kit SD Card Image to your microSD card
 
   1- Download, install, and launch [Etcher](https://www.balena.io/etcher)
   
   2- Click “Select image” and choose the zipped image file downloaded earlier.
   3- Insert your microSD card if not already inserted.
     Click Cancel if Windows prompts you with a dialog like this:
     
  ![Jetson_Nano-Getting_Started-Windows-Etcher_Cancel](https://user-images.githubusercontent.com/64277741/179656202-88348754-6d7e-4475-87d7-8b5dba8fb98c.png)

   4- Click “Select drive” and choose the correct device.
   
   ![Jetson_Nano-Getting_Started-Windows-Etcher_Select_Drive](https://user-images.githubusercontent.com/64277741/179657185-fd60e08d-9f44-437c-883c-b6de5a748ae3.png)
   
   5- Click “Flash!” It will take Etcher about 10 minutes to write and validate the image if your microSD card is connected via USB3.
   
   6- After Etcher finishes, Windows may let you know it doesn’t know how to read the SD Card. Just click Cancel and remove the microSD card.
   
   ![Jetson_Nano-Getting_Started-Windows-SD_Card_Prompt](https://user-images.githubusercontent.com/64277741/179657505-e526e28b-21d4-48f8-9742-09c8be5299b6.png)

   7- After your microSD card is ready, proceed to Setup 
   
   
  ### Setup 
  
  
 #### Initial Setup with Display Attached
 
  1- Insert the microSD card (with system image already written to it) into the slot on the underside of the Jetson Nano module.
   
   ![Jetson_Nano-Getting_Started-Setup-Insert_microSD-B01](https://user-images.githubusercontent.com/64277741/179658397-9f784596-b374-4564-802f-b5cc407dc8e2.png)
  
  2- Power on your computer display and connect it.
  
  3-Connect the USB keyboard and mouse.
  
  4-Connect your Micro-USB power supply ,The kit will power on and boot automatically.
  
  ##### First Boot
  
  A green LED next to the Micro-USB connector will light as soon as the kit powers on.
  When you boot the first time, the kit will take you through some initial setup, including:

  1- Review and accept NVIDIA Jetson software EULA
  2- Select system language, keyboard layout, and time zone
  3- Create username, password, and computer name
  4- Select APP partition size—it is recommended to use the max size suggested
  5- After Logging In ,You will see this screen
   
 #### install ROS2 
 
 1- Launch terminal using CTRL+ALT+T
 
 ##### Set locale 
 
           locale  # check for UTF-8

           sudo apt update && sudo apt install locales
           sudo locale-gen en_US en_US.UTF-8
           sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
           export LANG=en_US.UTF-8

           locale  # verify settings
 
 ##### Setup Sources
 
  You will need to add the ROS 2 apt repositories to your system. First, make sure that the Ubuntu Universe repository is
  enabled by checking the output of this command.    
  
          apt-cache policy | grep universe
         
  This should output a line like the one below:
  
           500 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
           release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=universe,b=amd64
  
  If you don’t see an output line like the one above, then enable the Universe repository with these instructions.
          
           sudo apt install software-properties-common
           sudo add-apt-repository universe
           
  Now add the ROS 2 apt repository to your system.
  
            sudo apt update && sudo apt install curl gnupg2 lsb-release
            sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key  -o /usr/share/keyrings/ros-archive-keyring.gpg

##### Install ROS 2 packages


            
