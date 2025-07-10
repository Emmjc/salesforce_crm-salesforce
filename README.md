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

# Phase 3: UI/UX Development & Customization (Milestones 13–20 Completed)

## 🎯 Overview

This phase focused on enhancing the user experience within the Tours & Travels CRM by configuring custom layouts, building dynamic forms, implementing interactive dashboards, and creating a reusable Lightning Web Component (LWC). It aimed to deliver a seamless, role-specific, and data-driven interface for all users of the system.

---

## 📦 Milestone 13: Lightning App Creation

**Objective:**  
Build a modern and role-specific Lightning App for Tours & Travels operations.

**Key Activities:**
- Created the **"Tours & Travels CRM"** Lightning App via App Manager.
- Added key items: `Customer Info`, `Travel Packages`, `Bookings`, `Employees`, `Booking Payments`, `Tasks`, `Reports`, `Dashboards`.
- Assigned access to `System Administrator` profile.

---

## 🧱 Milestone 14: Editing Page Layouts

**Objective:**  
Organize and personalize record layouts for each object to improve usability.

**Objects Updated:**
- `Customer Info`, `Booking`, `BookingGuest`, `TravelPackage`, `Employee`, `Booking Payments`, `Feedback`.

**Highlights:**
- Rearranged fields, added related lists, and tailored views per object to improve data entry and visibility.

---

## ⚙️ Milestone 15: Dynamic Forms

**Objective:**  
Make form fields responsive and context-aware.

**Implementation:**
- Enabled **Dynamic Forms** for `Booking` records.
- Configured conditional visibility for fields like `Cancellation Date`, `Cancel Confirmation`, and `Approval Status` based on Booking Status.
- Activated for both Desktop and Mobile views.

---

## 👥 Milestone 16: Users Setup

**Objective:**  
Create and assign users with appropriate roles and profiles.

**Highlights:**
- Created sample users for roles like `Travel Agent`, `Travel Agent Manager`.
- Assigned Salesforce Platform licenses.
- Encountered a user limit (could create 3 out of 4 planned test users).

---

## 📊 Milestone 17: Reports

**Objective:**  
Gain actionable insights from CRM data.

**Reports Created:**
1. **Monthly Revenue Report** – Pie chart with revenue buckets (Low/Medium/High)
2. **Pending Payments**
3. **Top Travel Packages (by Booking Count)**
4. **Employee Role Distribution**
5. +5 more custom reports tailored to business questions

**Reflections:**  
This milestone emphasized how **data visibility drives business strategy**—by analyzing payment status, top packages, and employee distribution, stakeholders can make smarter decisions.

---

## 📈 Milestone 18: Dashboards

**Objective:**  
Visualize key metrics from reports in a high-level format.

**Activities:**
- Created **"Tours & Travels Dashboard"** with 4 components, including Pie and Bar charts.
- Created 2 additional dashboards using report data for role-based decision-making.
- Enhanced non-technical user experience through visual summaries.

---

## ⚡ Milestone 19: Lightning Web Component (LWC)

**Objective:**  
Build an interactive UI to filter Travel Packages by Country.

**Key Outputs:**
- Developed an Apex Controller (`TravelPackageController`)
- Built LWC `travelPackageSelector` that:
  - Dynamically displays filtered packages
  - Shows key travel details without page reload
- Deployed component to App, Home, and Record pages

---

## 🧩 Milestone 20: Lightning App Page

**Objective:**  
Create a dedicated App Page to host the LWC.

**Activities:**
- Created `Travel Package Selector` app page
- Embedded the `travelPackageSelector` component using Lightning App Builder
- Activated the app page and added it to the Tours & Travels CRM navigation

---

## 💭 Reflection & Learnings

Phase 3 allowed me to experience how Salesforce empowers UX customization without heavy code. Key insights:

- **Dynamic Forms and Page Layouts** provide unmatched flexibility for tailoring record visibility.
- **Reports and Dashboards** are not just features—they are essential tools for **business intelligence**.
- **Lightning Web Components** offer modern frontend capabilities, making the CRM more interactive and engaging.
- Designing with users in mind makes the platform more intuitive for both technical and non-technical roles.

