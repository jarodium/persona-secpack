# PROTOCOLS #

## Overview ##

As the one responsible for managing security on the Core systems some protocols must be in place so that data in the network is particulary safe, so all communication between systems and devices is encrypted.
The core philosophy should be that any device can transmit/receive encrypted data as fast as possible and that process of encryption/decryption is not taxing for the device.

## Network ##

The network is built with 4 Core Systems in place ( Home, SecPack, Dummy and Hub for each house division ). Devices are connected to the network through the Hub.

All devices, every day, at a random time between work hours and with milisecond precision should receive a new key. This key should be in the form of an simple MD5 hash, containing one of a hundred methods of working this hash. For example: Take Unix Timestamp, add it an unique id with a random prefix ( uniqueid() from PHP ). Or another, Take the current windspeed, multiply it by the sqrt of PI and subtract the current temperatura in celsius.

Ridicilous as it seem the resulting hash will be used to encrypt/decrypt data

# Network - Hubs #

- Adding more Hubs to the network requires manual installation and definition in Home, which in turn propagates this change to SecPack and Dummy.

- Each Hub is responsible of finding new devices automatically through "linear discovery" and then, relay that information to SecPack.
   - Seckpack will then register the new device, give it an internal id, store the command schema and generate a secure key. This key is then relayed to the Hub, which in turn sends it to the Device in order to store the key.
   - This ledger could also contain which HUB belongs the device, but we would then have to find a new procedure to "move" one device from one Hub to another.
   
Linear discovery is when a device first connects to a Hub and asks SecPack if the device is registered. If the Device is not registered, the device sends it's command schema to the SecPack and waits for a key and the assigned id. If the Device is already registered it receives a new key to be stored.

- Hubs will only receive commands from devices and the SecPack, so any device adition/removal must be properly updated in the hosts file.

# Network - Core #

- All Core communication to a Device...

