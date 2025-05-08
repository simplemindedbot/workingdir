Here are detailed Gherkin-style acceptance criteria for the user story you provided, covering the storage of all defined analysis and assertion fields in the analytics database:

⸻

Feature: Store All Defined Analysis and Assertion Fields in the Analytics Database

Feature: Persist structured CBCI output data for downstream consumption

  Background:
    Given the analytics database schema is defined and accessible
    And the application has completed analysis and assertion processing

  Scenario: Store core metadata fields
    When a new analysis is completed
    Then the following fields are stored in the database:
      | Field Name               |
      | Analysis Date           |
      | Analysis ID             |
      | Analysis Revision ID    |
      | User ID                 |
      | Username                |
      | Entity Name             |
      | WCIS ID                 |
      | Optimist ID             |
      | Analysis Status         |

  Scenario: Store processing diagnostics fields
    When processing metrics are captured for an analysis
    Then the following fields are stored in the database:
      | Field Name                       |
      | Processing Duration             |
      | Extraction Time (if applicable) |
      | Prep Time (if applicable)       |
      | Tachyon Call Duration           |
      | Assertion Routine Time          |
      | Total Time                      |

  Scenario: Store Areas of Attention metrics
    When Areas of Attention are assessed
    Then the following fields are stored in the database:
      | Field Name                                  |
      | Metric Accuracy Rating                      |
      | Metric Accuracy Category                    |
      | Metric Accuracy Free Form Comments          |
      | Materiality Rating                          |
      | Materiality Category                        |
      | Materiality Free Form Comments              |
      | Areas of Attention Overall                  |
      | Areas of Attention Character Count          |

  Scenario: Store Financial Analysis metrics
    When financial statements are analyzed
    Then the system stores the following for each section:
      | Section            | Fields                                                |
      | Income Statement   | Accuracy Rating, Accuracy Category, Accuracy Comments |
      |                    | Completeness Rating, Category, Comments              |
      | Balance Sheet      | Completeness Rating, Category, Comments              |
      | Cash Flow          | Completeness Rating, Category, Comments              |
      | Summary Comments   | Overall Financial Analysis Comments                  |
      | Meta               | Original Version Character Count                     |
      |                    | Editable Version Character Count                     |

  Scenario: Store assertion-related fields
    When the assertion process completes
    Then the following fields are stored in the database:
      | Field Name            |
      | Assertion Results     |
      | Overall Satisfaction Rating |

  Scenario: Validate required fields are not null
    Given all required fields are defined in the schema
    When a record is written to the database
    Then all required fields must contain valid, non-null values
    And any optional fields not present default to null or empty

  Scenario: Support extensibility for new fields
    Given new fields are added to the CBCI model in the future
    When the schema is updated
    Then existing storage logic can be extended to support the new fields
    Without disrupting prior data

  Scenario: Audit data storage operation
    When analysis data is stored in the database
    Then a success or failure log is written for the operation
    And the log includes the Analysis ID, timestamp, and any error messages


⸻

Optional Enhancements:
	•	Add schema validation rules (e.g., enum values for categories, numeric types for ratings).
	•	Track versioning or source system metadata for each field batch.
	•	Capture the assertion engine version or ruleset used (future story).

Would you like a data dictionary companion for this user story, showing field names, data types, and constraints?