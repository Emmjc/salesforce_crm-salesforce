# salesforce_crm-salesforce

# Phase 1: Requirement Analysis & Planning

## Overview

This phase focuses on establishing a strong foundation for building a scalable and efficient Salesforce CRM solution tailored for the Tours & Travels industry. It includes understanding how global travel agencies operate, identifying system requirements, planning data and security models, and determining the tools and Salesforce features required to support end-to-end operations.

---

## 1. Understanding Business Requirements

### 🎯 Objective

Understand how Tours and Travel agencies operate globally, including the challenges they face in managing:

- Bookings
- Customer relationships
- Payments
- Tour management
- Employee collaboration

### 🔍 Approach

- Analyzed roles and expectations of stakeholders including travel agents, customer service managers, and finance teams.
- Researched customer expectations from a CRM.
- Identified pain points in existing systems such as manual booking, delayed communication, and poor tracking of feedback.

**Sources Used:**
- ChatGPT
- Google Search
- Salesforce Official Documentation
- Trailhead by Salesforce

### ✅ Key Business Requirements

- Manage global customers and bookings with country-specific packages
- Handle family, group, solo, and corporate trips with membership levels
- Enable real-time communication on booking/payment status
- Automate feedback collection and reminders
- Support employee task assignment
- Track revenue, feedback scores, and retention metrics

---

## 2. Defining Project Scope & Objectives

### 🗂️ Project Scope

- Build a scalable CRM for global travel agencies
- Cover full booking lifecycle from inquiry to payment and feedback
- Design data model, UI/UX, automations, and reports
- Enforce role-based access for customers, agents, guides, and admins

### 🎯 Objectives Summary

- Streamline operations and reduce manual tasks
- Enhance customer satisfaction through automation
- Deliver personalized experiences and efficient feedback handling
- Empower decision-making through analytics

---

## 3. Gathering & Analyzing User Needs

### 👥 Users Involved

- Customers
- Travel Agents
- Tour Guides
- Finance Team
- Admin Team

### 🔑 Key Functional Needs

- Smooth onboarding and package selection
- Booking customization (transport, accommodation, etc.)
- Dynamic pricing based on membership levels
- Automated email confirmations (booking/payment)
- Feedback follow-ups via task automation

### 🛠️ Tools Used

- **Google Forms** – For collecting user inputs
- **Miro** – For user journey mapping
- **User Personas** – For guiding design thinking

---

## 4. Identifying Key Salesforce Features & Tools

### 🧰 Salesforce Features Planned

- **Custom Objects:**  
  `Booking__c`, `TravelPackage__c`, `Customer__c`, `Employee__c`, `BookingPayment__c`, `Feedback__c`, `BookingGuest__c`

- **Standard Objects:**  
  `Task`

- **Automation:**  
  Flows, Process Builders, Workflow Rules, Approval Processes

- **Apex Code:**  
  Triggers, Test Classes, Future Methods, Batch Apex, Queueable Apex, Schedulable Apex

- **UI & Experience:**  
  Lightning App Pages, Dynamic Forms, Lightning Web Components (LWC)

- **Security:**  
  Profiles, Permission Sets, Field-Level Security, Record-Level Security

- **Analytics:**  
  Custom Reports, Dashboards

- **Email Services:**  
  Email Alerts, Templates

---

## 5. Designing Data Model and Security Model

### 📊 Data Model

- `Booking__c` linked to `Customer__c`, `Employee__c` (Guide), and `TravelPackage__c`
- `TravelPackage__c` includes locations, transport, availability, pricing
- `Booking__c` stores travel dates, group size, accommodations, billing info
- `BookingPayment__c` uses a lookup to `Booking__c`
- `Feedback__c` linked to `Booking__c` and `Customer__c`
- `BookingGuest__c` is a master-detail child of `Booking__c`

### 🔐 Security Model

- **Role Hierarchy:** Travel Manager > Travel Agent, Guide
- **Profiles:** Admin, Finance, Agent, Guide, Customer Service Rep
- **Permission Sets:** For report access and object-level permissions
- **Field-Level Security:** Sensitive payment data hidden from non-finance users
- **Record-Level Security:** Sharing rules for guide-customer relationships

---

✅ **Status:** Completed  
📅 **Estimated Duration:** ~42 hours  
📁 **Next Phase:** Salesforce Development (Backend & Configurations)
