Description
===========
This scripts aims to fix network crash on WSL2 Windows 10 host when using USB Tethering.

Prerequisites
=============

In order for this script to work you need to enable network sharing on the main NIC to the WSL Adapter (vEthernet WSL).

Script
=============

The following script must be executed as root

.. code-block:: none

  # Clean the ip addresses
  ip -4 address flush label eth0

  # Setup our static ip within the subnet of the vEthernet WSL NIC
  ip addr add 192.168.137.10/24 dev eth0

  # Clean and add default route
  ip route delete default
  ip route add default via 192.168.137.1
