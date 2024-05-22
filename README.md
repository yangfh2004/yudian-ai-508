# YUDIAN AI-508 Temperature Controller Driver
The LabVIEW driver for YUDIAN Artificial Intelligence Temperature Controller, used by many automatic controlled furnaces (e.g. furnaces made by MTI Corp.) You may use this driver to easily integrate your smart furnaces into your process control software and fabrication workflow.

## Contribution
I developed this driver during my spare time when I was still working on electronics packaging and semiconductor fabrication. The driver was originally shared on NI forum but not very accessible.

You are welcome to make contributions to this repo by creating an issue or pull-request. I will review them every month and maintain this repo with my best efforts.

## Usage
This is a third-party LabVIEW driver for RS485 communication bus. MIT license.

### VISA API
If you have a VISA time-out problem. This is how to debug it:

- First use its official software and see if it works, if so, it indicates the software problem, otherwise, you have the hardware problem. 
You also need check with your controller, it has to allow the remote control mode or it supports remote control.

- If you are using the right cable and the official software comes with the controller does work, you need use a serial port communication monitor software to monitor all the communication on the serial port and carefully compare it to the communication log data with official software. I use [this tool](http://www.serial-port-monitor.com/)

- It is free while I was debugging this. Once you find the difference between this driver and the official one, revise the code according to the official protocol and it shall work. You may contribute your update this repo and it could benefit everyone.

- It might because that YUDIAN recently upgrade the firmware of AI-508 and the existing driver no longer works. If so, you may debug this version and update to the new version. And you are welcome to upload your revision to share with other engineers.

### RS485 Bus
I recommend to use a generic USB/RS485 converter. This driver only supports RS485 protocol. **This is NOT RS232. if you use most common RS232, it won't work.**

To configure the RS485, you need setup it according to the user manual of your converter and your PC. Then, if you have multiple devices on the RS485 bus, make sure that you choose the correct address, e.g. You need to use the corresponding address number in every sub vi. 

### Programming
You may setup the number of steps/segments in your controller program. You also need to set the temperatures and time for each segment. You can also download current program from the controller to double check it. 

While your program is running, you may use a while loop (or a thread) to get the real-time temperature reading periodically and integrate it with any other control logic.

All those sub vi, you can find in the sub folder and they have been tested. You may stop the program using stop vi. In all, go thru the source code first, you will find the driver is straightforward and easy to understand and use.


