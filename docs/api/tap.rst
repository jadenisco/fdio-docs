.. _Developerdocs-fdiovpp-mastersrcvnetunixtapapi:

.. toctree::

TAP
====================================================================
Source: /vnet/unix/tap.api

This file defines vpe control-plane API messages for the Linux kernel TAP device driver

tap_connect
################################################################
Initialize a new tap interface with the given paramters

Returns:
*****************************************


Parameters:
*****************************************

u8 - ip4_mask_width
------------------------------------------------------------------


u8 - ip4_address_set
------------------------------------------------------------------


u32 - custom_dev_instance
------------------------------------------------------------------


u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - ip6_mask_width
------------------------------------------------------------------


u8 - use_random_mac
------------------------------------------------------------------
let the system generate a unique mac address

u8 - ip6_address_set
------------------------------------------------------------------


u8[64] - tag
------------------------------------------------------------------


u8 - renumber
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8[6] - mac_address
------------------------------------------------------------------
mac addr to assign to the interface if use_radom not set

u8[16] - ip6_address
------------------------------------------------------------------


u8[64] - tap_name
------------------------------------------------------------------
name to associate with the new interface

u8[4] - ip4_address
------------------------------------------------------------------



tap_connect_reply
################################################################
Reply for tap connect request

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


tap_modify
################################################################
Modify a tap interface with the given paramters

Returns:
*****************************************


Parameters:
*****************************************

u32 - custom_dev_instance
------------------------------------------------------------------


u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - use_random_mac
------------------------------------------------------------------
let the system generate a unique mac address

u32 - sw_if_index
------------------------------------------------------------------
interface index of existing tap interface

u8 - renumber
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8[6] - mac_address
------------------------------------------------------------------
mac addr to assign to the interface if use_radom not set

u8[64] - tap_name
------------------------------------------------------------------
name to associate with the new interface


tap_modify_reply
################################################################
Reply for tap modify request

Returns:
*****************************************


Parameters:
*****************************************

i32 - retval
------------------------------------------------------------------
return code

u32 - sw_if_index
------------------------------------------------------------------
software index if the modified tap interface

u32 - context
------------------------------------------------------------------
returned sender context, to match reply w/ request


tap_delete
################################################################
Delete tap interface

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
interface index of existing tap interface

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


sw_interface_tap_details
################################################################
Reply for tap dump request

Returns:
*****************************************


Parameters:
*****************************************

u8[64] - dev_name
------------------------------------------------------------------
Linux tap device name

u32 - sw_if_index
------------------------------------------------------------------
software index of tap interface

u32 - context
------------------------------------------------------------------


