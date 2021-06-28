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
*to get the current status
$ sudo rpi-eeprom-update
*if needed, to update the firmware
 $ sudo rpi-eeprom-update -a
 $ sudo reboot  
