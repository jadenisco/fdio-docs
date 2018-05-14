.. _Developerdocs-fdiovpp-mastersrcpluginslacplacpapi:

.. toctree::

LACP
====================================================================
Source: /plugins/lacp/lacp.api

This file defines vpe control-plane API messages for the bonding device driver

sw_interface_lacp_details
################################################################
Reply for lacp dump request

Returns:
*****************************************


Parameters:
*****************************************

u16 - actor_system_priority
------------------------------------------------------------------
actor system priority

u16 - partner_port_number
------------------------------------------------------------------
partner port number

u32 - tx_state
------------------------------------------------------------------
tx machine state

u16 - partner_port_priority
------------------------------------------------------------------
partner port priority

u32 - ptx_state
------------------------------------------------------------------
ptx machine state

u16 - actor_port_number
------------------------------------------------------------------
actor port number

u16 - partner_key
------------------------------------------------------------------
partner key

u8[6] - actor_system
------------------------------------------------------------------
actor system

u32 - sw_if_index
------------------------------------------------------------------
software index of slave interface

u8 - partner_state
------------------------------------------------------------------
partner state

u8[64] - bond_interface_name
------------------------------------------------------------------
name of bond interface

u16 - actor_key
------------------------------------------------------------------
actor key

u8[6] - partner_system
------------------------------------------------------------------
partner system

u16 - partner_system_priority
------------------------------------------------------------------
partner system priority

u32 - context
------------------------------------------------------------------


u32 - rx_state
------------------------------------------------------------------
rx machine state

u32 - mux_state
------------------------------------------------------------------
mux machine state

u8[64] - interface_name
------------------------------------------------------------------
name of slave interface

u8 - actor_state
------------------------------------------------------------------
actor state

u16 - actor_port_priority
------------------------------------------------------------------
actor port priority

