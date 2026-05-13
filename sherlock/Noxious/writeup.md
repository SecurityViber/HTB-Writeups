# Sherlock: Noxious

## Key Concepts

- **LLMNR** (Link-Local Multicast Name Resolution) — Port 5355/UDP. Used to resolve hostnames on local networks when DNS fails; exploitable via poisoning attacks.
- **NTLM** (NT LAN Manager) — Challenge-response authentication protocol used in Active Directory. Capturing the NTLM challenge + proof hash allows offline cracking.
- **NTLMSSP** (NT LAN Manager Security Support Provider) — Binary message protocol facilitating NTLM challenge-response authentication.

## Tools & Commands

Crack a captured NTLMv2 hash:
```sh
hashcat -a 0 -m 5600 hashfile.txt /usr/share/wordlists/rockyou.txt
```

## Wireshark Tips

- Filter for LLMNR traffic: `udp.port == 5355`
- Use **Statistics → Endpoints** to identify the most active hosts

## Key Learnings

- DHCP traffic can reveal when an IP was assigned to a host, helping correlate hostname and IP at a given point in time.
- Look for `SMB2 Session Setup Response` packets with `NTLMSSP_CHALLENGE` — these contain the hash material needed for cracking.
