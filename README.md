# Authenticated Operating Channel Information (A-OCI)
Prevention of KRACK attack using A-OCI and its formal analysis. This repository contains
a code base related to the A-OCI implementation both on the authenticator and the supplicant side.
The integrity checks on the PMKID to validate that the channel is not sent in a WPA2 handshake.
The empirical analysis of the A-OCI implementation in the form of packet-level verification. 
The formal analysis uses a tamarin prover by including A-OCI-related parameters like signs and channels
in the WPA2 handshake messages. Finally, the KRACK script to run the KRACK Attack



**Features:**

- A-OCI
- Empirical Analysis
- Formal Analysis
- Integrity Checks
- KRACK script
  
## Building

- Install dependencies (Scapy)
```
sudo apt install python-pip
pip install scapy
```


## Compile and Run different code base

- A-OCI - In A-OCI, the folder contains the hostapd and the wpa_supplicant folder. The updated files are mainly wpa.c and wpa_auth.c. The folder also contains the debug file after execution
- executing the modified hostapd and wpa_supplicant code. The debug contains the A-OCI parameters of 45 bytes sent from the supplicant to the authentication in the WPA key field.
- The compilation and the execution of the code can be performed with the following commands.
```
To compile and run the hostapd
cd A-OCI/hostapd/hostapd
Compile:  make BINDIR=/usr/sbin LIBDIR=/usr/lib
Run:  ./hostapd -i interface_name -c /etc/hostapd/hostapd.confg -d
To compile and run the supplicant
cd A-OCI/wpa_supplicant/wpa_supplicant
Compile: make BINDIR=/usr/sbin LIBDIR=/usr/lib 
Run:  ./wpa_supplicant -i interface_name -c /etc/wpa_supplicant/configuration_file -d
```

-Empirical Analysis

```
- Empirical Analysis - In this folder, the communication between the modified hostapd and supplicant is present in the form the captured pcap file. The
folder also contains the snapshot of the pcap file which contains the modified code packet as a Proof-of-concept. To capture this traffic a Wi-Fi adapter
is configured in monitor mode and the communication is captured.

```


- Formal Analysis

```
-Formal Analysis - In this folder, the formal analysis code is present and implemented in the tamarin prover. The updated model file is present in the .spthy format.
To generate the automatic proof following commands can be used. The generate.sh can be updated to run for the different .spthy models. To run this script
tamarin prover needs to be installed with its corresponding dependencies. Please refer the tamarin prover developer website for detailed installation https://tamarin-prover.com/

cd formal-analysis/
./proof_generation/generate_proof.sh
```
- Integrity Check
```
- Integrity Check - This folder contains the integrity check performed to check whether the channel is sent in the WPA2 handshake messages. It contains
the captured pcap file after performing the different experiments by setting up the authenticator on the different channels and looking into the changes in the PMKID.
```
- KRACK Script

```
-KRACK script - This folder contains the KRACK script to run the KRACK attack. To run this script different dependencies along with multiple Wi-Fi adapters need to be
configured in different managed, master, and monitor modes.
Please follow the github of the KRACK attack developer for further details https://github.com/vanhoefm/krackattacks-poc-zerokey

```
