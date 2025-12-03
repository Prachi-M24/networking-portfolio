
# Networking Basics — Day 1

This document contains hands-on networking labs, notes, and observations for Day 1. It includes theory, practical exercises, outputs, and key points useful for Zscaler and networking interviews.

---

## 1. OSI vs TCP/IP

**OSI Model:** 7 layers — Physical → Data Link → Network → Transport → Session → Presentation → Application  

**TCP/IP Model:** 4 layers — Network Access → Internet → Transport → Application  

**Mapping:**  
- TCP/IP Application = OSI Application + Presentation + Session  
- TCP/IP is widely used because it reflects real-world protocols.

**ASCII Diagram:**

```

## OSI Model      TCP/IP Model

Application    Application
Presentation   Application
Session        Application
Transport      Transport
Network        Internet
Data Link      Network Access
Physical       Network Access

````

**Interview Tip:** Be ready to explain how TCP/IP maps to OSI in real-world networks.

---

## 2. DNS

**Purpose:** Translates **domain names → IP addresses**.  

**Common Records:**
- **A / AAAA:** Address record (IPv4 / IPv6)  
- **CNAME:** Alias  
- **MX:** Mail Exchange  
- **TXT:** Text / verification  
- **PTR:** Reverse lookup

**Query Types:**
- **Recursive:** DNS server resolves the full query for the client  
- **Iterative:** DNS server provides the next DNS server to query  

**Lab: nslookup**

```bash
nslookup google.com
````

**Sample Output:**

```
Server:  192.168.0.1
Address: 192.168.0.1

Name:    google.com
Address: 142.250.77.78
```

**Observation:** DNS resolution is successful; note authoritative vs non-authoritative responses.

---

## 3. HTTP / HTTPS

**HTTP:** Standard web protocol. Common status codes: 200, 301, 403, 404, 500

**HTTPS:** HTTP + **TLS encryption**

**TLS Handshake Steps:**

1. **Client Hello:** Proposes supported protocols & cipher suites
2. **Server Hello:** Selects protocol, sends certificate
3. **Certificate validation** by client
4. **Key exchange:** Secure channel established

**Lab: HTTPS Certificate Inspection**

* Open `https://apple.com` in Chrome
* Click **Lock icon → Certificate**
* Observe:

  * **Issued To:** [www.apple.com](http://www.apple.com)
  * **Issued By:** DigiCert or Apple Public EV Server
  * **Validity:** Start → Expiry dates
  * **Public Key & Algorithm:** RSA / ECDSA

**Observation:** TLS handshake ensures encryption; certificate confirms website authenticity.

---

## 4. Proxy vs VPN

**Proxy:** Application layer; forwards web traffic; can filter content

**VPN:** Network layer; encrypted tunnel; routes all traffic

**Zscaler:** Cloud Proxy; inspects traffic at application layer; can perform SSL inspection

**Lab: Proxy Testing (Learning Purpose)**

1. Configure browser/system to use a public proxy: `IP:Port`
2. Visit any website
3. Observe:

   * Speed difference
   * IP address change using [https://whatismyipaddress.com](https://whatismyipaddress.com)

**Observation:** Proxy adds an extra hop → increases latency. Zscaler behaves similarly but with optimized cloud nodes.

---

## 5. IP Addressing

**Public vs Private IP:**

* Private = internal LAN
* Public = Internet

**CIDR Notation:** /24, /16 → determines subnet size

**Subnet Mask & Default Gateway:** Identify network vs host parts

**Example:**

```
IP Address: 192.168.1.10
Subnet Mask: 255.255.255.0 (/24)
Network: 192.168.1.0
Host Range: 192.168.1.1 – 192.168.1.254
Default Gateway: 192.168.1.1
```

**Observation:** Understanding CIDR, subnetting, and IP classes is essential for network design and troubleshooting.

---

## References

* Cloudflare Learning: [https://www.cloudflare.com/learning/](https://www.cloudflare.com/learning/)
* GeeksforGeeks Networking: [https://www.geeksforgeeks.org/](https://www.geeksforgeeks.org/)
* MDN HTTP Status Codes: [https://developer.mozilla.org/en-US/docs/Web/HTTP/Status](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)

---

## Interview Notes

* Recursive vs Iterative DNS queries are important for Zscaler roles
* TLS handshake steps are frequently asked
* Difference between Proxy and VPN is key for cloud security roles
* CIDR and subnetting are essential for networking interviews

---



Do you want me to do that next?
```
