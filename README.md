# Local Threat Intelligence Lab: Uncensored LLM Analysis 🛡️🤖

![Docker](https://img.shields.io/badge/Container-Docker-blue?logo=docker)
![Ollama](https://img.shields.io/badge/AI%20Backend-Ollama-white)
![Open WebUI](https://img.shields.io/badge/Frontend-Open%20WebUI-green)
![Security](https://img.shields.io/badge/Focus-Threat%20Intelligence-red)

## 📋 Executive Summary
This project demonstrates the deployment of an **isolated, air-gapped Artificial Intelligence environment** aimed at researching **Shadow AI risks** and **Adversarial Machine Learning**.

By leveraging Docker containers and "uncensored" Large Language Models (LLMs), this lab simulates how threat actors utilize Generative AI for malware development and social engineering, allowing for the development of better defensive strategies (Blue Teaming) and forensic analysis.

**Analyst:** Roy Castro
**Objective:** Certified Ethical Hacker (CEH) practical application & Infrastructure Hardening.

---

## 🏗️ Phase 1: Infrastructure as Code (IaC) & Deployment

To ensure reproducibility and isolation, the environment was built using **Docker Compose** on a Windows Subsystem for Linux (WSL2) layer. This architecture prevents direct host contamination while allowing full hardware acceleration.

### 1. Environment Preparation
Checking prerequisites and initializing the WSL2 subsystem to host the Linux-based container engine.
![WSL Setup](AI-Images/01_wsl_prerequisites_setup.jpg)
> *Environment preparation: Initializing Windows Subsystem for Linux (WSL2) to support the containerized architecture.*

### 2. Architecture Definition
The stack consists of two microservices: **Ollama** (Model Inference Engine) and **Open WebUI** (Interface), communicating over a private bridge network `red-aislada`.
![IaC Manifest](AI-Images/02_iac_architecture_manifest.jpg)
> *Infrastructure-as-Code (IaC): Docker Compose manifest defining the isolated bridge network and service orchestration for Ollama and Open WebUI.*

### 3. Service Deployment & Health Checks
Successful provisioning of the container stack. Verification via `docker ps` ensures services are healthy and utilizing the defined ports (3000 for UI, 11434 for API).
![Deployment Status](AI-Images/03_service_deployment_status.jpg)
> *Service Orchestration: Verified container status showing active 'cerebro-ai' and 'interfaz-usuario' microservices running on the local Docker engine.*

---

## 🧠 Phase 2: Model Provisioning (LLMOps)

Standard commercial models (e.g., GPT-4, Gemini) have safety guardrails. To simulate real-world threat vectors, I provisioned **`dolphin-mistral:latest`**, a 7-billion parameter uncensored model known for its lack of refusal mechanisms.

![Model Provisioning](AI-Images/04_model_provisioning_status.jpg)
> *Model Ingestion: Successful provisioning of the 'dolphin-mistral' uncensored model (7B parameters) within the local Open WebUI environment.*

---

## ⚔️ Phase 3: Red Team Operations (Simulated Attacks)

This phase demonstrates the **dual-use nature of AI**. The goal is to generate artifacts that a Threat Actor would create, to study their structure and signatures.

### 1. Malware Development Simulation (Ransomware)
**Input (The Prompt):** A specifically crafted prompt requesting a Python script for file encryption, bypassing standard ethical filters.
![Malware Prompt](AI-Images/05a_malware_poc_prompt.jpg)
> *Attack Vector Simulation (Input): Crafting a specific prompt to test the model's refusal mechanisms against malware generation requests.*

**Output (The Code):** The model generates a functional Python class `RansomwareAttack` with encryption logic. This serves as a Proof of Concept (PoC) for how easily malicious code can be synthesized.
![Malware Execution](AI-Images/05b_malware_poc_execution.jpg)
> *Attack Vector Simulation (Output): The uncensored model successfully bypasses safety filters, generating a functional Python ransomware script with encryption logic explanation.*

### 2. Social Engineering Campaigns
Generating a targeted Spear-Phishing email. The AI effectively utilizes psychological triggers (Urgency + Authority) to craft a convincing IT Support impersonation email.
![Phishing](AI-Images/06_social_engineering_phishing.jpg)
> *Social Engineering Vector: Drafting a targeted spear-phishing campaign exploiting urgency and authority bias for security awareness training.*

---

## 🔍 Phase 4: Blue Team & Forensics

Effective security requires visibility. Even in "Shadow AI" deployments, the container logs provide a forensic trail of activity.

![Forensic Logs](AI-Images/07_forensic_audit_logs.jpg)
> *Forensic Auditing & Logging: Analyzing container logs to trace API endpoint usage (`/api/chat`) and response latency (4m 42s generation time) during the simulation.*

---

## ⚠️ Disclaimer
**EDUCATIONAL PURPOSE ONLY.**
This repository and its contents are strictly for educational and research purposes related to Cybersecurity and Ethical Hacking. The malware examples and attack vectors demonstrated here are conducted in a controlled, isolated environment. The author (Roy Castro) does not condone the use of this information for illegal activities.
