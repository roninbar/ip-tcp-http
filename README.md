# How Does the Web Work?

## Overview

The web consists of 4 layers (should be considered bottom-up):

| Layer # | Layer Name | Protocols | Related Concepts |
|---------|------------|-----------|------------------|
| 4 | Application | HTTP &bull; Every application-specific protocol, e.g. email (POP3 &bull; SMTP &bull; IMAP), WhatsApp, Netflix... | Request/Response &bull; URL &bull; HTTP Methods (GET, PUT, POST, DELETE...) &bull; HTTP Headers
| 3 | Transport | TCP &bull; UDP | Client/Server &bull; Connection &bull; Port &bull; Socket
| 2 | Internet   | IP | IP Address &bull; IPv4/IPv6
| 1 | Link      | **M**edium **A**ccess **C**ontrol (WiFi &bull; Ethernet &bull; ADSL &bull; ISDN) | MAC Address

## The Link Layer

## The Internet Layer

- Analogy: international mail

## The Transport Layer

### Case Study: Online Chess
- Each player has an application that shows the current state of the board.
- Each move can be described using some formal notation and sent to the opponent using IP.
- Missing Features:
    - Lost packets
    - Alternating turns
    - Finding an opponent
    - Determining if someone won
    - Maintaining a history of played games
    - Sharing the computer with other applications