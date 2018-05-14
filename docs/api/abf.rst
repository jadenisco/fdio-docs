.. _Developerdocs-fdiovpp-mastersrcpluginsabfabfapi:

.. toctree::

ABF
====================================================================
Source: /plugins/abf/abf.api

This file defines the vpp control-plane API messages used to control the ABF plugin

abf_plugin_get_version
################################################################
Get the plugin version

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


abf_plugin_get_version_reply
################################################################
Reply to get the plugin version

Returns:
*****************************************


Parameters:
*****************************************

u32 - major
------------------------------------------------------------------
Incremented every time a known breaking behavior change is introduced

u32 - minor
------------------------------------------------------------------
Incremented with small changes, may be used to avoid buggy versions

u32 - context
------------------------------------------------------------------
returned sender context, to match reply w/ request

