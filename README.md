# Real Time Image-to-text-convertor
Image to Text is basically real time OCR(optical character Recognition)
It extract the text data from the image and translate to the normal text data which is readable for the human,
The use of OCR by enterprises increases operational efficiency to ensure every customer is satisfied with the services rendered. This technology 
enables enterprises and organisations to improve customer experience by making unstructured content searchable.

This Project was based on detecting of TEXT data from active camera and capture the words which is displayed in TFT LCD screen of Raspberry pi, This model is created by using python script and single board cpu (raspberry pi 4) 

## Raspberry Pi Touch Display
The Raspberry Pi Touch Display is an LCD display which connects to the Raspberry Pi through the DSI connector. In some situations, it allows for the use of both the HDMI and LCD displays at the same time (this requires software support).
![MPI7001-02](https://user-images.githubusercontent.com/42414598/139531359-9877cb44-d8b9-4d0e-bde0-3d61ff9f2ede.jpg)


## Board Support
# Step 1, Install Raspbian official image
Download the latest image from the official download.
Install the system according to the official tutorial steps.
# Step 2, modify the “config.txt”
After the programming of Step1 is completed, open the config.txt file of TF card root directory and
add the following code at the end of the file, save and eject Micro SD Card safely:
max_usb_current=1
hdmi_force_hotplug=1
config_hdmi_boost=7
hdmi_group=2
hdmi_mode=87
hdmi_drive=1
display_rotate=0
hdmi_cvt 1024 600 60 6 0 0 0
# Step 3, Drive the 5inch HDMI Display-B with the Raspberry Pi
Insert the TF Card to Raspberry Pi, connect the Raspberry Pi and LCD by HDMI cable; connect USB cable to one of the four USB ports of Raspberry Pi,
and connect the other end of the USB cable to the USB port of the LCD; then supply power to Raspberry Pi; after that if the display and touch both are OK,
it means drive successfully (please use the full 2A for power supply).


# how to operate:
## step 1: Place any paper with Black text data 
## step 2: hold the object or paper in front of the camera and click on the red button , an image will be capture 
## step 3: Then wait for 2 seconds your image will be processed 
## step 4: Text will be display on the Black and White terminal in the screen

# Circuit Diagram 
![Push button AI Vehcile Detection System ](https://user-images.githubusercontent.com/42414598/137728743-3485b7cb-738a-4523-b3fb-ebf959fe8b20.jpg)


# Resources
Material Required for the Projects 
## Hardwares 
* Raspberry Pi 4
* USB web Camera
* Push Button 
* 7 inch LCD display screen 
* Power sources 
## Programming 
* OpenCV Package 4.5
* Python 3.9 
* Tesseract-OCR
# Methodology
Hardware connections very important which provides the overview of circuit in the project , if connections are correct then output will be displayed on the screen of LCD   
Python is a wonderful and powerful programming language that's easy to use (easy to read and write) and, with Raspberry Pi, lets you connect your project to the real world.
## Step 1: Install Python Packages 
* A package is basically a directory with Python files and a file with the name __init__.py. This means that every directory inside of the Python path, which contains a file named __init__.py, will be treated as a package by Python. It's possible to put several modules into a Package.
* Raspberry pi operated by Raspbian is a Debian-based engineered especially for the Raspberry Pi and it is the perfect general-purpose OS for Raspberry users 
* Install Raspberry pi GPIO packages: pip install RPi.GPIO
* Type " pinout " in Terminal of Raspberry pi 
## Step 2 : Install Opencv in Raspberry pi  
###### to get the current status
* $ sudo rpi-eeprom-update
###### if needed, to update the firmware
* $ sudo rpi-eeprom-update -a
* $ sudo reboot 
###### Version check.
Before you install OpenCV on your Raspberry Pi 4, it is time for a final version check. Many readers just jump into the guide, skipping the introduction, often because they have already an operating system working. For those, please give the command uname -a and check your version.
* $ python3 --version
###### Dependencies.
The OpenCV software uses other third-party software libraries. These have to be installed first. Some come with the Raspbian operating system, others may have been gathered over time, but it's better to be safe than sorry, so here is the complete list. Only the latest packages are installed by the procedure.
* $ sudo apt-get update
* $ sudo apt-get upgrade
* $ sudo apt-get install cmake gfortran
* $ sudo apt-get install libjpeg-dev libtiff-dev libgif-dev
* $ sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev
* $ sudo apt-get install libgtk2.0-dev libcanberra-gtk*
* $ sudo apt-get install libxvidcore-dev libx264-dev libgtk-3-dev
* $ sudo apt-get install libtbb2 libtbb-dev libdc1394-22-dev libv4l-dev
* $ sudo apt-get install libopenblas-dev libatlas-base-dev libblas-dev
* $ sudo apt-get install libjasper-dev liblapack-dev libhdf5-dev
* $ sudo apt-get install protobuf-compiler
* $ sudo apt-get install qt5-default
* $ cd ~
* $ wget -O opencv.zip https://github.com/opencv/opencv/archive/4.5.0.zip
* $ wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/4.5.0.zip

* $ unzip opencv.zip
* $ unzip opencv_contrib.zip
* $ mv opencv-4.5.0 opencv
* $ mv opencv_contrib-4.5.0 opencv_contrib
###### Install a virtual environment.
Step one is some administration. We only use Python 3 because the support of Python 2.7 has stopped at the beginning of 2020. You have first to determine your Python 3 version   and location.
The Python location in the above commands was /usr/bin/python3.7. This location is passed as an argument in the echo command. The next step is installing the virtual      environment software. This can be done with the following commands.
* $ sudo pip3 install virtualenv
* $ sudo pip3 install virtualenvwrapper
* $ echo "export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3.7" >> ~/.bashrc
###### reload profile
* $ source ~/.bashrc
* $ echo "export WORKON_HOME=$HOME/.virtualenvs" >> ~/.bashrc
* $ echo "source /usr/local/bin/virtualenvwrapper.sh" >> ~/.bashrc
* $ source ~/.bashrc
* $ mkvirtualenv cv450
###### without sudo!!!!
* $ pip3 install numpy
##### Build Make 
* $ cd ~/opencv/
* $ mkdir build
* $ cd build
* $ cmake -D CMAKE_BUILD_TYPE=RELEASE \
          -D CMAKE_INSTALL_PREFIX=/usr/local \
          -D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib/modules \
          -D ENABLE_NEON=ON \
          -D ENABLE_VFPV3=ON \
          -D WITH_OPENMP=ON \
          -D WITH_OPENCL=OFF \
          -D BUILD_TIFF=ON \
          -D WITH_FFMPEG=ON \
          -D WITH_TBB=ON \
          -D BUILD_TBB=ON \
          -D BUILD_TESTS=OFF \
          -D WITH_EIGEN=OFF \
          -D WITH_GSTREAMER=OFF \
          -D WITH_V4L=ON \
          -D WITH_LIBV4L=ON \
          -D WITH_VTK=OFF \
          -D WITH_QT=OFF \
          -D OPENCV_ENABLE_NONFREE=ON \
          -D INSTALL_C_EXAMPLES=OFF \
          -D INSTALL_PYTHON_EXAMPLES=OFF \
          -D BUILD_opencv_python3=TRUE \
          -D OPENCV_GENERATE_PKGCONFIG=ON \
          -D BUILD_EXAMPLES=OFF ..
 * Before we can start the actual build, the memory swap space needs to be enlarged. For daily use a swap memory of 100 Mbyte is sufficient. However, with the massive build ahead of use, extra memory space is crucial. Enlarge the swap space with the following command.
* $ sudo nano /etc/dphys-swapfile
* This command opens Nano, a very lightweight text editor, with the system file dphys-swapfile. With the arrow keys, you can move the cursor to the CONF_SWAPSIZE line where the new value 2048 can be entered. Next, close the session with the <Ctrl+X> key combination. With <Y> and <Enter> changes are being saved in the same file.
* $ sudo /etc/init.d/dphys-swapfile stop
* $ sudo /etc/init.d/dphys-swapfile start
* $ make -j4
###### Make.
Now everything is ready for the great build. This takes a lot of time. Be very patient is the only advice here. Don't be surprised if at 99% your build seems to be crashed. That is 'normal' behaviour. Even when your CPU Usage Monitor gives very low ratings like 7%. In reality, your CPU is working so hard it has not enough time to update these usage numbers correctly.
You can speed things up with four cores working simultaneously (make -j4). On a Raspberry Pi 4, it takes just over an hour to build the whole library. Sometimes the system crashes for no apparent reason at all at 99% or even 100%. In that case, restart all over again, as explained at the end of this page, and rebuild with make -j1.
Probably you get a whole bunch of warnings during the make. Don't pay to much attention to it. They are generated by subtle differences in template overload functions due to little version differences. 
* $ sudo make install
* $ sudo ldconfig
###### cleaning (frees 300 KB)
* $ make clean
* $ sudo apt-get update
          
## Tesseract: 
Python-tesseract is an optical character recognition (OCR) tool for python. That is, it will recognize and “read” the text embedded in images.
* The latest installers can be downloaded here: https://github.com/UB-Mannheim/tesseract/wiki
* pip install pytesseract

# Operations
* ---> Place any paper with Black text data 
* ---> hold the object or paper in front of the camera and click on the red button , an image will be capture 
* ---> Then wait for 2 seconds your image will be processed 
* ---> Text will be display on the Black and White terminal in the screen
# Conclusion 
Optical Character Recognition is a field of research in Artificial Intelligence and Computer Vision that consists in extracting text from images.
Today OCR is knowing an unprecedented revolution thanks to using Artificial Intelligence tools.OCR became not only an image-to-text traditional conversion process but also a human mistakes checker.
# Reference 
* https://github.com/UB-Mannheim/tesseract/wiki
* https://projects.raspberrypi.org/en/projects/using-pip-on-raspberry-pi
* https://pypi.org/project/pytesseract/
* https://qengineering.eu/install-opencv-4.5-on-raspberry-pi-4.html

