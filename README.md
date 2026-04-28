# 🧱 Layered Infrastructure & Automation Lab

![Architecture](https://github.com/William112792/layered-infrastructure-lab/blob/main/diagrams/architecture.png?raw=true)

This repository demonstrates a **multi-layered infrastructure platform** with **environment-based deployment strategy**, designed to reflect real-world Dev/Test/QA/Prod practices.

It showcases:

* Layered infrastructure design (Virtualization → Storage → Containers → Apps)
* Environment segmentation (Test / QA / Prod / Cloud)
* Reverse proxy and routing strategy
* Containerized workload orchestration
* Public vs private access models
* Foundation for CI/CD pipeline integration

This is a **live, functional environment**, not a theoretical build.

---

# 🌐 Environments

## 🧪 Test Environment (Development Validation)

* http://testme.wmg-pve.duckdns.org
* Hosted locally (Dockge → Node.js container)

**Purpose**

* Feature testing
* Rapid iteration
* Breaking changes allowed

---

## 🧬 QA Environment (Pre-Production Validation)

* http://qame.wmg-pve.duckdns.org
* Hosted locally (Dockge → Node.js container)

**Purpose**

* Integration testing
* Regression validation
* Pre-release verification

---

## 🛡️ Production Environment (Self-Hosted)

* http://prodme.wmg-pve.duckdns.org
* Hosted locally (Dockge → Node.js container)

**Purpose**

* Stable production workloads
* Mirrors real-world deployment behavior
* Controlled updates only

---

## ☁️ Canonical Cloud Environment (GitHub Pages)

* https://william112792.github.io/

**Purpose**

* Public-facing portfolio
* Global availability via CDN
* Acts as **authoritative production reference**

---

## 🔁 Primary Access Endpoint

* http://me.wmg-pve.duckdns.org

**Behavior**

* Redirects → GitHub Pages (Cloud Environment)
* Simplified user entry point

---

# 🔄 Environment Strategy

| Environment | Hosting        | Stability | Purpose                       |
| ----------- | -------------- | --------- | ----------------------------- |
| Test        | Local (Dockge) | Low       | Development / experimentation |
| QA          | Local (Dockge) | Medium    | Validation / staging          |
| Prod        | Local (Dockge) | High      | Self-hosted production        |
| Cloud       | GitHub Pages   | Highest   | Public canonical version      |

---

# 🧩 Layered Architecture

## 🔷 Layer 1 — Virtualization (Proxmox)

**Purpose**

* Hypervisor and VM orchestration
* Hardware abstraction

**Capabilities**

* Disk pass-through
* Snapshot management
* Resource isolation

---

## 🔷 Layer 2 — Storage (TrueNAS VM)

**Purpose**

* Centralized storage abstraction
* RAID and redundancy management

**Concepts Demonstrated**

* Storage pooling
* Disk-level visibility
* Dependency on virtualization layer

---

## 🔷 Layer 3 — Container Orchestration (Dockge)

**Purpose**

* Manage containerized workloads
* Environment-specific deployments

**Key Role in Environments**

* Hosts:

  * Test containers
  * QA containers
  * Production containers

---

## 🔷 Layer 4 — Application Layer (Node.js Containers)

Each environment runs as an **independent container instance**:

* Test → Port 3001
* QA → Port 3002
* Prod → Port 3003

**Characteristics**

* Isolated runtime per environment
* Same codebase, different deployment stages
* Controlled promotion between environments

---

# 🌐 Networking & Routing Layer

## Nginx (Reverse Proxy + Traffic Control)

**Core Functions**

* Domain-based routing
* Reverse proxy to containers
* HTTP → HTTPS handling
* 301/302 redirects
* Centralized entry point

---

## Domain Routing Logic

| Domain                     | Destination             |
| -------------------------- | ----------------------- |
| testme.wmg-pve.duckdns.org | Test Container          |
| qame.wmg-pve.duckdns.org   | QA Container            |
| prodme.wmg-pve.duckdns.org | Prod Container          |
| me.wmg-pve.duckdns.org     | Redirect → GitHub Pages |
| william112792.github.io    | Cloud Environment       |

---

# 🔄 Deployment & Pipeline Concept

This environment models a **progressive deployment pipeline**:

```text
Code Change
   ↓
Test Environment (Auto Deploy / Rapid Iteration)
   ↓
QA Environment (Validation / Regression Testing)
   ↓
Production Environment (Controlled Release)
   ↓
Cloud Publish (GitHub Pages - Canonical)
```

### Pipeline Intent

* Enforce environment separation
* Validate before promotion
* Maintain stable production baseline
* Provide globally accessible final version

---

# 🔐 Access Model

## Public Access

* Controlled via Nginx
* Only selected services exposed

## Private Access (Tailscale)

* Secure internal services
* Zero-trust style connectivity
* No public exposure required

---

# 📦 Supporting Infrastructure

## Containers

* WikiJS (knowledgebase)
* Calibre-Web
* Plex
* VPN services
* DuckDNS automation

## Networking

* DuckDNS for dynamic DNS
* Tailscale for private networking

---

# 🧠 Design Principles

### 1. Environment Isolation

Each environment operates independently to prevent cross-impact.

### 2. Layered Responsibility

Each layer serves a single purpose:

* Compute
* Storage
* Orchestration
* Application
* Access

### 3. Controlled Exposure

* Public endpoints are intentional
* Internal systems remain private

### 4. Real-World Alignment

Mirrors enterprise patterns:

* Dev → QA → Prod → Cloud

---

# 🔄 End-to-End Flow

```text
User → DuckDNS → Nginx → Environment Container → Storage (TrueNAS) → Disk (Proxmox Host)
```

---

# 🚀 Future Enhancements

* Full CI/CD automation (GitHub Actions)
* Automated environment promotion
* Infrastructure as Code (Terraform / Ansible)
* Monitoring stack (Prometheus / Grafana)
* Centralized logging
* Backup and replication strategy

---

# 👤 Author

Billy Gordon
Endpoint Automation Engineer

Focus Areas:

* Endpoint Automation (Intune / Autopilot)
* Infrastructure Design
* Dev/Test/Prod Lifecycle Strategy
* Containerized Environments
