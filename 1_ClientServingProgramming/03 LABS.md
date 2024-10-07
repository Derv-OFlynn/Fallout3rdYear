### <mark style="background: #FF5582A6;">Lab 2:</mark>

<mark style="background: #FF5582A6;">Wireshark</mark> is a packet sniffing program that network admins can use to isolate and troubleshoot problems on the network

Can be used maliciously to capture usernames, passwords, emails and web pages.

![](https://i.imgur.com/W3xg2wg.png)

Analysing Telnet, SSH, FTP and HTTP.

FTP and HTTP happen on the internet.

Telnet and SSH happen on a router.

Telnet is not encrypted -> can view traffic on Wireshark. Can see keystrokes, all sent in separate packages.

SSH is very secure.

### <mark style="background: #FF5582A6;">TO NOTE:</mark>

<mark style="background: #FF5582A6;">The three sections of the screen layout,</mark>
- Top section shows number, time, source, destination, protocol, length and info
- Source and destination look like MAC addresses?
- Length is length of bytes
- The info shows if it is a request, response, http or get, etc.
- The bottom left section gives details about selected packet. Shows frame, IP version, cert, etc.
- Bottom right shows hex and some unencrypted plaintext.

<mark style="background: #FF5582A6;">The Header Field structures associated with each framing entity, </mark>

<mark style="background: #FF5582A6;">Addressing fields associated with each framing entity,</mark>

<mark style="background: #FF5582A6;">The raw data “on the wire”.</mark>


# <mark style="background: #FF5582A6;">LAB 3</mark>

Download thingy

Unzip it

The ubuntu14.04-1.vbox one is partially configured

Add it and 2 into vbox

Set 1st vbox adapter as NAT. Click advanced tab and say "connected bia table". Turn on port forwarding. Might be entries.

Name: soc
Password: letmein

Machine 1: 192.168.1.11
Machine 2: 192.168.1.12

Connect using WinSCP

Use Putty to connect.

Done