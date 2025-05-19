# User Story: Generate One-Time Ad-Hoc Report for Immediate Download

## Title
CBCI Admin - Generate a One-Time Report for Immediate Download

## Description
**As a**  
CBCI Administrator  

**I want to**  
generate a one-time, ad-hoc report using filters and have the report streamed directly for download upon completion  

**So that**  
I can quickly retrieve a targeted dataset without needing to save a persistent report configuration or schedule  

---

# Gherkin Acceptance Criteria

## Feature: Generate One-Time Ad-Hoc Report for Immediate Download

### Scenario: Create and download a one-time report
**Given** the admin has entered valid filter criteria (e.g., Entity Name, Date Range)  
**And** has selected the report format (CSV or JSON)  
**When** they click the "Download Now" button  
**Then** the system generates the report on-demand  
**And** streams the report file directly to the user's browser for immediate download  

---

### Scenario: Validate required fields before download
**Given** the admin has not entered all required filter fields  
**When** they click "Download Now"  
**Then** the system displays an error indicating the missing fields  
**And** prevents report generation  

---

### Scenario: Include raw JSON if requested
**Given** the admin has selected "Include Raw JSON from LLM"  
**When** the report is generated  
**Then** the output includes the raw model JSON in the selected format  

---

### Scenario: Include only most recent revision
**Given** the admin checks "Include Only Most Recent Revision"  
**When** the report is generated  
**Then** only the latest revision for each analysis is included in the report  

---

### Scenario: Show progress and completion status
**Given** the admin has submitted the download request  
**When** the report is processing  
**Then** the UI displays a loading or progress indicator  
**And** notifies the user when the download begins or fails