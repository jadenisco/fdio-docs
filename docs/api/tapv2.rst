.. _Developerdocs-fdiovpp-mastersrcvnetdevicestaptapv2api:

.. toctree::

TAPV2
====================================================================
Source: /vnet/devices/tap/tapv2.api

This file defines vpe control-plane API messages for the Linux kernel TAP device driver

tap_create_v2
################################################################
Initialize a new tap interface with the given paramters

Returns:
*****************************************


Parameters:
*****************************************

u8 - host_ip4_addr_set
------------------------------------------------------------------
host IPv4 ip address should be set

u8[6] - host_mac_addr
------------------------------------------------------------------
host side interface mac address

u16 - rx_ring_sz
------------------------------------------------------------------
the number of entries of RX ring

u32 - id
------------------------------------------------------------------
interface id, 0xffff means auto

u8 - host_mac_addr_set
------------------------------------------------------------------
host side interface mac address should be set

u8[64] - host_bridge
------------------------------------------------------------------
host bridge to attach interface to

u8[64] - host_namespace
------------------------------------------------------------------
host namespace to attach interface to

u8[6] - mac_address
------------------------------------------------------------------
mac addr to assign to the interface if use_radom not set

u8[64] - host_if_name
------------------------------------------------------------------
host side interface name

u8 - host_namespace_set
------------------------------------------------------------------
host namespece should be set

u8 - host_ip4_prefix_len
------------------------------------------------------------------
host IPv4 ip address prefix length

u8 - host_if_name_set
------------------------------------------------------------------
host side interface name should be set

u8[4] - host_ip4_addr
------------------------------------------------------------------
host IPv4 ip address

u8[16] - host_ip6_addr
------------------------------------------------------------------
host IPv6 ip address

u8 - host_bridge_set
------------------------------------------------------------------
host bridge should be set

u8 - host_ip6_prefix_len
------------------------------------------------------------------
host IPv6 ip address prefix length

u8 - host_ip6_gw_set
------------------------------------------------------------------
host IPv6 default gateway should be set

u8[16] - host_ip6_gw
------------------------------------------------------------------
host IPv6 default gateway */ define tap_create_v2 { u32 client_index; u32 context; u32 id; u8 use_random_mac; u8 mac_address[6]; u16 tx_ring_sz; /* optional, default is 256 entries, must be power of 2 */ u16 rx_ring_sz; /* optional, default is 256 entries, must be power of 2

u8 - use_random_mac
------------------------------------------------------------------
let the system generate a unique mac address

u8 - host_ip4_gw_set
------------------------------------------------------------------
host IPv4 default gateway should be set

u16 - tx_ring_sz
------------------------------------------------------------------
the number of entries of TX ring

u8 - host_ip6_addr_set
------------------------------------------------------------------
host IPv6 ip address should be set

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8[4] - host_ip4_gw
------------------------------------------------------------------
host IPv4 default gateway

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


tap_create_v2_reply
################################################################
Reply for tap create reply

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


tap_delete_v2
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


sw_interface_tap_v2_details
################################################################
Reply for tap dump request

Returns:
*****************************************


Parameters:
*****************************************

u8 - host_ip6_prefix_len
------------------------------------------------------------------
host IPv6 ip address prefix length; 0 if unset

u8[16] - host_ip6_addr
------------------------------------------------------------------
host IPv6 ip address

u8[6] - host_mac_addr
------------------------------------------------------------------
mac address assigned to the host side of the interface

u8[64] - host_bridge
------------------------------------------------------------------
host bridge the interface is attached into

u16 - rx_ring_sz
------------------------------------------------------------------
the number of entries of RX ring

u32 - sw_if_index
------------------------------------------------------------------
software index of tap interface

u8[64] - host_namespace
------------------------------------------------------------------
host namespace the interface is attached into

u8[64] - dev_name
------------------------------------------------------------------
Linux tap device name

u8[64] - host_if_name
------------------------------------------------------------------
host side interface name

u32 - context
------------------------------------------------------------------


u8[4] - host_ip4_addr
------------------------------------------------------------------
host IPv4 ip address

u16 - tx_ring_sz
------------------------------------------------------------------
the number of entries of TX ring

u8 - host_ip4_prefix_len
------------------------------------------------------------------
host IPv4 ip address prefix length; 0 if unset

u32 - id
------------------------------------------------------------------
interface id

