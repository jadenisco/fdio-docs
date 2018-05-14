.. _Developerdocs-fdiovpp-mastersrcvnetbierbierapi:

.. toctree::

BIER
====================================================================
Source: /vnet/bier/bier.api

This file defines vpp BIER control-plane API messages which are generally called through a shared memory interface.

bier_table_id
################################################################
BIER Table Indentifier

Returns:
*****************************************
typeonly

Parameters:
*****************************************

u8 - bt_sub_domain
------------------------------------------------------------------
the sud-domain

u8 - bt_hdr_len_id
------------------------------------------------------------------


u8 - bt_set
------------------------------------------------------------------
The BIER set


bier_table_add_del
################################################################
BIER Table Add / del route

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - bt_label
------------------------------------------------------------------
The MPLS label for the table (0 or all ones means not set) If the label is not set, then it is assumed that non-MPLS encoding is used.

vl_api_bier_table_id_t - bt_tbl_id
------------------------------------------------------------------
The BIER table-id the route is added in

u8 - bt_is_add
------------------------------------------------------------------
Is this a route add or delete

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


bier_route_add_del
################################################################
BIER Route Add / del route

Returns:
*****************************************
autoreply

Parameters:
*****************************************

vl_api_fib_path_t[br_n_paths] - 
------------------------------------------------------------------


u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - br_n_paths
------------------------------------------------------------------
The number of paths

u32 - br_bp
------------------------------------------------------------------
The Bit-position value

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8 - br_is_replace
------------------------------------------------------------------
Are the paths specfied replacing those already present or are they to be combined.

u8 - br_is_add
------------------------------------------------------------------
Is this a route add or delete

vl_api_bier_table_id_t - br_tbl_id
------------------------------------------------------------------
The BIER table-id the route is added in


bier_imp_add
################################################################
BIER Imposition Add

Returns:
*****************************************


Parameters:
*****************************************

u8[bi_n_bytes] - 
------------------------------------------------------------------


u8 - bi_n_bytes
------------------------------------------------------------------
The number of bytes in the following bit-string. VPP only supports BSL of 1024 and less, so this is a u8 field.

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

vl_api_bier_table_id_t - bi_tbl_id
------------------------------------------------------------------
The BIER table-id used to forward post encap

u16 - bi_src
------------------------------------------------------------------
The source Bit-position in the encap.

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


bier_imp_add_reply
################################################################
Reply for BIER route add / del request

Returns:
*****************************************


Parameters:
*****************************************

i32 - retval
------------------------------------------------------------------
return code

u32 - bi_index
------------------------------------------------------------------
The index of the created imposition object.

u32 - context
------------------------------------------------------------------
returned sender context, to match reply w/ request


bier_imp_del
################################################################
BIER Imposition Del

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - bi_index
------------------------------------------------------------------
The index of the imposition object (as returned from the ADD)

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


bier_disp_table_add_del
################################################################
BIER Disposition Table Add / del route

Returns:
*****************************************
autoreply

Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u32 - bdt_tbl_id
------------------------------------------------------------------


u8 - bdt_is_add
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


bier_disp_entry_add_del
################################################################
BIER Disposition Entry Add / del

Returns:
*****************************************
autoreply

Parameters:
*****************************************

vl_api_fib_path_t[bde_n_paths] - 
------------------------------------------------------------------


u8 - bde_n_paths
------------------------------------------------------------------


u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u32 - bde_tbl_id
------------------------------------------------------------------
The BIER dispositiontable-id the route is added in

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8 - bde_is_add
------------------------------------------------------------------
Is this a route add or delete

u16 - bde_bp
------------------------------------------------------------------
The Bit-position value for the entry, i.e. the sender's Use 0 for the default (match any source) entry.

u8 - bde_payload_proto
------------------------------------------------------------------
The payload protocol for which the next-hop is added

