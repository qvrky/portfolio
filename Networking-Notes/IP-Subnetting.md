# What is a Subnet Mask?

First, you have to understand what an IP address is. Internet Protocol (IP) is a unique mailing address for your device so packets know where to land. Every device has to have an IP address to communicate with other devices, so packets of data can be sent and received correctly. 

The specific IP address type is IPv4. An IPv4 address is a 32-bit numeric address written as 4 groups of numbers separated by a full stop. Each group of numbers is called an octet, so an IPv4 address has 4 octets and usually looks something like **192.168.10.1**. In this example, **192** is a single octet, **168** is another, etc. The number range in each octet is 0 - 255, which gives you 256 possible values. 

An IP address consists of two parts: 
* **First part** - Network address
* **Second part** - Host (device) address

Every network has a unique address. The host address (or host ID) is what's assigned to hosts within that network, such as computers, phones, laptops, routers, etc. So, every host will have a unique host address.

### How do we tell which portion is for the network and which is for the host?
This is where a subnet mask becomes important. A subnet mask is a number that resembles an IP address, and it shows how many bits in the IP address belong to the network. It does this by masking the network portion of the IP address.

---

### Translating to Binary
Computers and networks don't understand numbers or words, only binary and bits. So how do we translate an IP address to binary?

This is an 8-bit octet chart:
**| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |**

The bits in each octet are represented by a number in this chart. If you hadn't noticed, all these numbers added together result in 255. Starting from the right, the first bit has a value of **1**, then with each step up, the number doubles. 

Each bit in the octet can either be a **1** or a **0**. If a number is a **1**, then the number that it represents counts. If the number is a **0**, then the number it represents does not count. 

For example, using **192.168.1.0**:
The first octet here is **192**. To get a binary number out of **192**, you need to first look at the octet chart, then you put **1**s under the numbers that will add up to the total of **192**, and **0**s under the rest, as follows:

"192"  ->  | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 | 
              1     1    0    0   0   0   0   0

Here you can see that **128 + 64 = 192**, so those two bits need to be **1**. The rest are left out because they don't add into **192**.

#### CHALLENGE:
Work out the next 3 octets with no help.

**Results:**

"168"  ->  | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |     
              1     0    1    0   1   0   0   0

"1"    ->  | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 | 
              0     0    0    0   0   0   0   1

"0"    ->  | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 | 
              0     0    0    0   0   0   0   0 


My results for **192.168.1.0** ----> **11000000 10101000 00000001 00000000**
*This is correct.*

---

### Subnet Mask Conversion
The subnet mask conversion works the exact same way. So if we wanted to translate the subnet mask **255.255.255.0**:

"255"  ->  | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 | 
              1     1    1    1   1   1   1   1 
"255"  ->  | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 | 
              1     1    1    1   1   1   1   1
"255"  ->  | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 | 
              1     1    1    1   1   1   1   1
"0"    ->  | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 | 
              0     0    0    0   0   0   0   0  

So it would be:
**255.255.255.0** ------> **11111111 11111111 11111111 00000000**

---

### Comparing the IP and Subnet Mask

If we compare the IP and subnet mask in binary, we get:
* **192.168.1.0**   ------> **11000000 10101000 00000001 00000000**
* **255.255.255.0** ------> **11111111 11111111 11111111 00000000**

To tell which portion of the IP is the network part, you line the binary up. Everywhere there is a **1** in the subnet mask, you cross that number out. Everywhere there is a **0**, don't cross it out. 

The results:
* **192.168.1.0**   ------> **//////// //////// //////// 00000000**
* **255.255.255.0** ------> **11111111 11111111 11111111 00000000**

This shows that the first 3 octets of the IP address are the network portion, and the remaining octet is the host portion. **1**s in the subnet mask represent the network address, and **0**s indicate the host address. 

#### Second Example:
* **172.17.10.3** ------> **10101100 00010001 00001010 00000011**
* **255.255.0.0** ------> **11111111 11111111 00000000 00000000**

Here, **172.17.x.x** belongs to the network, and **x.x.10.3** belongs to the host. This is the depth of subnetting but in its most basic form: where there is a **255**, that number stays and belongs to the network, and where there is a **0**, that number changes for each different host on the network.

---


### In Real Terms

Your home has a local network. Your devices speak to each other and other devices on the internet. This network consists of a phone, laptop, PC, and TV. But how do all these devices talk to the internet and the World Wide Web? 

It needs a gateway. 

Your router is your **default gateway**, and it sounds complicated, but if you just take the name at face value, it's easy:
* **"default"** - the normal choice
* **"gateway"** - a door that takes you somewhere

So it's the normal doorway to somewhere. The default doorway out of your local network.

Although your router does this, in itself, it is also just a device or host, and it is connected to the main network which is your ISP's network. Forget the ISP part and just think *"router is the default gateway and it is just a host/device just like a laptop or phone"*. If this is the case, your router needs an IP address just like your phone. Let's say your phone's IP address is **192.168.1.13**, with a subnet mask of **255.255.255.0**. **192.168.1** belongs to your network, and **.13** belongs to your phone (the host/device). So when you are on Google and you search "WikiHow", you are sending data or information from your IP address to the Google server's IP address to access WikiHow. This info or data comes from your IP which ends in **.13**, so when the data gets sent back, your router knows to send it straight to host no.13. 

The router can only do this due to 2 concepts:
* **DHCP** - Dynamic Host Configuration Protocol
* **NAT** - Network Address Translation

These topics are more discussed in their named files.


