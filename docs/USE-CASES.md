# Use cases

## Map
  - [[UC-01] Account Creation (Verification Level 1)](#uc-01-account-creation-verification-level-1)
  - [[UC-02] Profile Specialization Setup](#uc-02-profile-specialization-setup)
  - [[UC-03] Phone Number Verification](#uc-03-phone-number-verification)
  - [[UC-04] Portfolio / Work Samples Upload](#uc-04-portfolio--work-samples-upload)
  - [[UC-05] Client Order History Review](#uc-05-client-order-history-review)
  - [[UC-06] Role Switching (Dual Profile)](#uc-06-role-switching-dual-profile)
  - [[UC-07] Identity Verification (KYC - Level 2)](#uc-07-identity-verification-kyc---level-2)
  - [[UC-08] Notification Preferences](#uc-08-notification-preferences)


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

## [UC-02] Profile Specialization Setup

**1. Description**

- **Actor:** Performer
    
- **Goal:** To define professional skills and categories to attract relevant job offers.
    

**2. Main Success Scenario (Happy Path)**

1. The Performer navigates to the "My Profile" or "Edit Skills" section.
    
2. The Performer selects one or more categories (e.g., Cleaning, IT, Delivery).
    
3. The Performer adds specific tags or a description of their experience.
    
4. The Performer clicks "Save Changes."
    
5. The System updates the profile and starts suggesting relevant orders in the feed.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Successful Update**
    
    - **Given** the performer has selected at least one valid category;
        
    - **When** they click "Save Changes";
        
    - **Then** the profile is updated, and a "Success" notification is shown.
        
- **[ ] AC 2: Minimum Requirements**
    
    - **Given** the performer tries to save an empty skills list;
        
    - **When** they click "Save Changes";
        
    - **Then** the system prevents the action and prompts the user to select at least one skill.
        
- **[ ] AC 3: Feed Synchronization**
    
    - **Given** the performer has saved new categories;
        
    - **When** they navigate to the "Find Work" tab;
        
    - **Then** the list of orders should be filtered/sorted based on these new categories by default.
        


## [UC-03] Phone Number Verification

**1. Description**

- **Actor:** User (Client or Performer)
    
- **Goal:** To increase account security and trust level by linking a verified phone number.
    

**2. Main Success Scenario (Happy Path)**

1. The User enters their phone number in the Verification section.
    
2. The System sends a 6-digit SMS code to the provided number.
    
3. The User enters the received code into the verification field.
    
4. The System validates the code.
    
5. The System marks the phone number as "Verified."
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Valid Code Entry**
    
    - **Given** the user enters the correct 6-digit code within the time limit;
        
    - **When** they submit;
        
    - **Then** the account status is updated to "Phone Verified."
        
- **[ ] AC 2: Invalid Code Handling**
    
    - **Given** the user enters an incorrect or expired code;
        
    - **When** they submit;
        
    - **Then** the system displays an "Invalid Code" error and allows a retry.
        
- **[ ] AC 3: Resend Cooldown**
    
    - **Given** the user just requested a code;
        
    - **When** they try to click "Resend SMS" immediately;
        
    - **Then** the system blocks the button for 60 seconds to prevent spam.
        


## [UC-04] Portfolio / Work Samples Upload

**1. Description**

- **Actor:** Performer
    
- **Goal:** To showcase previous work results to prove competence to potential clients.
    

**2. Main Success Scenario (Happy Path)**

1. The Performer goes to the "Portfolio" tab.
    
2. The Performer uploads one or multiple images/documents.
    
3. The Performer adds a title and description for each item.
    
4. The System saves the files and displays them on the Performer's public profile.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Image Upload Limits**
    
    - **Given** the user selects a supported file format (JPG/PNG) under the size limit (e.g., 5MB);
        
    - **When** they upload;
        
    - **Then** the image is processed and displayed in the gallery.
        
- **[ ] AC 2: Unsupported File Type**
    
    - **Given** the user tries to upload an unsupported format (e.g., .exe or .zip);
        
    - **When** the file is selected;
        
    - **Then** the system shows an error message and rejects the file.
        
- **[ ] AC 3: Metadata Persistence**
    
    - **Given** the user provides a title and description for a portfolio item;
        
    - **When** the portfolio is saved;
        
    - **Then** the information must be correctly associated and displayed with that specific image.
        


## [UC-05] Client Order History Review

**1. Description**

- **Actor:** Client
    
- **Goal:** To view past activity and reuse previous order templates for efficiency.
    

**2. Main Success Scenario (Happy Path)**

1. The Client navigates to the "My Orders" section.
    
2. The System displays a list of orders categorized by status (Completed, Cancelled, In Progress).
    
3. The Client clicks on a past order to see details.
    
4. The Client clicks "Duplicate" to create a new order based on the old one.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: List Filtering**
    
    - **Given** the client has multiple orders in different states;
        
    - **When** they select the "Completed" filter;
        
    - **Then** only finished jobs are shown in the list.
        
- **[ ] AC 2: Template Duplication**
    
    - **Given** a client chooses a past order;
        
    - **When** they click "Re-post/Duplicate";
        
    - **Then** the system opens a new order form pre-filled with the original title, description, and category.
        


## [UC-06] Role Switching (Dual Profile)

**1. Description**

- **Actor:** User
    
- **Goal:** To switch between "Client" and "Performer" modes without logging out.
    

**2. Main Success Scenario (Happy Path)**

1. The User clicks on the profile menu.
    
2. The User selects the "Switch to Performer" (or Client) toggle.
    
3. The System changes the interface (navigation bar, dashboard widgets) to match the selected role.
    
4. The User continues using the app with the selected role's permissions.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: UI Transformation**
    
    - **Given** the user is currently in "Client" mode;
        
    - **When** they toggle to "Performer";
        
    - **Then** the "Post a Job" button is replaced by "Find Work" or similar performer-centric navigation.
        
- **[ ] AC 2: State Persistence**
    
    - **Given** the user switches roles;
        
    - **When** they refresh the page or restart the app;
        
    - **Then** the system must remember the last active role.
        

## [UC-07] Identity Verification (KYC - Level 2)

**1. Description**

- **Actor:** Performer
    
- **Goal:** To obtain a "Verified" badge and unlock high-budget orders by providing legal ID.
    

**2. Main Success Scenario (Happy Path)**

1. The Performer navigates to "Trust & Verification."
    
2. The Performer uploads a photo of a government-issued ID.
    
3. The Performer takes a "selfie" for face matching.
    
4. The System (or Admin) reviews the documents.
    
5. The System grants "Level 2" status and adds a badge to the profile.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Submission Flow**
    
    - **Given** the user provides all required documents;
        
    - **When** they submit for review;
        
    - **Then** the status changes to "Pending Verification," and the user is notified.
        
- **[ ] AC 2: Rejection Handling**
    
    - **Given** the ID photo is blurry or invalid;
        
    - **When** the admin rejects the verification;
        
    - **Then** the user receives a notification with a specific reason and an option to resubmit.
        


## [UC-08] Notification Preferences

**1. Description**

- **Actor:** User
    
- **Goal:** To control how and when they receive alerts about platform activity.
    

**2. Main Success Scenario (Happy Path)**

1. The User goes to "Settings" -> "Notifications."
    
2. The User toggles specific alerts (e.g., New Messages: ON, Order Updates: ON, Marketing: OFF).
    
3. The User selects the channel (Push, Email, or SMS).
    
4. The System saves the preferences.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Granular Control**
    
    - **Given** the user disables "Email Notifications" for "Marketing";
        
    - **When** a marketing campaign is sent;
        
    - **Then** the user should not receive an email but may still receive Push notifications if enabled.
        
- **[ ] AC 2: Instant Application**
    
    - **Given** a user changes a setting;
        
    - **When** an event occurs immediately after;
        
    - **Then** the system must respect the new settings without requiring a re-login.
