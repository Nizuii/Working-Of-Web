# What is Network Reconaissance?

**Network Reconaissance** is the art of gathering information about a target network before any attack or security assessment. Think of it like "scouting phase" before any mission. Lets take a look at what reconaissance is. **Reconaissance** is the process of passively or actively collecting information about a target. Its domains, IP address, open ports, running services and technologies. It is the very first phase in any pentetration test or attack. There are 2 types of reconaissance:
- **Passive Reconaissance**: Gathering information without touching the target (WHOIS, DNS lookups, Google searches).
- **Active Reconaissance**: Directly probing the target (Port Scanning, Service Detection).

## 1. Domain Reconaissance, WHOIS & DNS.

WHOIS is a public database that stores registration info about domain names - who owns them, when they expire, what nameservers they use.

DNS Recon maps out the domain's structure by querying DNS records.

- `A` record - IP address of a domain.
- `MX` record - Mail Servers.
- `NS` record - Nameserver.
- `CNAME` - Aliases/subdomains.
- `TXT` - Various text records.

Tools used: `whois`, `nslookup`, `dig`, `dnsx`, `subdinder`.

<img width="1869" height="1030" alt="image" src="https://github.com/user-attachments/assets/d39b31a6-4070-45c0-8423-9da0b85c4481" />

## 2. Live Host, Open Ports, Running Services.

Once we know the IP range, we ping sweep to find which host are alive, then port scan to find open doors. Nmap is the primary tool here:
- `-sn` - Ping sweep (find live hosts).
  <img width="1859" height="1024" alt="image" src="https://github.com/user-attachments/assets/2e515dcf-2f78-47e6-9895-15236bcfffce" />
- `-sV` - Service version detection.

  
