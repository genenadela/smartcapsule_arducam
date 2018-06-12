Arducam 5MP: ov5642

1. Install the following: wiringpi, i2c-tools, libi2c-dev, python-smbus
sudo apt-get install git

2. Make a directory in the Pi Zero, and change to that directory
sudo mkdir /home/camera
cd /home/camera

3. Clone Arducam library
sudo git clone https://github.com/arducam/raspberrypi

4. Compile library
cd raspberrypi/ArduCAM4Pi/
sudo make

5. Hardware Connections
CS 		Pin 11
MOSI  	Pin 19
MISO  	Pin 21
SCK  	Pin 23
GND  	Pin 6
3.3V 	Pin 1
SDA 	Pin 3
SCL 	Pin 5

6. Enable I2C and SPI in config
sudo nano /boot/config.txt

find the parameters in the file:

										#---------------------
										#dtparam=i2c_arm=on
										#dtparam=spi=on

remove the comments so that:

										#---------------------
										dtparam=i2c_arm=on
										dtparam=spi=on
										
then do:
sudo raspi-config

Go to interfacing and enable I2C and SPI. Reboot.

7. To test, go the the directory you installed the ArduCAM4Pi/

cd /home/camera/raspberrypi/ArduCAM4Pi/

sudo ./ov5642_capture -c test.jpg 640x480

The test file should appear in the same directory.
