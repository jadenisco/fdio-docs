.. _Developerdocs-fdiovpp-mastersrcpluginsflowprobeflowprobeapi:

.. toctree::

FLOWPROBE
====================================================================
Source: /plugins/flowprobe/flowprobe.api

This file defines the vpp control-plane API messages used to control the flowprobe plugin

flowprobe_tx_interface_add_del
################################################################
Enable / disable per-packet IPFIX recording on an interface

Returns:
*****************************************
autoreply manual_print

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - is_add
------------------------------------------------------------------
add address if non-zero, else delete

u32 - sw_if_index
------------------------------------------------------------------
index of the interface */ autoreply manual_print define flowprobe_tx_interface_add_del { /* Client identifier, set from api_main.my_client_index */ u32 client_index;  /* Arbitrary context, so client can match reply to request */ u32 context;  /* Enable / disable the feature */ u8 is_add; u8 which;  /* 0 = ipv4, 1 = l2, 2 = ipv6 */  /* Interface handle

u8 - which
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

