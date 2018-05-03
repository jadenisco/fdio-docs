.. _ipapi:

.. toctree::

IP
=========================================
This file defines vpp IP control-plane API messages which are generally called through a shared memory interface.

ip_table_add_del
################################################################
Add / del table request A table can be added multiple times, but need be deleted only once.

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u8[64] - name
------------------------------------------------------------------
A client provided name/tag for the table. If this is not set by the client, then VPP will generate something meaningfull.

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - is_add
------------------------------------------------------------------


u32 - table_id
------------------------------------------------------------------
table ID associated with the route This table ID will apply to both the unicats and mlticast FIBs

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8 - is_ipv6
------------------------------------------------------------------
V4 or V6 table


ip_fib_dump
################################################################
Dump IP fib table

Returns:
*****************************************


Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - context
------------------------------------------------------------------



ip_fib_details
################################################################
IP FIB table response

Returns:
*****************************************
manual_endian manual_print

Parameters:
*****************************************

u32 - count
------------------------------------------------------------------
the number of fib_path in path

u8 - address_length
------------------------------------------------------------------


u8[64] - table_name
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------


u8[4] - address
------------------------------------------------------------------


u32 - table_id
------------------------------------------------------------------
IP fib table id @address_length - mask length @address - ip4 prefix

vl_api_fib_path_t[count] - path
------------------------------------------------------------------
array of of fib_path structures


ip6_fib_dump
################################################################
Dump IP6 fib table

Returns:
*****************************************


Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - context
------------------------------------------------------------------



ip6_fib_details
################################################################
IP6 FIB table entry response

Returns:
*****************************************
manual_endian manual_print

Parameters:
*****************************************

u32 - count
------------------------------------------------------------------
the number of fib_path in path

u8 - address_length
------------------------------------------------------------------
mask length

u8[64] - table_name
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------


u8[16] - address
------------------------------------------------------------------
ip6 prefix

u32 - table_id
------------------------------------------------------------------
IP6 fib table id

vl_api_fib_path_t[count] - path
------------------------------------------------------------------
array of of fib_path structures


ip_neighbor_dump
################################################################
Dump IP neighboors

Returns:
*****************************************


Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - sw_if_index
------------------------------------------------------------------
the interface to dump neighboors, ~0 == all

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8 - is_ipv6
------------------------------------------------------------------
[1|0] to indicate if address family is ipv[6|4]


ip_neighbor_details
################################################################
IP neighboors dump response

Returns:
*****************************************


Parameters:
*****************************************

u8 - is_static
------------------------------------------------------------------
[1|0] to indicate if neighbor is statically configured

u32 - sw_if_index
------------------------------------------------------------------
The interface used to reach the neighbor

u32 - context
------------------------------------------------------------------
sender context which was passed in the request

u8[6] - mac_address
------------------------------------------------------------------


u8[16] - ip_address
------------------------------------------------------------------


u8 - is_ipv6
------------------------------------------------------------------
[1|0] to indicate if address family is ipv[6|4]


ip_neighbor_add_del
################################################################
IP neighbor add / del request

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u8 - is_static
------------------------------------------------------------------


u8 - is_no_adj_fib
------------------------------------------------------------------
Do not create a corresponding entry in the FIB table for the neighbor.

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - is_add
------------------------------------------------------------------
1 to add neighbor, 0 to delete

u32 - sw_if_index
------------------------------------------------------------------
interface used to reach neighbor

