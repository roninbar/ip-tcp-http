# How Does the Web Work?

# Introduction

-   Cold War origins (ARPANET)
-   Global distributed network
-   The Internet is made up of many **L**ocal **A**rea **N**etworks, like the ones in your home or office building.
-   The LANs are connected by the _Internet backbone_.

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
-   Mail analogy: to send a letter to someone, you need to
    -   put the letter in an envelope.
    -   write the recipient's address on one side of the envelope.
    -   write the sender's address (yours) on the other side.
    -   close the envelope and put it in the local mailbox.
    -   The mail service takes care of delivering your letter to the recipient.
-   Similarly, to send digital information to another computer on the same LAN, you need to
    -   Construct a _data frame_, made up of
        1. The _frame header_, containing the physical addresses of the sender and the recipient.
        2. The actual data, or _payload_
        3. The _frame footer_
    -   Transmit the frame over the physical medium (wire or radio frequency) connecting your device to the router.
    -   The router repeats the frame over the medium that connects it to the recipient.
    -   The other computer extracts the payload from the frame and interprets it somehow.

## The Internet Layer

-   Allows communications between any two computers on the Internet.
-   Analogy: international mail

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
