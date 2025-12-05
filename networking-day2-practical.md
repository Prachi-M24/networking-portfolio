# 📄 **networking-day2-practical.md**

````
# Networking — Day 2 Practical Labs (NAT, Routing, VPN, Firewall, Ports)
----

## 🔵 1. NAT Verification Lab

### Step 1 — Find Private IP
```bash
ipconfig
````

Observe:

* IPv4 Address → 192.168.x.x or 10.x.x.x
* Default Gateway → Your router

### Step 2 — Identify Public IP (NAT Output)

Visit:
[https://whatismyipaddress.com/](https://whatismyipaddress.com/)

Compare:

* Private IP (from ipconfig)
* Public IP (from website)

**Result:** NAT is translating private → public.

---

## 🔵 2. Routing Labs

### Step 1 — View Routing Table

```bash
route print
```

Check:

* IPv4 Route Table
* Default route → `0.0.0.0  0.0.0.0  <your-gateway>`

### Step 2 — Trace Route to Internet Sites

```bash
tracert google.com
tracert microsoft.com
tracert openai.com
```

Observe:

* Hop 1 → Your gateway
* Next hops → ISP routers
* Final hop → destination

---

## 🔵 3. VPN Behavior Simulation (No VPN Needed)

### Step 1 — Check routes with no VPN

```bash
route print
```

You will see ONLY one default route.

### If you connect a VPN later:

Check again—VPNs usually add:

* Additional default route (Full Tunnel)
* Specific subnets only (Split Tunnel)

This demonstrates how VPN modifies routing.

---

## 🔵 4. Firewall Practical

### Step 1 — Open Windows Firewall GUI

```
wf.msc
```

### Step 2 — Identify existing rules

Check:

* Inbound Rules
* Outbound Rules

### Step 3 — Create a Block Rule (Test)

Path:
Outbound Rules → New Rule → Port → TCP → 80 → Block

Try opening:

```
http://example.com
```

**Expected:** HTTP fails (port 80 blocked).
HTTPS (443) still works.

Delete the rule after testing.

---

## 🔵 5. Ports & Protocols Practical

### Step 1 — Check active connections

```bash
netstat -ano
```

Look for:

* Port 80 / 443 → Browser
* Port 53 → DNS
* Port 3389 → RDP
* Port 22 → SSH (if any)

### Step 2 — DNS Query Testing

```bash
nslookup google.com
nslookup microsoft.com
nslookup openai.com
```

Output shows:

* DNS Server used
* A records (IP addresses)

---

## 🔵 6. Summary of Commands Used

| Purpose            | Command             |
| ------------------ | ------------------- |
| Private IP         | `ipconfig`          |
| Routing table      | `route print`       |
| Trace route        | `tracert <domain>`  |
| Firewall console   | `wf.msc`            |
| Active connections | `netstat -ano`      |
| DNS lookup         | `nslookup <domain>` |

---



Just tell me: **“Make it more professional”** or **“Create full practical portfolio structure”**.
```
