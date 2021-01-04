# How Does the Web Work?

## Overview

The internet consists of 4 layers (should be considered bottom-up):

| Layer # | Layer Name | Protocols | Related Concepts |
|---------|------------|-----------|------------------|
| 4 | Application | HTTP &bull; Every application-specific protocol, e.g. email (POP3 &bull; SMTP &bull; IMAP), WhatsApp, Netflix... | Domain Names, DNS &bull; Request/Response &bull; URL &bull; HTTP Methods (GET, PUT, POST, DELETE...) &bull; HTTP Headers
| 3 | Transport | TCP &bull; UDP | Client/Server &bull; Connection &bull; Port &bull; Socket
| 2 | Internet   | IP | IP Address &bull; IPv4/IPv6
| 1 | Link      | **M**edium **A**ccess **C**ontrol (WiFi &bull; Ethernet &bull; ADSL &bull; ISDN) | Physical (MAC) Address

The *World Wide Web* consists of all the things (websites, browsers, applications, servers) that use HTTP.

## The Link Layer

## The Internet Layer
- Cold War origins (ARPANET)
- Global distributed network
- Analogy: international mail

## The Transport Layer

### 1st Case Study: Online Chess
- Each player has an application that shows the current state of the board.
- Each move can be described using some formal notation and sent to the opponent using IP.
- Missing features:
    - Finding an opponent
    - Sharing the computer with other applications
    - Lost packets, retransmission

### 2nd Case Study: Chat
- Missing features:
    - Finding your contacts
    - Sharing the computer with other applications
    - Lost packets, retransmission
    - Out-of-order packets
    - Packet size limit

