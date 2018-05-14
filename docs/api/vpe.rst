.. _Developerdocs-fdiovpp-mastersrcvppapivpeapi:

.. toctree::

VPE
====================================================================
Source: /vpp/api/vpe.api

This file defines vpe control-plane API messages which are generally called through a shared memory interface.

control_ping
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


control_ping_reply
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


cli
################################################################
Process a vpe parser cli string request

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

u64 - cmd_in_shmem
------------------------------------------------------------------
pointer to cli command string


cli_reply
################################################################
vpe parser cli string response

Returns:
*****************************************


Parameters:
*****************************************

u64 - reply_in_shmem
------------------------------------------------------------------
Reply string from cli processing if any

i32 - retval
------------------------------------------------------------------
return code for request

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


get_node_index
################################################################
Get node index using name request

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

u8[64] - node_name
------------------------------------------------------------------
node_name[] - name of the node


get_node_index_reply
################################################################
Get node index using name request

Returns:
*****************************************


Parameters:
*****************************************

i32 - retval
------------------------------------------------------------------
return code for the request

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u32 - node_index
------------------------------------------------------------------
index of the desired node if found, else ~0


add_node_next
################################################################
Set the next node for a given node request

Returns:
*****************************************


Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8[64] - next_name
------------------------------------------------------------------
next_name[] - node to add as the next node

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8[64] - node_name
------------------------------------------------------------------
node_name[] - node to add the next node to


add_node_next_reply
################################################################
IP Set the next node for a given node response

Returns:
*****************************************


Parameters:
*****************************************

u32 - next_index
------------------------------------------------------------------
the index of the next node if success, else ~0

i32 - retval
------------------------------------------------------------------
return code for the add next node request

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request


show_version
################################################################
show version

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


show_version_reply
################################################################
show version response

Returns:
*****************************************


Parameters:
*****************************************

u8[32] - build_date
------------------------------------------------------------------


u8[32] - version
------------------------------------------------------------------
version of the program

u8[32] - program
------------------------------------------------------------------
name of the program (vpe)

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

i32 - retval
------------------------------------------------------------------
return code for the request

u8[256] - build_directory
------------------------------------------------------------------
root of the workspace where the program was built


get_node_graph_reply
################################################################
get_node_graph_reply

Returns:
*****************************************


Parameters:
*****************************************

u64 - reply_in_shmem
------------------------------------------------------------------
result from vlib_node_serialize, in shared memory. Process with vlib_node_unserialize, remember to switch heaps and free the result.

i32 - retval
------------------------------------------------------------------
return code

u32 - context
------------------------------------------------------------------
returned sender context, to match reply w/ request


get_next_index
################################################################
Query relative index via node names

Returns:
*****************************************


Parameters:
*****************************************

u32 - client_index
------------------------------------------------------------------
opaque cookie to identify the sender

u8[64] - next_name
------------------------------------------------------------------
next node from node_name to find relative index of

u32 - context
------------------------------------------------------------------
sender context, to match reply w/ request

u8[64] - node_name
------------------------------------------------------------------
name of node to find relative index from


get_next_index_reply
################################################################
Reply for get next node index

Returns:
*****************************************


Parameters:
*****************************************

u32 - next_index
------------------------------------------------------------------
index of the next_node

i32 - retval
------------------------------------------------------------------
return value

u32 - context
------------------------------------------------------------------
sender context which was passed in the request

