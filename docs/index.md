# Welcome to the sum-opensource documentation

This project provides a wrapper for the JANUS library for a more convenient use, both stand-alone and integrated as part of the [SubSeaPulse SuM](https://www.subseapulse.com/products/#sum) project.

When used stand-alone, sum-opensource constitutes a complete acoustic SDM software stack, taking care of the whole transmission and reception processes: from message coding/decoding and modulation to interfacing with audio interfaces.
More precisely, the suite will manage DAC/ADC access, perform DSP operations using JANUS, manage transmission and reception plus, when installed and run on the SuM, GPIO functions for controlling the TX/RX switch.
The project's software is intended to be run on Linux, therefore this guide provides information for installation and usage only for these systems.

If embedded in the SuM this module instead allows the modem's software suite to make use of the official JANUS library allowing powerful, noise-resistant underwater communication while taking advantage of the SuM's flexibility and versatility.

## Index
Please refer to the different sections of this guide:

* [Installation](install.md) contains the steps to install the software.
* [Usage](usage.md) contains information about the command-line usage and parameters.
* [Home](index.md) - this page: index and credits.

## Credits

[SubSeaPulse Srl](https://www.subseapulse.com/)
