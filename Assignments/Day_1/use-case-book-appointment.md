## **📝 Use Case: Receptionist Books an Appointment for a High-Risk Patient**

---

### **Use Case ID:** UC-001

### **Use Case Name:** Book Appointment for High-Risk Patient

---

## **👤 Actor**
**Receptionist** (Sarah - Front desk staff at Dr. Sarah's GP Surgery)

---

## **✅ Precondition**
(What must be true **before** this process starts)

1. Receptionist is logged into Salesforce
2. Patient record already exists in the system (Contact object)
3. Patient has been flagged as high-risk (High_Risk__c = True)
4. At least one appointment slot is available for the requested date/time
5. Receptionist has permission to create Appointment records

---

## **⚡ Trigger**
(What **starts** this process)

**Patient calls the surgery and requests an appointment**

*Example:* "Hello, this is Mrs. Johnson. I need to book an appointment for next Tuesday at 2 PM."

---

## **📋 Steps**
(Main flow - everything goes smoothly)

### **Step 1:** Receptionist answers the phone and identifies the patient
- Patient provides name: "Mrs. Elizabeth Johnson"
- Receptionist confirms identity (date of birth, address)

### **Step 2:** Receptionist searches for patient record in Salesforce
- Navigate to **Contacts** tab
- Search for "Elizabeth Johnson"
- Open the patient's Contact record

### **Step 3:** Receptionist notices the high-risk flag
- Contact record displays: **High Risk Flag = ☑ Checked**
- High Risk Reason shows: "Diabetic, elderly (78 years old)"
- Receptionist makes a mental note to prioritize this appointment

### **Step 4:** Receptionist checks appointment availability
- Navigate to **Appointments** tab
- Filter by: **Appointment Date = Next Tuesday (2025-10-21)**
- Check if 2:00 PM slot is available (no existing appointment at that time)

### **Step 5:** Receptionist confirms availability with patient
- "Yes, Mrs. Johnson, we have a slot available on Tuesday, October 21st at 2:00 PM with Dr. Sarah. Would that work for you?"
- Patient confirms: "Yes, that's perfect."

### **Step 6:** Receptionist creates new Appointment record
- Click **New** button on Appointments object
- Fill in fields:
  - **Patient:** Elizabeth Johnson (lookup to Contact)
  - **Appointment Date:** 2025-10-21
  - **Appointment Time:** 14:00
  - **Status:** Scheduled (default value)
  - **Doctor Name:** Dr. Sarah

### **Step 7:** Receptionist adds notes about high-risk status (optional)
- In the **Notes** field (if available), add: "High-risk patient - diabetic, elderly. Please allow extra time."

### **Step 8:** Receptionist saves the appointment
- Click **Save**
- Salesforce creates the Appointment record with a unique Appointment Name (e.g., APT-00001)

### **Step 9:** Receptionist confirms appointment details with patient
- "All set, Mrs. Johnson. Your appointment is confirmed for Tuesday, October 21st at 2:00 PM with Dr. Sarah. Please arrive 10 minutes early."

### **Step 10:** Receptionist ends the call
- Patient thanks receptionist and hangs up
- Receptionist moves on to next task

---

## **✅ Postcondition**
(What is **true** after this process completes)

1. New Appointment record exists in Salesforce with Status = "Scheduled"
2. Appointment is linked to patient's Contact record (visible in Related List)
3. Appointment appears in the surgery's calendar/list view for October 21st at 2:00 PM
4. Dr. Sarah can see the appointment when she reviews her schedule
5. The 2:00 PM slot is no longer available for other patients (prevents double-booking)
6. Patient has a confirmed appointment and knows when to arrive

---

## **⚠️ Alternative Flow**
(What happens if something goes **wrong**)

---

### **Alternative Flow 1: Double-Booking Detected**

**Trigger:** At **Step 6**, when receptionist tries to save the appointment, Salesforce detects another appointment already exists for the same date/time with the same doctor.

**Steps:**

1. **Salesforce displays error message:**
   - "Error: An appointment already exists for Dr. Sarah on 2025-10-21 at 14:00. Please choose a different time."

2. **Receptionist acknowledges the error:**
   - "I'm sorry, Mrs. Johnson, it looks like that slot was just booked by another receptionist. Let me check other available times."

3. **Receptionist checks alternative times:**
   - Filter Appointments by date: 2025-10-21
   - Identify available slots: 10:00 AM, 3:00 PM, 4:30 PM

4. **Receptionist offers alternatives:**
   - "We have slots available at 10:00 AM, 3:00 PM, or 4:30 PM. Which would work best for you?"

5. **Patient chooses alternative:**
   - "I'll take the 3:00 PM slot."

6. **Receptionist creates appointment with new time:**
   - Update **Appointment Time:** 15:00 (3:00 PM)
   - Click **Save**
   - Appointment is successfully created

7. **Return to Step 9** (confirm appointment details with patient)

---

### **Alternative Flow 2: Patient Record Not Found**

**Trigger:** At **Step 2**, receptionist cannot find patient record in Salesforce.

**Steps:**

1. **Receptionist searches multiple times:**
   - Search by name: "Elizabeth Johnson" - no results
   - Search by phone number - no results

2. **Receptionist informs patient:**
   - "Mrs. Johnson, I don't see your record in our system. Are you a new patient, or have you been here before?"

3. **Patient responds:**
   - "I've been coming here for 10 years!"

4. **Receptionist realizes data migration issue:**
   - Patient record may not have been migrated from old paper system

5. **Receptionist creates new patient record:**
   - Navigate to **Contacts** tab
   - Click **New**
   - Fill in patient details:
     - First Name: Elizabeth
     - Last Name: Johnson
     - Date of Birth: 1947-03-15
     - Phone: 07700 900456
     - High Risk Flag: ☑ Checked
     - High Risk Reason: "Diabetic, elderly"
   - Click **Save**

6. **Return to Step 4** (check appointment availability)

---

### **Alternative Flow 3: No Slots Available**

**Trigger:** At **Step 4**, receptionist finds no available slots for the requested date/time.

**Steps:**

1. **Receptionist checks availability:**
   - All slots on 2025-10-21 are fully booked

2. **Receptionist informs patient:**
   - "I'm sorry, Mrs. Johnson, we're fully booked on Tuesday. However, because you're a high-risk patient, let me check if we can fit you in."

3. **Receptionist escalates to senior receptionist or practice manager:**
   - "We have a high-risk patient (diabetic, elderly) requesting an appointment. Can we add an extra slot?"

4. **Manager approves emergency slot:**
   - "Yes, add her at 1:30 PM - we'll squeeze her in."

5. **Receptionist offers emergency slot:**
   - "Good news, Mrs. Johnson. We can fit you in at 1:30 PM on Tuesday."

6. **Patient accepts:**
   - "Thank you so much!"

7. **Return to Step 6** (create appointment with 1:30 PM time)

---

### **Alternative Flow 4: Patient Requests Unavailable Doctor**

**Trigger:** At **Step 5**, patient requests a specific doctor who is not available.

**Steps:**

1. **Patient requests specific doctor:**
   - "Can I see Dr. Patel instead of Dr. Sarah?"

2. **Receptionist checks Dr. Patel's schedule:**
   - Dr. Patel is on holiday that week

3. **Receptionist informs patient:**
   - "I'm sorry, Dr. Patel is on holiday that week. Dr. Sarah is available, or we can book you for the following week when Dr. Patel returns."

4. **Patient decides:**
   - Option A: "I'll see Dr. Sarah" → Return to **Step 6**
   - Option B: "I'll wait for Dr. Patel" → Receptionist checks next week's availability and returns to **Step 4**

---

## **📊 Summary Table**

| **Element** | **Details** |
|-------------|-------------|
| **Actor** | Receptionist (Sarah) |
| **Precondition** | Patient exists in system, flagged as high-risk, slots available, receptionist has permissions |
| **Trigger** | Patient calls requesting appointment |
| **Main Steps** | 10 steps: Identify patient → Search record → Notice high-risk flag → Check availability → Confirm → Create appointment → Add notes → Save → Confirm with patient → End call |
| **Postcondition** | Appointment created, linked to patient, slot reserved, patient confirmed |
| **Alternative Flows** | 4 scenarios: Double-booking, patient not found, no slots available, doctor unavailable |

---

## **✅ Key Takeaways**

### **What Makes This a Good Use Case:**

1. ✅ **Clear actor** (Receptionist)
2. ✅ **Specific preconditions** (patient exists, high-risk flag set)
3. ✅ **Defined trigger** (patient calls)
4. ✅ **Detailed steps** (10 steps with specific actions)
5. ✅ **Clear postcondition** (appointment created and confirmed)
6. ✅ **Multiple alternative flows** (handles errors and edge cases)

---

## **🎯 How This Relates to Salesforce Design**

| Use Case Element | Salesforce Feature Needed |
|------------------|---------------------------|
| "Search for patient" | Contact object with search functionality |
| "Notice high-risk flag" | High_Risk__c checkbox field on Contact |
| "Check availability" | Appointment__c object with Date/Time fields + List View |
| "Prevent double-booking" | Validation rule on Appointment__c (check for duplicates) |
| "Create appointment" | Appointment__c custom object with fields |
| "Link to patient" | Lookup relationship: Appointment__c → Contact |

---

**This is exactly what you'd present in an interview! Does this help? 💪**