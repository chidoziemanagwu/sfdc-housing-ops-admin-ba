📝 **Day 2 Assignment**  
**Scenario: GP Surgery System (Building on Day 1)**  

**Context:**  
Yesterday you designed the data model for a GP Surgery. Today, you'll build it in Salesforce.

---

### **Task 1: Create Custom Objects**  
Build these 3 custom objects *(Remember to enable Object Classification settings for each!)*:

#### **1. `GP_Appointment__c`**  
**Object Settings:**  
- **Label:** Appointment  
- **Plural Label:** Appointments  
- **Object Name:** GP_Appointment  
- **Record Name:** Appointment Number  
  - **Data Type:** Auto Number  
  - **Display Format:** `APT-{0000}`  
  - **Starting Number:** 1  
- **Allow Reports:** ✅ Checked  
- **Allow Activities:** ✅ Checked  

**Optional Features:**  
✅ Allow in Chatter Groups  

**Object Classification:**  
✅ Allow Sharing  
✅ Allow Bulk API Access  
✅ Allow Streaming API Access  

**Fields:**  
- `Patient__c` (Lookup to Contact) – **Required**  
- `GP__c` (Lookup to User) – **Required**  
- `Appointment_Date__c` (Date/Time) – **Required**  
- `Appointment_Type__c` (Picklist: Face-to-Face, Telephone, Video, Home Visit) – **Default:** Face-to-Face  
- `Status__c` (Picklist: Scheduled, Confirmed, Completed, Cancelled, No-Show) – **Default:** Scheduled  
- `Duration_Minutes__c` (Number, default 15)  
- `Reason_for_Visit__c` (Long Text Area, 3 lines)  
- `High_Risk_Patient__c` (Formula Checkbox)  
  - **Formula:** `Contact.High_Risk__c`  
  *(Assumes you added `High_Risk__c` checkbox to Contact)*  
- `Appointment_End_Time__c` (Formula Date/Time)  
  - **Formula:** `Appointment_Date__c + (Duration_Minutes__c / 1440)`  
  *(1440 = minutes in a day)*  
- `Notes__c` (Long Text Area, 4 lines)  

---

#### **2. `GP_Prescription__c`**  
**Object Settings:**  
- **Label:** Prescription  
- **Plural Label:** Prescriptions  
- **Object Name:** GP_Prescription  
- **Record Name:** Prescription Number  
  - **Data Type:** Auto Number  
  - **Display Format:** `RX-{00000}`  
  - **Starting Number:** 1  
- **Allow Reports:** ✅ Checked  

**Optional Features:**  
✅ Allow in Chatter Groups  

**Object Classification:**  
✅ Allow Sharing  
✅ Allow Bulk API Access  
✅ Allow Streaming API Access  

**Fields:**  
- `Patient__c` (Lookup to Contact) – **Required**  
- `Prescribed_By__c` (Lookup to User) – **Required**  
- `Medication_Name__c` (Text, 100) – **Required**  
- `Dosage__c` (Text, 50) – **Required**  
- `Issue_Date__c` (Date, default `TODAY()`) – **Required**  
- `Expiry_Date__c` (Date)  
- `Status__c` (Picklist: Active, Collected, Expired, Cancelled) – **Default:** Active  
- `Days_Until_Expiry__c` (Formula Number)  
  - **Formula:** `Expiry_Date__c - TODAY()`  
- `Repeat_Prescription__c` (Checkbox)  
- `Instructions__c` (Long Text Area, 3 lines)  

---

#### **3. `GP_Medical_Record__c`**  
**Object Settings:**  
- **Label:** Medical Record  
- **Plural Label:** Medical Records  
- **Object Name:** GP_Medical_Record  
- **Record Name:** Record Number  
  - **Data Type:** Auto Number  
  - **Display Format:** `MR-{000000}`  
  - **Starting Number:** 1  
- **Allow Reports:** ✅ Checked  
- **Track Field History:** ✅ Checked  

**Optional Features:**  
✅ Allow in Chatter Groups  

**Object Classification:**  
✅ Allow Sharing  
✅ Allow Bulk API Access  
✅ Allow Streaming API Access  

**Fields:**  
- `Patient__c` (Lookup to Contact) – **Required**  
- `Record_Date__c` (Date, default `TODAY()`) – **Required**  
- `Record_Type__c` (Picklist: Consultation, Test Result, Diagnosis, Referral, Vaccination) – **Required**  
- `Recorded_By__c` (Lookup to User) – **Required**  
- `Diagnosis__c` (Text, 255)  
- `Notes__c` (Long Text Area, 5 lines) – **Required**  
- `Confidential__c` (Checkbox, default checked)  
- `Related_Appointment__c` (Lookup to `GP_Appointment__c`)  

---

### **Task 2: Create Tabs**  
Create tabs for all 3 objects:  
- **Appointments** (use calendar icon)  
- **Prescriptions** (use pill/medicine icon)  
- **Medical Records** (use clipboard icon)  

---

### **Task 3: Create Custom App**  
Create a **"GP Surgery"** app with all 3 objects in the navigation.

---

### **Task 4: Configure Page Layouts**  
For each object, organize fields into logical sections (like we did for Housing objects).

---

### **Task 5: Add Related Lists**  
- **Contact page layout:** Add *Appointments*, *Prescriptions*, *Medical Records*  
- **Appointment page layout:** Add *Medical Records*

---

### **Task 6: Create Test Data**  
- Create **1 Contact (Patient)** with `High_Risk__c = TRUE`  
- Create **1 Appointment** for that patient (high-risk)  
- Create **1 Prescription**  
- Create **1 Medical Record** linked to the appointment  

---

### **Task 7: Test Your Configuration**  
Run these tests:  
- **Test Auto Numbers:** Verify `APT-0001`, `RX-00001`, `MR-000001` generate correctly  
- **Test Formula (`High_Risk_Patient`):** Verify appointment shows high-risk flag when patient is high-risk  
- **Test Formula (`Appointment_End_Time`):** Create appointment at 10:00 AM with 30-minute duration → End time should be 10:30 AM  
- **Test Formula (`Days_Until_Expiry`):** Create prescription with expiry date 7 days from now → Should show 7  
- **Test Related Lists:** Verify patient record shows all appointments, prescriptions, and medical records  

---

### **Deliverables:**  
- 📸 Screenshot: Object Manager for `GP_Appointment__c` showing all fields  
- 📸 Screenshot: Configured page layout for `GP_Appointment__c`  
- 📸 Screenshot: GP Surgery app in App Launcher with all 3 objects in navigation  
- 📸 Screenshot: One test appointment record showing:  
  - `High_Risk_Patient__c = TRUE`  
  - `Appointment_End_Time__c` calculated correctly  
- 📸 Screenshot: Contact (Patient) record showing related lists (Appointments, Prescriptions, Medical Records)  
- ✍️ **Written Answer (2–3 sentences):** Explain why Auto Number is better than Text for Appointment Number  

---

### **Bonus Challenge (Optional):**  
Add a formula field to **Contact** called `Total_Appointments__c` that counts how many appointments the patient has.  
> **Hint:** You'll need to use a **Roll-Up Summary field** (we'll cover this properly on Day 3, but try researching it!)