### **User Story 1: Display Metrics in Centralized Admin Dashboard**

**As** a System Admin or Data Science user  
**I want** to view a centralized location on the Landing Page showing Optimist data inputs used by the AI  
**So that** I can easily review and analyze the key metrics associated with AI prompts

**Acceptance Criteria:**
- The centralized dashboard displays the following columns for each metric:
  - Prompt Name
  - Optimist Industry Template
  - Optimist Alias ID
  - Account Type
  - Optimist Account Name
  - Rename Flag
  - Renamed Account Name
  - Formula
  - Output Flag
  - Output Order
  - Percentage Ratio Flag
  - Append an X
  - YOY Change Needed
  - Most Recent Data Only
  - Materiality Threshold
  - Notes

---

### **User Story 2: Role-Based Access to Admin Dashboard**

**As** a platform  
**I want** to control access to the centralized metrics dashboard based on user entitlement  
**So that** only authorized users can view or edit metrics

**Acceptance Criteria:**
- System Admin users: Full access to view and edit metrics
- Data Science users: View-only access
- Business Users, Read-Only, and UAT Testers: No visibility or access to the centralized location
- Users without access cannot navigate to the page via URL

---

### **User Story 3: Add New Metric Entry in Real-Time**

**As** a System Admin  
**I want** to create a new metric entry in real-time  
**So that** I can quickly configure new AI inputs when needed

**Acceptance Criteria:**
- Admin can launch a "New Metric" modal/form
- All required fields must be present and validated
- The new metric is saved and appears immediately in the dashboard
- Input fields align with metric attributes from User Story 1

---

### **User Story 4: Add a New Parameter to an Existing Metric**

**As** a System Admin  
**I want** to create a new parameter (e.g., append rules, YOY flag, rename flag) for a specific account/metric in real-time  
**So that** I can fine-tune AI input logic as needed

**Acceptance Criteria:**
- Admin can select a metric and append a new parameter value
- Updated parameters are immediately reflected in the dashboard
- Validation rules ensure parameter format and uniqueness

---

### **User Story 5: Edit Existing Metrics in Real-Time**

**As** a System Admin  
**I want** to edit the fields of an existing metric  
**So that** I can correct or update information dynamically

**Acceptance Criteria:**
- Edits can be made inline or via an "Edit Metric" modal
- Changes must be saved and reflected in the dashboard without refresh
- Edited fields must follow the same validation rules as new entries

---

### **User Story 6: Search, Sort, and Filter Metrics**

**As** a System Admin or Data Science user  
**I want** to search, sort, and filter metrics  
**So that** I can find specific data quickly within the dashboard

**Acceptance Criteria:**
- Sort by any column
- Filter by Prompt Name, Alias ID, or Account Type at minimum
- Search across all displayed fields
- Search results are case-insensitive and partial matches are allowed

---

### **User Story 7: Audit Logging of Metric Changes**

**As** a platform  
**I want** to log all metric changes  
**So that** there is an audit trail of who made what changes and when

**Acceptance Criteria:**
- Each create/edit action logs:
  - Username
  - Timestamp
  - Action type (Create or Edit)
  - Fields changed (with before/after values for edits)
- Logs are stored securely and can be exported or reviewed via Admin tools

---

### **User Story 8: Navigation to Admin Metrics Dashboard**

**As** a System Admin or Data Science user  
**I want** a clearly marked navigation link from the Landing Page to the centralized metrics dashboard  
**So that** I can easily access the AI input configuration tools

**Acceptance Criteria:**
- Link only appears for entitled users
- Clicking the link routes the user to the centralized dashboard
- Non-authorized users cannot access the page by URL

---
Here are **Gherkin-formatted acceptance criteria** for each of the 8 user stories related to the centralized Optimist metrics dashboard:

---

### **User Story 1: Display Metrics in Centralized Admin Dashboard**

```gherkin
Feature: Display Optimist Metrics in Centralized Admin Dashboard

Scenario: Authorized user views the centralized dashboard
  Given I am logged in with System Admin or Data Science entitlement
  When I navigate to the Centralized Optimist Metrics Dashboard
  Then I should see a table with the following columns:
    | Prompt Name              |
    | Optimist Industry Template |
    | Optimist Alias ID        |
    | Account Type             |
    | Optimist Account Name    |
    | Rename Flag              |
    | Renamed Account Name     |
    | Formula                  |
    | Output Flag              |
    | Output Order             |
    | Percentage Ratio Flag    |
    | Append an X              |
    | YOY Change Needed        |
    | Most Recent Data Only    |
    | Materiality Threshold    |
    | Notes                    |
```

