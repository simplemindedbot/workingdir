# User Story: Add Report UI with New Tabbed Interface in CBCI Admin Dashboard

**Title:** Introduce Tabbed Interface and Define Layout for Add Report Screen

**As a** Product Owner  
**I want to** introduce a new tabbed interface in the CBCI Administration Dashboard  
**And** define the fields and layout of the "Add Report" screen under the new "Reports" tab  
**So that** we can support modular expansion of administrative functionality, starting with the ability to configure and schedule extract reports

---

## Context

The CBCI Administration interface has been redesigned to support a modular tabbed layout. This structure allows for scalable expansion across multiple administrative functions. The **"Reports"** tab is the first such function and introduces a user interface for creating, editing, and scheduling report extracts.

---

## Acceptance Criteria

### Scenario: CBCI Admin Dashboard now includes tabbed navigation
**Given** I am an admin user accessing the CBCI Admin Dashboard  
**Then** I see a new tabbed navigation UI with the following tabs:
- **Analysis record**
- **Announcement management**
- **Variable Modeling**
- **Reports** (new)

---

### Scenario: Reports tab displays new report list and creation UI
**Given** I click on the "Reports" tab  
**Then** I see:
- A filterable **Report List** at the top (search, filter, and activate/deactivate reports)
- An **Add Report** section below it with configurable inputs for generating extract reports

---

## Field Definitions and Layout for Add Report UI

### Section: Report Metadata
- **Report name** – Text input (required)  
- **Entity name** – Text input with autocomplete (required)  
- **WCIS ID** – Text input (optional)  
- **Optimist ID** – Text input (optional)

### Section: Report Criteria
- **Start date** – Date picker (required)  
- **End date** – Date picker (required)  
- **Report time** – Time input (human-readable format, e.g., `13:00`) (required)  
- **Analysis status** – Dropdown list (optional)  
- **Include raw JSON from LLM** – Checkbox  
- **Include only most recent revision** – Checkbox

### Section: Notification
- **Notification emails** – Multi-select field with auto-complete and “Edit” button  
  - Opens modal to select from internal user directory

### Section: Recurrence
- **Recurring Report** – Toggle switch (ON/OFF)  
  - If ON, additional fields display:  
    - **Frequency** – Dropdown (e.g., Daily, Weekly, Monthly)  
    - **Time of Day** – Time picker  
  - If OFF, the report is treated as a one-time execution

---

### Scenario: Required field validation
**Given** I am completing the Add Report form  
**When** I omit required fields (e.g., report name, entity name, date range, or report time)  
**Then** the system prevents submission and displays validation messages

---

### Scenario: Layout follows CBCI design conventions
**Then** the layout follows consistent CBCI UI standards:
- Label/input alignment
- Grouped sections
- Tabular report list preview at the top
- Action buttons at bottom:  
  - **Reset**  
  - **Save changes**  
  - **Save as new report**

---

### Scenario: Editing a report pre-fills the Add Report form
**Given** I select a report from the Report List  
**Then** its saved configuration populates the Add Report form for editing or cloning