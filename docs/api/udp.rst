.. _Developerdocs-fdiovpp-mastersrcvnetudpudpapi:

.. toctree::

UDP
====================================================================
Source: /vnet/udp/udp.api

This file defines vpp UDP control-plane API messages which are generally called through a shared memory interface.

udp_encap_add_del
################################################################
Add / del table request A table can be added multiple times, but need be deleted only once.

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u16 - src_port
------------------------------------------------------------------


u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - is_add
------------------------------------------------------------------


u8[16] - src_ip
------------------------------------------------------------------


u32 - table_id
------------------------------------------------------------------
table ID associated with the encap destination

u16 - dst_port
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8[16] - dst_ip
------------------------------------------------------------------


u8 - is_ip6
------------------------------------------------------------------


u32 - id
------------------------------------------------------------------