---

### **User Story 2: Role-Based Access to Admin Dashboard**

```gherkin
Feature: Role-based access to Optimist Metrics Dashboard

Scenario: System Admin has full access
  Given I am logged in with System Admin entitlement
  When I navigate to the Centralized Optimist Metrics Dashboard
  Then I should be able to view and edit metrics

Scenario: Data Science user has view-only access
  Given I am logged in with Data Science entitlement
  When I navigate to the Centralized Optimist Metrics Dashboard
  Then I should be able to view but not edit metrics

Scenario: Unauthorized user cannot access the dashboard
  Given I am logged in with Business User, Read-Only, or UAT Tester entitlement
  When I attempt to access the Centralized Optimist Metrics Dashboard
  Then I should receive an access denied message
  And I should not see a link to the dashboard in the UI
```

---

### **User Story 3: Add New Metric Entry in Real-Time**

```gherkin
Feature: Create a new Optimist metric in real-time

Scenario: System Admin creates a new metric
  Given I am logged in with System Admin entitlement
  When I click "Add Metric"
  And I fill in all required fields with valid values
  And I click "Save"
  Then a new metric should be saved and appear in the dashboard
  And I should see a confirmation message
```

---

### **User Story 4: Add a New Parameter to an Existing Metric**

```gherkin
Feature: Add new parameter to an existing Optimist metric

Scenario: System Admin adds a new parameter
  Given I am logged in with System Admin entitlement
  And I am viewing a specific metric
  When I click "Edit"
  And I add a new value for a parameter (e.g. YOY Change Needed = true)
  And I click "Save"
  Then the updated parameter should be reflected in the dashboard
  And the update should be logged
```

---

### **User Story 5: Edit Existing Metrics in Real-Time**

```gherkin
Feature: Edit existing Optimist metrics

Scenario: System Admin edits an existing metric
  Given I am logged in with System Admin entitlement
  And I am viewing the Optimist Metrics Dashboard
  When I click "Edit" on a metric
  And I update the Formula and Output Order fields
  And I click "Save"
  Then the metric should update with the new values
  And I should see a confirmation message
  And the changes should be logged
```

---

### **User Story 6: Search, Sort, and Filter Metrics**

```gherkin
Feature: Search, sort, and filter Optimist metrics

Scenario: Search by keyword
  Given I am viewing the Optimist Metrics Dashboard
  When I enter "Revenue" into the search bar
  Then I should see only rows where any field contains "Revenue"

Scenario: Sort by Output Order
  Given I am viewing the Optimist Metrics Dashboard
  When I click the "Output Order" column header
  Then the metrics should be sorted in ascending numerical order

Scenario: Filter by Account Type
  Given I am viewing the Optimist Metrics Dashboard
  When I select "Operating" in the Account Type filter
  Then I should see only metrics with Account Type = "Operating"
```

---

### **User Story 7: Audit Logging of Metric Changes**

```gherkin
Feature: Log all metric changes for audit

Scenario: Log creation of a new metric
  Given I am a System Admin
  When I create a new metric
  Then the action should be logged with:
    | Action Type | Username | Timestamp | Affected Fields |

Scenario: Log edit of an existing metric
  Given I am a System Admin
  When I change the Output Flag of an existing metric
  Then the action should be logged with:
    | Action Type | Username | Timestamp | Changed Fields and Before/After Values |
```

---

### **User Story 8: Navigation to Admin Metrics Dashboard**

```gherkin
Feature: Provide access to centralized dashboard via Landing Page

Scenario: Eligible user sees link to dashboard
  Given I am logged in as a System Admin or Data Science user
  When I view the Landing Page
  Then I should see a link labeled "Optimist Metrics Dashboard"
  And clicking it should take me to the centralized metrics page

Scenario: Ineligible user does not see link
  Given I am logged in as a Read-Only or UAT user
  When I view the Landing Page
  Then I should not see a link to the Optimist Metrics Dashboard
  And direct access via URL should result in access denied
```

