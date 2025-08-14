# OSI Model (7 Layers)

```mermaid
flowchart TB
  subgraph OSI_Model["OSI Model (Top → Bottom)"]
    A7["Layer 7 — Application
• HTTP, FTP, SMTP, DNS
• User-level services"]
    A6["Layer 6 — Presentation
• TLS/SSL, JPEG, JSON
• Encryption, compression, translation"]
    A5["Layer 5 — Session
• NetBIOS, RPC, gRPC
• Session setup, checkpoints"]
    A4["Layer 4 — Transport
• TCP, UDP, QUIC*
• Segmentation, reliability, flow control"]
    A3["Layer 3 — Network
• IP, ICMP, OSPF, BGP
• Logical addressing & routing"]
    A2["Layer 2 — Data Link
• Ethernet, Wi-Fi (802.11), PPP
• Framing, MAC, ARP"]
    A1["Layer 1 — Physical
• Copper, Fiber, Radio
• Bits on the wire (voltages, light, RF)"]
  end

  %% Devices per layer
  D7["— Apps/Servers —"]
  D4["— Host OS/Kernel —"]
  D3["— Routers —"]
  D2["— Switches/Bridges —"]
  D1["— Hubs/Repeaters/Cables —"]

  %% Stack order
  A7 --> A6 --> A5 --> A4 --> A3 --> A2 --> A1

  %% Annotations to typical devices
  A7 --- D7
  A6 --- D7
  A5 --- D7
  A4 --- D4
  A3 --- D3
  A2 --- D2
  A1 --- D1

  %% PDU types
  classDef pdu fill:#f0f9ff,stroke:#0ea5e9,stroke-width:1px,color:#0a0a0a;
  P4["PDU: Segments (TCP) / Datagrams (UDP)"]:::pdu
  P3["PDU: Packets"]:::pdu
  P2["PDU: Frames"]:::pdu
  P1["PDU: Bits"]:::pdu

  A4 --- P4
  A3 --- P3
  A2 --- P2
  A1 --- P1

  %% Notes
  note1["*QUIC runs over UDP at the Transport layer but integrates crypto & multiplexing akin to L4/L5 concerns"]
  A4 --- note1