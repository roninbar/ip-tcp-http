# How Does the Web Work?

# Introduction

-   Cold War origins (ARPANET)
-   Global decentralized network
-   The Internet is made up of many **L**ocal **A**rea **N**etworks, like the ones in your home or office building, as well as some **W**ide **A**rea **N**etworks.
-   The LANs and WANs are connected by the _Internet backbone_.

## Overview

The internet consists of 4 layers (should be considered bottom-up):

| Layer # | Layer Name  | Protocols                                                                                                        | Related Concepts                                                                                                         |
| ------- | ----------- | ---------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| 4       | Application | HTTP &bull; Every application-specific protocol, e.g. email (POP3 &bull; SMTP &bull; IMAP), WhatsApp, Netflix... | Domain Names, DNS &bull; Request/Response &bull; URL &bull; HTTP Methods (GET, PUT, POST, DELETE...) &bull; HTTP Headers |
| 3       | Transport   | TCP &bull; UDP                                                                                                   | Client/Server &bull; Connection &bull; Port &bull; Socket                                                                |
| 2       | Internet    | IP                                                                                                               | IP Address &bull; IPv4/IPv6                                                                                              |
| 1       | Link        | **M**edium **A**ccess **C**ontrol (WiFi &bull; Ethernet &bull; ADSL &bull; ISDN)                                 | Physical (MAC) Address, _Internet Backbone_                                                                              |

## The Link Layer

-   Allows direct communication between computers that are connected by a _physical medium_ (wire, radio frequency, optical cable...)
-   LANs usually use _Ethernet_ cables and/or _WiFi_ to connect end devices to a central router.
-   End devices have a 48-bit _physical, or MAC, address_.
-   To send a message from one computer to another on the same LAN, the sender must know the recipient's physical address.
-   Pneumatic tube analogy: to send medicine or a specimen (the "payload") to someone else in the hospital, you need to
    1.  Put the payload in a capsule.
        1.  Write the recipient's name on one side of the capsule.
        1.  Write the sender's name (yours) on the other side.
    1.  Put the capsule in your end of the pneumatic tube and send it to the sorting room.
    1.  A worker in the sorting room receives the capsule, reads who is supposed to receive it, puts it in the proper tube and sends it to that person's room.
    1.  The recipient opens the capsule and takes the payload.
-   Similarly, to send digital information to another computer on the same LAN, you need to
    1.  Construct a _data frame_, made up of
        1.  The _frame header_, containing the physical addresses of the sender and the recipient.
        1.  The actual data, or _payload_
        1.  The _frame footer_
    1.  Transmit the frame over the physical medium (wire or radio frequency) connecting your device to the router.
    1.  The router repeats the frame over the medium that connects it to the recipient.
    1.  The other computer extracts the payload from the frame and interprets it somehow.

![By en:User:Cburnett original work, colorization by en:User:Kbrose - Original artwork by en:User:Cburnett, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=1546338](/images/UDP_encapsulation.svg)

## The Internet Layer

-   Consists of one main protocol, the _Internet Protocol_ (IP) and several auxilliary protocols.
-   Allows communications between _any two_ computers on the Internet, not just those that are directly connected to each other.
-   Uses other computers on the Internet as _gateways_ (i.e. relays) between different networks.
-   IP software is built into the operating systems of the end computers and of the gateways.
-   To send a message from a computer in Tel Aviv to a computer in Honolulu, computers on the Internet cooperatively plan a _route_.
-   Route: a series of "legs" or "hops" connected by gateways.
-   To send a letter to someone in Honolulu,
    1. Put the letter in an "international" envelope.
        1. Write the recipient's address on one side of the envelope.
        1. Write the sender's address (yours) on the other side.
    1. Put the international envelope in a special "international" mailbox.
    1. The international mail service plans a route to the recipient through a series of intermediate stops, for example,
        1. Tel Aviv
        1. Rome
        1. Paris
        1. New York
        1. San Francisco
        1. Honolulu
    1. Then they take your envelope and put it in _another_ envelope.
        1. On one side of this envelope they write "Rome".
        1. On the other side they write "Tel Aviv".
    1. They put the envelope in a special

![en:User:Cburnett original work, colorization by en:User:Kbrose, CC BY-SA 3.0 &lt;http://creativecommons.org/licenses/by-sa/3.0/&gt;, via Wikimedia Commons](/images/IP_stack_connections.svg)

## The Transport Layer

### 1st Case Study: Online Chess

-   Each player has an application that shows the current state of the board.
-   Each move can be described using some formal notation and sent to the opponent using IP.
-   Missing features:
    -   Finding an opponent
    -   Sharing the computer with other applications
    -   Lost packets, retransmission

### 2nd Case Study: Chat

-   Missing features:
    -   Finding your contacts
    -   Sharing the computer with other applications
    -   Lost packets, retransmission
    -   Out-of-order packets
    -   Packet size limit

