### <mark style="background: #FF5582A6;">Format of Internet Packets:</mark>

The IP software defines its own internet packet format known as an <mark style="background: #FF5582A6;">IP datagram</mark>.

It is a <mark style="background: #FF5582A6;">universal</mark>, <mark style="background: #FF5582A6;">virtual</mark> packet which has a particular format/structure which is very different to that of a hardware frame.

It can carry a <mark style="background: #FF5582A6;">single</mark> octet of data or multiple octets up to a maximum of <mark style="background: #FF5582A6;">64K</mark> octets (including the header)

### <mark style="background: #FF5582A6;">IP datagram header format:</mark>

![](https://i.imgur.com/afycdXO.png)

### <mark style="background: #FF5582A6;">Forwarding an IP datagram:</mark>

Recall that a router makes its routing decision based on the <mark style="background: #FF5582A6;">destination IP address</mark>.

Routing information is stored in a <mark style="background: #FF5582A6;">routing table</mark>. This table must be <mark style="background: #FF5582A6;">initialised</mark> on boot-up and updated if the topology changes:

The next three slides show example <mark style="background: #FF5582A6;">Routing Tables</mark>:
- The first slide recalls a high-level <mark style="background: #FF5582A6;">Routing Table</mark> from previous discussions,
- The second and third slides shows a <mark style="background: #FF5582A6;">Routing Table</mark> from a real router.

![](https://i.imgur.com/FyJCz28.png)

![](https://i.imgur.com/hvE88uM.png)

Note the network numbers and the connections to the routers.

The Routing Table router 1 (R1) is shown on the next slide.

![](https://i.imgur.com/uNmEBdF.png)

The <mark style="background: #FF5582A6;">physical network</mark> does not understand the datagram format.

Instead the datagram is placed in the <mark style="background: #FF5582A6;">data area</mark> of a <mark style="background: #FF5582A6;">hardware frame</mark>.

This is known as <mark style="background: #FF5582A6;">encapsulation</mark>.

![](https://i.imgur.com/pB3xJZ3.png)

### <mark style="background: #FF5582A6;">IP Encapsulation:</mark>

This process is applied on each leg of the transmission path.

The datagram is stored in memory without the additional frame header information.

The size of the frame header may vary as it traverses different network technologies.

![](https://i.imgur.com/if8mwjQ.png)

### <mark style="background: #FF5582A6;">IP Datagram and the internet:</mark>

![](https://i.imgur.com/6ZrjhyF.png)

### <mark style="background: #FF5582A6;">Encapsulation and Information flow between the layers on an end-host</mark>

![](https://i.imgur.com/R0CrDL7.png)
