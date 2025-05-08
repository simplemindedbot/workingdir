
# High-Level User Stories for MNPI Control

## 1. Centralized MNPI Evaluation Functionality
**As** a platform engineer  
**I want** to implement a centralized service that checks for MNPI-flagged content across deal packages  
**So that** all CBCI workflows can consistently enforce access rules without duplicating logic.

## 2. Automatic MNPI Checks in Analysis Creation  
**As** an analyst  
**I want** the system to automatically check for MNPI-flagged data when I initiate a new analysis  
**So that** I am prevented from including MNPI content unintentionally.

## 3. Prevent Unauthorized Access to MNPI Data  
**As** a system  
**I want** to block access to MNPI-flagged content unless the user has appropriate entitlements  
**So that** regulatory requirements are met and sensitive information is protected.

## 4. Access Control Enforcement in All Workflows  
**As** a compliance officer  
**I want** MNPI access checks to be applied across all user workflows (viewing, editing, initiating, accessing via link)  
**So that** there is no backdoor path for unauthorized users to access MNPI content.

## 5. Future Support for Conditional MNPI Access  
**As** a product owner  
**I want** the system to support future functionality where certain users can access MNPI content with proper logging and justification  
**So that** we can support nuanced access requirements in future regulatory or business scenarios.

## 6. Nightly MNPI Flag Synchronization from RV/CRM  
**As** a data engineer  
**I want** the MNPI flags from RV/CRM to be synchronized nightly into CBCI’s centralized access control logic  
**So that** decisions are based on up-to-date regulatory information.

## 7. Audit Logging for MNPI Access Decisions  
**As** an auditor  
**I want** all MNPI-related access decisions (allow, deny, override) to be logged with user ID, timestamp, and justification (if applicable)  
**So that** we can demonstrate compliance during internal or external audits.

## 8. Maintainable Access Logic via Common Component  
**As** a developer  
**I want** all MNPI access checks to be implemented through a single shared function  
**So that** changes to business rules can be made in one place and applied consistently across all workflows.

## 9. Warning Banner on Analysis Interfaces  
**As** a CBCI user  
**I want** a visible warning when working with analyses that may involve MNPI  
**So that** I am aware of potential data sensitivity before proceeding.

## 10. Fail-Safe Behavior for Unknown MNPI Status  
**As** a compliance engineer  
**I want** the system to assume content is MNPI if its status cannot be confirmed  
**So that** we err on the side of caution and prevent data leakage.
