Networking
=============================

Overview
--------

Networking in vscout has both a wide area network (WAN) and a local area
netowrk (LAN) aspect to it. For our MVP, only syncing through LAN will be
supported. Details on other networking features will be discussed in the
:ref:`Future Plan` section.

LAN Syncing
--------------------------

The requirements for LAN syncing are that frames or packets of data be sent
to and from devices (ideally full-duplex for less latency). It should be able
to find only other devices with the app installed. Authentication after the fact
will ensure the device is part of the same organization. There is no client
server architecture and dedicated servers; it is decentralized.

Initiating the Connection (UDP Broadcast)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

After first opening the app and specifiying an organization and access level,
a UDP broadcast on a specified port will be initiated. Other devices with the
app will listen on the specified port and store the IPv4 and IPv6 address of
the device if possible (some routers don't support IPv4 and others IPv6).
At the end of the session, the IP addresses will be deleted (consider caching).
The standard protocol for initiating a TCP and WebSockets connection will then
occur. This will be done using the dart:io or/and connectivity library. 

WebSockets Frames
~~~~~~~~~~~~~~~~~~~~

Each WebSockets frame will have a payload format of most probably JSON. On
either end, there will most likely be JSON validators to prevent processing
corrupt or incomplete transmissions.


.. _Future Plan:

Future Plan
-----------------

WAN
~~~~~~
In a much later version, syncing databases through WANs may be supported,
but won't be a priority unless there is high demand. This could be useful
at Worlds and Provs where team members can attempt to scout from the
livestreams remotely. 

VexDB API
~~~~~~~~~~~

Later on, we will be able to use the VexDB API to obtain match level
information throught the internet to supplement or verify user entries.

Security
~~~~~~~~~~~~

Eventually there will be encryption added to the WebSockets frames
in order to prevent sniffing attacks.
