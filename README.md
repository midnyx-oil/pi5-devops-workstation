# 🚀 Raspberry Pi 5 DevOps Workstation

> 🧠 **A high-efficiency, portable developer + operations machine** designed to code, build, host, monitor, and automate from anywhere — even off-grid.

---

## 🎯 Purpose
A fully mobile, battery-powered workstation built on the Raspberry Pi 5 that enables:
- 💻 Full-stack development
- 🐳 App hosting with Docker
- ⚙️ GitHub Actions CI/CD pipeline execution
- 🧠 Local and on-demand database management
- 📊 Real-time system monitoring
- 🔋 Power-aware shutdown and off-grid resilience

---

## 🏗️ Phase-by-Phase Architecture

### 🧱 Phase 1 – Developer Workstation Setup
- 🛠️ `git`, `gh` (GitHub CLI)
- 🐍 `python3`, `pip3`
- 🟩 `nodejs`, `npm`
- 🧰 `build-essential`
- 🖥️ `code` (Visual Studio Code)
- ✨ (optional) `micro` terminal editor

### 🐳 Phase 2 – Lightweight Mobile Server
- ✅ `Docker` installed via official script
- 🔧 `Portainer` deployed on port `9000` for GUI-based container management
- 👤 Docker group configured for passwordless access

### 🧠 Phase 3 – Smart Hybrid Database Strategy
- ⚡ `SQLite3` installed for local, embedded database use
- 🐘 `PostgreSQL` dockerized — started only on demand using `~/start_postgres.sh`

```bash
#!/bin/bash
docker start my_postgres 2>/dev/null || docker run --name my_postgres \
  -e POSTGRES_PASSWORD=mysecretpassword \
  -d -p 5432:5432 postgres
```

### ⚙️ Phase 4 – GitHub Actions Self-Hosted Runner
- 🛠️ Actions runner registered via `~/actions-runner`
- 🧷 Installed as a systemd service for automatic startup:

```ini
[Service]
ExecStart=/home/phil/actions-runner/run.sh
WorkingDirectory=/home/phil/actions-runner
User=phil
Restart=always
```

- 🔄 Auto-starts on boot and listens for workflow jobs

### 📊 Phase 5 – Monitoring + UX Polish
- 🧪 `glances` for terminal-based system diagnostics
- 🌐 `netdata` for full visual dashboards (`http://localhost:19999`)
- ⚡ `.bashrc` aliases added for speed:

```bash
alias dps='docker ps'
alias gs='git status'
alias gl='glances'
alias startpg='~/start_postgres.sh'
```

- 🛑 `safe-shutdown.sh` script monitors battery and auto-shuts down when below 15%

---

## 🔐 Security & Optimization
- 🧠 CPU frequency scaling: dynamic from 600MHz–2.4GHz
- 🔥 UFW firewall enabled: ports 22 (SSH) and 9000 (Portainer)
- 📐 Touchscreen accuracy calibrated
- ⚡ Auto-login + fast boot enabled
- 🔋 Power bank + Magedok monitor support tuned

---

## 💡 Ready for Anything
- 🧑‍💻 Code apps in VS Code or terminal
- 📦 Build and test containers
- 🚀 Deploy microservices in Docker
- 🔁 Run GitHub Actions workflows on battery
- 📈 Monitor it all in real-time with Glances or Netdata

---

## 🧭 Future Extensions
- 🛡️ Tailscale for secure remote access
- 🧪 Ansible for cloning config to other Pi 5 units
- 📚 Obsidian for offline knowledge management
- ⚙️ Git auto-deploy pipelines to Docker
- 🌍 Remote data collection for IoT or logging projects

---

## 🏁 System Tagline
> 🎙️ "Built to move. Ready to code. Engineered to deploy."

---

## 🤝 Credits & License
Crafted with care on Raspberry Pi 5 by **Phil Nicholas**  
Guided + documented with help from ChatGPT  
📄 MIT License or your preferred open license

