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
  - [[UC-09] Job Posting (Basic Info)](#uc-09-job-posting-basic-info)
  - [[UC-10] Geolocation Tagging](#uc-10-geolocation-tagging)
  - [[UC-11] Visual Documentation (Photo Attachments)](#uc-11-visual-documentation-photo-attachments)
  - [[UC-12] Deadline Management](#uc-12-deadline-management)
  - [[UC-13] Pricing Model Selection](#uc-13-pricing-model-selection)
  - [[UC-14] Save Order as Draft](#uc-14-save-order-as-draft)
  - [[UC-15] Order Cancellation (Pre-selection)](#uc-15-order-cancellation-pre-selection)


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


## [UC-09] Job Posting (Basic Info)

**1. Description**

- **Actor:** Client
    
- **Goal:** To publish a new job opportunity with essential details to attract performers.
    

**2. Main Success Scenario (Happy Path)**

1. The Client clicks the "Post a Job" button.
    
2. The Client enters a descriptive Title, a detailed Description, and a Budget.
    
3. The Client selects a Category (e.g., Household, Delivery).
    
4. The Client clicks "Publish."
    
5. The System validates the data and makes the post visible in the public feed.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Mandatory Fields** 
    - **Given** the user leaves the Title or Budget empty;
    - **When** they click "Publish";
        
    - **Then** the system highlights the missing fields and prevents submission.
        
- **[ ] AC 2: Budget Formatting** 
    - **Given** the user enters a non-numeric value in the budget field;
    
    - **When** they attempt to submit;
        
    - **Then** the system displays a "Must be a valid number" error.
        
- **[ ] AC 3: Feed Visibility** 
    - **Given** a successful publication;
    
    - **When** any Performer refreshes the feed;
        
    - **Then** the new job appears at the top of the list.
        

---

## [UC-10] Geolocation Tagging

**1. Description**

- **Actor:** Client
    
- **Goal:** To specify the physical location of the task so local performers can find it.
    

**2. Main Success Scenario (Happy Path)**

1. During the job creation process, the Client clicks "Set Location."
    
2. The Client either types an address or selects their current GPS position.
    
3. The System displays the location on a map preview.
    
4. The Client confirms the location.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Address Autocomplete** 
    - **Given** the user starts typing an address;
    
    - **When** they have typed at least 3 characters;
        
    - **Then** the system provides a list of suggested addresses.
        
- **[ ] AC 2: Manual Pin Placement** 
    - **Given** the user is on the map view;
    
    - **When** they click a specific spot on the map;
        
    - **Then** the system updates the coordinates to that specific location.
        

---

## [UC-11] Visual Documentation (Photo Attachments)

**1. Description**

- **Actor:** Client
    
- **Goal:** To provide visual context for the task (e.g., a photo of a broken faucet or a package to be delivered).
    

**2. Main Success Scenario (Happy Path)**

1. The Client clicks "Add Photos" on the job creation screen.
    
2. The Client selects images from their device or takes a new photo via camera.
    
3. The System uploads the files and shows thumbnails.
    
4. The Client publishes the job with the attached photos.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Multiple Uploads** 
    - **Given** a user wants to show different angles;
    
    - **When** they select up to 5 images;
        
    - **Then** the system should handle the bulk upload and display all thumbnails.
        
- **[ ] AC 2: Attachment Removal** 
    - **Given** a user uploaded the wrong photo by mistake;
    
    - **When** they click the "X" on the thumbnail;
        
    - **Then** the file is removed from the draft immediately.
        

---

## [UC-12] Deadline Management

**1. Description**

- **Actor:** Client
    
- **Goal:** To set a time limit for when the task must be completed.
    

**2. Main Success Scenario (Happy Path)**

1. The Client selects a Date and Time using a picker.
    
2. The Client labels the deadline (e.g., "ASAP" or "Scheduled").
    
3. The System displays the "Time Remaining" to potential performers.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Past Date Prevention** 
    - **Given** the user opens the date picker;
    
    - **When** they try to select a date in the past;
        
    - **Then** the system must disable those dates and prevent selection.
        
- **[ ] AC 2: Short-term Warning** 
    - **Given** a user sets a deadline within 1 hour;
    
    - **When** they click save;
        
    - **Then** the system flags the order as "Urgent" in the feed.
        

---

## [UC-13] Pricing Model Selection

**1. Description**

- **Actor:** Client
    
- **Goal:** To choose between a fixed payment or allowing performers to bid their own price.
    

**2. Main Success Scenario (Happy Path)**

1. The Client toggles between "Fixed Price" and "Open for Offers."
    
2. The Client enters a starting price/limit.
    
3. The System adjusts the "Apply" button for performers (either "Accept Price" or "Make a Bid").
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Bidding Range** 
    - **Given** "Open for Offers" is selected;
    
    - **When** the job is published;
        
    - **Then** the UI must clearly show "Negotiable" to the performers.
        

---

## [UC-14] Save Order as Draft

**1. Description**

- **Actor:** Client
    
- **Goal:** To save progress on a complex job description without publishing it immediately.
    

**2. Main Success Scenario (Happy Path)**

1. The Client fills out some fields in the job form.
    
2. The Client clicks "Save as Draft."
    
3. The System stores the information in the "My Drafts" section.
    
4. The Client returns later to finish and publish.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Data Persistence** 
    - **Given** a user has a saved draft;
    
    - **When** they close the app and return;
        
    - **Then** all previously entered text and settings must be restored.
        
- **[ ] AC 2: Draft Expiration** 
    - **Given** a draft hasn't been touched for 30 days;
    
    - **When** the system runs a cleanup;
        
    - **Then** the draft is removed to save storage.
        

---

### [UC-15] Order Cancellation (Pre-selection)

**1. Description**

- **Actor:** Client
    
- **Goal:** To remove a job posting if it's no longer needed, provided no performer has been hired yet.
    

**2. Main Success Scenario (Happy Path)**

1. The Client opens their active job posting.
    
2. The Client clicks "Cancel Order."
    
3. The System asks for a reason (optional).
    
4. The System removes the job from the public feed.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: State Restriction** 
    - **Given** a performer has already been hired;
    
    - **When** the client tries to cancel;
        
    - **Then** the system redirects them to the "Dispute/Cancel Agreement" flow instead of simple deletion.

### [UC-31] Withdraw Application

**1. Description**

- **Actor:** Performer
    
- **Goal:** To cancel an application if they are no longer available or interested.
    

**2. Main Success Scenario (Happy Path)**

1. The Performer goes to their "Applications" list.
    
2. The Performer clicks "Withdraw" on a pending application.
    
3. The System asks for confirmation.
    
4. The System removes the application and deletes the entry from the Client's applicant list.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Removal from Client View**
    
    - **Given** the performer withdraws;
        
    - **When** the client refreshes their applicant list;
        
    - **Then** that performer's entry must no longer be visible.
        
- **[ ] AC 2: Hire State Restriction**
    
    - **Given** the client has already clicked "Hire" (status is In Progress);
        
    - **When** the performer tries to withdraw;
        
    - **Then** the button should be disabled (must use "Cancel Order" flow instead).
        

---

### [UC-32] Real-time Status: "Heading There"

**1. Description**

- **Actor:** Performer / Client
    
- **Goal:** To inform the client that the performer has started traveling to the job site.
    

**2. Main Success Scenario (Happy Path)**

1. The Performer opens the active job.
    
2. The Performer clicks "On my way."
    
3. The System updates the status for the Client.
    
4. The Client sees an "In Transit" status and an estimated time of arrival (if GPS is enabled).
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Visual Indicator**
    
    - **Given** the performer clicks "On my way";
        
    - **When** the client views the job;
        
    - **Then** a status badge "Performer is En Route" must be visible.
        
- **[ ] AC 2: Timestamp Logging**
    
    - **Given** the status change occurs;
        
    - **When** the system saves the update;
        
    - **Then** it must log the exact time the travel started for dispute resolution purposes.


### [UC-33] Secure In-App Messaging

**1. Description**

- **Actor:** User (Client or Performer)
    
- **Goal:** To communicate safely within the platform without sharing personal phone numbers or messengers.
    

**2. Main Success Scenario (Happy Path)**

1. The User opens an active order.
    
2. The User clicks "Open Chat."
    
3. The User types a message and clicks "Send."
    
4. The System delivers the message instantly to the recipient.
    
5. The System stores the chat history for future reference or dispute resolution.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Real-time Delivery**
    
    - **Given** both users are online;
        
    - **When** a message is sent;
        
    - **Then** it must appear in the recipient's chat window within 1 second.
        
- **[ ] AC 2: Privacy Protection**
    
    - **Given** the chat is active;
        
    - **When** a user tries to find the other's phone number or email;
        
    - **Then** the system must keep that data hidden unless a user explicitly shares it in text.
        
- **[ ] AC 3: Attachment Support**
    
    - **Given** the user is in the chat;
        
    - **When** they click the "Paperclip" icon;
        
    - **Then** they must be able to select and send a file or image from their device.
        

---

### [UC-34] Progress Photo Documentation

**1. Description**

- **Actor:** Performer
    
- **Goal:** To send photos of the work-in-progress or the final result to the client for transparency.
    

**2. Main Success Scenario (Happy Path)**

1. The Performer opens the job chat or "Active Order" screen.
    
2. The Performer takes a photo of the completed task.
    
3. The Performer adds a caption (e.g., "Faucet fixed").
    
4. The System uploads the photo and notifies the Client.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Proof of Work**
    
    - **Given** the performer is at the location;
        
    - **When** they upload a photo through the app;
        
    - **Then** the system should automatically tag the photo with a timestamp.
        
- **[ ] AC 2: Resolution Optimization**
    
    - **Given** the user uploads a high-res photo;
        
    - **When** the system processes it;
        
    - **Then** it should be compressed to save mobile data while maintaining legible quality.
        

---

### [UC-35] "Work Started" Trigger

**1. Description**

- **Actor:** Performer
    
- **Goal:** To formally signal that they have arrived and are beginning the task.
    

**2. Main Success Scenario (Happy Path)**

1. The Performer arrives at the job site.
    
2. The Performer clicks "Start Working."
    
3. The System records the start time.
    
4. The System updates the status for the Client to "In Progress."
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Proximity Check**
    
    - **Given** the job has a specific location;
        
    - **When** the performer clicks "Start Working" but is more than 500m away;
        
    - **Then** the system should prompt "Are you sure you are at the location?".
        
- **[ ] AC 2: Client Notification**
    
    - **Given** the status changes;
        
    - **When** the system updates;
        
    - **Then** the client must receive a push notification: "[Performer] has started the task."
        

---

### [UC-36] "Task Completed" Declaration

**1. Description**

- **Actor:** Performer
    
- **Goal:** To notify the client that the work is finished and they are ready to be paid.
    

**2. Main Success Scenario (Happy Path)**

1. The Performer finishes the work.
    
2. The Performer clicks "Mark as Completed."
    
3. The System prompts the performer to attach a final result photo.
    
4. The System changes the status to "Pending Client Approval."
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Final Step Requirement**
    
    - **Given** the performer clicks "Completed";
        
    - **When** they have not attached a required photo (if specified by the client);
        
    - **Then** the system should remind them to add a photo before finalizing.
        

---

### [UC-37] Job Approval (Closure)

**1. Description**

- **Actor:** Client
    
- **Goal:** To confirm they are satisfied with the result and officially close the order.
    

**2. Main Success Scenario (Happy Path)**

1. The Client receives a "Task Completed" notification.
    
2. The Client inspects the work (or the uploaded proof).
    
3. The Client clicks "Confirm & Release Payment."
    
4. The System changes the status to "Completed" and triggers the payment release.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Irreversibility**
    
    - **Given** the client clicks "Confirm";
        
    - **When** the action is saved;
        
    - **Then** the order cannot be moved back to "In Progress" without support intervention.
        

---

### [UC-38] Revision Request (Rework)

**1. Description**

- **Actor:** Client
    
- **Goal:** To ask the performer to fix specific issues before the payment is released.
    

**2. Main Success Scenario (Happy Path)**

1. The Client reviews the "Completed" task but finds an issue.
    
2. The Client clicks "Request Revision."
    
3. The Client types what needs to be fixed.
    
4. The System puts the job back into "In Progress" and notifies the Performer.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Specificity Requirement**
    
    - **Given** the client selects "Revision";
        
    - **When** they try to submit without a comment;
        
    - **Then** the system blocks the action and asks for a description of the required changes.
        
- **[ ] AC 2: Status Visibility**
    
    - **Given** a revision is requested;
        
    - **When** the performer views the job;
        
    - **Then** the status must be highlighted as "Needs Attention" or "Rework Requested."
        

---

### [UC-39] Message Read Receipts

**1. Description**

- **Actor:** User
    
- **Goal:** To know if their message has been seen by the other party to manage expectations.
    

**2. Main Success Scenario (Happy Path)**

1. User A sends a message to User B.
    
2. User B opens the chat and views the message.
    
3. The System updates the status of the message to "Read" (e.g., double checkmarks).
    
4. User A sees the "Read" indicator.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Visual Feedback**
    
    - **Given** a message is delivered but not opened;
        
    - **When** the sender views the chat;
        
    - **Then** the system shows a "Delivered" icon.
        
- **[ ] AC 2: State Synchronization**
    
    - **Given** User B opens the app on a different device (laptop vs mobile);
        
    - **When** they read the message;
        
    - **Then** the status must update across all platforms for the sender.
        

---

### [UC-40] No-Response Alert (Inactivity)

**1. Description**

- **Actor:** System
    
- **Goal:** To detect when a performer or client is ignoring messages during an active order and escalate the issue.
    

**2. Main Success Scenario (Happy Path)**

1. A message is sent by the Client during an "In Progress" job.
    
2. The System detects that the Performer hasn't opened the chat for 4 hours.
    
3. The System sends a reminder push notification to the Performer.
    
4. The System notifies the Client that they can contact support if the delay continues.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Automatic Trigger**
    
    - **Given** the 4-hour window has passed without activity;
        
    - **When** the system background worker runs;
        
    - **Then** a "Gentle Reminder" notification is sent to the inactive party.
        
- **[ ] AC 2: Escalation Path**
    
    - **Given** inactivity lasts for 12 hours;
        
    - **When** the system detects this;
        
    - **Then** a "Report Issue" button must be prominently displayed to the active party.


### [UC-41] Payment Method Integration

**1. Description**

- **Actor:** Client
    
- **Goal:** To securely link a credit/debit card to the account for seamless job payments.
    

**2. Main Success Scenario (Happy Path)**

1. The Client navigates to "Wallet" -> "Add Payment Method."
    
2. The Client enters card details (Number, Expiry, CVV).
    
3. The System performs a test transaction (e.g., $0.00 or $1.00 authorization) via a payment gateway.
    
4. The System saves a secure token representing the card (not the actual card number).
    
5. The Client sees the card in their list of payment methods.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Successful Tokenization**
    
    - **Given** the card details are valid and pass the 3D-Secure check;
        
    - **When** the user clicks "Save Card";
        
    - **Then** the system must store a payment token and display the last 4 digits of the card.
        
- **[ ] AC 2: Invalid Card Handling**
    
    - **Given** an expired card or incorrect CVV;
        
    - **When** the authorization fails;
        
    - **Then** the system must display the specific error from the payment provider and not save the card.
        

---

### [UC-42] Escrow Fund Reservation (Secure Deal)

**1. Description**

- **Actor:** System / Client
    
- **Goal:** To "freeze" the job funds on the Client's card when a Performer is hired, ensuring the money is available for the Performer upon completion.
    

**2. Main Success Scenario (Happy Path)**

1. The Client clicks "Hire" on a specific Performer.
    
2. The System calculates the Total (Price + Service Fee).
    
3. The System requests a "Hold" from the payment gateway.
    
4. The System notifies the Performer that the funds are secured.
    
5. The job status moves to "In Progress."
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Insufficient Funds**
    
    - **Given** the Client's card is declined due to a lack of funds;
        
    - **When** the "Hire" action is triggered;
        
    - **Then** the system must block the hiring process and prompt the Client to use a different card.
        
- **[ ] AC 2: State Persistence**
    
    - **Given** the funds are on hold;
        
    - **When** the job is active;
        
    - **Then** neither the Client nor the Performer can access the money until the job is "Completed" or "Cancelled."
        

---

### [UC-43] Performer Wallet Balance

**1. Description**

- **Actor:** Performer
    
- **Goal:** To track total earnings, pending payments, and available funds for withdrawal.
    

**2. Main Success Scenario (Happy Path)**

1. The Performer navigates to the "Wallet" or "Earnings" section.
    
2. The System displays three balances: "Pending" (In-progress jobs), "Cleared" (Completed, waiting for payout), and "Total Earned."
    
3. The Performer views a summary of recent earnings.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Real-time Update**
    
    - **Given** a Client approves a job;
        
    - **When** the Performer opens the Wallet;
        
    - **Then** the amount must move from "Pending" to "Cleared" immediately.
        
- **[ ] AC 2: Currency Consistency**
    
    - **Given** the platform operates in a specific region;
        
    - **When** the wallet is displayed;
        
    - **Then** all amounts must be formatted according to the local currency (e.g., $ or â¬) and locale.
        

---

### [UC-44] Payout Request (Withdrawal)

**1. Description**

- **Actor:** Performer
    
- **Goal:** To transfer cleared earnings from the platform wallet to a personal bank account.
    

**2. Main Success Scenario (Happy Path)**

1. The Performer clicks "Withdraw Funds."
    
2. The Performer enters the amount and selects a saved bank account.
    
3. The System validates that the Performer has enough "Cleared" funds.
    
4. The System initiates the transfer and updates the Wallet balance.
    
5. The Performer receives a "Withdrawal Initiated" email.
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Minimum Withdrawal Limit**
    
    - **Given** the user tries to withdraw $2 while the minimum is $10;
        
    - **When** they click "Withdraw";
        
    - **Then** the system must block the action and show the minimum requirement.
        
- **[ ] AC 2: Fraud Check Delay**
    
    - **Given** a large withdrawal request;
        
    - **When** the request is submitted;
        
    - **Then** the system should flag it for "Admin Review" and set the status to "Pending Review" instead of "Processed."
        

---

### [UC-45] Transaction History and Receipts

**1. Description**

- **Actor:** User
    
- **Goal:** To have a clear, auditable record of all financial activity on the platform.
    

**2. Main Success Scenario (Happy Path)**

1. The User opens "Transaction History."
    
2. The System displays a list of all payments, holds, and withdrawals.
    
3. The User clicks on a specific entry.
    
4. The System provides a detailed breakdown (Job ID, Date, Amount, Fees, Tax).
    
5. The User clicks "Download PDF Receipt."
    

**3. Acceptance Criteria (AC)**

- **[ ] AC 1: Search and Filter**
    
    - **Given** a user has hundreds of transactions;
        
    - **When** they filter by "Date Range";
        
    - **Then** the list should update to show only the relevant entries.
        
- **[ ] AC 2: Accurate Fee Breakdown**
    
    - **Given** a job payment;
        
    - **When** viewing the receipt;
        
    - **Then** it must clearly separate the Job Price from the Platform Service Fee.
