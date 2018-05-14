.. _Developerdocs-fdiovpp-mastersrcvnetbondingbondapi:

.. toctree::

BOND
====================================================================
Source: /vnet/bonding/bond.api

This file defines vpe control-plane API messages for the bonding device driver

bond_create
################################################################
Initialize a new bond interface with the given paramters

Returns:
*****************************************


Parameters:
*****************************************

u8 - lb
------------------------------------------------------------------
load balance, optional (0=l2, 1=l34, 2=l23) valid for xor and lacp modes. Otherwise ignored

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - use_custom_mac
------------------------------------------------------------------
if set, mac_address is valid

u8 - mode
------------------------------------------------------------------
mode, required (1=round-robin, 2=active-backup, 3=xor, 4=broadcastcast, 5=lacp)

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8[6] - mac_address
------------------------------------------------------------------
mac addr to assign to the interface if use_custom_mac is set


bond_create_reply
################################################################
Reply for bond create reply

Returns:
*****************************************


Parameters:
*****************************************

i32 - retval
------------------------------------------------------------------
return code

u32 - sw_if_index
------------------------------------------------------------------
software index allocated for the new tap interface

u32 - context
------------------------------------------------------------------
returned sender context, to match reply w/ request


bond_delete
################################################################
Delete bond interface

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - sw_if_index
------------------------------------------------------------------
interface index of slave interface

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


bond_enslave
################################################################
Initialize a new bond interface with the given paramters

Returns:
*****************************************


Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - is_long_timeout
------------------------------------------------------------------
90 seconds vs default 3 seconds neighbor timeout

u32 - sw_if_index
------------------------------------------------------------------
slave sw_if_index

u8 - is_passive
------------------------------------------------------------------
interface does not initiate the lacp protocol, remote must be active speaker

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u32 - bond_sw_if_index
------------------------------------------------------------------
bond sw_if_index


bond_enslave_reply
################################################################
Reply for bond enslave reply

Returns:
*****************************************


Parameters:
*****************************************

i32 - retval
------------------------------------------------------------------
return code

u32 - context
------------------------------------------------------------------
returned sender context, to match reply w/ request


bond_detach_slave
################################################################
bond detach slave

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - sw_if_index
------------------------------------------------------------------
interface index of slave interface

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


sw_interface_bond_details
################################################################
Reply for bond dump request

Returns:
*****************************************


Parameters:
*****************************************

u8 - lb
------------------------------------------------------------------
load balance algo

u32 - slaves
------------------------------------------------------------------
config slave count

u32 - sw_if_index
------------------------------------------------------------------
software index of bond interface

u8 - mode
------------------------------------------------------------------
bonding mode

u32 - context
------------------------------------------------------------------


u32 - active_slaves
------------------------------------------------------------------
active slaves count

u8[64] - interface_name
------------------------------------------------------------------
name of interface


sw_interface_slave_dump
################################################################
bond slave dump

Returns:
*****************************************


Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - sw_if_index
------------------------------------------------------------------
interface index of bond interface

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


sw_interface_slave_details
################################################################
Reply for slave dump request

Returns:
*****************************************


Parameters:
*****************************************

u8 - is_passive
------------------------------------------------------------------


u8 - is_long_timeout
------------------------------------------------------------------
90 seconds vs default 3 seconds neighbor timeout

u8[64] - interface_name
------------------------------------------------------------------
name of interface

u32 - sw_if_index
------------------------------------------------------------------
software index of slave interface

u32 - context
------------------------------------------------------------------


