# CBCI Reports Tab User Stories and Acceptance Criteria

## Story 1: Search and Manage Existing Reports

**Title:** CBCI Admin - Search, View, and Manage Existing Scheduled Reports

**As a** CBCI Administrator  
**I want to** view, filter, and manage the list of existing scheduled and ad-hoc reports from the Reports tab  
**So that** I can monitor, activate, deactivate, or modify report configurations as needed

### Acceptance Criteria

- Filters are available for Report Name, Entity Name, Start Date, End Date, and Requesting User
- System displays matching reports based on filter criteria
- Reports list shows: Report Name, Entity Name, Frequency, Time of Day, Start Date, End Date, Status, Actions
- Action links allow me to Activate or Deactivate a report
- Deactivated reports remain visible but show as Inactive
- Clicking a Report Name opens the report for editing
- Reset Filters clears all filter fields

## Story 2: Create and Schedule a New Report

**Title:** CBCI Admin - Create and Schedule a New Recurring or Ad-hoc Report

**As a** CBCI Administrator  
**I want to** create a new report with defined criteria and optionally set it to run on a recurring basis  
**So that** the system automatically generates the report according to my schedule or allows for a single manual run

### Acceptance Criteria

- I can specify Report Name, Entity Name, WCIS ID, Optimist ID, Start Date, End Date
- I can select Report Time (specific time of day in 24-hour format)
- I can choose Analysis Status (dropdown selection)
- I can check/uncheck to Include Raw JSON from LLM
- I can choose whether to Include Only Most Recent Revision
- I can select notification email recipients from a pre-populated list
- I can toggle Recurring Report ON/OFF
- If Recurring ON, I must set a schedule (daily, monthly, etc.)
- I can save the report as New or Update an existing one
- Confirmation is shown when the report is saved

## Story 3: Select Notification Email Recipients

**Title:** CBCI Admin - Select Email Recipients for Report Notifications

**As a** CBCI Administrator  
**I want to** choose specific users from a list of available email addresses to receive report notifications  
**So that** the correct stakeholders are informed when reports are generated

### Acceptance Criteria

- The Notification Emails section displays how many email addresses are currently selected
- Clicking Edit opens a selection dialog with the full list of available recipients
- I can search/filter within the dialog to find specific users by name or email address
- I can select or deselect individual users
- Selected recipients are displayed as a comma-separated list once saved
- Changes are not applied until I click Save changes or Save as new report
- There is a limit to the number of selectable recipients (configurable; example: 500)
- System prevents saving if recipient list exceeds maximum