.. _Developerdocs-fdiovpp-mastersrcvnetqosqosapi:

.. toctree::

QOS
====================================================================
Source: /vnet/qos/qos.api

This file defines QoS record and mark API messages which are generally called through a shared memory interface.

qos_record_enable_disable
################################################################
Enable/Disable QoS recording The QoS bits from the packet at the specified input layer are copied into the packet. Recording should be used in conjunction with marking

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------


u8 - input_source
------------------------------------------------------------------
The input source/layer at which the QoS bits are copied from the packet. See qos_source_t.

u8 - enable
------------------------------------------------------------------
enable=1 or disable the feautre

u32 - sw_if_index
------------------------------------------------------------------
The interface on which recording is enabled.

u32 - context
------------------------------------------------------------------



qos_egress_map_update
################################################################
Update a QoS Map A QoS map, translates from the QoS value in the packet set by the 'record' feature, to the value used for output in the 'mark' feature. There is one row in the map for each input/record source. The MAP is then applied to the egress interface at for a given output source

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------


vl_api_qos_egress_map_row_t[4] - rows
------------------------------------------------------------------
one row (per-input source) of output values

u32 - map_id
------------------------------------------------------------------
client provided identifier for the map

u32 - context
------------------------------------------------------------------



qos_egress_map_delete
################################################################
Delete a Qos Map

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------


u32 - map_id
------------------------------------------------------------------
ID of the map to delete

u32 - context
------------------------------------------------------------------



qos_mark_enable_disable
################################################################
Enable/Disable QoS marking The QoS bits from the packet are mapped (using the desired egress map) into the header of the 'output-source'. Marking should be used in conjunction with recording

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u8 - enable
------------------------------------------------------------------
enable=1 or disable the feautre

u32 - map_id
------------------------------------------------------------------
The ID of the MAP in which the translation from input to output is performed.

u32 - client_index
------------------------------------------------------------------


u32 - sw_if_index
------------------------------------------------------------------
The interface on which recording is enabled.

u8 - output_source
------------------------------------------------------------------
The output source/layer at which the QoS bits are written into the packet. See qos_source_t.

u32 - context
------------------------------------------------------------------


