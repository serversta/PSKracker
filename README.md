# Overview [![License: GPL v3](https://img.shields.io/badge/License-GPL%20v3-blue.svg)](https://github.com/soxrok2212/PSKracker/blob/master/LICENSE)

**PSKracker** is a collection of WPA/WPA2/WPS default algorithms/password generators/pingens written in C.

# Requirements

GCC compiler

# Setup

**Download**

`git clone https://github.com/soxrok2212/pskracker`

**Build**

```bash
cd pskracker/src
make
```

**Install**

`sudo make install`

# Usage

```
Usage: pskracker <arguments>

Required Arguments:
	
	-t, --target	: Target model number

Optional Arguments:
	-b, --bssid	: BSSID of target
	-W, --wps	: Output possible WPS pin(s) only
	-s, --serial	: Serial number
	-f, --force	: Force full output
	-h, --help	: Display help/usage
```

# Usage Example

`pskracker -t <target> -e <security/encryption type> -s <serial number> -m <mac address>`

# Supported Models

Types: bruteforce and psk
Bruteforce means the output of PSKracker should be piped into a password recovery tool, such as Hashcat.
Psk means you will be given one (or a handful) of possible keys.

```
ATT Arris NVG589 [bruteforce]
ATT Arris NVG599 [bruteforce]

Comcast/Xfinity Cisco DPC3939 [psk][bssid]
Comcast/Xfinity Cisco DPC3941 [psk][bssid]
Comcast/Xfinity Arris TG1682G [psk][bssid]
```

# Targeted Example

```
$ pskracker -t nvg599
  ...
  aaae7uas5wrj
  aaae7v3qrvbu
  ...
```

```
$ pskracker -t dpc3941 -b 112233445566
  PSK: 5756C3915966657704
```

# Supported OS

PSKracker should compile on macOS, Windows (with cygwin), and any Linux system.  
It has been tested on macOS High Sierra 10.13.2, Windows 10, and Ubuntu 16.04.  
Embedded systems are not supported, though may still work. PSKracker is intended to be run on true pentesting environments (Desktop/Workstation/Laptop). Some psk generators (not bruteforce) are still suitable for embedded systems, but I will not provide support due to the nature of the tool.

# Acknowledgements

Thank you to `rofl0r`, `wiire` and `datahead` for my first C endeavors!  
Thank you to `AAnarchYY` for research dedication and motivation.

# Disclaimer

This project is intended for testing and securing your own networks or networks you have permission to audit. This is not intended to be used maliciously.

In publishing these documents and source code, I (and other developers/contributors) take no responsibility for your actions. What you do with everything in this repository, as well as any information online, is your responsibility. Use this repo wisely. In light of anything I may have failed to mention regarding laws to any country or civilized region, this does not grant the excuse to include the developers or contributors in any way in your legal statements or prosecutor. Thank you.

# References

### Xfinity Home Security Network Algorithm
* [CVE-2017-9476](https://nvd.nist.gov/vuln/detail/CVE-2017-9476)
* [Bastille DEFCON 25 Whitepaper](https://github.com/BastilleResearch/CableTap/blob/master/doc/pdf/DEFCON-25-Marc-Newlin-CableTap-White-Paper.pdf)

### ATT NVG589 and NVG599 Algorithm
* [Hashcat Forum (mrfancypants)](https://hashcat.net/forum/thread-6170-post-35739.html#pid35739)
