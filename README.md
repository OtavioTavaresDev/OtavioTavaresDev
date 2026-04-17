# 🔥 AttackSim

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)](https://python.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-009688?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![Next.js](https://img.shields.io/badge/Next.js-14-black?logo=next.js&logoColor=white)](https://nextjs.org)
[![Docker](https://img.shields.io/badge/Docker-24.0+-2496ED?logo=docker&logoColor=white)](https://docker.com)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

## Continuous Attack Simulation Platform for Modern Security Teams

**Simulate real-world attacks. Detect vulnerabilities early. Ship secure software.**

---

> ⚠️ **Important Notice**  
> AttackSim is designed strictly for authorized security testing.  
> - Only test systems you own or have explicit permission to test  
> - All attack executions are sandboxed and controlled  
> - Misuse of this tool may violate laws and regulations  
> *This project was built with a responsible security mindset.*

---

## 🎯 Problem Statement

Modern development pipelines suffer from:

- ❌ Infrequent and expensive penetration testing  
- ❌ Lack of continuous security validation  
- ❌ Limited offensive security expertise among developers  
- ❌ Vulnerabilities reaching production environments  

## 💡 Solution

AttackSim introduces **continuous, automated attack simulation** integrated into the development lifecycle.

Core principles:

- 🐳 **Isolation-first execution** – Docker sandbox per attack  
- 🧩 **Modular attack system** – plug-and-play modules  
- 📊 **Developer-friendly reporting** – actionable insights  
- 🔄 **CI/CD integration** – continuous validation  

---

## 🏗️ Architecture
Frontend (Next.js)
↓
API Gateway (FastAPI)
↓
Attack Orchestrator
↓
Attack Modules (Pluggable)
↓
Sandbox Executor (Docker)
↓
Target Application
↓
Report Engine + Risk Scoring
↓
PostgreSQL (History & Analytics)

text

---

## ⚡ Core Features

### 🔥 Attack Simulation Engine
- Real attack execution (not signature-based scanning)
- Modular architecture for extensibility
- Dynamic module loading

### 🧪 Isolation & Safety
- Dedicated Docker container per attack
- Resource and execution constraints
- No direct host interaction

### 📊 Risk & Reporting
- OWASP-aligned severity classification
- Risk scoring (0–100)
- Actionable remediation guidance

### 🔄 Continuous Security
- CI/CD integration (GitHub Actions, GitLab CI)
- Automated security validation before deployment
- Historical tracking of vulnerabilities

### 🖥️ Modern Interface
- Real-time scan visualization
- Clean UI with Next.js + Tailwind
- Developer-friendly workflows

---

## 🧩 Supported Attack Modules

| Module | Description | Severity |
|--------|-------------|----------|
| SQL Injection | Error-based, blind, time-based detection | 🔴 CRITICAL |
| XSS | Reflected and DOM-based | 🟠 HIGH |
| Directory Traversal | Unauthorized file access | 🔴 CRITICAL |
| Command Injection | OS command execution | 🔴 CRITICAL |
| Brute Force | Authentication attack simulation | 🟠 HIGH |
| Open Redirect | Unsafe redirect validation | 🟡 MEDIUM |
| Security Headers | Missing security protections | 🟢 LOW |

---

## 📋 Requirements

- Docker Engine 20.10+
- Docker Compose 2.20+
- 4GB RAM minimum (8GB recommended)
- Linux, macOS, or WSL2 (Windows)

---

## 🚀 Quick Start (Docker)

```bash
git clone https://github.com/OtavioTavaresDev/attacksim.git
cd attacksim
docker-compose up -d --build
After startup:

Frontend → http://localhost:3000

API Docs → http://localhost:8000/docs

🔐 Environment Variables
Create a .env file in the backend/ directory:

env
DATABASE_URL=postgresql://user:pass@db:5432/attacksim
SECRET_KEY=your-secret-key-here
JWT_ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
See .env.example for all options (copy it from the repo).

🧪 Testing Environment
AttackSim includes intentionally vulnerable endpoints for validation.

⚠️ These endpoints are for testing purposes only.

Example:

text
http://localhost:8000/api/v1/attacks/test-sqli?id=1
🧩 Creating Custom Modules
AttackSim is designed to be extensible. Create a new module:

python
from .base import AttackModule

class CustomAttack(AttackModule):
    name = "Custom Attack"
    description = "Description of the attack"
    severity = "high"

    def run(self, target: str) -> dict:
        return {
            "success": True,
            "severity": "high",
            "details": "Vulnerability detected",
            "remediation": "Steps to fix"
        }
Modules are automatically discovered by the orchestrator.

🔄 CI/CD Integration Example
yaml
- name: Run Attack Simulation
  run: |
    curl -X POST "https://your-instance/api/v1/scan" \
      -H "Authorization: Bearer ${{ secrets.ATTACKSIM_TOKEN }}" \
      -H "Content-Type: application/json" \
      -d '{
        "target_url": "https://staging.app.com",
        "module_name": "SQL Injection"
      }'
📂 Project Structure
text
attacksim/
├── backend/           # FastAPI application
├── frontend/          # Next.js dashboard
├── docker/            # Dockerfiles and configs
├── docker-compose.yml
└── README.md
🧠 Design Philosophy
AttackSim was built around three principles:

Realism → simulate actual attacker behavior

Isolation → guarantee safe execution

Continuity → integrate security into development flow

🗺️ Roadmap
Machine learning anomaly detection

Advanced attack chaining

Multi-target scanning

Team collaboration features

📄 License
MIT License – see LICENSE file for details.

⭐ Final Note
AttackSim is not just a tool.
It is a step toward a future where:

Security is not a phase — it is a continuous process.

<div align="center"> <b>Simulate. Detect. Evolve.</b> </div> ```
