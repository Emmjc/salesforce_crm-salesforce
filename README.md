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

# Phase 2: Salesforce Backend Configuration (Milestones 1–4 Completed)

## 📌 Milestone 1: Salesforce Developer Account Setup

**Objective:**  
Set up a Salesforce Developer account as the foundation for CRM development.

**Highlights:**
- Successfully registered on [developer.salesforce.com](https://developer.salesforce.com/signup)
- Activated and accessed the Salesforce Setup area
- Gained initial understanding of Salesforce as a powerful cloud-based CRM platform that supports sales, service, analytics, and more

---

## 🧱 Milestone 2: Custom Object Creation

**Objective:**  
Create the key custom objects required for managing the travel and booking processes.

**Objects Created:**
- `Customer_Info__c`
- `Booking__c`
- `BookingGuest__c`
- `TravelPackage__c`
- `BookingPayment__c`
- `Employee__c`
- `Feedback__c`

Each object represents a core entity in the Tours & Travels business model.

---

## 📂 Milestone 3: Tabs Creation

**Objective:**  
Provide UI accessibility to custom objects via tab creation.

**Tabs Created For:**
- Customer Info
- Booking
- Booking Guest
- Travel Package
- Payment
- Employee
- Feedback

Tabs allow users to navigate and manage object data directly from the app interface.

---

## 🔗 Milestone 4: Fields & Relationships Setup

**Objective:**  
Define and implement the fields and inter-object relationships needed to support full business operations.

**Key Accomplishments:**
- Created all required fields for each object (text, picklist, checkbox, formula, etc.)
- Built global picklist value sets for Country, City, Trip Type, Membership, and more
- Established Lookup and Master-Detail relationships between key objects (e.g., Booking → Customer, Guide Assigned → Employee)
- Implemented calculated fields for travel billing, accommodation costs, and age/age category
- Configured roll-up summary fields and validation-ready inputs

---

## 💭 Reflection & Learnings

This stage gave me hands-on experience with the foundational elements of Salesforce development. Some important realizations:

- **Data modeling is critical** before jumping into automation. A well-thought-out structure prevents future errors and rework.
- **Salesforce makes it easy** to create complex business logic with point-and-click tools, especially through formula fields and picklists.
- **Global picklists** enhance consistency and reuse across objects and workflows.
- Working manually with object and field configurations has given me a strong appreciation for planning relationships, dependencies, and UI visibility.

---

## 🧩 Milestone 5: Field Dependencies

**Objective:** Implement dynamic field behavior based on controlling picklist values.

**Highlights:**
- BookingGuest: Country → City dependency
- Booking: Membership → Preferred Accommodation
- Employee: Department → Role and Country → City

This improved form relevance and usability across objects.

---

## ✅ Milestone 6: Validation Rules

**Objective:** Ensure data integrity across objects before record creation or updates.

**Key Validation Rules:**
- Phone must be 10 digits (Customer Info)
- Email must follow valid format
- Prevent future-dated birthdays
- Age must be > 0 (BookingGuest)
- Mandatory fields based on roles (e.g., Language Spoken for Guides)
- Booking Status must default to “Pending” on creation

---

## 🔄 Milestone 7: Approval Process

**Objective:** Implement structured approval for booking cancellations.

**Features:**
- Multi-step approval flow for cancellations
- Custom email templates for approval/rejection
- Field updates and email alerts based on outcomes
- Roles and profiles used for submitter and approver logic

---

## 🔃 Milestone 8: Flows

**Objective:** Automate logic where BookingGuest count must not exceed Booking’s number of travelers.

**Flow Summary:**
- Triggered on BookingGuest creation/update
- Fetches parent Booking record
- Prevents saving if guest count exceeds allowed limit
- Displays dynamic error popup using Flow Builder

---

## ⚙️ Milestone 9: Workflow Rules

**Objective:** Automate follow-up task creation after booking completion.

**Rule:**
- When Booking Status = Completed
- Auto-create a Task for the Booking Owner
- Task includes feedback follow-up with due date 3 days after travel ends

---

## 🔁 Milestone 10: Process Builder

**Objective:** Update Booking Status to "Confirmed" when a BookingPayment is marked as "Completed."

**Process:**
- Triggered on BookingPayment insert/update
- Automatically updates related Booking record’s status

---

## 🧩 Milestone 11: Triggers (Apex)

**Trigger 1:**  
On Booking creation:
- Automatically creates a related BookingPayment record (status = "Pending")
- Creates BookingGuest records based on `Number_of_Travelers__c`

**Trigger 2:**  
On Booking update:
- If Booking Status changes to "Confirmed", a confirmation email is sent asynchronously using a future method

---

## ⏳ Milestone 12: Asynchronous Apex

**Objective:** Handle long-running and scheduled logic with Apex.

**Techniques Used:**
- **Future Apex:** Confirmation emails after status change
- **Queueable Apex + Scheduler:**  
  - Reminder emails sent 3 days before travel start date
- **Batchable Apex + Scheduler:**  
  - Daily payment reminder for "Pending" bookings created yesterday
  - Final admin email confirming batch completion

---

## 💭 Reflection & Learnings

Completing all 12 backend configuration milestones helped me gain hands-on experience with the most critical aspects of Salesforce development. Here’s what I learned:

- **Automation layers in Salesforce are powerful and layered:** I saw how Flows, Workflows, Process Builder, and Apex each play different roles in system automation.
- **Code vs Click:** Declarative tools are great for many use cases, but real flexibility comes from Apex (Triggers, Future, Batch, Queueable).
- **Governance matters:** Using validation rules, field dependencies, and approval processes helped enforce clean data and proper workflows.
- **Async Apex ensures scalability:** It was exciting to build real-time email flows and scheduled tasks that improve customer communication and reduce manual overhead.

---

✅ **Phase Status:** Fully Completed  
📅 **Phase Duration:** Estimated 60–70 hours  
📁 **Next Phase:** UI/UX Development & Customization
