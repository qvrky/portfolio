# What is a Subnet Mask?

Internet Protocol (IP) is a unique mailing address for your device so packets know where to land. Every device has to have an IP address to communicate with other devices, so packets of data can be sent and received correctly. 

The specific IP address type is IPv4. An IPv4 address is a 32-bit numeric address written as 4 groups of numbers separated by a full stop. Each group of numbers is called an octet, so an IPv4 address has 4 octets and usually looks something like **192.168.10.1**. In this example, **192** is a single octet, **168** is another, etc. The number range in each octet is 0 - 255, giving 256 possible values. 

An IP address consists of two parts: 
* **Network address** - Identifies the network
* **Host address** - Identifies the specific device on that network 

Every network has a unique address, and every host on it has its own unique host address (host ID)

## How do we tell which portion is for the network and which is for the host?

A subnet mask is a number that resembles an IP address, and it shows how many bits in the IP address belong to the network. It does this by masking the network portion of the IP address.


## Translating to Binary

Computers only understand binary. So how do we translate an IP address to binary?

This is an 8-bit octet chart:
**| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |**

The bits in each octet are represented by a number in this chart. Each bit in the octet can either be a **1** (counts) or a **0** (doesn't count)

For example, using **192.168.1.0**:
The first octet here is **192**. To get a binary number out of **192**, you need to first look at the octet chart, then you put **1**s under the numbers that will add up to the total of **192**, and **0**s under the rest, as follows:

"192"  ->  | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 | 
              1     1    0    0   0   0   0   0

Here you can see that **128 + 64 = 192**, so those two bits need to be **1**. The rest are left out because they don't add into **192**.

### CHALLENGE:
Work out the next 3 octets with no help.

**Results:**

"168"  ->  | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |     
              1     0    1    0   1   0   0   0

"1"    ->  | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 | 
              0     0    0    0   0   0   0   1

"0"    ->  | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 | 
              0     0    0    0   0   0   0   0 


My results for **192.168.1.0** ----> **11000000.10101000.00000001.00000000**
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
**255.255.255.0** ------> **11111111.11111111.11111111.00000000**

---

### Comparing the IP and Subnet Mask

If we compare the IP and subnet mask in binary, we get:
* **192.168.1.0**   ------> **11000000.10101000.00000001.00000000**
* **255.255.255.0** ------> **11111111.11111111.11111111.00000000**

To tell which portion of the IP is the network part, you line the binary up. Everywhere there is a **1** in the subnet mask, you cross that number out. Everywhere there is a **0**, don't cross it out. 

The results:
* **192.168.1.0**   ------> **////////.////////.////////.00000000**
* **255.255.255.0** ------> **11111111.11111111.11111111.00000000**

This shows that the first 3 octets of the IP address are the network portion, and the remaining octet is the host portion. **1**s in the subnet mask represent the network address, and **0**s indicate the host address. 

#### Second Example:
* **172.17.10.3** ------> **10101100.00010001.00001010.00000011**
* **255.255.0.0** ------> **11111111.11111111.00000000.00000000**

Here, **172.17.x.x** belongs to the network, and **x.x.10.3** belongs to the host. This is the depth of subnetting but in its most basic form: where there is a **255**, that number stays and belongs to the network, and where there is a **0**, that number changes for each different host on the network.


# More complex subnetting

Converting the subnet or the IP to binary here is useless, as the subnets are very easy to read:

* "255.255.255.0" 
* "255.255.0.0" 

Finding the network portion here is simple, but what if the IP address and subnet mask is as follows

**"172.24.1.0"**
**"255.255.224.0"**

Here, in the subnet mask, the first two octets are "255" but the third is "224"

First we convert both the subnet mask and the IP to bianry: 

   255  .   255  .  224   .   0                     172  .   24   .   1    .   0    

11111111.11111111.11100000.00000000              10101100.00011000.00000001.00000000


if we line them up and compare like I did earlier:

**10101100.00011000.00000001.00000000**
**////////.////////.///00000.00000000**
**11111111.11111111.11100000.00000000**


**Here you can see that out of 32 bits, 19 belong to the network, and 13 belong to the host**


