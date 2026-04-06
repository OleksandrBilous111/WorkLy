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
