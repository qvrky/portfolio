# Internet Protocols

## Transmission Protocols: TCP vs. UDP

### TCP (Transmission Control Protocol)
* TCP is the reliable mailman. Slower but much more reliable.
* The 3-Way Handshake: Before any data is sent, TCP establishes a connection:
  1. SYN: Client asks to synchronise.
  2. SYN-ACK: Server acknowledges and requests to sync back.
  3. ACK: Client acknowledges. Connection established.
* Why it's reliable: data is split into numbered pieces (sequence numbers). The receiver acknowledges what arrives, asks again for any missing piece, and puts everything back in order, like a puzzle.
* Note: TCP retransmits lost data, but if the connection breaks entirely, nothing is guaranteed.

### UDP (User Datagram Protocol)
* UDP is the less reliable, but fast mailman. Instead of performing a handshake, it just shouts the data out not worrying if anything is listening for it.
* It is commonly used for live streaming and gaming where speed matters more than losing a few dropped frames.

## FTP (File Transfer Protocol)

## SSH (Super Secure Shell)

## HTTP (Hyper Text Transfer Protocol)

## HTTPS (Hyper Text Transfer Protocol Secure)
