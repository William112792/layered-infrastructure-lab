# 🧱 Layered Infrastructure & Automation Lab

This repository demonstrates a **real-world, multi-layered infrastructure design** built to showcase:

- Network segmentation
- Virtualization architecture
- Storage abstraction
- Containerized workloads
- Reverse proxy and routing design
- Public + private access models

This is not theoretical — each layer is implemented and actively used.

---

# 🌐 Live Entry Points

## Public Resume / Portfolio
- https://william112792.github.io/

## Reverse Proxy / Redirect Example
- http://me.wmg-pve.duckdns.org/ → Redirects to GitHub resume

## Application Access Example
- http://books.dmsk.duckdns.org/ → Calibre-Web (when online)

---

# 🌍 Domain & Routing Strategy

## DuckDNS Domains

- `dmsk.duckdns.org` → Application routing
- `wmg-pve.duckdns.org` → Infrastructure + redirect control

### Purpose
- External access routing
- Reverse proxy mapping
- Environment segmentation
- Redirect handling

---

# 🖥️ Physical Infrastructure Layer

## Custom Server Node

### Hardware Design
- NAS Board (multi-drive support)  
  https://www.amazon.com/gp/product/B0FNQM7PWR

- Rackmount Chassis  
  https://www.amazon.com/gp/product/B09HLCNKM3

### Goals
- Scalability
- Drive expansion
- Segmented workloads
- Persistent storage layer

---

# 🧩 Layered Architecture

This environment is intentionally built in **stacked layers**, each with a defined responsibility.

---

## 🔷 Layer 1 — Virtualization (Proxmox)

### Purpose
- Hypervisor / VM orchestration
- Resource control
- Hardware abstraction

### Key Features
- Drive pass-through
- Manual serial assignment
- Snapshot control
- ISO boot for recovery
- SMART monitoring visibility

### Concept Demonstrated
- Enterprise virtualization fundamentals (VMWare ESXi equivalent)

---

## 🔷 Layer 2 — Storage (TrueNAS VM)

### Purpose
- Centralized storage management
- RAID configuration
- Data redundancy

### Requirements
- Serial numbers passed from Proxmox
- Disk-level awareness

### Concept Demonstrated
- Storage abstraction
- RAID design
- Dependency on lower-layer hardware mapping

---

## 🔷 Layer 3 — Container Orchestration (Dockge)

### Purpose
- Lightweight container management
- Docker-style deployments
- Environment variable control

### Features
- Compose-style configuration
- Rapid deployment of services
- Simplified container lifecycle management

### Concept Demonstrated
- Containerization fundamentals
- Environment-based configuration

---

## 🔷 Layer 4 — Application Layer (Containers)

### Purpose
- Deliver functional services
- Share resources efficiently
- Maintain isolation between apps

### Storage Integration
- Uses TrueNAS pools
- Monitors:
  - Disk usage
  - Cleanup per application

### Concept Demonstrated
- Resource sharing with isolation
- Storage-aware application deployment

---

# 🌐 Networking & Access Layer

## Nginx (Reverse Proxy + Redirect Engine)

### Functions
- Reverse proxy routing
- Domain-based application access
- HTTP → HTTPS redirection
- External → internal mapping

---

## Example Configurations

### Redirect

http://me.wmg-pve.duckdns.org/

→ https://william112792.github.io/


### Reverse Proxy

http://books.dmsk.duckdns.org/

→ Calibre-Web container


---

# 📦 Application Stack

## Deployed Containers

- **WikiJS** → Internal knowledgebase
- **Calibre-Web** → Book management
- **Plex** → Media streaming
- **Tailscale** → Private network access
- **DuckDNS Automation** → Dynamic DNS updates
- **Custom VPN Containers** → Segmented routing

---

# 🔐 Access Model

## Public Access
- Limited endpoints exposed via Nginx
- Example:
  - Calibre-Web (selectively online)

---

## Private Access (Tailscale)

### Purpose
- Secure internal access
- Avoid exposing sensitive services publicly

### Benefits
- Encrypted network tunnel
- Device-based access control
- Zero-trust style networking

---

# 🧠 Design Philosophy

This environment is built around:

## 1. Layered Separation
Each layer has a **single responsibility**

## 2. Controlled Exposure
- Public access is intentional
- Sensitive services remain private

## 3. Scalability
- Add containers without redesigning system
- Expand storage independently

## 4. Observability
- Storage visibility via TrueNAS
- VM-level control via Proxmox

## 5. Real-World Parity
Mirrors enterprise patterns:
- Hypervisor → Storage → Containers → Apps → Access Layer

---

# 🔄 End-to-End Flow

id="infra-flow"
User Request → DuckDNS → Nginx → Container → Storage (TrueNAS) → Disk (Proxmox Host)

---

# ⚙️ Key Takeaways
- Virtualization enables full system control
- Storage must be abstracted and validated
- Containers provide scalability and isolation
- Reverse proxy enables controlled exposure
- Private networking (Tailscale) reduces risk surface

---

# 🚀 Future Enhancements
- Automated container deployment pipelines
- Monitoring stack (Prometheus / Grafana)
- Centralized logging
- AI-driven infrastructure insights
- Backup and replication strategies

---

# 👤 Author

Billy Gordon
Endpoint Automation Engineer

Focused on:

- Automation-first infrastructure
- Scalable system design
- Secure and segmented environments
