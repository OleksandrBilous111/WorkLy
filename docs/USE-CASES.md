# Use cases
## [UC-01] Account Creation (Verification Level 1)
### 1. Description
**Actor:** User / Client

**Goal:** To gain access to the service features available for users with Verification Level 1.

### 2. Main Success Scenario (Happy Path)
  1. The User navigates to the registration form.
  2. The User enters the required information: Nickname, Email, Password, and Phone Number.
  3. The User clicks the "Sign Up" button.
  4. The System validates the format of the entered data.
  5. The System performs a background check on the data (uniqueness, etc.).
  6. The System creates the account and grants the User access to the platform (limited to non-fully verified features).

### 3. Acceptance Criteria (AC)
**[ ] AC 1:** Successful Registration Given the user provides valid data in all fields;

When the user clicks "Sign Up";

Then the account is created, and the user is redirected to the dashboard with "Level 1" access.

**[ ] AC 2:** Input Format Validation Given the user enters data in an incorrect format (e.g., invalid email or phone number);

When the user attempts to submit the form;

Then the system must display an error message specifically indicating which field contains the error.

**[ ] AC 3:** Duplicate Data Check Given the user enters an Email or Nickname that is already registered in the system;

When the user clicks "Sign Up";

Then the system must prevent registration and display a message stating that the account already exists.

**[ ] AC 4:** Required Fields (Empty State) Given one or more fields are left blank;

When the user clicks "Sign Up";

Then the system must block the submission and highlight the missing fields as mandatory.

## [UC-03] Identity Verification (Verification Level 3)

### 1. Description
**Actor:** Registered User (with verified phone number and 2FA enabled)

**Goal:** To obtain full access to all application features and remove account restrictions by completing identity and liveness verification.

### 2. Main Success Scenario (Happy Path)
1. The User navigates to the Verification Panel and clicks the **"Verify"** button.
2. The User selects the appropriate document type and uploads the required files.
3. The System performs an automated validation of the document’s authenticity and data.
4. Upon successful document validation, the System redirects the User to the Video Verification interface and provides instructions.
5. The User completes the identity confirmation (Liveness Check), and the System redirects them to the Home Page.
6. The System grants the User "Verified" status and unlocks all restricted features.

### 3. Acceptance Criteria (AC)

**[ ] AC 1: Security Prerequisites**
Given the user has not confirmed their phone number or enabled Two-Factor Authentication (2FA);
When the user attempts to start Level 3 verification;
Then the system must block access and prompt the user to complete these security steps first.

**[ ] AC 2: Sequential Flow Logic**
Given the user has not completed Level 2 verification;
When the user attempts to access Level 3;
Then the system must automatically redirect the user to the Level 2 verification block.

**[ ] AC 3: Document Validity and Age Check**
Given the user uploads a document;
When the system processes the data;
Then it must verify that the document is valid (not expired) and that the user meets the minimum age requirement (18+).

**[ ] AC 4: Liveness Check Trigger**
Given the user is in the verification process;
When the document validation stage is successfully passed;
Then the system must immediately initiate the Video Verification interface.

**[ ] AC 5: Fraud and Forgery Prevention**
Given the user submits forged documents or attempts to deceive the system;
When the fraud is detected;
Then the system must automatically block the user's account and ban their MAC address.

**[ ] AC 6: Minor User Handling**
Given the system identifies the user as a minor (under 18) during the check;
When the verification is processed;
Then the system must redirect the user to a specialized "Minor Identity Confirmation" flow to assign appropriate restricted permissions.