u8[16] - dst_address
------------------------------------------------------------------
ip4 or ip6 address of the neighbor */ autoreply define ip_neighbor_add_del { u32 client_index; u32 context; u32 sw_if_index; /* 1 = add, 0 = delete

/* - 1
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8[6] - mac_address
------------------------------------------------------------------
l2 address of the neighbor

u8 - is_ipv6
------------------------------------------------------------------
1 for IPv6 neighbor, 0 for IPv4


set_ip_flow_hash
################################################################
Set the ip flow hash config for a fib request

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u8 - src
------------------------------------------------------------------
if non-zero include src in flow hash

u8 - reverse
------------------------------------------------------------------
if non-zero include reverse in flow hash

u8 - proto
------------------------------------------------------------------
if non-zero include proto in flow hash

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - dst
------------------------------------------------------------------
if non-zero include dst in flow hash

u8 - dport
------------------------------------------------------------------
if non-zero include dport in flow hash

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u32 - vrf_id
------------------------------------------------------------------
vrf/fib id

u8 - sport
------------------------------------------------------------------
if non-zero include sport in flow hash

u8 - is_ipv6
------------------------------------------------------------------
if non-zero the fib is ip6, else ip4


sw_interface_ip6nd_ra_config
################################################################
IPv6 router advertisement config request

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - min_interval
------------------------------------------------------------------


u8 - managed
------------------------------------------------------------------


u8 - default_router
------------------------------------------------------------------


u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - suppress
------------------------------------------------------------------


u32 - initial_interval
------------------------------------------------------------------


u32 - sw_if_index
------------------------------------------------------------------


u32 - max_interval
------------------------------------------------------------------


u8 - other
------------------------------------------------------------------


u8 - cease
------------------------------------------------------------------


u8 - ll_option
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u32 - lifetime
------------------------------------------------------------------


u8 - send_unicast
------------------------------------------------------------------


u8 - is_no
------------------------------------------------------------------


u32 - initial_count
------------------------------------------------------------------



sw_interface_ip6nd_ra_prefix
################################################################
IPv6 router advertisement prefix config request

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u8 - address_length
------------------------------------------------------------------
the prefix length

u8 - no_onlink
------------------------------------------------------------------
The prefix is not on link. Make sure this is consistent with the off_link parameter else YMMV

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - no_autoconfig
------------------------------------------------------------------
Setting for the A-flag. When set indicates that this prefix can be used for stateless address configuration.

u32 - val_lifetime
------------------------------------------------------------------
The length of time in seconds (relative to the time the packet is sent) that the prefix is valid for the purpose of on-link determination.  A value of all one bits (0xffffffff) represents infinity

u32 - sw_if_index
------------------------------------------------------------------
The interface the RA prefix information is for

u8 - no_advertise
------------------------------------------------------------------
Do not advertise this prefix

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8[16] - address
------------------------------------------------------------------
address[] - The prefix to advertise

u8 - use_default
------------------------------------------------------------------
Revert to default settings

u8 - off_link
------------------------------------------------------------------
The prefix is off link (it is not configured on the interface) Configures the L-flag, When set, indicates that this prefix can be used for on-link determination.

u8 - is_no
------------------------------------------------------------------
add/delete

u32 - pref_lifetime
------------------------------------------------------------------
The length of time in seconds (relative to the time the packet is sent) that addresses generated from the prefix via stateless address autoconfiguration remain preferred [ADDRCONF].  A value of all one bits (0xffffffff) represents infinity.


ip6nd_proxy_add_del
################################################################
IPv6 ND proxy config

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - is_del
------------------------------------------------------------------


u32 - sw_if_index
------------------------------------------------------------------
The interface the host is on

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8[16] - address
------------------------------------------------------------------
The address of the host for which to proxy for


ip6nd_proxy_details
################################################################
IPv6 ND proxy details returned after request

Returns:
*****************************************


Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------


u32 - sw_if_index
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8[16] - address
------------------------------------------------------------------



ip6nd_proxy_dump
################################################################
IPv6 ND proxy dump request

Returns:
*****************************************


Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


ip6nd_send_router_solicitation
################################################################
Start / stop sending router solicitation

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - stop
------------------------------------------------------------------
if non-zero then stop sending router solicitation, otherwise start sending router solicitation

u32 - irt
------------------------------------------------------------------
initial retransmission time

u32 - sw_if_index
------------------------------------------------------------------
software interface index of interface for sending router solicitation

u32 - mrt
------------------------------------------------------------------
maximum retransmission time

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u32 - mrd
------------------------------------------------------------------
maximum retransmission duration

u32 - mrc
------------------------------------------------------------------
maximum retransmission count


sw_interface_ip6_enable_disable
################################################################
IPv6 interface enable / disable request

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - enable
------------------------------------------------------------------
if non-zero enable ip6 on interface, else disable */ autoreply define sw_interface_ip6_enable_disable { u32 client_index; u32 context; u32 sw_if_index; u8 enable;   /* set to true if enable

u32 - sw_if_index
------------------------------------------------------------------
interface used to reach neighbor

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


sw_interface_ip6_set_link_local_address
################################################################
IPv6 set link local address on interface request

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
interface to set link local on

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8[16] - address
------------------------------------------------------------------
address[] - the new link local address


ip_add_del_route
################################################################
Add / del route request

Returns:
*****************************************
autoreply

Parameters:
*****************************************

vl_api_fib_mpls_label_t[next_hop_n_out_labels] - ck
------------------------------------------------------------------


u8 - next_hop_n_out_labels
------------------------------------------------------------------
the number of labels in the label stack

u32 - next_hop_via_label
------------------------------------------------------------------
The next-hop is a resolved via a local label

u8 - is_source_lookup
------------------------------------------------------------------
The the path is a deaggregate path (i.e. a lookup in another table) is the lookup on the packet's source address or destination.

u8 - next_hop_proto
------------------------------------------------------------------


u8 - is_unreach
------------------------------------------------------------------
Drop the packet and rate limit send ICMP unreachable

u8 - is_udp_encap
------------------------------------------------------------------
The path describes a UDP-o-IP encapsulation.

u8 - is_dvr
------------------------------------------------------------------
Does the route resolve via a DVR interface.

u32 - next_hop_sw_if_index
------------------------------------------------------------------


u32 - classify_table_index
------------------------------------------------------------------


u8 - dst_address_length
------------------------------------------------------------------


u8[16] - next_hop_address
------------------------------------------------------------------


u8 - next_hop_weight
------------------------------------------------------------------
Weight for Unequal cost multi-path

u8 - is_add
------------------------------------------------------------------
1 if adding the route, 0 if deleting

u8 - is_classify
------------------------------------------------------------------


u8 - is_drop
------------------------------------------------------------------
Drop the packet

u8 - is_prohibit
------------------------------------------------------------------
Drop the packet and rate limit send ICMP prohibited

u8 - is_ipv6
------------------------------------------------------------------
0 if an ip4 route, else ip6

u8 - is_local
------------------------------------------------------------------
The route will result in packets sent to VPP IP stack

u32 - next_hop_id
------------------------------------------------------------------
Used when the path resolves via an object that has a unique identifier.

u8 - is_multipath
------------------------------------------------------------------
Set to 1 if this is a multipath route, else 0

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - next_hop_preference
------------------------------------------------------------------
Path that are up that have the best preference are are used for forwarding. lower value is better.

u8[16] - dst_address
------------------------------------------------------------------


u8 - is_resolve_attached
------------------------------------------------------------------


u32 - table_id
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u32 - next_hop_table_id
------------------------------------------------------------------


u8 - is_resolve_host
------------------------------------------------------------------



ip_mroute_add_del
################################################################
Add / del route request

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u8 - is_local
------------------------------------------------------------------


u32 - bier_imp
------------------------------------------------------------------


u32 - rpf_id
------------------------------------------------------------------


u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8[16] - nh_address
------------------------------------------------------------------


u8 - is_add
------------------------------------------------------------------


u8[16] - grp_address
------------------------------------------------------------------


u16 - grp_address_length
------------------------------------------------------------------


u32 - itf_flags
------------------------------------------------------------------


u8 - next_hop_afi
------------------------------------------------------------------
Use dpo_proto_t FIXME

u8[16] - src_address
------------------------------------------------------------------


u32 - next_hop_sw_if_index
------------------------------------------------------------------


u32 - table_id
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8 - is_ipv6
------------------------------------------------------------------


u32 - entry_flags
------------------------------------------------------------------



ip_mfib_dump
################################################################
Dump IP multicast fib table

Returns:
*****************************************


Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - context
------------------------------------------------------------------



ip_mfib_details
################################################################
IP Multicast FIB table response

Returns:
*****************************************
manual_endian manual_print

Parameters:
*****************************************

u32 - count
------------------------------------------------------------------
the number of fib_path in path

u8 - address_length
------------------------------------------------------------------


u32 - rpf_id
------------------------------------------------------------------


u8[4] - src_address
------------------------------------------------------------------


u8[4] - grp_address
------------------------------------------------------------------


u32 - entry_flags
------------------------------------------------------------------


u32 - table_id
------------------------------------------------------------------
IP fib table id @address_length - mask length @grp_address - Group address/prefix @src_address - Source address

u32 - context
------------------------------------------------------------------


vl_api_fib_path_t[count] - path
------------------------------------------------------------------
array of of fib_path structures


ip6_mfib_dump
################################################################
Dump IP6 multicast fib table

Returns:
*****************************************


Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - context
------------------------------------------------------------------



ip6_mfib_details
################################################################
IP6 Multicast FIB table response

Returns:
*****************************************
manual_endian manual_print

Parameters:
*****************************************

u32 - count
------------------------------------------------------------------
the number of fib_path in path

u8 - address_length
------------------------------------------------------------------


u8[16] - src_address
------------------------------------------------------------------


u8[16] - grp_address
------------------------------------------------------------------


u32 - table_id
------------------------------------------------------------------
IP fib table id @address_length - mask length @grp_address - Group address/prefix @src_address - Source address

u32 - context
------------------------------------------------------------------


vl_api_fib_path_t[count] - path
------------------------------------------------------------------
array of of fib_path structures


ip_punt_police
################################################################
IP punt policer

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - policer_index
------------------------------------------------------------------
Index of policer to use

u8 - is_add
------------------------------------------------------------------
1 to add neighbor, 0 to delete

u8 - is_ip6
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


ip_punt_redirect
################################################################
IP punt redirect

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u8[16] - nh
------------------------------------------------------------------
The next-hop to redirect the traffic to.

u32 - tx_sw_if_index
------------------------------------------------------------------
the TX interface to which traffic shoulde be redirected.

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - is_add
------------------------------------------------------------------
1 to add neighbor, 0 to delete

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u32 - rx_sw_if_index
------------------------------------------------------------------


u8 - is_ip6
------------------------------------------------------------------



ip_source_and_port_range_check_add_del
################################################################
Configure IP source and L4 port-range check

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
1 if add, 0 if delete

u8 - number_of_ranges
------------------------------------------------------------------
length of low_port and high_port arrays (must match)

u16[32] - high_ports
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8[16] - address
------------------------------------------------------------------
array of address bytes

u32 - vrf_id
------------------------------------------------------------------
fib table/vrf id to associate the source and port-range check with @note To specify a single port set low_port and high_port entry the same

u16[32] - low_ports
------------------------------------------------------------------


u8 - mask_length
------------------------------------------------------------------
mask length for address entry

u8 - is_ipv6
------------------------------------------------------------------



ip_source_and_port_range_check_interface_add_del
################################################################
Set interface source and L4 port-range request

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


u32 - sw_if_index
------------------------------------------------------------------


u32 - udp_in_vrf_id
------------------------------------------------------------------


u32 - tcp_out_vrf_id
------------------------------------------------------------------


u32 - udp_out_vrf_id
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u32 - tcp_in_vrf_id
------------------------------------------------------------------



ip_probe_neighbor
################################################################
IP probe neighbor address on an interface by sending an ARP request (for IP4) or ICMP6 Neighbor Solicitation (for IP6)

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - is_ipv6
------------------------------------------------------------------
[1|0] to indicate if address family is IPv[6|4]

u32 - sw_if_index
------------------------------------------------------------------
interface index

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8[16] - dst_address
------------------------------------------------------------------
target IP address to send IP addr resolution request


want_ip4_arp_events
################################################################
Register for IP4 ARP resolution event on receing ARP reply or MAC/IP info from ARP requests in L2 BDs

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - enable_disable
------------------------------------------------------------------
1 => register for events, 0 => cancel registration

u32 - pid
------------------------------------------------------------------
sender's pid

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u32 - address
------------------------------------------------------------------
exact IP4 address of interested arp resolution event, or 0 to get MAC/IP info from ARP requests in BDs


ip4_arp_event
################################################################
Tell client about an IP4 ARP resolution event or MAC/IP info from ARP requests in L2 BDs

Returns:
*****************************************


Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - pid
------------------------------------------------------------------
client pid registered to receive notification

u32 - sw_if_index
------------------------------------------------------------------
interface which received ARP packet

u8 - mac_ip
------------------------------------------------------------------
0: ARP resolution event, 1: MAC/IP info from L2 BDs

u8[6] - new_mac
------------------------------------------------------------------
the new mac address

u32 - address
------------------------------------------------------------------
the exact ip4 address of interest


want_ip6_nd_events
################################################################
Register for IP6 ND resolution event on recieving NA reply MAC/IP info from ICMP6 Neighbor Solicitation in L2 BDs

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - enable_disable
------------------------------------------------------------------
1 => register for events, 0 => cancel registration

u32 - pid
------------------------------------------------------------------
sender's pid

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8[16] - address
------------------------------------------------------------------
the exact IP6 address of interested ND resolution event, or 0 to get MAC/IP info from ICMP6 NS in L2 BDs.


ip6_nd_event
################################################################
Tell client about an IP6 ND resolution or MAC/IP info from ICMP6 Neighbor Solicitation in L2 BDs.

Returns:
*****************************************


Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - pid
------------------------------------------------------------------
client pid registered to receive notification

u32 - sw_if_index
------------------------------------------------------------------
interface which received ARP packet

u8 - mac_ip
------------------------------------------------------------------
0: ND resolution event, 1: MAC/IP info from L2 BDs

u8[6] - new_mac
------------------------------------------------------------------
the new mac address

u8[16] - address
------------------------------------------------------------------
the exact ip6 address of interest


want_ip6_ra_events
################################################################
Register for ip6 router advertisement events

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - enable_disable
------------------------------------------------------------------
1 => register for events, 0 => cancel registration

u32 - pid
------------------------------------------------------------------
sender's pid

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


ip6_ra_prefix_info
################################################################
Struct representing RA prefix info

Returns:
*****************************************
typeonly

Parameters:
*****************************************

u32 - valid_time
------------------------------------------------------------------
RA prefix info valid time

u8 - dst_address_length
------------------------------------------------------------------
RA prefix info destination address length

u32 - preferred_time
------------------------------------------------------------------
RA prefix info preferred time

u8 - flags
------------------------------------------------------------------
RA prefix info flags

u8[16] - dst_address
------------------------------------------------------------------
RA prefix info destination address


ip6_ra_event
################################################################
Tell client about a router advertisement event

Returns:
*****************************************


Parameters:
*****************************************

vl_api_ip6_ra_prefix_info_t[n_prefixes] - 
------------------------------------------------------------------


u8[16] - router_address
------------------------------------------------------------------


u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - pid
------------------------------------------------------------------
client pid registered to receive notification

u8 - current_hop_limit
------------------------------------------------------------------
RA current hop limit

u32 - neighbor_reachable_time_in_msec
------------------------------------------------------------------
RA neighbor reachable time in msec

u32 - time_in_msec_between_retransmitted_neighbor_solicitations
------------------------------------------------------------------
 time in msec between retransmitted neighbor solicitations

u8 - flags
------------------------------------------------------------------
RA flags

u32 - sw_if_index
------------------------------------------------------------------


u32 - n_prefixes
------------------------------------------------------------------


u16 - router_lifetime_in_sec
------------------------------------------------------------------
RA lifetime in seconds


proxy_arp_add_del
################################################################
Proxy ARP add / del request

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - is_add
------------------------------------------------------------------
1 if adding the Proxy ARP range, 0 if deleting

u8[4] - hi_address
------------------------------------------------------------------


u32 - vrf_id
------------------------------------------------------------------
VRF / Fib table ID

u8[4] - low_address
------------------------------------------------------------------



proxy_arp_intfc_enable_disable
################################################################
Proxy ARP add / del request

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

/* - 1
------------------------------------------------------------------


u8 - enable_disable
------------------------------------------------------------------
1 to enable Proxy ARP on interface, 0 to disable */ autoreply define proxy_arp_intfc_enable_disable { u32 client_index; u32 context; u32 sw_if_index; /* 1 = on, 0 = off

u32 - sw_if_index
------------------------------------------------------------------
Which interface to enable / disable Proxy Arp on

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


reset_fib
################################################################
Reset fib table request

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - vrf_id
------------------------------------------------------------------
vrf/table id of the fib table to reset

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8 - is_ipv6
------------------------------------------------------------------
an ipv6 fib to reset if non-zero, else ipv4


set_arp_neighbor_limit
################################################################
Set max allowed ARP or ip6 neighbor entries request

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - arp_neighbor_limit
------------------------------------------------------------------
the new limit, defaults are ~ 50k

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8 - is_ipv6
------------------------------------------------------------------
neighbor limit if non-zero, else ARP limit


ioam_enable
################################################################
IOAM enable : Enable in-band OAM

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u8 - pot_enable
------------------------------------------------------------------


u8 - trace_enable
------------------------------------------------------------------
iOAM Trace enabled or not flag

u32 - client_index
------------------------------------------------------------------


u8 - seqno
------------------------------------------------------------------
To enable Seqno Processing

u8 - analyse
------------------------------------------------------------------
Enabling analysis of iOAM at decap node

u32 - node_id
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------


u16 - id
------------------------------------------------------------------
profile id


ioam_disable
################################################################
iOAM disable

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u16 - id
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


ip_reassembly_enable_disable
################################################################
Enable/disable reassembly feature

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - enable_ip6
------------------------------------------------------------------
enable ip6 reassembly if non-zero, disable if 0

u32 - sw_if_index
------------------------------------------------------------------
interface to enable/disable feature on

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8 - enable_ip4
------------------------------------------------------------------
enable ip4 reassembly if non-zero, disable if 0

