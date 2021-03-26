## For Linux 
### Step 1 :Install the Prequisites
Some tools need to be installed on the computer before proceeding to the next steps.
```sh
sudo apt-get install git wget flex bison gperf python3 python3-pip python3-setuptools cmake ninja-build ccache libffi-dev libssl-dev dfu-util libusb-1.0-0
```
### Step 2 : Get ESP-IDF
To build applications for the ESP32, you need the software libraries provided by Espressif in ESP-IDF repository.
```sh
mkdir -p ~/esp
cd ~/esp
git clone --recursive https://github.com/espressif/esp-idf.git
```
ESP-IDF will be downloaded into ~/esp/esp-idf
### Step 3 : Set up the tools
Aside from the ESP-IDF, you also need to install the tools used by ESP-IDF, such as the compiler, debugger, Python packages, etc.
```sh
cd ~/esp/esp-idf
./install.sh
```
### Step 4 : Set up the environment variables
The installed tools are not yet added to the PATH environment variable. To make the tools usable from the command line, some environment variables must be set.
```sh
. $HOME/esp/esp-idf/export.sh
```
Note the space between the leading dot and the path!
### Step 5 : Start a Project
Now you are ready to prepare your application for ESP32.
```sh
cd %userprofile%\esp
xcopy /e /i %IDF_PATH%\examples\get-started\hello_world hello_world
```
### Step 6 : Connect Your Device
Now connect your ESP32 board to the computer and check under what serial port the board is visible.
Serial ports have the Name
* Starting with /dev/tty
### Step 7 : Configure
Now you are ready to prepare your application for ESP32.
```sh
cd ~/esp/hello_world
idf.py set-target esp32
idf.py menuconfig
```
### Step 8 : Build the Project
Build the project by running:
```sh
idf.py build
```
### Step 9 : Flash onto the Device
Flash the binaries that you just built (bootloader.bin, partition-table.bin and hello-world.bin) onto your ESP32 board by running.:
* Note : Press Down the Boot Button on ESP32 and then execute the Flash command
```sh
idf.py -p PORT [-b BAUD] flash
```
* Example Port - /dev/ttyUSB0 
* (Depending on the port you used for connecting the board the port can vary from /dev/ttyUSB0 and Zero can be replaced by any other consecutive number)