---

# Phase 4: Data Migration, Testing & Security (Milestones 21–29 Completed)

## 🔍 Milestone 21: Field History Tracking

**Objective:**  
Track changes to important fields for audit purposes.

**Implemented On:**
- `Booking`: Tracked changes to `Number of Travelers`, `Booking Status`, and `TravelPackage`.
- `TravelPackage`: Tracked changes to `Price Per Person` and `Availability Status`.

---

## 🚫 Milestone 22: Duplicate & Matching Rules

**Objective:**  
Prevent duplicate data entry in `Customer Info`.

**Steps Taken:**
- Created a **Matching Rule** on `Email` and `Phone` using exact match.
- Created a **Duplicate Rule** to alert users if duplicate entries are attempted, while allowing the save (for review purposes).

---

## 👤 Milestone 23: Profiles

**Objective:**  
Define object- and field-level access based on job functions.

**Custom Profiles Created:**
- Travel Agent (Full access to bookings and customer info)
- Tour Guide (Read-only access)
- Finance Officer (Access to bookings and payments)
- Marketing Executive (Access to travel packages)
- Customer Service Rep (Access to feedbacks)

**Security Settings Updated:**
- Session timeout: 2 hours
- Password policies set to minimum 8 characters, never expires

---

## 🧭 Milestone 24: Roles & Role Hierarchy

**Objective:**  
Set up data visibility structure based on organization hierarchy.

**Roles Created:**
- Under CEO:
  - Travel Agent Manager
    - Travel Agent
    - Travel Tour Guide
  - Finance Officer
  - Marketing Executive
  - Customer Service Rep

---

## 🛡️ Milestone 25: Permission Sets

**Objective:**  
Extend specific permissions without changing base profiles.

**Permission Set Created:**
- **Extra Permission for Travel Agent Manager**
  - Grants full CRUD access to the `TravelPackage` object
  - Assigned directly to a Travel Agent Manager user

---

## 🔐 Milestone 26: Sharing Settings

**Objective:**  
Control default record visibility and enforce access rules.

**Key Updates:**
- Set `Customer Info` object OWD to **Private**
- Added sharing rule: Auto-share Customer Info records from "Travel Agent" to "Tour Guide" with **Read-Only** access

---

## ✅ Milestone 27: Apex Test Classes

**Objective:**  
Validate custom logic and meet Salesforce deployment requirements.

**Test Class Created:**
- `BookingTriggerTest`
  - Verifies trigger-based creation of `Booking_Payment__c` and `BookingGuest__c` records
  - Ensures correct guest count and payment status
  - Run successfully with 100% test coverage

---

## 🧪 Milestone 28: Test Cases & Defect Fixing

**Objective:**  
Ensure app functionality through structured testing.

**Test Cases Documented:**
1. Customer creation
2. Booking creation and auto-creation of related records
3. Payment status update triggering Booking confirmation and email
4. Multiple additional test cases for real-life scenarios (e.g., cancellation flow, validation rules, duplicate prevention)

🗂️ *Note: A separate test case document was submitted as part of final deliverables.*

---

## 📥 Milestone 29: Data Import Wizard

**Objective:**  
Import initial dataset into core objects.

**Data Imported Using Wizard:**
- `Customer Info`
- `TravelPackage`
- `Employee`

**Highlights:**
- CSVs with 20+ sample records per object
- Fields were manually mapped and reviewed
- Post-import validation performed through record listings

---

## 💭 Reflection & Learnings

This phase helped reinforce the importance of:
- **Clean, secure data management**
- **Granular access control using roles, profiles, and permissions**
- **Reliable test automation** to validate backend logic
- **User-level visibility and collaboration** through sharing rules
- **Streamlined data onboarding** using the Import Wizard

It was a rewarding experience seeing the system behave exactly as intended across different user roles, security settings, and operational flows.

---

✅ **Phase Status:** Completed  
📅 **Estimated Duration:** ~80+ hours  
📁 **Next Phase:** Final Review, Documentation & Deployment


