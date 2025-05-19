# Gherkin Acceptance Criteria for CBCI Download Report Stories

## Feature: Search and Manage Existing Reports

### Scenario: Filter reports using report name and entity name
**Given** the admin is on the Reports tab  
**When** they enter a report name and entity name in the filter fields  
**And** click the Apply button  
**Then** the report list displays only matching results

### Scenario: View report details
**Given** the admin sees a list of scheduled reports  
**When** they click on a report name  
**Then** the report's full configuration loads in the Add Report panel

### Scenario: Activate a deactivated report
**Given** a report is listed with status "Inactive"  
**When** the admin clicks the Activate link in the Actions column  
**Then** the report status changes to "Active"

### Scenario: Deactivate an active report
**Given** a report is listed with status "Active"  
**When** the admin clicks the Deactivate link in the Actions column  
**Then** the report status changes to "Inactive"

### Scenario: Reset report filters
**Given** filters have been entered in the Reports tab  
**When** the admin clicks the Reset Filters button  
**Then** all filter fields are cleared

---

## Feature: Create and Schedule New Report

### Scenario: Create a one-time report with filter criteria
**Given** the admin enters Report Name, Entity Name, Start Date, and End Date  
**When** they click Save as New Report  
**Then** the report is saved and appears in the Report List

### Scenario: Configure recurring report schedule
**Given** the admin has enabled Recurring Report  
**When** they select a frequency (One-time, Daily, Weekly, Monthly, or Quarterly)  
**And** click Save  
**Then** the recurring job is scheduled and visible in the Reports list

### Scenario: Include raw model JSON in report
**Given** the admin selects the checkbox for "Include Raw JSON from LLM"  
**When** the report is generated  
**Then** the resulting file includes the raw JSON output from the model

### Scenario: Limit report to most recent analysis revision
**Given** the admin checks "Include Only Most Recent Revision"  
**When** the report is generated  
**Then** only the latest revision for each analysis is included

### Scenario: Validate required fields before saving
**Given** required fields like Report Name or Date Range are empty  
**When** the admin clicks Save  
**Then** the system displays a validation error and does not save the report

---

## Feature: Select Email Recipients for Report Notifications

### Scenario: Display number of selected recipients
**Given** the admin is configuring a report  
**Then** the Notification Emails field displays "X of Y selected"

### Scenario: Edit the list of recipients
**Given** the admin clicks Edit next to Notification Emails  
**When** the recipient selection dialog opens  
**Then** they can search and select from a list of available users

### Scenario: Limit number of email recipients
**Given** the admin selects more than the maximum allowed recipients  
**When** they attempt to save the report  
**Then** the system prevents the save and shows an error

### Scenario: Persist email recipient selections
**Given** the admin selects recipients and saves the report  
**When** they reopen the report for editing  
**Then** the previously selected recipients are shown as selected