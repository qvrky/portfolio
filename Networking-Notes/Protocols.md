# Core Networking & Internet Protocols

# Domain Name System (DNS)
* DNS is essentially a phonebook with corresponding domain names and IP addresses. This protocol often uses UDP/53.
* How it works (The Chain):
  1. The computer checks its local cache.
  2. If missing, it asks the recursive resolver (like 8.8.8.8 or 1.1.1.1).
  3. The resolver acts as the middleman, asking the root server. The root server doesn't actually know the IPs of anything; it just knows who does.
  4. The Root points to the TLD server (Top Level Domain like '.com', '.co.uk').
  5. The TLD points to the authoritative name server for that specific site.
  6. The IP address is retrieved, cached, and sent back to the browser.

# IP Addressing & Subnetting
* Internet Protocol (IP): A unique mailing address for your device so packets know where to land.
* IPv4 Structure: An IP address, e.g. 192.132.145.3, consists of 32 bits split into 4 octets. These octets are separated by '.'.
* The Subnet Mask: A subnet mask, e.g. 255.255.255.0, tells the computer which part of the IP belongs to the network (the street name) and which part belongs to the host device (the house number). 
* Example: A mask of '255.255.255.0' means the first three octets belong to the network, and the last octet is the individual machine.

# Network Address Translation (NAT)
* There is a problem with IPv4, there aren't enough public IPv4 addresses for every device on Earth. So we came up with a solution. NAT. NAT allows an entire home router network to share one public IP address.
* How it works: The router acts as a gatekeeper. It saves your local device's internal IP in a NAT Translation Table, swaps it for the router's public IP, sends the packet out, and uses the table to route the returning data back to the exact phone or laptop that asked for it.

# Transmission Protocols: TCP vs. UDP
## TCP (Transmission Control Protocol)
* TCP is the reliable mailman. Slower but much more reliable.
* The 3-Way Handshake: Before any data is sent, TCP establishes a connection:
  1. SYN: Client asks to synchronise.
  2. SYN-ACK: Server acknowledges and requests to sync back.
  3. ACK: Client acknowledges. Connection established.
* Why it's reliable: data is split into numbered pieces (sequence numbers). The receiver acknowledges what arrives, asks again for any missing piece, and puts everything back in order, like a puzzle.
* Note: TCP retransmits lost data, but if the connection breaks entirely, nothing is guaranteed.

## UDP (User Datagram Protocol)
* UDP is the less reliable, but fast mailman. Instead of performing a handshake, it just shouts the data out not worrying if anything is listening for it.
* It is commonly used for live streaming and gaming where speed matters more than losing a few dropped frames.

# FTP (File Transfer Protocol)


