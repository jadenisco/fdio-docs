.. _Developerdocs-fdiovpp-mastersrcpluginsaclaclapi:

.. toctree::

ACL
====================================================================
Source: /plugins/acl/acl.api

This file defines the vpp control-plane API messages used to control the ACL plugin

acl_plugin_get_version
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


acl_plugin_get_version_reply
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


acl_plugin_control_ping
################################################################
Control ping from client to api server request

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


acl_plugin_control_ping_reply
################################################################
Control ping from the client to the server response

Returns:
*****************************************


Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

i32 - retval
------------------------------------------------------------------
return code for the request

u32 - vpe_pid
------------------------------------------------------------------
the pid of the vpe, returned by the server

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


acl_rule
################################################################
Access List Rule entry

Returns:
*****************************************
typeonly manual_print

Parameters:
*****************************************

u16 - srcport_or_icmptype_last
------------------------------------------------------------------
end of source port or ICMP4/6 type range

* - is
------------------------------------------------------------------


u8 - is_permit
------------------------------------------------------------------
deny (0), permit (1), or permit+reflect(2) action on this rule.

u8 - is_ipv6
------------------------------------------------------------------
IP addresses in this rule are IPv6 (1) or IPv4 (0)

* - use
------------------------------------------------------------------


u16 - srcport_or_icmptype_first
------------------------------------------------------------------
beginning of source port or ICMP4/6 type range

* - for
------------------------------------------------------------------


