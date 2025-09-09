# 📘 DevOps & Networking Cheatsheet  

A quick reference guide for OSI model, DNS records, Linux filesystems, networking basics, and Kubernetes essentials.  

---

## 🌐 OSI Model (7 Layers)  

🔹 **Top → Bottom**  

1. **Application 🖥️** – User interaction (browsers, WhatsApp, email).  
   - Protocols: HTTP, SMTP, FTP  
2. **Presentation 🎨** – Data translation, encryption, compression.  
   - Examples: JPEG, MP3, SSL/TLS  
3. **Session 🔑** – Manages connections (start, maintain, end).  
   - Example: video call sessions  
4. **Transport 🚚** – Reliable delivery (segmentation, error checking).  
   - Protocols: TCP (reliable), UDP (fast, no guarantee)  
5. **Network 🌍** – Routing data across networks.  
   - Protocols: IP, ICMP  
6. **Data Link 🔗** – Local delivery (MAC addresses, switches).  
   - Protocols: Ethernet, Wi-Fi  
7. **Physical ⚡** – Hardware, cables, fiber optics, signals.  

🧠 **Mnemonic**:  
`All People Seem To Need Data Processing`  

---

## 📡 DNS Records  

| Record | Purpose | Example |
| ------ | ------- | ------- |
| **A** | Domain → IPv4 | `example.com → 93.184.216.34` |
| **AAAA** | Domain → IPv6 | `example.com → 2606:...` |
| **CNAME** | Alias → another domain | `www.example.com → example.com` |
| **MX** | Mail servers | `example.com → mail.example.com` |
| **TXT** | Arbitrary text (SPF, DKIM, DMARC) | `"v=spf1 include:_spf.google.com ~all"` |
| **NS** | Authoritative DNS servers | `ns1.dnsprovider.com` |
| **SOA** | Zone control info | Primary NS, contact email |
| **PTR** | Reverse DNS lookup | `93.184.216.34 → example.com` |
| **SRV** | Service records (host/port) | `_sip._tcp.example.com → sipserver.example.com:5060` |
| **CAA** | Restrict SSL/TLS cert issuers | `issue "letsencrypt.org"` |

---

## 💾 Linux Filesystems  

Linux filesystems commonly listed in `/etc/fstab`:  

- **ext2 / ext3 / ext4** → Standard Linux filesystems (ext4 is default).  
- **xfs** → High-performance, widely used in RHEL/CentOS.  
- **btrfs** → Advanced features (snapshots, checksumming).  
- **reiserfs** → Old journaling FS (rare today).  
- **jfs** → IBM filesystem, less common.  

---

## 🌍 DNS Ports  

- **UDP 53** → Default DNS queries (fast, lightweight).  
- **TCP 53** → Used when:  
  - Responses are large (DNSSEC, CDNs, IPv6).  
  - Zone transfers (AXFR/IXFR).  
  - Security protocols (DoT, DoH).  

---

## 🔐 DNS: UDP vs TCP  

- **Originally UDP**: Faster, low overhead, suitable for small queries.  
- **Now often TCP**:  
  - Larger responses (DNSSEC, CDNs).  
  - More reliable (prevents spoofing).  
  - Required for zone transfers.  
  - Supports DoT/DoH security.  
  - Reduces DDoS amplification risks.  

---

## 🛠️ Troubleshooting  

**Issue: `Bind for 0.0.0.0:8000`**  
👉 Run:  
```bash
netstat -ntulp | grep 8000
```
Check if port **8000** is already in use.  

---

## ☸️ Kubernetes Essentials  

- **Written in**: Go (Golang).  
- **Best databases for Kubernetes apps**:  
  - Structured: **PostgreSQL, MySQL**  
  - Unstructured: **MongoDB, Cassandra**  

### 🔧 Useful Commands  

```bash
# Get shell inside a pod
kubectl exec -it <pod-name> -- /bin/bash   # if bash available
kubectl exec -it <pod-name> -- /bin/sh     # if only sh available

# Cluster info
kubectl cluster-info

# List nodes
kubectl get nodes

# List pods in namespace
kubectl get pods -n default

# Describe pod
kubectl describe pod <pod-name>
```  

---

📌 **This README is designed as a quick refresher for DevOps, Linux admins, and Kubernetes practitioners.**  
