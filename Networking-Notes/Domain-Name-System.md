# Domain Name System (DNS)

## What is DNS?
* DNS is essentially a phonebook with corresponding domain names and IP addresses. This protocol often uses UDP/53.

## How it works (The Chain):
  1. The computer checks its local cache.
  2. If missing, it asks the recursive resolver (like 8.8.8.8 or 1.1.1.1).
  3. The resolver acts as the middleman, asking the root server. The root server doesn't actually know the IPs of anything; it just knows who does.
  4. The Root points to the TLD server (Top Level Domain like '.com', '.co.uk').
  5. The TLD points to the authoritative name server for that specific site.
  6. The IP address is retrieved, cached, and sent back to the browser.