# OrderFlow AI – Agentic Sales Order Creation with UiPath Maestro

## Project Description

OrderFlow AI is an enterprise-grade agentic automation solution that automates the Sales Order creation process from customer emails to SAP.

The solution monitors a Microsoft 365 mailbox for incoming customer purchase orders. A UiPath Robot extracts the email body and attachment content and sends the combined text to an AI-powered Order Extraction Agent.

The extracted order data is then validated by an Order Completeness Agent to ensure all mandatory business fields are available.

If all mandatory fields are present, UiPath Maestro orchestrates the SAP automation workflow to create the Sales Order automatically.

If information is missing, Maestro routes the process to a human reviewer through Action Center. After validation, the workflow resumes automatically and completes the SAP transaction.

The solution demonstrates how AI Agents, RPA, Human-in-the-loop, and BPMN orchestration can work together to automate enterprise business processes.

---

# Business Problem

Many organizations still receive customer purchase orders through emails and PDF attachments.

Employees manually:

- Read emails
- Extract order information
- Validate mandatory fields
- Enter data into SAP

This process is repetitive, time-consuming, and prone to errors.

OrderFlow AI reduces manual effort while keeping humans involved only when business decisions are required.

---

# UiPath Components Used

The solution is built entirely on UiPath Automation Cloud using the following components:

- UiPath Automation Cloud
- UiPath Studio
- UiPath Maestro BPMN
- UiPath Agent Builder
- UiPath Action Center
- UiPath Integration Service
- Microsoft 365 Activities
- PDF Activities
- SAP GUI Activities
- JSON Activities

---

# Agent Type

This project uses **Low-code Agents** created using **UiPath Agent Builder**.

Agents Used:

1. Order Extraction Agent
2. Order Completeness Agent

No coded agents were used.

---

# Solution Architecture

Customer Email
        ↓
UiPath Robot
        ↓
Order Extraction Agent
        ↓
Order Completeness Agent
        ↓
Decision
   ↓             ↓
Complete      Missing Data
   ↓             ↓
SAP Robot   Human Validation
      ↓           ↓
      └──────┬────┘
             ↓
      Sales Order Created

---

# Workflow

1. Monitor Outlook mailbox.
2. Read email body.
3. Extract text from PDF attachment.
4. Combine email and attachment text.
5. Invoke Order Extraction Agent.
6. Receive structured JSON.
7. Invoke Order Completeness Agent.
8. If complete:
   - Continue to SAP.
9. If incomplete:
   - Create Action Center task.
   - Wait for reviewer.
   - Resume workflow.
10. Create Sales Order in SAP.
11. End Process.

---

# Setup Instructions

## Prerequisites

- UiPath Automation Cloud Account
- UiPath Studio
- UiPath Maestro enabled
- Agent Builder enabled
- Action Center enabled
- Microsoft 365 Connection
- SAP GUI Installed
- SAP GUI Scripting Enabled
- Valid SAP Credentials

## Installation

1. Clone this repository.

2. Open the project in UiPath Studio.

3. Restore NuGet packages.

4. Configure Microsoft 365 connection.

5. Configure SAP credentials.

6. Publish the automation to Automation Cloud.

7. Import the Maestro BPMN process.

8. Create the two agents in Agent Builder.

9. Configure Action Center.

10. Execute the process.

---

# Repository Structure

Main.xaml

Email Automation

Agent Prompts

SAP Automation

Maestro BPMN

Documentation

README.md

---

# Technologies Used

- UiPath Studio
- UiPath Maestro
- UiPath Agent Builder
- Action Center
- Microsoft 365
- SAP GUI
- PDF Activities
- JSON
- VB.NET

---

# Future Improvements

- Customer Master Validation
- Material Master Validation
- Inventory Check
- Pricing Validation
- ERP API Integration
- Multi-language Support
