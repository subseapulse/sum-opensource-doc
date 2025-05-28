# Usage of the sum-opensource module

After [installation](install.md), the binary file `janus_executable` will be created inside the `janus_executable` folder. That file is executable and has to run for the modem to operate.

## Parameters

`janus_executable` can be run specifying either no parameters or all of them.
When specifying parameters, the user must provide all of them in the following order:

	./janus_executable sampling_frequency center_frequency bandwidth tx_gain wot hd mac src_addr dest_addr verbosity
	
Previous versions of the executable (release v1.0) used less parameters, as listed below:

	./janus_executable sampling_frequency center_frequency bandwidth tx_gain src_addr dest_addr verbosity
When no parameters are specified default values are used.

The parameters are explained in detail in the table below. Default values are also reported.

|Parameter name		    |Info								                            |Valid type [and range]		    |Default value	|Version constraints|
|-----------------------|---------------------------------------------------------------|-------------------------------|---------------|-------------------|
|sampling_frequency	    |Sampling rate used by the DAC/ADC				                |`int`				            |44100		    |                   |
|center_frequency	    |Central frequency of the signal (depends on JANUS band)	    |`int`				            |11520		    |                   |
|bandwidth		        |Signal bandwidth (depends on JANUS band)			            |`int`				            |4160		    |                   |
|tx_gain		        |Transmitter gain (power)					                    |`float`[0.01-0.99]		        |0.9		    |                   |
|wot		            |(preliminary) JANUS wake-up-tone support (**tx only!**)        |0=disabled,1=enabled		    |0		        |v1.1 onwards       |
|hd		                |Half-duplex mode (disables rx when transmitting)               |0=disabled,1=enabled		    |1		        |v1.1 onwards       |
|mac		            |Additional MAC layer support for addressing (as below)         |0=disabled,1=enabled		    |0		        |v1.1 onwards       |
|src_addr		        |Source node (modem) identification number			            |`int`[1-15]			        |1		        |                   |
|dest_addr		        |Identification number of the destination node (modem)		    |`int`[0-15], **0=broadcast**	|0		        |                   |
|verbosity		        |Verbosity level of the program					                |0, 1, 2			            |0		        |                   |


## Usage
**`janus_executable` needs to run for the whole time the modem is operational.** The process will both wait for user data to be transmitted and simultaneously will listen to the audio input for incoming signals. Depending on the specified verbosity level, it will also print statistics on sent/incoming frames: level 0 won't output anything while level 2 will print all statistics about sent and incoming data frames. Level 1 will print partial statistics only.
If you wish to use a single terminal for running the modem software and sending/receiving data you may run the modem in background using `./janus_executable [params]&` (not to use with verbosity >0).

By default, the executable will send and receive data to/from the user through a TCP socket: the user must connect to port 55555 in order to visualize incoming messages and send ones. On Linux, **nc** may be used: the appropriate syntax for connection will be `nc localhost 55555`.

Version 1.0 of the software includes by default a basic MAC system where all packets include a 1-byte header with source address (src_addr) and destination address (dest_addr) that are evaluated on packet reception to whether decode or discard the packet. Starting from version 1.1 this behaviour can be toggled with the 'mac' parameter: if disabled, the provided 'src_addr' and 'dest_addr' are simply ignored.
