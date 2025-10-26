# Hi there, I'm Sunny 👋 

## About Me

I love to read and experiment with building **scalable infrastructure**, **automating complex workflows**, and creating **reliable deployment pipelines** that bridge the gap between development and production. Applying this to the field of Machine Learning / AI is exciting for me since it bridges the gap between theoretical analysis and practical value.

Currently, I'm working on **container orchestration**, **observability platforms**, and **infrastructure as code** to build more robust and maintainable systems.

My background:

- MEng Aerospace Engineering (Hons.) from Brunel University London
- 3.5+ years experience at HSBC as a Corporate/Investment Banker
- 7+ years working on and growing my Homelab

**Let's Connect!** Please feel free to contact me at: sanabil.t.qureshi@gmail.com

## Featured Projects

### 🔧 **Infrastructure & DevOps**
- **[Predictive Fan Control System](https://github.com/SanabilQureshi/Predictive-Fan-Control-System)**  
   Docker-based thermal management with PID control, featuring Prometheus monitoring and auto-provisioned Grafana dashboards.

- **[University Timetable Scraper](https://github.com/SanabilQureshi/Brunel-Timetable-Scraper)**  
   Automated web scraping tool using Selenium and BeautifulSoup to extract and convert academic schedules to ICS format.

---

### 🤖 **Machine Learning & Engineering**
- **[Neural Network Framework from Scratch](https://github.com/SanabilQureshi/neural_networks.cpp)**  
   Pure C++ implementation of deep learning fundamentals including backpropagation, optimisers (Adam, SGD), achieving 97%+ MNIST accuracy.

- **[Autonomous Computer Vision System](https://github.com/SanabilQureshi/MEng-Autonomous-Computer-Vision-Robot)**  
   High-speed robotic quality control using TensorFlow and OpenCV for real-time defect detection in manufacturing (MEng thesis).

---

### 📊 **Data Engineering & Analytics**
- **[Banking Portfolio Analysis Tool](link)**  
   Internal analytics tool at HSBC delivering £50M+ Risk Weighted Assets (RWAs) optimisation opportunities across corporate portfolio.

---

## 🛠️ Toolbox

- **Languages:** Python, C++, SQL, Bash/Shell scripting, Powershell (beginner)
- **ML/AI:** TensorFlow, OpenCV, Neural network implementations, Model deployment
- **LLMs**: vLLM, llama.cpp,  Pydantic, Gradio, Custom RAG solutions
- **Cloud & DevOps:** Container orchestration, Service mesh concepts, Secret management, Network isolation
- **Infrastructure:** Docker, Docker Compose, Kubernetes concepts, Linux (server) administration
- **Monitoring:** Prometheus, Grafana
- **Automation:** CI/CD pipelines, Web scraping (Selenium/BeautifulSoup), IaC practices



---



# 🏗️ My Homelab Infrastructure

The work/fun never stops with my homelab, it's something that I started building in 2018 and have been adding to it ever since! Parts of it are in production (usable for family/friends without complaints) and the rest has evolved many many times as my understanding and appetite grew for mimicking enterprise technology that I see around me every day. 

What started out as a single laptop with a broken screen but fully functional as a server, eventually grew into a multi-node infrastructure that benefits others and myself on a daily basis.


## A brief summary of my Homelab journey

<details>
<summary><b>Early Infrastructure (Years 1-3)</b></summary>

- Started with a Dell R720 running bare metal Linux for computation and experimentation, learning about hardware, Linux administration, and resource management. Used lots during my MEng course, especially for my dissertations involving molecular dynamics shock-wave analysis and CNN-based machine learning (Bachelors + Masters)
- Explored Windows Server with Hyper-V to understand Microsoft's virtualisation stack while running multiple VMs for family members. Built several custom PCs during this period to learn about hardware compatibility, power requirements, PCIe topology, and component selection.

</details>

<details>
<summary><b>Virtualisation & Networking (Years 3-5)</b></summary>

- Began networking journey with a Cisco RV325 router in bridge mode before eventually obtaining PPPoE credentials and deploying a UDM Pro to replace ISP hardware entirely. Self-deployed CAT6 cabling throughout the house and implemented VLAN segmentation with firewall rules for network isolation.
- Upgraded to Dell R730 with ESXi as the primary hypervisor, experimenting extensively with GPU passthrough and SR-IOV to provide dedicated discrete GPUs to individual VMs. Deployed VMware Horizon to give family members seamless access to their Windows VMs.
- Tested Proxmox as an alternative hypervisor and built a Ceph cluster for high-performance distributed storage during intensive ML training workloads, ultimately gaining valuable exposure to different architectural approaches.

</details>

<details>
<summary><b>Containerisation & Modern Stack (Years 5-7)</b></summary>

- Shifted from heavy virtualisation to containerised services, adopting Docker and Docker Compose with services deployed on a dedicated NUC managed via Portainer. Deployed various reverse proxies ([NGINX Proxy Manager](https://github.com/NginxProxyManager/nginx-proxy-manager)) and modern authentication patterns ([Authelia](https://github.com/authelia/authelia), [Authentik](https://github.com/goauthentik/authentik), Cloudflare) to allow secure access outside of the network.
- Built the GPU compute workstation (Fractal) and transitioned to QEMU/KVM for Linux-based virtualisation, developing workflow automations for my key daily needs (ZFS storage, power management), IoT (Home Assistant), and AI services (local LLM inference).

</details>

<details>
<summary><b>Today</b></summary>

*Current Stack:* QEMU/KVM, ESXi, Docker/Docker Compose, Portainer, UniFi networking, ZFS, Prometheus/Grafana, WireGuard, vLLM/llama.cpp, Home Assistant, Ubuntu Server/Debian/Fedora

*Previously Used Extensively:* Proxmox, Ceph, Hyper-V, Windows Server, VMware Horizon, Cisco networking, SR-IOV/GPU passthrough

*Core Skills:* Linux system administration, container orchestration, network architecture and security, storage management, infrastructure automation (Bash/Python), monitoring and observability, PKI/certificate management, hardware selection and configuration, GPU infrastructure management

</details>

[Authelia](https://github.com/authelia/authelia)
[Authentik](https://github.com/goauthentik/authentik)
[Home Assistant](https://github.com/home-assistant)
[Prometheus](https://github.com/prometheus/prometheus)
[Grafana](https://github.com/grafana/grafana)
[Memos](https://github.com/usememos/memos)

---

## Current setup

**Heavy Compute & Virtualization**

- Fractal
  - EPYC 7542 server (196GB ECC RAM, 8x GPUs) running Fedora with QEMU/KVM for GPU-accelerated workloads including LLM inference servers (vLLM, llama.cpp), model fine-tuning, and classical ML pipelines for real-time CCTV video processing. 
  - To get all 8 GPUs running at Gen4x8 speeds, I configured PCIe bifurcation with retimers to maintain signal integrity across all GPU slots and have an IPMI/IP-KVM setup for full remote out-of-band management of the whole system without needing to be physically present
- Mandelbrot
  - Dell R730 (dual Xeon E5-2680 v4, 384GB ECC RAM) running ESXi for mixed Windows/Linux VM workloads and testing environments. Previously used Proxmox and made scripts to allow safe export and import.
  - Also runs dedicated Windows VM's for family members and when having a LAN party. High speed NVME/SAS storage acts as a cache for local-only updates and file storage.

**Lightweight containerisation**

- Lenovo M920Q NUC running Ubuntu Server LTS hosts 30+ containerised services managed through Portainer using Docker Compose stacks, including N8N workflow automation integrated with local LLM APIs, Jupyter notebook servers, PDF tools ([Stirling-PDF](https://github.com/Stirling-Tools/Stirling-PDF)), and note-taking applications ([Memos](https://github.com/usememos/memos), [ByteStash](https://github.com/jordan-dalby/ByteStash), [Trilium](https://github.com/TriliumNext/Trilium)).
- Services run on custom bridge networks for isolation with persistent volume mounts backed up daily/weekly to separate NAS servers and monthly to cold storage.

**Networking**

- UniFi stack (UDM Pro, 24-port PoE switch, multiple APs) with VLAN segmentation for IoT, services, management, and guest networks, each with dedicated firewall rules. Inter-device connectivity uses SFP+ 10GbE links.
- Self-terminated and deployed CAT6 cabling throughout the house connecting to a central patch panel in the rack, with WireGuard VPN credentials setup for remote access by family/friends.
- All internal services use custom DNS entries with SSL certificates from a self-hosted Certificate Authority running air-gapped on a Raspberry Pi 5.

**Storage**

- UNAS Pro (14TB Intel Enterprise SSDs) for daily-use data accessible via SMB/NFS, with a Dell KTN-STL3 JBOD (60TB across two RAID-Z2 vdevs) using ZFS for archival storage.
- Custom Bash scripts interface with [Home Assistant](https://github.com/home-assistant) API to safely power on/off the JBOD, monitor power draw during HDD spin-up, verify system readiness, and mount/unmount ZFS pools with pre-flight safety checks. Automated rsync to remote cloud storage follows 3-2-1 backup principles.

**Monitoring & Automation**

- Home Assistant (RPi 5) manages IoT devices, power monitoring for rack equipment, and exposes API endpoints for my own automation workflows.
- [Prometheus](https://github.com/prometheus/prometheus) and [Grafana](https://github.com/grafana/grafana) provide infrastructure monitoring with custom hooks for a PID-controlled fan management system that dynamically adjusts Dell server fan speeds based on workload and temperature with real-time telemetry and alerting.

**AI/ML Services**

- LLM inference servers (vLLM, llama.cpp) running on the GPU cluster provide REST API access for integration with N8N workflows and various applications ([OpenWebUI](https://github.com/open-webui/open-webui), [ComfyUI](https://github.com/comfyanonymous/ComfyUI), custom [Gradio](https://github.com/gradio-app/gradio)).
- Classical ML models process RTSP streams from home CCTV cameras, integrated into UniFi Protect via an RTSP-to-ONVIF proxy. Planning to use a Coral TPU for edge-device realtime detection.