Perfect. Here are **validation-focused Gherkin scenarios** added to the relevant user stories to ensure each input field is properly constrained and user-friendly during **metric creation and editing**.

---

## ✅ Extended Gherkin Scenarios for **User Story 3**: Create a New Metric

```gherkin
Feature: Validate required fields when creating a new metric

Scenario: Display error for missing required fields
  Given I am a System Admin
  And I click "Add Metric"
  When I leave the "Prompt Name" field empty
  And I click "Save"
  Then I should see an error message "Prompt Name is required"
  And the metric should not be saved

Scenario: Display error for invalid data type
  Given I am adding a new metric
  When I enter "abc" in the "Output Order" field
  And I click "Save"
  Then I should see an error message "Output Order must be a number"

Scenario: Prevent duplicate Optimist Alias ID for the same Prompt Name
  Given a metric already exists with Prompt Name "Revenue" and Alias ID "A123"
  When I attempt to create another metric with the same values
  Then I should see an error message "Duplicate entry: Prompt and Alias ID combination must be unique"

Scenario: Materiality Threshold must be a valid percentage
  Given I am editing or adding a metric
  When I enter "150%" into the "Materiality Threshold" field
  Then I should see an error message "Materiality Threshold must be between 0% and 100%"

Scenario: Optional fields accept empty values
  Given I am adding a new metric
  When I leave the "Formula" and "Notes" fields blank
  And I click "Save"
  Then the metric should be saved without errors
```

---

## ✅ Extended Gherkin Scenarios for **User Story 5**: Edit Existing Metric

```gherkin
Feature: Validate input fields during metric editing

Scenario: Display validation errors when required fields are removed
  Given I am editing a metric
  When I clear the value of the "Optimist Account Name" field
  And I click "Save"
  Then I should see an error message "Optimist Account Name is required"
  And the metric should not be updated

Scenario: Prevent invalid boolean flag values
  Given I am editing the "YOY Change Needed" field
  When I enter "maybe" instead of "true" or "false"
  Then I should see an error message "YOY Change Needed must be true or false"
```

---

## ✅ Additional Input Validation Notes (for Developers or BRD)

| **Field**                    | **Type**      | **Required** | **Validation Rules**                                                                 |
|-----------------------------|---------------|--------------|---------------------------------------------------------------------------------------|
| Prompt Name                 | Text          | Yes          | Max 100 chars, must be unique with Alias ID                                          |
| Optimist Industry Template  | Text          | Yes          | Must match known template values (dropdown preferred)                                |
| Optimist Alias ID           | Text/ID       | Yes          | Unique per Prompt Name                                                               |
| Account Type                | Enum/Text     | Yes          | Valid values: Operating, Non-operating, etc.                                         |
| Rename Flag                 | Boolean       | No           | true/false only                                                                       |
| Renamed Account Name        | Text          | Conditional  | Required if Rename Flag = true                                                       |
| Formula                     | Text          | No           | Valid math expression syntax (optional)                                              |
| Output Flag                 | Boolean       | No           | true/false only                                                                       |
| Output Order                | Integer       | Conditional  | Required if Output Flag = true; must be positive integer                             |
| Percentage Ratio Flag       | Boolean       | No           | true/false only                                                                       |
| Append an X                | Boolean       | No           | true/false only                                                                       |
| YOY Change Needed           | Boolean       | No           | true/false only                                                                       |
| Most Recent Data Only       | Boolean       | No           | true/false only                                                                       |
| Materiality Threshold       | Percent (0-1) | No           | Must be a float between 0 and 1 or entered as percentage (e.g., 5% = 0.05)           |
| Notes                       | Text (long)   | No           | Max 500 characters                                                                   |

---

Let me know if you'd like to embed these into a **requirements traceability matrix** or exported into a CSV or Excel for Jira import.

**Q1:** Do you want a UI wireframe sketch to go with the “Add Metric” form and validation?
**Q2:** Should the Materiality Threshold be shown as a slider, dropdown, or numeric input with % sign?
**Q3:** Do you want to establish naming or formatting conventions (e.g., camelCase vs Title Case) for fields like Prompt Name or Alias ID?