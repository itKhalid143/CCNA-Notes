# Note

- IP is ConnectionLess
	- Every Packer is treated Individually and Separately.
	- No guarantee packets arrived nor the order of the packets.
***

# Transport Layer-4

Segmentation (MTU depends on physical mediums).

## TCP

- Connection Oriented (Sessions), Delivery acknowledgement and reliability.
- Connection must first Established between Sender and Receiver.
- Supports 65495 bytes in single segment, MSS and Path MTU Discovery. (Sender and Receiver can automatically determine maximun transmission)
- Flow Control, to prevent sending data too quickly to avoid retransmission. (Usage of Sliding Window to control the flow of data)
- Sequence number to Track (Sequencing), Full Duplex mode, Error checking (Checksum 16 Bit).
- Acknowledgement of Receipt.
- Header: 16-bit Source port, 16-bit Destination port, 32-bit Sequences Number, 32-bit Acknowledgement number, 20-60 bytes Header, Flags (Quality of Service), 16-bits Windows Size(Currently willing to receive), 16-bit Checksum, 16-bits Urgentpointer, Options, Data.
- Three-Way handshake
	- SYN (Seq, CTL Flag = SYN).
	- SYN/ACK (CTL, Seq, Ack (The expected next sequence number) ).
	- ACK.

## UDP

- ConnectionLess.
- Doesn't implement Flow control.
- Provides limited error delivery, No data recovery features.
- Minimum 8 bytes, Maximum 65535 bytes.

***

# Terminology

## Session Multiplexing

- Single host with single IP Address is able to communicate with multiple Servers/Devices Simultaneously.

## Socket

Socket is a Combination of: 
	- IP Address of a host.
	- Port number used.
	- Transport Protocol used.

## Sequence Numbers:

- To ensure Successful Delivery. (Randomly choosed at first)

## Port Numbers

- A port number is a way to identify a specific process to which an internet or other network message is to be forwarded when it arrives at a server.

## Windows size

- Indicates the windows size (Number of data segments the sender is allowed to send at a time) when sending requests. (It's good for different powerful devices)
- When packet dropped by the network, the host will slow down (reduce Windows size).
- It is determined by (And may change automatically):
	- Windows granted to sender.
	- Congestion Window (CWND).
	- Initially set to very low value, increases at exponential rate. (Congestion avoidance)	

## Wred Weighted Random Early Detection - Quality of Service

- Improve efficiency of TCP transmission.
- Avoid Global Synchronization.
- Increasing / Decreasing the segments.