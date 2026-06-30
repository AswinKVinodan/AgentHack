# OrderFlow AI - Agentic Sales Order Creation with UiPath Maestro

## Overview

OrderFlow AI is an agentic sales order automation solution built on the UiPath Platform using **UiPath Maestro BPMN**, **Agent Builder**, **Action Center**, and **SAP GUI Automation**.

The solution automates the complete sales order creation process by extracting order information from customer emails, validating the extracted data using AI agents, routing incomplete orders for human review, and automatically creating sales orders in SAP.

This project demonstrates how AI agents, robotic process automation, and human decision-makers can work together within a single orchestrated workflow.

---

## Business Problem

Organizations receive customer purchase orders through emails in various formats such as:

* Email body
* PDF attachments
* Scanned purchase orders

Sales teams manually:

* Read customer emails
* Extract order information
* Verify mandatory fields
* Enter data into SAP
* Send order confirmations

This manual process is repetitive, time-consuming, and prone to errors.

---

## Solution Architecture

```
Customer Email
        │
        ▼
UiPath Robot
(Read Email & Attachments)
        │
        ▼
Order Extraction Agent
(Extract Structured Data)
        │
        ▼
Order Completeness Agent
(Check Mandatory Fields)
        │
        ▼
Decision
 ┌──────────────┴──────────────┐
 │                             │
 ▼                             ▼
Complete                 Missing Information
 │                             │
 ▼                             ▼
SAP GUI Robot         Human Validation
 │                             │
 └──────────────┬──────────────┘
                ▼
         SAP Sales Order
                ▼
      Order Confirmation
```

---

## Components Used

* UiPath Automation Cloud
* UiPath Maestro BPMN
* UiPath Studio
* UiPath Agent Builder
* UiPath Action Center
* Microsoft 365 Activities
* PDF Activities
* SAP GUI Automation

---

## AI Agents

### Order Extraction Agent

Responsible for extracting structured sales order information from unstructured emails and attachments.

Extracted fields include:

* Customer Name
* Purchase Order Number
* Material Number
* Quantity
* Delivery Date
* Delivery Address

Output is returned as structured JSON.

---

### Order Completeness Agent

Validates whether all mandatory fields required for SAP Sales Order creation are available.

If mandatory information is missing, the process is routed to human validation.

Example response:

```json
{
  "Status":"Incomplete",
  "MissingFields":[
      "Material Number",
      "Delivery Date"
  ]
}
```

---

## Human-in-the-Loop

Incomplete orders are automatically routed to UiPath Action Center.

The reviewer:

* Reviews extracted data
* Completes missing fields
* Corrects incorrect values
* Submits the task

UiPath Maestro automatically resumes the workflow after approval.

---

## SAP GUI Automation

After successful validation, UiPath Robot performs SAP GUI automation.

The robot:

1. Launches SAP Logon
2. Logs into SAP
3. Opens the Sales Order Creation transaction (VA01)
4. Populates customer and order information
5. Creates the Sales Order
6. Captures the generated Sales Order Number
7. Logs the transaction
8. Sends an order confirmation (optional)

---

## Technologies Used

* UiPath Studio
* UiPath Maestro BPMN
* UiPath Agent Builder
* UiPath Action Center
* Microsoft 365 Outlook
* PDF Activities
* SAP GUI Scripting
* JSON
* VB.NET

---

## Prerequisites

Before running the project:

* UiPath Automation Cloud account
* UiPath Studio
* UiPath Maestro enabled
* Agent Builder enabled
* SAP GUI installed
* SAP GUI Scripting enabled on both client and server
* Microsoft 365 mailbox
* Required UiPath packages installed

---

## Workflow

1. Monitor Outlook mailbox.
2. Read email body and attachments.
3. Extract attachment text.
4. Combine email body and attachment content.
5. Send combined text to the Order Extraction Agent.
6. Receive structured JSON.
7. Send JSON to the Order Completeness Agent.
8. If complete:

   * Create Sales Order in SAP.
9. If incomplete:

   * Create Action Center task.
   * Wait for reviewer.
   * Resume workflow.
   * Create Sales Order in SAP.
10. Complete the process.

---

## Future Enhancements

* Customer master validation
* Material master validation
* Inventory availability checks
* Pricing validation
* Multi-language document support
* ERP API integration
* Confidence-based routing
* Business analytics dashboard

---

## Repository Structure

```
OrderFlowAI
│
├── Main.xaml
├── EmailProcessing.xaml
├── OrderExtraction.xaml
├── Validation.xaml
├── SAPSalesOrder.xaml
├── ActionCenter.xaml
├── Data
│     ├── SampleEmails
│     ├── SamplePDFs
│     └── TestData
├── Agents
│     ├── OrderExtractionAgent
│     └── OrderCompletenessAgent
├── Documentation
│     ├── Architecture.png
│     └── BPMN.png
└── README.md
```

---

## Business Benefits

* Reduces manual order processing effort
* Improves data accuracy
* Accelerates sales order creation
* Enables human oversight for exceptions
* Demonstrates enterprise-grade agentic automation
* Simplifies orchestration using UiPath Maestro

---

## License

This project is released under the MIT License.

---

## Developed for

**UiPath AgentHack 2026**

Track: **UiPath Maestro BPMN**

Project: **OrderFlow AI – Agentic Sales Order Creation with UiPath Maestro**
