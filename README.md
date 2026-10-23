VS Code + ARC-1 MCP + SAP BTP ABAP Environment
This repository documents a hands-on implementation for connecting GitHub Copilot in local Visual Studio Code to an SAP BTP ABAP Environment using the ARC-1 Model Context Protocol (MCP) server.

The objective is to enable AI-assisted, read-only exploration and analysis of ABAP repository objects through SAP ADT APIs.

Architecture
Developer
   |
   v
GitHub Copilot in Local VS Code
   |
   | MCP (stdio)
   v
ARC-1 MCP Server
   |
   | BTP Service Key
   | OAuth 2.0 / PKCE
   v
SAP BTP ABAP Environment
   |
   | ADT APIs (HTTPS)
   v
ABAP Repository
   |
   +-- SAPSearch
   +-- SAPRead
   +-- Dependency Analysis
   +-- CDS / RAP Analysis
Components Used
Visual Studio Code
GitHub Copilot
Model Context Protocol (MCP)
ARC-1
Node.js / npx
SAP Business Application Studio
SAP BTP
SAP BTP ABAP Environment
SAP ADT APIs
Eclipse ADT
GitHub
Hands-On Flow
*1. Connect VS Code to SAP Business Application Studio
Local Visual Studio Code was connected to an SAP Business Application Studio landscape.

The BAS dev space was used for:

Git access
ARC-1 repository exploration
Node.js / npx validation
MCP configuration testing
*2. Configure ARC-1 MCP Server
ARC-1 was configured as an MCP server for GitHub Copilot.

The final working MCP server runs locally on Windows using:

npx -y arc-1@latest
*3. Connect ARC-1 to SAP BTP ABAP Environment
Authentication uses an SAP BTP ABAP Environment service key.

The service key is stored outside the Git repository.

ARC-1 performs interactive OAuth authentication and accesses the ABAP Environment using SAP ADT APIs.

*4. Access the ABAP Repository
GitHub Copilot can invoke ARC-1 SAP tools such as:

SAPSearch
SAPRead
Example validation was performed against custom package:

ZBPA_WORKFLOW
Example prompt:

Using the SAPSearch tool from arc-1, search the connected SAP
system for package ZBPA_WORKFLOW and list the ABAP objects in
that package. Do not search the local workspace.
Security
This repository does NOT contain:

SAP passwords
BTP service-key credentials
OAuth access tokens
OAuth refresh tokens
Client secrets
.env files
Real service keys must be stored outside the repository.

Example Windows location:

C:\Users\xxxxxxxx\.config\arc-1\btp-service-key.json
Example BAS location:

/home/user/.config/arc-1/btp-service-key.json
The initial implementation keeps ARC-1 read-only.

Repository Structure
VS-MCP-ABAP/
├── README.md
├── .gitignore
├── docs/
│   └── VS_MCP_ABAP_Setup_Guide.docx
├── images/
│   └── ARC-1_Architecture_Diagram.png
└── config/
    ├── mcp-windows-example.json
    └── mcp-bas-example.json
Documentation
The docs directory contains the detailed hands-on guide including:

BAS connection
Git/GitHub setup
ARC-1 installation and testing
MCP configuration
BTP service-key setup
OAuth authentication
SAPSearch / SAPRead validation
Troubleshooting
Issues encountered and resolutions
Reference Tutorials
ARC-1 GitHub Repository
SAP Business Application Studio Toolkit
Important
ARC-1 itself is maintained in its own GitHub repository. This repository does not duplicate the ARC-1 source code.

This repository contains only the configuration examples, architecture, documentation, screenshots, and learnings from the hands-on implementation.