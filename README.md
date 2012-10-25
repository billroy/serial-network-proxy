# bitty.py: serial network telnet server in python

This is a serial port proxy.  It makes your arduino's serial connection available over the network connection of your PC, for connection via telnet, nc, or your favorite telnet client.

You can unplug one Arduino and plug in another and bitty will find it.  And the network port and baud rate are adjustable.

## Requires:
	python
	pyserial from http://pyserial.wiki.sourceforge.net/pySerial

## Usage:

To use: first, start the serial-to-net proxy and leave it running:

	$ python bitty.py [options]

and then, in another terminal window, connect to it with your favorite telnet or nc program:

	$ nc localhost 8080
	$ telnet localhost 8080
	$ telnet arduino.bitlash.net 8080

Plug in Arduino and you should connect up automatically.  You'll see something like this:

	$ nc localhost 8080
	g'day from bitty 1.0 -- type 'logout' to disconnect
	Connecting to /dev/tty.usbserial-A600emm9... connected.
	bitlash here! v2.0 (c) 2012 Bill Roy -type HELP- 943 bytes free
	> ls
	...

To exit: Type 'logout' when done for a clean disconnect.

	> logout
	Disconnected.

You can terminate bitty with ^C.


## Options

	-h, --help            show this help message and exit
	-p PORT, --port=PORT  network connection port [8080]
	-u USBDEVICE, --usbdevice=USBDEVICE
						name of USB serial port device for serial connection
						[/dev/tty.usbserial*]
	-b BAUD, --baud=BAUD  baud rate for port specified by -u [57600]
	-k, --keyboard-passthru
	-d, --debug           

The keyboard-passthru option enables simultaneous use of a keyboard (connected via a usbserial terminal monitor) and the network connection to control bitlash on the arduino.

The debug option shows details of the serial streams.
