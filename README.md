# Real Time Image-to-text-convertor
Image to Text is basically real time OCR(optical character Recognition)
It extract the text data from the image and translate to the normal text data which is readable for the human,
The use of OCR by enterprises increases operational efficiency to ensure every customer is satisfied with the services rendered. This technology 
enables enterprises and organisations to improve customer experience by making unstructured content searchable.

This Project was based on detecting of TEXT data from active camera and capture the words which is displayed in TFT LCD screen of Raspberry pi, This model is created by using python script and single board cpu (raspberry pi 4) 
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
###### Step one is some administration. We only use Python 3 because the support of Python 2.7 has stopped at the beginning of 2020. You have first to determine your Python 3 version   and location.
###### The Python location in the above commands was /usr/bin/python3.7. This location is passed as an argument in the echo command. The next step is installing the virtual      environment software. This can be done with the following commands.
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
* make -j4
