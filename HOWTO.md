#How to set up a Raspberry Pi Wixel receiver#

>Based on using the Raspbian distribution.

First login to your Pi and set it up with a .local name, see: [assigning a .local address](http://www.howtogeek.com/167190/how-and-why-to-assign-the-.local-domain-to-your-raspberry-pi/)

Make sure packages are installed:

`sudo apt-get update && sudo apt-get -y install git screen python python-pycurl wget sdcc`

Download the usb wixel python code:

`git clone https://github.com/jamorham/python-usb-wixel-xdrip.git`

`cd python-usb-wixel-xdrip`

Run the auto-installer:

`sh forusb.sh`

This will compile the wixel firmware and install the python script

If all is good you should see "Waiting for connections" on the screen 
and a flashing yellow light on the Wixel until it gets the first dex signal.

xDrip+ [versions after 20th Feb 2017](https://github.com/NightscoutFoundation/xDrip/releases) allow for easy setup by accessing the `System Status` -> `IP collector` page and your raspberry pi should be automatically detected. Tapping on its address on this page allows you to automatically configure the settings if you have followed the instructions above for [assigning a .local address](http://www.howtogeek.com/167190/how-and-why-to-assign-the-.local-domain-to-your-raspberry-pi/)

Alternatively, within [xDrip+](https://jamorham.github.io/#xdrip-plus) select `WiFi Wixel` in `Data source` settings section and add `raspberry.local:50005` in to `List of Receivers` or whatever your Raspberry Pi hostname is.

Using `raspberry.local:50005` may not work on all android devices, if it doesn't try instead using the IP address, eg `192.168.5.123:50005` in the `List of Receivers` replacing with the real ip address.

After reboot you can check the script is running with:
`sudo screen -r wixel`
