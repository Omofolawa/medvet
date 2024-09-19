# Medvet: GMP Compliant QC Operation System
The project is a **Quality Control (QC) Release System** for a sterile manufacturing environment. The system handles user authentication, data transcription, batch processing, and QC tests to ensure compliance with both ALCOA principles and Annex 1 of EudraLex guidelines.

## Stakeholder User Stories:

### 1. User Account Management
- As a QC Analyst, I need to securely log into the system so that I can enter QC test results.
- As an Administrator, I need to create, manage, and authenticate user accounts securely.
  
### 2. QC Test Entry
- As a QC Analyst, I need to enter and save QC test results for each batch, so that the batch can be assessed for compliance.

### 3. Batch Approval
- As a QA Manager, I need to ensure all QC test results for a batch comply with regulatory standards before I can approve the batch for release.

### 4. Data Integrity and Audit Log
- **As a Regulatory Inspector, I need an audit trail of user activities, so that I can verify the integrity of the QC test results and user actions.

----------------------------------------------------------------------------------------------------------------------------------------------------

## Technical Requirements:

1. User Account System:
   - Store user credentials securely using **SHA-256 hashing with salt**.
   - Users should be able to log in using their credentials.
   - Maintain role-based access control (e.g., Administrator, QC Analyst, QA Manager).

2. QC Test System:
   - Store test results for **Appearance**, **Assay**, **Sterility**, and **Endotoxin**.
   - Ensure data entry follows **ALCOA principles** (e.g., timestamping, user attribution).

3. Batch Processing:
   - Allow creation and management of batches, including the tracking of test results.
   - Implement business logic to approve batches only when all test results are marked as **"Complies"**.

4. Error Handling:
   - Ensure all stored procedures handle errors gracefully with transactions and rollback mechanisms.

5. Audit Log:
   - Log all user actions (e.g., data entry, approvals) to ensure traceability and regulatory compliance.

------------------------------------------------------------------------------------------------------------------------------------------------------

## Acceptance Criteria:

1. User Login System:
   - Users can securely create and log into accounts.
   - Passwords are stored securely using **SHA-256** with a salt.
   - Role-based access control works as expected.

2. QC Test Entry:
   - All 4 QC tests (Appearance, Assay, Sterility, Endotoxin) can be entered for each batch.
   - Tests are marked as either "Complies" or "Non-compliant."
   - The system validates and stores the test results with proper error handling.

3. Batch Approval:
   - A batch can only be approved if all 4 QC tests are completed and marked as "Complies."
   - If any test is missing or marked as "Non-compliant," the batch cannot be approved.

4. Error Handling:
   - Any error in stored procedures is handled gracefully with transaction rollback and detailed error messages.

5. Audit Log:
   - All user actions, including login, test entries, and batch approvals, are logged and can be reviewed.

--------------------------------------------------------------------------------------------------------------------------------------------------------

###Database statement:
The database keeps track of **users**, who can log in, perform actions, and have their activity recorded in an **audit log**. Users can also approve **batches** of products and carry out **quality control tests** on them. Each batch goes through required tests, and users with specific roles (like admin or QC analyst) decide whether to approve or reject the batch based on the results. The system ties **batches** to the **users** who approve them and links the **QC test data** to each batch. Everything users do is logged for transparency and compliance.
