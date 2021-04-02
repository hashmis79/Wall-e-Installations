# Table Of Contents
* WALL-E Installations
    * [For Windows](#for-windows)
    * [For Linux](#for-linux)
* [Commands](#commands)
# For Windows
First We are going to install ESP-IDF First and then Wall-E files
## 1. Download the installer from ( https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/windows-setup.html#esp-idf-tools-installer )
<p align="center">
  <img src="https://user-images.githubusercontent.com/66636289/112637273-f8ae2180-8e63-11eb-8f96-4921fd6c1441.png">
</p>

## 2. After Downloading open .exe file, select `I accept` then click Next>.
<p align="center">
  <img src="https://user-images.githubusercontent.com/66636289/112638237-0c0dbc80-8e65-11eb-8e18-4cfb65691d55.png">
</p>

## 3. In my case I already had python3.6 and github on my system. If you don’t, then select the install python, install git options 
<p align="center">
  <img src="https://user-images.githubusercontent.com/66636289/112638419-3eb7b500-8e65-11eb-94a9-0510cb33845e.png">
</p>

## 4. The 1st option is only available for those already have github. For rest Choose the 'Install Git' option  
<p align="center">
  <img src="https://user-images.githubusercontent.com/66636289/112638775-9c4c0180-8e65-11eb-8891-9cd4e185f84c.png">
</p>

## 5. 
<p align="center">
  <img src="https://user-images.githubusercontent.com/66636289/112639270-154b5900-8e66-11eb-8f93-29c0a2b279d6.png">
</p>

## 6.
<p align="center">
  <img src="https://user-images.githubusercontent.com/66636289/112639872-c4883000-8e66-11eb-9151-f4a7c72c0dbb.png">
</p>

## 7. Click on Install then after Installation check all boxes and click on Finish.
<p align="center">
  <img src="https://user-images.githubusercontent.com/66636289/112640010-f00b1a80-8e66-11eb-9856-88497a69e134.png">
</p>
<p align="center">
  <img src="">
</p>

## 8. ESP-IDF Command Prompt & Poweshell window will pop-up :
<p align="center">
  <img src="https://user-images.githubusercontent.com/66636289/112640831-bc7cc000-8e67-11eb-828a-2e77f53dbca7.png">
</p>
<p align="center">
  <img src="ttps://user-images.githubusercontent.com/66636289/112641114-11203b00-8e68-11eb-9e43-f37664525e50.png">
</p>
 
## 9. Run 'export.bat' in ESP-IDF Command Prompt:
<p align="center">
  <img src="https://user-images.githubusercontent.com/66636289/112641393-5ba1b780-8e68-11eb-85ba-c27e137258b8.png">
</p>

## 10 . Run `idf.py build`
<p align="center">
  <img src="https://user-images.githubusercontent.com/66636289/112641959-d965c300-8e68-11eb-9d95-5a71c5625174.png">
</p>

<p align="center">
  <img src="https://user-images.githubusercontent.com/66636289/112641989-dff43a80-8e68-11eb-81a7-67f6faf1d322.png">
</p>

## Wall-E Files
## Step 1 : Cloning the Wall-E Git Repo
To clone the Repo just execute the following command on terminal
```sh
cd %userprofile%\esp
git clone https://github.com/SRA-VJTI/Wall-E_v2.2-beta.git
cd Wall-E_v2.2
git checkout dev
```
## Step 2 : Installation of SRA-Board Components
Insatalling SRA-Boarch Components in the Components folder
```sh
cd %userprofile%\esp\Wall-E_v2.2.beta/components
git clone https://github.com/SRA-VJTI/sra-board-component.git
```
# For Linux 
## Step 1 : Cloning the Wall-E Git Repo
To clone the Repo just execute the following command on terminal
```sh
git clone https://github.com/SRA-VJTI/Wall-E_v2.2-beta.git
cd Wall-E_v2.2-beta
git checkout dev
```
## Step 2 : Installing the Necessary Prerequisites(ESP-IDF etc)
Run the following commands for a quick install on Linux-based systems:
```sh
cd Wall-E_v2.2-beta
sudo chmod +x wall_e_install.sh
./wall_e_install.sh
```
After this, test the hello_world example in the same terminal; if it runs without any errors, log out & log back in.
```sh
cd ~/esp/esp-idf/examples/get-started/hello_world
idf.py flash monitor
```
## Step 3 : Installation of SRA-Board Components
Insatalling SRA-Boarch Components in the Components folder
```sh
cd Wall-E_v2.2.beta/components
git clone https://github.com/SRA-VJTI/sra-board-component.git
```
# Commands
This is the Basic Procedure For Compiling and Flashing a Project code on the ESP32
## Step 1 : Set Up Environtment variables
In the terminal where you are going to use ESP-IDF, run:
* For Linux
```sh
. $HOME/esp/esp-idf/export.sh
```
* For Windows
```sh
%userprofile%\esp\esp-idf\export.bat
```
Through this command specify the Folder/Project in which we will to be using ESP-IDF 
## Step 2 : Start a Project
Now you are ready to prepare your application for ESP32.
```sh
cd %userprofile%\esp
xcopy /e /i %IDF_PATH%\examples\get-started\hello_world hello_world
```
## Step 3 : Connect Your Device
Now connect your ESP32 board to the computer and check under what serial port the board is visible.
Serial ports have the Name
* Starting with /dev/tty
## Step 4 : Configure
Now you are ready to prepare your application for ESP32.
```sh
cd ~/esp/hello_world #Navigating to the file
idf.py set-target esp32 #Command for Setting the Target 
idf.py menuconfig # Command for Opening the Configuration Menu
```
If the previous steps have been done correctly, the following menu appears :
<p align="center">
  <img src="Assets/project-configuration1.png">
</p>

* This menu helps us to change the Parameters. Currenty we dont need to change anything.
## Step 5 : Build the Project
Build the project by running:
```sh
idf.py build #Command for building the code
```
This command will compile the application and all ESP-IDF components, then it will generate the bootloader, partition table, and application binaries.
<p align="center">
  <img src="Assets/build.png">
</p>

## Step 6 : Flash onto the Device
Flash the binaries that you just built (bootloader.bin, partition-table.bin and hello-world.bin) onto your ESP32 board by running.:
* Note : Press Down the Boot Button on ESP32 and then execute the Flash command
```sh
idf.py -p PORT [-b BAUD] flash 
```
* For Linux 
* PORT - /dev/ttyUSB0 (`idf.py -p /dev/ttyUSB0 -b 2000000 flash`)
* For Windows 
* PORT - /COM1 (`idf.py -p /COM1 -b 2000000 flash`)
* (Depending on the port you used for connecting the board the port can vary from /dev/ttyUSB0 and Zero can be replaced by any other consecutive number)


