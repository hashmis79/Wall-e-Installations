# Commands
This is the basic procedure for compiling and flashing a code on the ESP32

### Step 1 : Set Up Environtment variables
In the terminal where you are going to use ESP-IDF, run:
- For Linux/MacOS  
   - Run `get_idf` command.
   - If `get_idf` command shows an error, use `. $HOME/esp/esp-idf/export.sh` command.
- For Windows
   - Run `%userprofile%\esp\esp-idf\export.bat` command.

Through this command specify the Folder/Project in which we will to be using ESP-IDF 

### Step 2 : Start a Project
Now you are ready to prepare your application for ESP32.
* For Linux/MacOS -
```sh
cd ~/esp
cp -r $IDF_PATH/examples/get-started/hello_world .
```
* For Windows -
```sh
cd %userprofile%\esp
xcopy /e /i %IDF_PATH%\examples\get-started\hello_world hello_world
```
### Step 3 : Connect Your Device
Connect your ESP32 board to the computer and check under what serial port the board is visible.
* Linux : `/dev/tty`
* MacOS : `/dev/cu`
* Windows : `COM1`

### Step 4 : Configure

* For Linux/MacOS -
```sh
cd ~/esp/hello_world #Navigating to the file
idf.py set-target esp32 #Command for Setting the Target 
idf.py menuconfig # Command for Opening the Configuration Menu
```
* For Windows -
```sh
cd %userprofile%\esp\hello_world #Navigating to the file
idf.py set-target esp32 #Command for Setting the Target
idf.py menuconfig #Command for Opening the Configuration
```
If the previous steps have been executed correctly, you screen will show this:
<p align="center">
  <img src="./documentation/Assets/project-configuration1.png">
</p>

### Step 5 : Build the Project
Build the project by running:
* Same for Both Linux and Windows
```sh
idf.py build #Command for building the code
```
This command will compile the application and all ESP-IDF components, then it will generate the bootloader, partition table, and application binaries.
<p align="center">
  <img src="./documentation/Assets/build.png">
</p>

### Step 6 : Flash onto the Device
Flash the binaries that you just built (bootloader.bin, partition-table.bin and hello-world.bin) onto your ESP32 board by running.:
```sh
idf.py -p PORT [-b BAUD] flash 
```
* For Linux 
   * PORT - /dev/ttyUSB0 (`idf.py -p /dev/ttyUSB0 -b 2000000 flash`)
* For MacOS
   * PORT - /dev/cu.usbserial-0001(`idf.py -p /dev/cu.usbserial-0001 -b 2000000 flash`) 
* For Windows 
   * PORT - /COM1 (`idf.py -p /COM1 -b 2000000 flash`)
* Depending on the port you used for connecting the board the port can vary from /dev/ttyUSB0 and Zero can be replaced by any other consecutive number
and for windows /COM1 one can be replaced by other number depending on the port to which you have connected esp.
* Note : In case you are unable to flash Press Down the Boot Button on ESP32 and then execute the Flash command

### Step 7 : Flash onto the Device
* For seeing the output given by esp32 we use this command after flashing
```sh
idf.py flash monitor
```


