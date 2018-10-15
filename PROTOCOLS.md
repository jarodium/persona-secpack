# PROTOCOLS #

## Overview ##

As the one responsible for managing security on the Core systems some protocols must be in place so that data in the network is particulary safe, so all communication between systems and devices is encrypted.
The core philosophy should be that any device can transmit/receive encrypted data as fast as possible and that process of encryption/decryption is not taxing for the device.

## Network ##

The network is built with 4 Core Systems in place ( Home, SeckPack, Dummy and Hub ).

- Adding more Hubs to the network requires manual installation and definition in Home, which in turn propagates this change to SeckPack and Dummy.

- Each Hub is responsible of finding new devices automatically through "linear discovery" and then, relay that information to SeckPack.
   - Seckpack will then register the new device, give it an internal id, store the command schema and generate a secure key. This key is then relayed to the Hub, which in turn sends it to the Device in order to store the key.
   
   .... work in progress
