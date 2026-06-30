# Day 15 – Networking Concepts: DNS, IP, Subnets & Ports
### Task 1: DNS – How Names Become IPs
1. Explain in 3–4 lines: what happens when you type `google.com` in a browser?

- 1.Browser checks its cache; if a miss → OS resolver checks.
- **DNS Lookup** :The browser queries the Domain Name System (DNS) to translate the human-readable text google.com into a machine-readable numeric IP address.
- 2.Resolver queries DNS server → root → TLD → authoritative DNS server.
- **Establish Connection**: The browser uses the retrieved IP address to set up a secure TCP/IP connection with Google’s servers.
- 3.Authoritative server returns IP (A/AAAA) record.
- **HTTP Request**: It sends a secure HTTPS request asking for the website content.
- 4.Browser initiates TCP connection → HTTP/HTTPS request → page loads.
- **Page Rendering**: Google's servers process the request and reply with HTML, CSS, and JavaScript files, which your browser parses and displays as a webpage on your screen.

2. What are these record types? Write one line each:

| Record Type | Purpose |
| ----------- | ------- | 
| A           | Maps a domain directly to an IPv4 address | 
| AAAA        | Maps a domain directly to an IPv6 address | 
| CNAME       | Alias one domain to another another domain name |
| MX          | Specifies mail servers for the domain | 
| NS          | Lists authoritative DNS servers responsible for the domain | 

3. Run: `dig google.com` — identify the A record and TTL from the output
A:- 142.251.222.174
TTL:- 229

### Task 2: IP Addressing
1. What is an IPv4 address? How is it structured? (e.g., `192.168.1.10`)
- An IPv4 address is a unique 32-bit numerical label assigned to every device connected to a computer network using the Internet Protocol, divided into 4 octets.
     - **32-Bit Length**: The full address contains exactly *32 binary bits* (zeros and ones).
     - **Four Octets**: The address is divided into four 8-bit segments called *octets*. Range from 0 - 255
     - **Network vs. Host**: A subnet mask splits the address into a *network ID* (identifies the specific network) and a *host ID* (identifies the specific device).

Structure Example `192.168.1.10`

| Octet | Decimal | Binary         |
|-------|--------|----------------|
| 1     | 192    | 11000000       |
| 2     | 168    | 10101000       |
| 3     | 1      | 00000001       |
| 4     | 10     | 00001010       |

### 2. Public vs Private IPs

| Public        | Private                     | 
| ----------- | ------------------------------- | 
|  Accessible on the Internet by anyone and routed worldwide | Hidden from the internet and cannot be reached from outside your local networks   |
| Assigned to your router by your Internet Service Provider (ISP). | Assigned to your device by your local router (usually via DHCP). |
| Globally unique address used to identify your network on the public internet. | Regionally unique address used only within your local network (like your home or office). |
| `8.8.8.8` (A public address used by Google's public DNS server). | `192.168.1.15` (A private address for a smartphone connected to a home Wi-Fi network). |

### 3. Private IP Ranges
- `10.0.0.0 – 10.255.255.255` - used for Large enterprise networks
- `172.16.0.0 – 172.20.255.255` - used for Medium corporate & campus networks 
- `192.168.0.0 – 192.168.255.255` - used for Home and small office networks

### 4. Run: `ip addr show` — identify which of your IPs are private
- private IP is 172.28.217.229

## Task 3: CIDR & Subnetting

### 1. What does `/24` mean in `192.168.1.0/24`?
- CIDR notation specifies **network bits**.  
- `/24` → 24 bits for network, 8 bits for host.
- The `/24` means the first three numbers (`192.168.1.`) are fixed for the network, leaving the last number free for up to 254 individual devices.
### 2. How many usable hosts in a `/24`? A `/16`? A `/28`?
Formula: `Usable Hosts = 2^(32 - CIDR) - 2`  
Higher CIDR number = Fewer IP's
Lower CIDR number = More IP's

   - `/24`: **254** usable hosts (2⁸ - 2).
   - `/16`: **65,534** usable hosts (2¹⁶ - 2).
   - `/28`: **14** usable hosts (2⁴ - 2).

  

