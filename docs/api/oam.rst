.. _Developerdocs-fdiovpp-mastersrcvppoamoamapi:

.. toctree::

OAM
====================================================================
Source: /vpp/oam/oam.api

This file defines vpe control-plane API messages which are generally called through a shared memory interface.

oam_event
################################################################
OAM event structure

Returns:
*****************************************


Parameters:
*****************************************

u8 - state
------------------------------------------------------------------


u8[4] - dst_address
------------------------------------------------------------------
dst_address[] -


want_oam_events
################################################################
Want OAM events request

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - enable_disable
------------------------------------------------------------------


u32 - pid
------------------------------------------------------------------
pid of the requesting process

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


oam_add_del
################################################################
OAM add / del target request

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - is_add
------------------------------------------------------------------
add target if non-zero, else delete

u8[4] - dst_address
------------------------------------------------------------------
dst_address[] - destination address of the target

u8[4] - src_address
------------------------------------------------------------------
src_address[] - source address to use for the updates

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u32 - vrf_id
------------------------------------------------------------------
vrf_id of the target

