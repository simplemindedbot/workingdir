# User Story: Notification Emails for Report Completion

**Title:** Specify Notification Emails for Report Completion

**As an** Admin user  
**I want to** specify one or more user IDs to receive an email notification when a report generation job completes  
**So that** relevant stakeholders are informed that their requested report is ready for access or download

---

## Acceptance Criteria

### Scenario: Add notification email recipients when scheduling a report
**Given** I am on the “Add Report” section of the Reports tab in CBCI Administration  
**When** I enter one or more valid user IDs or email addresses into the “Notification emails” field  
**And** I save the report configuration  
**Then** those recipients will be saved along with the report definition

---

### Scenario: Send email when report completes successfully
**Given** a scheduled or ad hoc report finishes processing  
**And** the job completes without error  
**Then** the system sends a notification email to all saved recipients  
**And** the email includes the report name, execution time, and a link or instructions for locating the report

---

### Scenario: Email content matches expected template
**Given** a notification email is sent  
**Then** it should match the following structure:

#### Email Template Structure

- **Subject:** `CBCI Report Ready: <Report Name>`

- **Body:**
  ```
  The CBCI report you requested has been generated successfully.

  Report Name: <Report Name>
  Requested By: <Requesting User>
  Entity Name: <Entity Name>
  Start Date: <Start Date>
  End Date: <End Date>
  Report Time: <Time of Execution>
  File Format: CSV / JSON

  You can access the report at the following location:
  <Report Download URL or File Path>

  Please note: Reports are retained according to internal data governance and retention policies.
  ```

- **Footer:**
  ```
  This is an automated message from the CBCI system. Please do not reply.
  For assistance, contact your CBCI administrator or the support team at <support alias>.
  ```

---

### Scenario: Do not send email if report fails
**Given** a report job encounters a processing error  
**Then** no email is sent to recipients  
**And** the error is logged and visible to administrators for follow-up

---

### Scenario: Support multiple recipients
**Given** multiple user IDs or email addresses were specified in the notification field  
**When** the report completes  
**Then** all specified recipients receive identical email notifications