u8 - proto
------------------------------------------------------------------
L4 protocol (http://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml)

* - they
------------------------------------------------------------------


* - TCP
------------------------------------------------------------------


* - Ranges
------------------------------------------------------------------


* - 0
------------------------------------------------------------------


u8 - dst_ip_prefix_len
------------------------------------------------------------------
Destination prefix length

u8 - tcp_flags_value
------------------------------------------------------------------
if proto==6, mask to AND the TCP flags in the packet with */  typeonly manual_print define acl_rule { u8 is_permit; u8 is_ipv6; u8 src_ip_addr[16]; u8 src_ip_prefix_len; u8 dst_ip_addr[16]; u8 dst_ip_prefix_len; /* * L4 protocol. IANA number. 1 = ICMP, 58 = ICMPv6, 6 = TCP, 17 = UDP. * 0 => ignore L4 and ignore the ports/tcpflags when matching. */ u8 proto; /* * If the L4 protocol is TCP or UDP, the below * hold ranges of ports, else if the L4 is ICMP/ICMPv6 * they hold ranges of ICMP(v6) types/codes. * * Ranges are inclusive, i.e. to match "any" TCP/UDP port, * use first=0,last=65535. For ICMP(v6), * use first=0,last=255. */ u16 srcport_or_icmptype_first; u16 srcport_or_icmptype_last; u16 dstport_or_icmpcode_first; u16 dstport_or_icmpcode_last; /* * for proto = 6, this matches if the * TCP flags in the packet, ANDed with tcp_flags_mask, * is equal to tcp_flags_value.

* - L4
------------------------------------------------------------------


u16 - dstport_or_icmpcode_last
------------------------------------------------------------------
end of destination port or ICMP4/6 code range

* - hold
------------------------------------------------------------------


u8[16] - dst_ip_addr
------------------------------------------------------------------
Destination prefix value

u16 - dstport_or_icmpcode_first
------------------------------------------------------------------
beginning of destination port or ICMP4/6 code range

u8 - src_ip_prefix_len
------------------------------------------------------------------
Source prefix length

u8 - tcp_flags_mask
------------------------------------------------------------------
if proto==6, match masked TCP flags with this value

u8[16] - src_ip_addr
------------------------------------------------------------------
Source prefix value

* - If
------------------------------------------------------------------



macip_acl_rule
################################################################
MACIP Access List Rule entry

Returns:
*****************************************
typeonly manual_print

Parameters:
*****************************************

u8 - src_ip_prefix_len
------------------------------------------------------------------
Source prefix length */  typeonly manual_print define macip_acl_rule { u8 is_permit; u8 is_ipv6; /* * The source mac of the packet ANDed with src_mac_mask. * The source ip[46] address in the packet is matched * against src_ip_addr, with src_ip_prefix_len set to 0. * * For better performance, minimize the number of * (src_mac_mask, src_ip_prefix_len) combinations * in a MACIP ACL.

u8[6] - src_mac_mask
------------------------------------------------------------------
AND source MAC address with this value before matching

* - For
------------------------------------------------------------------


u8 - is_permit
------------------------------------------------------------------
deny (0), permit (1) action on this rule.

* - (src_mac_mask,
------------------------------------------------------------------


* - against
------------------------------------------------------------------


* - in
------------------------------------------------------------------


* - The
------------------------------------------------------------------


u8[16] - src_ip_addr
------------------------------------------------------------------
Source prefix value

u8[6] - src_mac
------------------------------------------------------------------
match masked source MAC address against this value

u8 - is_ipv6
------------------------------------------------------------------
IP addresses in this rule are IPv6 (1) or IPv4 (0)


acl_add_replace
################################################################
Replace an existing ACL in-place or create a new ACL

Returns:
*****************************************
manual_print manual_endian

Parameters:
*****************************************

u32 - count
------------------------------------------------------------------
number of ACL rules @r - Rules for this access-list */  manual_print manual_endian define acl_add_replace { u32 client_index; u32 context; u32 acl_index; /* ~0 to add, existing ACL# to replace */ u8 tag[64]; /* What gets in here gets out in the corresponding tag field when dumping the ACLs.

u32 - acl_index
------------------------------------------------------------------
an existing ACL entry (0..0xfffffffe) to replace, or 0xffffffff to make new ACL

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8[64] - tag
------------------------------------------------------------------
a string value stored along with the ACL, for descriptive purposes

vl_api_acl_rule_t[count] - r
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


acl_add_replace_reply
################################################################
Reply to add/replace ACL

Returns:
*****************************************


Parameters:
*****************************************

i32 - retval
------------------------------------------------------------------


u32 - acl_index
------------------------------------------------------------------
index of the updated or newly created ACL

u32 - context
------------------------------------------------------------------
returned sender context, to match reply w/ request


acl_del
################################################################
Delete an ACL

Returns:
*****************************************
autoreply manual_print

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - acl_index
------------------------------------------------------------------
ACL index to delete

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


acl_interface_add_del
################################################################
Use acl_interface_set_acl_list instead Append/remove an ACL index to/from the list of ACLs checked for an interface

Returns:
*****************************************
autoreply manual_print

Parameters:
*****************************************

u32 - acl_index
------------------------------------------------------------------
index of ACL for the operation */  autoreply manual_print define acl_interface_add_del { u32 client_index; u32 context; u8 is_add; /* * is_input = 0 => ACL applied on interface egress * is_input = 1 => ACL applied on interface ingress

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - is_add
------------------------------------------------------------------
add or delete the ACL index from the list

u32 - sw_if_index
------------------------------------------------------------------
the interface to alter the list of ACLs on

u8 - is_input
------------------------------------------------------------------
check the ACL on input (1) or output (0)

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


acl_interface_set_acl_list
################################################################
Set the vector of input/output ACLs checked for an interface

Returns:
*****************************************
autoreply manual_print

Parameters:
*****************************************

u8 - count
------------------------------------------------------------------
total number of ACL indices in the vector

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - sw_if_index
------------------------------------------------------------------
the interface to alter the list of ACLs on

u8 - n_input
------------------------------------------------------------------


u32[count] - acls
------------------------------------------------------------------
vector of ACL indices */  autoreply manual_print define acl_interface_set_acl_list { u32 client_index; u32 context; u32 sw_if_index; u8 count; u8 n_input; /* First n_input ACLs are set as a list of input ACLs, the rest are applied as output

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


acl_dump
################################################################
Reply to set the ACL list on an interface

Returns:
*****************************************


Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - acl_index
------------------------------------------------------------------
ACL index to dump, ~0 to dump all ACLs */  define acl_dump { u32 client_index; u32 context; u32 acl_index; /* ~0 for all ACLs

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


acl_details
################################################################
Details about a single ACL contents

Returns:
*****************************************
manual_endian manual_print

Parameters:
*****************************************

u32 - count
------------------------------------------------------------------
Number of rules in this ACL

vl_api_acl_rule_t[count] - r
------------------------------------------------------------------
Array of rules within this ACL */  manual_endian manual_print define acl_details { u32 context; u32 acl_index; u8 tag[64]; /* Same blob that was supplied to us when creating the ACL, one hopes.

u8[64] - tag
------------------------------------------------------------------
Descriptive tag value which was supplied at ACL creation

u32 - acl_index
------------------------------------------------------------------
ACL index whose contents are being sent in this message

u32 - context
------------------------------------------------------------------
returned sender context, to match reply w/ request


acl_interface_list_dump
################################################################
Dump the list(s) of ACL applied to specific or all interfaces

Returns:
*****************************************


Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - sw_if_index
------------------------------------------------------------------
interface to dump the ACL list for */  define acl_interface_list_dump { u32 client_index; u32 context; u32 sw_if_index; /* ~0 for all interfaces

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


acl_interface_list_details
################################################################
Details about a single ACL contents

Returns:
*****************************************


Parameters:
*****************************************

u8 - count
------------------------------------------------------------------
total length of acl indices vector

u8 - n_input
------------------------------------------------------------------


u32[count] - acls
------------------------------------------------------------------
the vector of ACL indices

u32 - sw_if_index
------------------------------------------------------------------
interface for which the list of ACLs is applied

u32 - context
------------------------------------------------------------------
returned sender context, to match reply w/ request


macip_acl_add
################################################################
Add a MACIP ACL

Returns:
*****************************************
manual_endian manual_print

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - count
------------------------------------------------------------------
number of rules in this MACIP ACL

vl_api_macip_acl_rule_t[count] - r
------------------------------------------------------------------
vector of MACIP ACL rules

u8[64] - tag
------------------------------------------------------------------
descriptive value for this MACIP ACL

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


macip_acl_add_reply
################################################################
Reply to add MACIP ACL

Returns:
*****************************************


Parameters:
*****************************************

i32 - retval
------------------------------------------------------------------


u32 - acl_index
------------------------------------------------------------------
index of the newly created MACIP ACL

u32 - context
------------------------------------------------------------------
returned sender context, to match reply w/ request


macip_acl_add_replace
################################################################
Add/Replace a MACIP ACL

Returns:
*****************************************
manual_endian manual_print

Parameters:
*****************************************

u32 - count
------------------------------------------------------------------
number of rules in this MACIP ACL

u32 - acl_index
------------------------------------------------------------------
an existing MACIP ACL entry (0..0xfffffffe) to replace, or 0xffffffff to make new MACIP ACL

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8[64] - tag
------------------------------------------------------------------
descriptive value for this MACIP ACL

vl_api_macip_acl_rule_t[count] - r
------------------------------------------------------------------
vector of MACIP ACL rules */  manual_endian manual_print define macip_acl_add_replace { u32 client_index; u32 context; u32 acl_index; /* ~0 to add, existing MACIP ACL# to replace

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


macip_acl_add_replace_reply
################################################################
Reply to add/replace MACIP ACL

Returns:
*****************************************


Parameters:
*****************************************

i32 - retval
------------------------------------------------------------------


u32 - acl_index
------------------------------------------------------------------
index of the newly created MACIP ACL

u32 - context
------------------------------------------------------------------
returned sender context, to match reply w/ request


macip_acl_del
################################################################
Delete a MACIP ACL

Returns:
*****************************************
autoreply manual_print

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - acl_index
------------------------------------------------------------------
MACIP ACL index to delete

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


macip_acl_interface_add_del
################################################################
Add or delete a MACIP ACL to/from interface

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
add (1) or delete (0) MACIP ACL from being used on an interface

u32 - acl_index
------------------------------------------------------------------
MACIP ACL index */  autoreply manual_print define macip_acl_interface_add_del { u32 client_index; u32 context; u8 is_add; /* MACIP ACLs are always input

u32 - sw_if_index
------------------------------------------------------------------
interface to apply the action to

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


macip_acl_dump
################################################################
Dump one or all defined MACIP ACLs

Returns:
*****************************************


Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - acl_index
------------------------------------------------------------------
MACIP ACL index or ~0 to dump all MACIP ACLs */  define macip_acl_dump { u32 client_index; u32 context; u32 acl_index; /* ~0 for all ACLs

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


macip_acl_details
################################################################
Details about one MACIP ACL

Returns:
*****************************************
manual_endian manual_print

Parameters:
*****************************************

u32 - count
------------------------------------------------------------------
length of the vector of MACIP ACL rules

vl_api_macip_acl_rule_t[count] - r
------------------------------------------------------------------
rules comprising this MACIP ACL

u8[64] - tag
------------------------------------------------------------------
descriptive tag which was supplied during the creation

u32 - acl_index
------------------------------------------------------------------
index of this MACIP ACL

u32 - context
------------------------------------------------------------------
returned sender context, to match reply w/ request


macip_acl_interface_get
################################################################
Get the vector of MACIP ACL IDs applied to the interfaces

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


macip_acl_interface_get_reply
################################################################
Reply with the vector of MACIP ACLs by sw_if_index

Returns:
*****************************************


Parameters:
*****************************************

u32 - count
------------------------------------------------------------------
total number of elements in the vector

u32[count] - acls
------------------------------------------------------------------
the vector of active MACIP ACL indices per sw_if_index

u32 - context
------------------------------------------------------------------
returned sender context, to match reply w/ request


macip_acl_interface_list_dump
################################################################
Dump the list(s) of MACIP ACLs applied to specific or all interfaces

Returns:
*****************************************


Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - sw_if_index
------------------------------------------------------------------
interface to dump the MACIP ACL list for */  define macip_acl_interface_list_dump { u32 client_index; u32 context; u32 sw_if_index; /* ~0 for all interfaces

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


macip_acl_interface_list_details
################################################################
Details about a single MACIP ACL contents

Returns:
*****************************************


Parameters:
*****************************************

u8 - count
------------------------------------------------------------------
total length of acl indices vector

u32[count] - acls
------------------------------------------------------------------
the vector of MACIP ACL indices

u32 - sw_if_index
------------------------------------------------------------------
interface for which the list of MACIP ACLs is applied

u32 - context
------------------------------------------------------------------
returned sender context, to match reply w/ request


acl_interface_set_etype_whitelist
################################################################
Set the ethertype whitelists on an interface. Takes effect when applying ACLs on the interface, so must be given prior.

Returns:
*****************************************
autoreply manual_print

Parameters:
*****************************************

u8 - count
------------------------------------------------------------------
total number of whitelisted ethertypes in the vector

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - sw_if_index
------------------------------------------------------------------
the interface to alter the list of ACLs on

u8 - n_input
------------------------------------------------------------------


u16[count] - whitelis
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


acl_interface_etype_whitelist_dump
################################################################
Dump the list(s) of Ethertype whitelists applied to specific or all interfaces

Returns:
*****************************************


Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - sw_if_index
------------------------------------------------------------------
interface to dump the ethertype whitelist for */  define acl_interface_etype_whitelist_dump { u32 client_index; u32 context; u32 sw_if_index; /* ~0 for all interfaces

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


acl_interface_etype_whitelist_details
################################################################
Details about ethertype whitelist on a single interface

Returns:
*****************************************


Parameters:
*****************************************

u8 - count
------------------------------------------------------------------
total number of whitelisted ethertypes in the vector

u8 - n_input
------------------------------------------------------------------


u32 - sw_if_index
------------------------------------------------------------------
interface for which the list of MACIP ACLs is applied

u32 - context
------------------------------------------------------------------
returned sender context, to match reply w/ request

u16[count] - whitelis
------------------------------------------------------------------


