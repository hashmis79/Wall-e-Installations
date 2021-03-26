#Walle installation
##Linux Installation
###Step 1 :Install the Prequisites
Some tools need to be installed on the computer before proceeding to the next steps.
'''sh
sudo apt-get install git wget flex bison gperf python3 python3-pip python3-setuptools cmake ninja-build ccache libffi-dev libssl-dev dfu-util libusb-1.0-0
'''
###Step 2 : Get ESP-IDF
To build applications for the ESP32, you need the software libraries provided by Espressif in ESP-IDF repository.
'''sh
mkdir -p ~/esp
cd ~/esp
git clone --recursive https://github.com/espressif/esp-idf.git
'''
ESP-IDF will be downloaded into ~/esp/esp-idf
###Step 3 : Set up the tools
Aside from the ESP-IDF, you also need to install the tools used by ESP-IDF, such as the compiler, debugger, Python packages, etc.
'''sh
cd ~/esp/esp-idf
./install.sh
'''
###Step 4 : Set up the environment variables
The installed tools are not yet added to the PATH environment variable. To make the tools usable from the command line, some environment variables must be set.
'''sh
. $HOME/esp/esp-idf/export.sh
'''