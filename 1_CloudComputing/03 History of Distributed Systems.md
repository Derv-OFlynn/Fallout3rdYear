### <mark style="background: #BABD00;">Evolution of Distributed Systems:</mark>

![](https://i.imgur.com/pqVCEWy.png)

<mark style="background: #BABD00;">Monolithic Systems (Single Tier):</mark>
- Central processing (mainframe)  
- Multiple access supported by time sharing Operating Systems  
- Primitive User Interface

<mark style="background: #BABD00;">Client/Server Database Systems (Two-Tier):</mark>
- Centralised DBMS, often running on a Unix system:
- Windows clients connect over a LAN.  
- Service Logic resides on a client, for example, calculation of pay after overtime rates etc..  
- Manual Installation of clients

<mark style="background: #BABD00;">Multi-Tier Systems:</mark>
- Database server on one host  
- Web server and Application server on another host  (connected by a LAN)  
- (Thin) Clients downloaded as applets. Communicates with the application server.  

![](https://i.imgur.com/oggBGaO.png)

![](https://i.imgur.com/6vQlM4C.png)

### <mark style="background: #BABD00;">Sample N-Tier (Twitter):</mark>

![](https://i.imgur.com/YuHX7i1.png)

### <mark style="background: #BABD00;">Centralised System Characteristics:</mark>

- One component with non-autonomous parts  
- Component shared by users all the time  
- All resources accessible  
- Software runs in a single process  
- Single Point of control  
- Single Point of failure

### <mark style="background: #BABD00;">Distributed System Characteristics:</mark>  

- Multiple autonomous components  
- Components are not shared by all users  
- Resources may not be accessible  
- Software runs in concurrent processes on different processors  
- Multiple Points of control  
- Multiple Points of failure

### <mark style="background: #BABD00;">Examples of Distributed Systems:</mark>

<mark style="background: #BABD00;">The Internet </mark> 

Heterogeneous network of computers and applications  

Implemented through the Internet Protocol Stack  

Typical configuration:
![](https://i.imgur.com/Set6LBr.png)

<mark style="background: #BABD00;">Distributed Multimedia- Systems</mark>  

Often use Internet infrastructure  

Characteristics  
- Heterogeneous data sources that need to be synchronized in real time  
	- Video  
	- Audio  
	- Text  
- Often: Distribution services  
	- Multicast  

Examples  
- Tele-teaching tools  
- Video- conferencing  
- Video and audio on demand

<mark style="background: #BABD00;">Intranets:</mark>  
- Locally administered network  
- Usually proprietary (e. g., the University campus network)  
- Interfaces with the Internet  
- Firewalls  
- Provides services internally and externally

![](https://i.imgur.com/s5qlO5f.png)

### <mark style="background: #BABD00;">Mobile and Ubiquitous Computing Systems:</mark>

Cellular phone systems (e. g., GSM, UMTS)  
- Resources being shared  
	- Radio frequencies  
	- Transmission times on one frequency (UMTS: multiplexing)  
	- The mobile on the move  

Laptop computers  
- Wireless LANs  
- Handheld devices,  
	- PDAs etc. – Bluetooth networks  

Wearable devices

![](https://i.imgur.com/v6XKXQg.png)

<mark style="background: #BABD00;">Embedded systems:</mark>  

**Avionics control systems**  - Flight management systems in aircraft  

**Automotive control systems** - Mercedes S- Class cars are equipped with 50+ autonomous embedded processors  

**Connected through proprietary bus** - like LANs  

**Consumer Electronics** - Audio HiFi equipment  

**Medical Devices** - Pace Makers

**Tele Surgery** - "Lindbergh Operation"

### <mark style="background: #BABD00;">Additional Notes:</mark>

<mark style="background: #BABD00;">GSM</mark> - (Global System for Mobile Communications, originally Groupe SpécialMobile), is a standard developed by the European Telecommunications Standards Institute (ETSI) to describe the protocols  for second-generation (2G) digital cellular networks used by mobile phones, first deployed in Finland in July 1991.[2] As of 2014 it has become the de facto global standard for mobile communications - with over 90% market share, operating in over 219 countries and territories.[3]  

<mark style="background: #BABD00;">UMTS</mark> - The Universal Mobile Telecommunications System (UMTS) is a third generation mobile  
cellular system for networks based on the GSM standard.  

<mark style="background: #BABD00;">Multiplexing</mark> (sometimes contracted to muxing) is a method by which multiple analog or digital signals are combined into one signal over a shared medium. The aim is to share an expensive resource.  

<mark style="background: #BABD00;">The Lindbergh Operation</mark> was a complete tele-surgical operation carried out by a team of French  
surgeons located in New York on a patient in Strasbourg, France (over a distance of several thousand miles) using telecommunications solutions based on high-speed services and sophisticated surgical robotics. The operation was performed successfully on September 7, 2001 by Professor Jacques Marescaux and his team from the IRCAD (Institute for Research into Cancer of the Digestive System). 
This was the first time in medical history that a technical solution proved capable of reducing the  time delay inherent to long distance transmissions sufficiently to make this type of procedure possible. The name was derived from that of American aviator Charles Lindbergh, because he was the first person to fly solo across the Atlantic