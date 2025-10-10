## **📝 Day 1 Assessment: Test Your Understanding**

**Time limit:** 30–45 minutes  
**Scenario:** You're building a Salesforce system for a different use case  
**Goal:** Apply what you learned today to a new problem

---

## **🏥 Scenario: GP Surgery Patient Management System**

### **Background**
Dr. Sarah runs a GP surgery with 5,000 registered patients. Currently, they use:
- Paper forms for patient registration
- Excel spreadsheet for appointment bookings
- Separate system for prescription requests
- Email for patient complaints

### **The Problem**
- Receptionists spend 30 minutes per day searching for patient records across systems
- Double-bookings happen 10% of the time (no real-time view of appointments)
- Prescription requests get lost in email (avg response time: 5 days)
- No way to flag high-risk patients (diabetics, elderly, etc.)

### **The Goal**
Build a Salesforce system to:
- Centralize patient records
- Manage appointments
- Track prescription requests
- Flag high-risk patients

---

## **📋 Your Assignment (4 Tasks)**

### **Task 1: Write a Problem Statement (10 mins)**

Create a problem statement document that includes:
1. **Context** (current state)
2. **Problem** (pain points with metrics)
3. **Proposed Solution** (what Salesforce will do)
4. **Success Metrics** (3 measurable goals for 90 days post-launch)
5. **Scope** (what's in/out of scope for MVP)

**Deliverable:** `problem-statement-gp-surgery.md`

---

### **Task 2: Design an ERD (15 mins)**

Design an Entity Relationship Diagram with **4 objects**:

1. **Account** (GP Surgery - there's only 1, but we'll use it for reporting)
2. **Contact** (Patient)
3. **Custom Object: Appointment__c**
4. **Custom Object: Prescription_Request__c**

**For each object, list:**
- 5–7 key fields (with data types)
- Relationships (lookups) between objects

**Draw the ERD** using:
- https://app.diagrams.net/ OR
- Pen and paper (take a photo)

**Deliverable:** `ERD-GP-Surgery.png` or photo

---

### **Task 3: Define Custom Fields (10 mins)**

For the **Appointment__c** custom object, define **5 custom fields**:

Create a table with these columns:
- Field Label
- API Name
- Data Type
- Required?
- Unique?
- Default Value
- Purpose

**Example:**

| Field Label | API Name | Data Type | Required? | Unique? | Default | Purpose |
|-------------|----------|-----------|-----------|---------|---------|---------|
| Appointment Date | Appointment_Date__c | Date | Yes | No | - | Date of appointment |
| ... | ... | ... | ... | ... | ... | ... |

**Deliverable:** Table (in markdown, Excel, or Google Sheets)

---

### **Task 4: Write 1 Use Case (10 mins)**

Write **1 detailed use case** for:

**"Receptionist books an appointment for a high-risk patient"**

Include:
- **Actor:** (who is performing the action)
- **Precondition:** (what must be true before this starts)
- **Trigger:** (what starts this process)
- **Steps:** (numbered list of 8–10 steps)
- **Postcondition:** (what's true after this completes)
- **Alternative Flow:** (what happens if something goes wrong - e.g., double-booking detected)

**Deliverable:** `use-case-book-appointment.md`

---

## **✅ Submission Checklist**

When you're done, you should have:

- [ ] `problem-statement-gp-surgery.md`
- [ ] `ERD-GP-Surgery.png` (or photo)
- [ ] Custom fields table (5 fields for Appointment__c)
- [ ] `use-case-book-appointment.md`

---

## **🎯 Success Criteria**

You've mastered Day 1 if you can:

✅ Write a problem statement with measurable success metrics  
✅ Design an ERD with 4 objects and correct relationships  
✅ Define custom fields with appropriate data types  
✅ Write a detailed use case with steps and alternative flows  
✅ Identify which fields should be required/unique  
✅ Explain *why* you made each design decision

---

## **💡 Hints**

**Hint 1:** Think about relationships
- Should Appointment__c link to Contact (Patient)? → Yes (Lookup)
- Should Prescription_Request__c link to Contact? → Yes (Lookup)
- Should Appointment__c link to Prescription_Request__c? → No (they're separate processes)

**Hint 2:** High-risk patients
- Where should you store "High Risk Flag"? (Contact or Account?)
- Answer: Contact (patient-specific, just like Vulnerability Flag in Day 1)

**Hint 3:** Preventing double-bookings
- What field on Appointment__c would help detect duplicates?
- Answer: Appointment_Date__c + Appointment_Time__c (you could create a validation rule later)

**Hint 4:** Data types
- Appointment Date → Date
- Appointment Time → Time
- Appointment Status → Picklist (Scheduled, Completed, Cancelled, No-Show)
- High Risk Flag → Checkbox

---

## **⏱️ Time Check**

- **Task 1 (Problem Statement):** 10 mins
- **Task 2 (ERD):** 15 mins
- **Task 3 (Custom Fields):** 10 mins
- **Task 4 (Use Case):** 10 mins

**Total:** 45 mins

---

## **🚀 Ready? Set Your Timer and Start!**

When you're done, share your deliverables and I'll review them + give you feedback on:
- What you nailed ✅
- What needs improvement 🔧
- Whether you're ready for Day 2 🎯

**Good luck! 💪**