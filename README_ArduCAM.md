Arducam 5MP: ov5642

1. Install the following: wiringpi, i2c-tools, libi2c-dev, python-smbus:
	```
	sudo apt-get install git
	sudo apt-get install wiringpi
	sudo apt-get install i2c-tools
	sudo apt-get install libi2c-dev
	sudo apt-get install python-smbus
	```

2. Make a directory in the Pi Zero, and change to that directory
	```
	sudo mkdir /home/camera
	cd /home/camera
	```

3. Clone Arducam library
	```
	sudo git clone https://github.com/arducam/raspberrypi
	```

4. Compile library
	```
	cd raspberrypi/ArduCAM4Pi/
	sudo make
	```

5. Hardware Connections
	```
	CS 	Pin 11
	MOSI  	Pin 19
	MISO  	Pin 21
	SCK  	Pin 23
	GND  	Pin 6
	3.3V 	Pin 1
	SDA 	Pin 3
	SCL 	Pin 5
	```

6. Enable I2C and SPI in config
	```
	sudo nano /boot/config.txt
	```

6a.find the parameters in the file:

	```
	#dtparam=i2c_arm=on
	#dtparam=spi=on
	```
6b.remove the comments so that:

	```
	dtparam=i2c_arm=on
	dtparam=spi=on
	```
										
then do:

	```
	sudo raspi-config
	```

Go to interfacing and enable I2C and SPI. Reboot.

7. Go to the directory where ArduCAM4Pi was installed, and change the define for the camera to fit the chosen camera. Comment out the unused camera
	```
	#define ov5642
	```
8. To test, go the the directory you installed the ArduCAM4Pi/
	```
	cd /home/camera/raspberrypi/ArduCAM4Pi/
	sudo ./ov5642_capture -c test.jpg 640x480
	```

The test file should appear in the same directory.
