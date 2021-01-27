# How Does the Internet Work?

# Introduction

-   Cold War origins (ARPANET)
-   Global decentralized network
-   The Internet is made up of many **L**ocal **A**rea **N**etworks, like the ones in your home or office building, and **W**ide **A**rea **N**etworks.

![Submarine Cable Map](/images/submarinecablemap.png)

## Overview

The Internet consists of 4 layers which are numbered from the bottom up:

| Layer # | Layer Name  | Protocols                                                                                                        | Related Concepts                                          |
| ------- | ----------- | ---------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| 4       | Application | HTTP &bull; Every application-specific protocol, e.g. email (POP3 &bull; SMTP &bull; IMAP), WhatsApp, Netflix... | Domain Names, DNS &bull; Request/Response &bull; URL      |
| 3       | Transport   | TCP &bull; UDP                                                                                                   | Client/Server &bull; Connection &bull; Port &bull; Socket |
| 2       | Internet    | IP                                                                                                               | IP Address &bull; IPv4/IPv6                               |
| 1       | Link        | WiFi &bull; Ethernet &bull; ADSL &bull; Cellular Data (LTE, 4G, 5G...)                                           | Physical (MAC) Address                                    |

## The Link Layer

-   Allows direct communication between computers that are connected by a _physical medium_ (wire, optical fiber, radio frequency, satellite link...) to each other or to a common router.
-   LANs usually use _Ethernet_ cables and/or _WiFi_ to connect end devices to a central router.
-   End devices have a 48-bit _physical, or MAC, address_.
-   To send a message from one computer to another on the same LAN, the sender must know the recipient's physical address.

![Pneumatic Tube Hub](/images/pneumatic-tube-hub-1900s.jpg)

![Pneumatic Tube Hub](/images/pneumatic-tube-hub-1940s.jpg)

![Pneumatic Capsule](/images/Pneumatic-Tube-New-York-City-Postal-Service-Mail.jpg)

-   Pneumatic tube analogy: to send a package, you need to
    1.  Put the package in a capsule.
        1.  Write the recipient's name on one side of the capsule.
        1.  Write the sender's name (yours) on the other side.
    1.  Put the capsule in your end of the pneumatic tube and send it to the sorting room.
    1.  A worker in the sorting room receives the capsule, reads who is supposed to receive it, puts it in the proper tube and sends it to that person's room.
    1.  The recipient opens the capsule and takes the package.
-   Similarly, to send digital information to another computer on the same LAN, the link layer
    1.  Constructs a _frame_, made up of
        1.  The _frame header_ (14 bytes), containing the physical addresses of the sender and the recipient.
        1.  The actual data, or _payload_.
        1.  The _frame footer_ (4 bytes).
    1.  Transmits the frame over the physical medium (wire or radio frequency) connecting your device to the router.
    1.  The router repeats the frame over the medium that connects it to the recipient.
    1.  The other computer extracts the payload from the frame and interprets it somehow.

## The Internet Layer

-   Allows communications between _any two_ computers on the Internet, not just those that are directly connected to each other.
-   Consists of one main protocol, the _Internet Protocol_ (IP) and several auxilliary protocols (e.g. ICMP).
-   IP Addresses:   

    | Version | Bits | Example                           |
    | ------- | ---- | --------------------------------- |
    | IPv4    | 32   | 10.83.237.32                      |
    | IPv6    | 128  | 2a03:2880:f22d:c5:face:b00c:0:167 |

-   Uses other computers on the Internet as _routers_, or _gateways_ (i.e. relays) between different networks.
-   IP software is built into the operating systems of the end computers and of each intermediate router.

![en:User:Cburnett original work, colorization by en:User:Kbrose, CC BY-SA 3.0 <http://creativecommons.org/licenses/by-sa/3.0/>, via Wikimedia Commons](/images/IP_stack_connections.svg)

-   To send a message to another computer on the Internet, the Internet layer
    1. Constructs a _packet_, made up of
        1. The _IP header_, containing the IP addresses of the sender and recipient.
        1. The actual data, or _payload_.
    1. If the destination address belongs to the local network:
        1. Send the packet, using the link layer, directly to the destination.
    1. If the destination address does not belong to the local network:
        1. Send the packet, using the link layer, to the _gateway_ (e.g. your DSL router).
        1. The gateway uses a _routing table_ to decide which neighboring router is closest to the packet's intended destination.
        1. Use the link layer to send it to that router (the next _hop_).
        1. Each hop brings the packet closer to its destination.
- So, an Ethernet frame contains an IP packet, which, in turn, contains the payload.

![By en:User:Cburnett original work, colorization by en:User:Kbrose - Original artwork by en:User:Cburnett, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=1546338](/images/UDP_encapsulation.svg)

![Matryoshka](/images/matryoshka.jpeg)

## The Transport Layer

So, the Internet layer allows us to communicate with any computer on the Internet. Why do we need more layers, then?

<table>
    <thead>
        <tr>
            <th>&nbsp;</th>
            <th>Comm<br/>Layer</th>
            <th>Implemented by</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>&nbsp;</td>
            <td>Application</td>
            <td>Application</td>
        </tr>
        <tr>
            <td>&nbsp;</td>
            <td>Transport</td>
            <td rowspan="3">OS</td>
        </tr>
        <tr>
            <td>&nbsp;</td>
            <td>Internet</td>
            <!-- <td>OS</td> -->
        </tr>
        <tr>
            <td>&nbsp;</td>
            <td rowspan="2">Link</td>
            <!-- <td>OS</td> -->
        </tr>
        <tr>
            <td>&nbsp;</td>
            <!-- <td>Link</td> -->
            <td colspan="2">Hardware</td>
        </tr>
    </tbody>
</table>

### Basic Operating System Concepts

#### Processes

-   Modern operating systems support _multitasking_: running more than one program at the same time.
-   A _process_ is an isolated execution environment in which the OS runs each program.
    -   You can think of a process as a kind of "bubble" that the OS inflates around the application's code and data, isolating it from the rest of the software running on the computer at the same time.
-   The process gives the application code the illusion that it the only program running on the computer.
-   If an application crashes, it doesn't crash the whole system.
-   Incoming IP packets are received by the OS.
-   However, most packets are meant to be handled by some specific application. For example, an HTTP response should go to the browser that requested it.
-   If we let each running process pick the packets it wants to handle, bad things are going to happen.

#### IPC

-   Processes can communicate with each other using a number of **I**nter-**P**rocess **C**ommunication mechanisms:
    -   Shared Memory
    -   Pipes
    -   TCP/IP Sockets
-   Shared memory and pipes only allow communication between two processes running on the same machine.

#### Sockets

-   Sockets allow communication between processes running on the same machine (using the _loopback_ network interface) or on different machines (using a physical network interface).
-   You can think of a socket as a physical socket (like a USB or RJ45 socket) embedded in the bubble's outer wall.
-   To communicate using sockets,
    1. One process acts as the _server_ and opens a socket "passively", waiting for connections on a _well-known port_ (e.g. port 21 for FTP).
    2. Another process opens a socket "actively", specifying a target host (e.g. 127.0.0.1 for the local host) and _port_ (e.g. 21).
    3. The transport layer establishes a TCP connection between the two processes.

### Case Study: FTP

#### FTP Demonstration
