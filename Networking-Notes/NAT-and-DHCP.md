# Network Address Translation (NAT)

## What is NAT?

## Why do we need NAT?
* There is a problem with IPv4, there aren't enough public IPv4 addresses for every device on Earth. So we came up with a solution. NAT. NAT allows an entire home router network to share one public IP address.

## How does NAT work?
* How it works: The router acts as a gatekeeper. It saves your local device's internal IP in a NAT Translation Table, swaps it for the router's public IP, sends the packet out, and uses the table to route the returning data back to the exact phone or laptop that asked for it.

# Dynamic Host Configuration Protocol (DHCP)

## What is DHCP?

## Why do we need DHCP?

## How does DHCP work?





### In Real Terms

Your home has a local network. Your devices speak to each other and other devices on the internet. This network consists of a phone, laptop, PC, and TV. But how do all these devices talk to the internet and the World Wide Web? 

It needs a gateway. 

Your router is your **default gateway**, and it sounds complicated, but if you just take the name at face value, it's easy:
* **"default"** - the normal choice
* **"gateway"** - a door that takes you somewhere

So it's the normal doorway to somewhere. The default doorway out of your local network.

Although your router does this, in itself, it is also just a device or host, and it is connected to the main network which is your ISP's network. Forget the ISP part and just think *"router is the default gateway and it is just a host/device just like a laptop or phone"*. This creates a network between the router and all the devices connecting to the internet via it. This network is called a subnet. A router, like any other device, needs an IP address. Let's say your phone's IP address is **192.168.1.13**, with a subnet mask of **255.255.255.0**. **192.168.1** belongs to your network, and **.13** belongs to your phone (the host/device). So when you are on Google and you search "WikiHow", you are sending data or information from your IP address to the Google server's IP address to access WikiHow. This info or data comes from your IP which ends in **.13**, so when the data gets sent back, your router knows to send it straight to host no.13. 

The router can only do this due to 2 concepts:
* **DHCP** - Dynamic Host Configuration Protocol
* **NAT** - Network Address Translation