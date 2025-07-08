Installation
=============================
## 1. Dependencies and prerequisites
Before installation, the following dependencies must be satisfied:

* JANUS library, to be installed in the default path. Refer to [the JANUS website](https://www.januswiki.com/) for download and installation procedures.

	`Note: usage of JANUS ver. 3.0.5 is recommended`
	
	**Please note** if you plan to use JANUS at a sampling frequency of 192kHz please patch the JANUS code before installing it [as described in this guide](https://github.com/subseapulse/sum-opensource-doc/raw/refs/heads/master/janus-hf-patch.pdf).

* libasound2 library, which can be installed by running

	`sudo apt-get install libasound2`

* libgpiod-dev library, which can be installed by running

	`sudo apt install libgpiod-dev`



## 2. Module installation

You may obtain the project's source code by cloning its Git repository using the following command:

	git clone https://github.com/subseapulse/sum-opensource.git

The project source files include an installation script named `installer.sh` which supports the following options:

	-h			List parameters (these)
	-p <path>	Prefix path (usually, home directory)
	-c			Clean repository

Standard installation is usually carried out typing the command
`./installer.sh -p /home/<youruser>`
where `<youruser>` is to be replaced by your system username.

After successfull installation you will find the `janus_executable` binary file inside the `janus_executable` directory. Running that file sets the hardware up and prepares for communication: see the [Usage](usage.md) section for further guidance.
