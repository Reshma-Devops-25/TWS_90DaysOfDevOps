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

1. What does `/24` mean in `192.168.1.0/24`?
- CIDR notation specifies **network bits**.  
- `/24` → 24 bits for network, 8 bits for host.
- The `/24` means the first three numbers (`192.168.1.`) are fixed for the network, leaving the last number free for up to 254 individual devices.
2. How many usable hosts in a `/24`? A `/16`? A `/28`?
Formula: `Usable Hosts = 2^(32 - CIDR) - 2`  
Higher CIDR number = Fewer IP's
Lower CIDR number = More IP's

   - `/24`: **254** usable hosts (2⁸ - 2).
   - `/16`: **65,534** usable hosts (2¹⁶ - 2).
   - `/28`: **14** usable hosts (2⁴ - 2).
3. Why Subnet?
- To divide large network into smaller, secure chunks to stop traffic, boost speed and manageable networks.

4. Quick Reference Table

| CIDR | Subnet Mask | Total IPs | Usable Hosts |
|------|-------------|-----------|--------------|
| /24  | 255.255.255.0   | 254   | 254          |
| /16  | 255.255.0.0     | 65534 | 65534        |
| /28  | 255.255.255.254 | 14    | 14           |

### Task 4: Ports – The Doors to Services
1. What is a port? Why do we need them?
- **Port:** a virtual, software-based endpoint that directs specific network traffic to the correct application or service on your device.
A port is a logical identifier used to distinguish different applications or services on a device, allowing network traffic to reach the correct program.

- **Service Identification:** Multiple applications running on the same device are distinguished using port numbers. For example, HTTP (port 80) and SMTP (port 25) can operate simultaneously on a single computer because each service listens on a different port, ensuring data reaches the correct service.
- **Efficient Data Routing:** When a device receives data from the network, port numbers help the operating system direct incoming packets to the appropriate application efficiently.
- **Traffic Control and Security:** Firewalls use port numbers to allow or block traffic for specific applications or services. Blocking traffic to certain ports helps prevent access to services that may pose security risks.
- **Service Scalability:** Port numbers enable a single device to support many services at the same time. By assigning different ports to different services, the system can scale and handle multiple network applications concurrently.

2. Common ports:

| Port | Service |
|------|---------|
| 22   | SSH     |
| 80   | HTTP    |
| 443  | HTTPS   |
| 53   | DNS     |
| 3306 | MySQL   |
| 6379 | Redis   |
| 27017| MongoDB |
  
3. Run `ss -tulpn` — match at least 2 listening ports to their services
    - `22`:- SSH
    - `53`:- DNS

### Task 5: Putting It Together

### 1. `curl http://myapp.com:8080` – networking concepts involved
- Your terminal translates `myapp.com` to an IP address and sends an unencrypted HTTP GET request directly to port **8080** instead of the standard web port.
- **DNS**: Resolve `myapp.com` → IP  
- **TCP**: Reliable transport layer  
- **HTTP**: Application protocol  
- **Port 8080**: Directs request to specific service  

### 2. App can't reach a database at `10.0.1.50:3306` — what would you check first?
  - **Network Line Check**: Run `ping 10.0.1.50` to see if the database server machine is online and reachable from your app server.
  - **Port Connectivity**: Run `nc -zv 10.0.1.50 3306` (or `telnet 10.0.1.50 3306`) to check if firewalls, security groups, or ACLs are blocking traffic on port 3306
  - **Database Listening Config**: Verify that the MySQL/MariaDB service is actually running on the target server and its bind-address configuration is set to `0.0.0.0` or `10.0.1.50` rather than just `127.0.0.1`.

### What I learned

1. **DNS Resolution is the Backbone of the Internet** – Domain names like google.com are translated into IP addresses through a hierarchy of caches, root/TLD, and authoritative servers, enabling browsers to connect to the right server.

2. **IP Addressing & Subnetting Organize Networks** – Understanding public vs private IPs, CIDR notation, and subnet masks helps manage networks efficiently and calculate usable hosts.

3. **Ports Direct Traffic to the Right Service** – Ports act as “doors” for applications; combined with IPs and protocols like TCP/HTTP, they ensure data reaches the correct service (e.g., web, database, email).

