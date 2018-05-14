.. _Developerdocs-fdiovpp-mastersrcvnetpgpgapi:

.. toctree::

PG
====================================================================
Source: /vnet/pg/pg.api

This file defines packet-generator interface APIs.

pg_create_interface
################################################################
PacketGenerator create interface request

Returns:
*****************************************


Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u32 - interface_id
------------------------------------------------------------------
interface index


pg_create_interface_reply
################################################################
PacketGenerator create interface response

Returns:
*****************************************


Parameters:
*****************************************

i32 - retval
------------------------------------------------------------------
return value for request

u32 - sw_if_index
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


pg_capture
################################################################
PacketGenerator capture packets on given interface request

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u8 - is_enabled
------------------------------------------------------------------
1 if enabling streams, 0 if disabling

u32 - count
------------------------------------------------------------------
number of packets to be captured

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - interface_id
------------------------------------------------------------------
pg interface index

u32 - pcap_name_length
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8[pcap_name_length] - fi
------------------------------------------------------------------



pg_enable_disable
################################################################
Enable / disable packet generator request

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - is_enabled
------------------------------------------------------------------
1 if enabling streams, 0 if disabling

u32 - stream_name_length
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8[stream_name_length] - 
------------------------------------------------------------------


