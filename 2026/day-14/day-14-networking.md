# Day 14 – Networking Fundamentals & Hands-on Checks

OSI layers (L1–L7) vs TCP/IP stack 

| OSI Layer (7) | OSI Layer Name   | TCP/IP Layer (4) | Key Concepts / Protocols |
|----|----|----|----|
| 7 |Application	|	 Application  | HHTP, FTP, SSH, DNS |
|6| Presentation	  |	Application    | SSL/TLS, Encryption, Compression|
|5|Session	| Application	|Session Management, Syncronization|
|4|Transport	| Transport	| TCP/UDP ports and reliability |
|3|Network	| Internet| IP addresses, IPsec and routing |
|2|Data-link	| Network access	| MAC addresses and switches like ethernet, ARP, VLAN |
|1|Physical| Network access | Cables, signals and electricity |
| |The OSI model is a conceptual framework for understanding how data is transmitted across a network | TCP/IP stands for Transmission Control Protocol/Internet Protocol and is a suite of communication protocols used to interconnect network devices on the internet.|

#### Where **IP**, **TCP/UDP**, **HTTP/HTTPS**, **DNS** sit in the stack

|    Protocol  |       Layer      |
|--------------|------------------|
|     IP       |  Internet Layer  |
|  TCP/UDP     |  Transport Layer |
| HTTP,HTTPS,DNS|  Application Layer|

Hands-on Checklist 
- **Identity:** `hostname -I` (or `ip addr show`)
- Observation: 172.28.217.229 172.17.0.1 Ip adress
    
  <img width="445" height="80" alt="Hostname" src="https://github.com/user-attachments/assets/45446633-4710-41b8-8c15-e44f9d01799b" />

- **Reachability:** `ping -c 4 google.com`
- Reachability: google.com (0% packet loss).
- Observation: Network connection is very good with ~1ms latency

<img width="850" height="234" alt="Ping" src="https://github.com/user-attachments/assets/763f4ab6-0fe1-447c-9a0a-682b9fb50850" />

  
- **Path:** `traceroute gogle.com`
- Obervation: Successfully reached the destonation at hop 18th,depspite a block of timeouts (* * *) on hops 9-15 caused by network security filtering.

<img width="735" height="456" alt="Traceroute" src="https://github.com/user-attachments/assets/d10b3fb1-9069-4219-aaa7-11682548dcad" />
 
- **Ports:** `ss -tulpn`
- Observation: SSH is listening on port 22 (on 0.0.0.0, meaning it accepts outside connections),and the local DNS resolver is listening on port 53 (on 127.0.0.54, for internal system use only)

<img width="1784" height="392" alt="ports" src="https://github.com/user-attachments/assets/138e2106-7f69-4268-a736-25ba89466fa9" />


- **Name resolution:** `dig google.com`
- Observation: The DNS query returned status: NOERROR and successfully resolved google.com to  IP address: 172.217.26.36

<img width="669" height="485" alt="resolved_ip" src="https://github.com/user-attachments/assets/d2c4eb73-6083-410c-8e3f-439a28ba9512" />

  
- **HTTP check:** `curl -I https://www.google.com`
- Observation: Received HTTP status is  200

  <img width="1907" height="411" alt="HTTP_Checks" src="https://github.com/user-attachments/assets/31fbda0b-d11c-4b74-a64f-ab2afff44a55" />

  
- **Connections snapshot:** `netstat -an | head` 
- Observation: Captured ESTABLISHED connection on port and multiple ports in LISTEN state.

<img width="760" height="250" alt="connection_listening" src="https://github.com/user-attachments/assets/ce12e74c-2096-418f-83d2-52f7bf94f7b1" />

### Mini Task: Port Probe & Interpret
1) Identify one listening port from `ss -tulpn`

<img width="1826" height="361" alt="listening_port" src="https://github.com/user-attachments/assets/6f3f8b29-bc12-4286-a52f-66d2ecf2bd3d" />

2) From the same machine, test it: `nc -zv localhost 22` or `curl -I http://localhost:22` 

<img width="647" height="84" alt="port_22_success" src="https://github.com/user-attachments/assets/9c47b236-e534-495c-8aef-5f7c862a5d31" />

- If not reachable: Next steps would be checking service status (systemctl status ssh) or firewall rules. I can also use nslookup google.com to get a non-authoritative answer.

  ## Reflection 
- Which command gives you the fastest signal when something is broken? ```ping```

- What layer (OSI/TCP-IP) would you inspect next if DNS fails? If HTTP 500 shows up?

- **If DNS Fails**
   - OSI: Layer 7 (Application) and TCP-IP: Application layer

  - Reason:
    - DNS stays in an application-layer protocol
    - Common issues include resolver misconfiguration,DNS service failure,or invalid records
    - If unresolved,move to:`Transport layer`

- **If HTTP 500 Shows Up**
  - OSI: Layer 7 (Application) and TCP-IP: Application layer

  - Reason:
    - TCP connection succeeded
    - Request reached the server
    - HTTP 500 indicates a server-side,application error,not a network issue

**Two follow-up checks you’d run in a real incident:**

1. DNS Troubleshooting
```bash
cat /etc/resolv.conf
dig google.com
```

2. HTTP 500 Troubleshooting
```bash
tail -f application.log
systemctl status <web-service>
```

