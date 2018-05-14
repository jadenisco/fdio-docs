.. _Developerdocs-fdiovpp-mastersrcvppstatsstatsapi:

.. toctree::

STATS
====================================================================
Source: /vpp/stats/stats.api

This file defines the stats API

want_stats
################################################################
Want Stats, enable/disable ALL stats updates

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
1 = enable stats, 0 = disable

u32 - pid
------------------------------------------------------------------
pid of process requesting stats updates

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


want_interface_simple_stats
################################################################
Want Interface Simple Stats, register for detailed interface stats

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
1 = enable stats, 0 = disable

u32 - pid
------------------------------------------------------------------
pid of process requesting stats updates  Please consider using want_per_interface_simple_stats with sw_if_index=~0

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


want_per_interface_simple_stats
################################################################
Want Per Interface simple Stats, register for continuous stats

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
1 = enable stats, 0 = disable

u32 - pid
------------------------------------------------------------------
pid of process requesting stats updates

u32 - num
------------------------------------------------------------------
number of sw_if_indexes

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u32[num] - sw_ifs
------------------------------------------------------------------
array of sw_if_index


want_interface_combined_stats
################################################################
Want Interface Combined Stats, register for continuous stats

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
1 = enable stats, 0 = disable

u32 - pid
------------------------------------------------------------------
pid of process requesting stats updates  Please consider using want_per_interface_combined_stats with sw_if_index=~0

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


want_per_interface_combined_stats
################################################################
Want Per Interface Combined Stats, register for continuous stats

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
1 = enable stats, 0 = disable

u32 - pid
------------------------------------------------------------------
pid of process requesting stats updates

u32 - num
------------------------------------------------------------------
number of sw_if_indexes

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u32[num] - sw_ifs
------------------------------------------------------------------
array of sw_if_index


want_ip4_fib_stats
################################################################
Want IP4 FIB Stats, register for continuous stats

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
1 = enable stats, 0 = disable

u32 - pid
------------------------------------------------------------------
pid of process requesting stats updates

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


want_ip6_fib_stats
################################################################
Want IP6 FIB Stats, register for continuous stats

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
1 = enable stats, 0 = disable

u32 - pid
------------------------------------------------------------------
pid of process requesting stats updates

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


want_ip4_mfib_stats
################################################################
Want IP4 muilticast FIB Stats, register for continuous stats

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
1 = enable stats, 0 = disable

u32 - pid
------------------------------------------------------------------
pid of process requesting stats updates

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


want_ip6_mfib_stats
################################################################
Want IP6 multicast FIB Stats, register for continuous stats

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
1 = enable stats, 0 = disable

u32 - pid
------------------------------------------------------------------
pid of process requesting stats updates

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


want_ip4_nbr_stats
################################################################
Want IP4 NBR Stats, register for continuous stats

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
1 = enable stats, 0 = disable

u32 - pid
------------------------------------------------------------------
pid of process requesting stats updates

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


want_ip6_nbr_stats
################################################################
Want IP6 NBR Stats, register for continuous stats

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
1 = enable stats, 0 = disable

u32 - pid
------------------------------------------------------------------
pid of process requesting stats updates

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


vnet_interface_simple_counters
################################################################
Simple stats counters structure

Returns:
*****************************************
manual_print manual_endian

Parameters:
*****************************************

u8 - vnet_counter_type
------------------------------------------------------------------


u32 - count
------------------------------------------------------------------
number of counters, equal to the number of interfaces in this stats block

u32 - first_sw_if_index
------------------------------------------------------------------
first sw index in block of index, counts

u64[count] - data
------------------------------------------------------------------
contiguous block of u64 counters  vnet_counter_type defined in enums - plural - in vnet/interface.h


vnet_interface_combined_counters
################################################################
Combined stats counters structure

Returns:
*****************************************
manual_print manual_endian

Parameters:
*****************************************

u8 - vnet_counter_type
------------------------------------------------------------------


u32 - count
------------------------------------------------------------------
number of counters, equal to the number of interfaces in this stats block

u32 - first_sw_if_index
------------------------------------------------------------------
first sw index in block of index, counts

vl_api_vlib_counter_t[count] - data
------------------------------------------------------------------
contiguous block of vlib_counter_t structures  vnet_counter_type defined in enums - plural - in vnet/interface.h


vnet_per_interface_simple_counters
################################################################
Simple per interface stats counters structure

Returns:
*****************************************
manual_print manual_endian

Parameters:
*****************************************

u32 - count
------------------------------------------------------------------
number of elements in message

u32 - timestamp
------------------------------------------------------------------
u32 vlib timestamp for control plane

vl_api_vnet_simple_counter_t[count] - data
------------------------------------------------------------------



vnet_per_interface_combined_counters
################################################################
Combined stats counters structure per interface

Returns:
*****************************************
manual_print manual_endian

Parameters:
*****************************************

u32 - count
------------------------------------------------------------------
number of elements in message

u32 - timestamp
------------------------------------------------------------------
u32 vlib timestamp for control plane

vl_api_vnet_combined_counter_t[count] - data
------------------------------------------------------------------



vnet_get_summary_stats
################################################################
Request for a single block of summary stats

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


vnet_get_summary_stats_reply
################################################################
Reply for vnet_get_summary_stats request

Returns:
*****************************************


Parameters:
*****************************************

u64[2] - total_pkts
------------------------------------------------------------------


i32 - retval
------------------------------------------------------------------
return code for request

u64[2] - total_bytes
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

f64 - vector_rate
------------------------------------------------------------------



stats_get_poller_delay
################################################################
Get delay between polling statistics

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


stats_get_poller_delay_reply
################################################################
Get delay between polling statistics reply

Returns:
*****************************************


Parameters:
*****************************************

u32 - delay
------------------------------------------------------------------
poller delay

i32 - retval
------------------------------------------------------------------
return code for request

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


want_udp_encap_stats
################################################################
Want UDP encap Stats, register for continuous stats

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - enable
------------------------------------------------------------------
1 = enable stats, 0 = disable

u32 - pid
------------------------------------------------------------------
pid of process requesting stats updates

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


udp_encap_counter
################################################################
Stat for one UDP encap object

Returns:
*****************************************
typeonly manual_print manual_endian

Parameters:
*****************************************

u64 - bytes
------------------------------------------------------------------
number of bytes sent

u64 - packets
------------------------------------------------------------------
number of packets sent

u32 - id
------------------------------------------------------------------
The ID of the object, same as passed for the create

