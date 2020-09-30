# BLEBeacon Dataset
The BLEBeacon dataset is a collection of Bluetooth Low Energy (BLE)  advertisement packets/traces generated from BLE beacons carried by people following their daily routine inside a university building for a whole month. A network of Raspberry Pi 3 (RPi)-based edge devices were deployed inside a multi-floor facility continuously gathering BLE advertisement packets and storing them in a cloud-based environment. The focus is on presenting a real-life realization of a location-aware sensing infrastructure, that can provide insights for smart sensing platforms, crowd-based applications, building management, and user-localization frameworks. 

Since 2019, the BLEBeacon dataset is part of the Community Resource for Archiving Wireless Data At Dartmouth (CRAWDAD): https://crawdad.org/unm/blebeacon/20190312/

To cite the dataset: 
> Dimitrios Sikeridis, Ioannis Papapanagiotou, Michael Devetsikiotis, CRAWDAD dataset unm/blebeacon (v. 2019‑03‑12), downloaded from https://crawdad.org/unm/blebeacon/20190312, Mar 2019.

> [Cite using BibTeX](https://crawdad.org/unm/blebeacon/20190312/)
 

# Technical Summary

## Operation




Users carried off-the-shelf Gimbal Series 10 iBeacons that continuously transmit BLE advertisement packets. The periodic transmission rate for each beacon is set to 1 Hz, with omni-directional antenna propagation setting, and transmission power of 0 dBm. The backbone of the system is a network of Raspberry Pi 3 (RPi), able to collect all generated packets. 

Regarding system operation two approaches were utilized in parallel:


![RSSI](https://github.com/dimisik/BLEBeacon-Dataset/blob/master/images/ARCH.png)
* RSSI Report: all advertisement packet receptions from beacon devices are directly reported to a server with a message that contains the beacon/user ID, the packet's Received Signal Strength Indicator (RSSI), a reception timestamp, and finally the ID of the RPi that received the advertisement (Fig. 1).


![Check](https://github.com/dimisik/BLEBeacon-Dataset/blob/master/images/check.png)
* Check-In/Check-Out Report: each RPi scanner continuously manages a list of current occupants/users in its proximity. A check in-timestamp is created during the user's initial entry, and while this beacon is still being detected by the RPi, a last seen-timestamp is updated. When the beacon is no longer detected a Check-In/Check-Out report packet is created and sent to the server containing the beacon/user ID, the check in-timestamp, the last seen-timestamp, and finally the ID of the RPi (Fig. 2). A thirty-second period is used to ensure that the occupant exited the RPi proximity.


## Dataset

The BLEBeacon dataset contains two files, one with the trial readings from the RSSI report operation (RSSI Report file) and the other from the Check-In/Check-Out report operation (Check-In Check-Out Report file). 
The RSSI Report file contains the following entries:
* Entry_id: unique identifier of a packet in the dataset.
* Beacon_id: unique identifier of the occupant/beacon.
* RSSI: the Received Signal Strength Indicator (RSSI) in dB.
* Timestamp: Date (Month/Day/Year) and Unix time (Hour:Second) of the advertisement packet reception moment from the Rpi.
* RPi_id: RPi that received the packet.


The Check-In/Check-Out Report file contains Entry_id, Beacon_id, and RPi_id as described above with the addition of two entries namely:
* In_time: Date (Month/Day/Year) and Unix time (Hour:Second) of the moment a user enters the RPi's vicinity and the first advertisement packet is received.
* Out_time: Date (Month/Day/Year) and Unix time (Hour:Second) of the last advertisement packet received from the same user by the specific RPi.


# Readme

Further information and a detailed description of the sensing infrastructure setup, the real-subject trial, and the BLEBeacon dataset can be found in: D. Sikeridis, I. Papapanagiotou, M. Devetsikiotis,  ["BLEBeacon: A Real-Subject Trial Dataset from Mobile Bluetooth Low Energy Beacons"](https://arxiv.org/abs/1802.08782), arXiv preprint arXiv:1802.08782, 2018.


### Research Papers


Publications related to the BLEBeacon dataset:

* D. Sikeridis, B.P. Rimal, I. Papapanagiotou, and M. Devetsikiotis, 2018. Unsupervised crowd-assisted learning enabling location-aware facilities. IEEE Internet of Things Journal, 5(6), pp.4699-4713. (Available in: https://ieeexplore.ieee.org/document/8305452)

* D. Sikeridis, M. Devetsikiotis, I. Papapanagiotou, ["Occupant Tracking in Smart Facilities: An Experimental Study"](http://ipapapa.github.io/Files/GlobalSIP_2017.pdf), IEEE GlobalSIP Symposium on Signal Processing for Smart Cities & Internet of Things, Nov. 2017, Montreal, Canada

* D. Sikeridis, M. Devetsikiotis, I. Papapanagiotou, ["A Cloud-Assisted Infrastructure for Occupancy Tracking in Smart Facilities"](http://ipapapa.github.io/Files/ICACON_2017.pdf), IBM Cloud Academy Conference (ICA CON) 2017, Wroclaw, Poland

* M. Inaya, M. Meli, D. Sikeridis, and M. Devetsikiotis, ["A Real-Subject Evaluation Trial for Location-Aware Smart Buildings"](http://ipapapa.github.io/Files/ICACON_2017.pdf),  Conference on Computer Communications Workshops (INFOCOM WKSHPS), Atlanta, GA, USA, May 1-4, IEEE 2017

A detailed survey about this area: 

* F. Zafari, I. Papapanagiotou, K. Christidis, ["Micro-location for Internet of Things equipped Smart Buildings"](http://ipapapa.github.io/Files/IEEEIOT2015.pdf), IEEE Internet of Things Journal, pp. 96-112, Feb. 2016 ([publisher link](http://ieeexplore.ieee.org/xpl/freeabs_all.jsp?arnumber=7120085))
