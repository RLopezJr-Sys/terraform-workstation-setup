# terraform-workstation-setup
Foundational Terraform workstation setup, package management, and path configuration on Windows PowerShell

# Terraform Workstation Setup (`terraform-workstation-setup`)

## 📌 Project Overview
This repository documents the foundational bootstrap process for establishing a local Infrastructure-as-Code (IaC) workstation on **Windows 10/11** using **PowerShell**, **`winget`**, and **HashiCorp Terraform**. 

To build genuine technical mastery, all commands were executed manually via the command line, and real-world operational friction points were logged and resolved rather than bypassed.

Step-by-Step Implementation & Execution LogPhase 1: Environment Baseline & Tool DeploymentPowerShell Version Audit: Verified the host system's PowerShell environment baseline to ensure compatibility and system version tracking. 

Command: $PSVersionTable.PSVersion   Automated Tool 

Deployment: Installed HashiCorp Terraform via the Windows Package Manager (winget) using explicit identifier parameters.   Command: winget install -e --id Hashicorp.Terraform Friction Point & Resolution (Path Environment Variables)

Challenge: The package manager successfully downloaded and extracted the Terraform binaries, but flagged that the system PATH environment variable had been modified. 

Resolution: Recognized that the active shell session needed to be restarted for the terminal to recognize the new terraform command alias.
<img width="1392" height="640" alt="installing terraform through powershell" src="https://github.com/user-attachments/assets/f658027a-8270-46d2-901a-4a990ce583d3" />


Phase 2: Lifecycle Management & Version Drift AnalysisBinary Verification Check: Launched a fresh terminal session post-restart to validate the installation and verify the active binary version. 

Command: terraform version Upstream Advisory Check & Package Manager Query: The local binary (v1.16.4) emitted a notification indicating an upstream release (v1.16.5) was available. A targeted package manager upgrade command was executed to test lifecycle management. 

Command: winget upgrade --id Hashicorp.Terraform   Friction Point & Resolution (Package Manifest Lag):Challenge: winget returned a "No available upgrade found" message, exposing a common real-world administrative challenge: package repository manifest lag. 

Analysis: While upstream maintainers publish point releases rapidly, community or official package registries often experience synchronization delays before their manifests reflect the newest version.Decision: Proceeded with the stable local baseline (v1.16.4), as core syntax, provider interactions, and local testing capabilities remain fully functional.
<img width="1468" height="440" alt="trying to upgrade" src="https://github.com/user-attachments/assets/fafbba79-c430-46de-a5f5-d3c7ae920f9c" />
