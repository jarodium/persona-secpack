# PROTOCOLS #

## Overview ##

As the one responsible for managing security on the Core systems some protocols must be in place so that data in the network is particulary safe, so all communication between systems and devices is encrypted.
The core philosophy should be that any device can transmit/receive encrypted data as fast as possible and that process of encryption/decryption is not taxing for the device.

## Network ##

The network is built with 4 Core Systems in place ( Home, SecPack, Dummy and Hub for each house division ). Devices are connected to the network through the Hub.

All devices, every day, at a random time between work hours and with milisecond precision should receive a new key. This key should be in the form of an simple MD5 hash, containing one of a hundred methods of working this hash. For example: Take Unix Timestamp, add it an unique id with a random prefix ( uniqueid() from PHP ). Or another, Take the current windspeed, multiply it by the sqrt of PI and subtract the current temperatura in celsius.

Ridicilous as it seem the resulting hash will be used to encrypt/decrypt data

# Network - Hubs #

- The Hub concept is removed from the system as it brings up the problem of adding/removing/updating device physical locations. To solve this, each device would be given a location ( point ) in the floor plan of the house. It is replaced by the SecPack's network monitoring service.

# Network - SecPack #

 
- SecPack will maintain a ledger containing the device and then, register the new device, give it an internal id, store the command schema and generate a secure key. This key is then relayed to the Device in order to store the key.
   
"Linear discovery" is when a device first connects to a Hub and asks SecPack if the device is registered. If the Device is not registered, the device sends it's command schema to the SecPack and waits for a key and the assigned id. If the Device is already registered it receives a new key to be stored. This new key is to be frequently updated to a random X times a day (where X is a random number 3 to 9)

Note: Advancements on networking and bandwidth should allow for this number of random times a day to be executed up to 20 times a day or by a hourly basis, but one should account for the number of devices and possible burdens in the household.


# Network - Core #

- Core will manage the frontend-to-backend commands. It will be responsible to relay commands to SecPack, which in turn, will be relaying commands to the device after proper whitelisting check on the commands the device has.

