# Feature: One-time Report Specification and Immediate Download

**As an** admin user  
**I want to** generate and immediately download a one-time report by specifying key filters  
**So that** I can retrieve relevant analysis data without scheduling

---

## Scenario: Required fields must be present

**Given** I am on the “One-time Report” screen  
**When** I leave the "Report Name", "From Date & Time", or "To Date & Time" field blank  
**And** I click the “IMMEDIATE DOWNLOAD” button  
**Then** I should see a validation message for each missing required field  
**And** the report should not be generated or downloaded

---

## Scenario: Optional filters refine the results if entered

**Given** I have entered values for one or more of "Entity Name", "WCIS ID", or "Optimist ID"  
**When** I click the “IMMEDIATE DOWNLOAD” button  
**Then** the report should include only analyses matching the specified filters within the selected date/time range and analysis status

---

## Scenario: No optional filters returns all matching analyses

**Given** I have entered a report name, from and to date/time, and selected an analysis status  
**And** I have not entered any values for "Entity Name", "WCIS ID", or "Optimist ID"  
**When** I click the “IMMEDIATE DOWNLOAD” button  
**Then** the report should include **all analyses** with the specified status that fall within the date/time range, regardless of entity, WCIS ID, or Optimist ID

---

## Scenario: Requesting user is automatically recorded

**Given** I am authenticated and on the report generation screen  
**When** I click the “IMMEDIATE DOWNLOAD” button  
**Then** the system should automatically record my user ID with the report request  
**And** include that information in the report metadata or audit trail

---

## Scenario: From Date is after To Date

**Given** I have selected a From Date that is later than the To Date  
**When** I click “IMMEDIATE DOWNLOAD”  
**Then** I should receive a validation message  
**And** the report should not be generated

---

## Scenario: Successful immediate download with valid inputs

**Given** I have entered a report name, a valid From Date & Time, a valid To Date & Time, and selected an analysis status  
**And** any optional filters are either filled or left blank  
**When** I click the “IMMEDIATE DOWNLOAD” button  
**Then** the system should generate the report using the specified criteria  
**And** download the report immediately in the selected output format  
**And** record my user ID in the request metadata

---

## Scenario: Include only the most recent revisions

**Given** I have selected the option to include only the most recent revision of each analysis  
**When** I click the “IMMEDIATE DOWNLOAD” button  
**Then** the report should include only the latest revision for each matching analysis within the specified filters

---

## Scenario: Include all revisions

**Given** I have selected the option to include all revisions of each analysis  
**When** I click the “IMMEDIATE DOWNLOAD” button  
**Then** the report should include all available revisions for each matching analysis within the specified filters

---

## Scenario: Include raw LLM JSON output

**Given** I have selected “Yes” for the “Include Raw LLM JSON” option  
**When** I click the “IMMEDIATE DOWNLOAD” button  
**Then** the report should include the raw JSON output from the language model for each included analysis

---

## Scenario: Do not include raw LLM JSON output

**Given** I have selected “No” for the “Include Raw LLM JSON” option  
**When** I click the “IMMEDIATE DOWNLOAD” button  
**Then** the report should exclude the raw JSON output from the language model

---

## Scenario: Download report in JSON format

**Given** I have selected “JSON” from the Output Format dropdown  
**When** I click the “IMMEDIATE DOWNLOAD” button  
**Then** the system should generate the report in JSON format  
**And** the file should download with a `.json` extension

---

## Scenario: Download report in CSV format

**Given** I have selected “CSV” from the Output Format dropdown  
**When** I click the “IMMEDIATE DOWNLOAD” button  
**Then** the system should generate the report in CSV format  
**And** the file should download with a `.csv` extension