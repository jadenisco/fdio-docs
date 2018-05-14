.. _Developerdocs-fdiovpp-mastersrcvnetfeaturefeatureapi:

.. toctree::

FEATURE
====================================================================
Source: /vnet/feature/feature.api

This file defines VPP feature control-plane API messages which are generally called through a shared memory interface.

feature_enable_disable
################################################################
Feature path enable/disable request

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u8 - enable
------------------------------------------------------------------
1 = on, 0 = off

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - sw_if_index
------------------------------------------------------------------
the interface

u8[64] - arc_name
------------------------------------------------------------------


u8[64] - feature_name
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

