# Use Cases — Housing Operations

## Use Case 1: Log a Repair
**Actor:** Repairs Agent  
**Precondition:** Tenant calls with a repair request  
**Steps:**
1. Agent opens Screen Flow "Log Tenant Issue"
2. Searches for Tenant by name or phone
3. Selects associated Property
4. Chooses "Repair" as issue type
5. Enters repair details (description, urgency)
6. Submits → Case created with Repairs record type
7. Auto-acknowledgment email sent to tenant

**Outcome:** Repair logged in <2 minutes; tenant receives confirmation


## Use Case 2: Acknowledge a Complaint
**Actor:** Complaints Officer  
**Precondition:** Complaint received via email or phone  
**Steps:**
1. Officer creates Case with Complaints record type
2. Fills in complaint details (category, description)
3. Saves Case → auto-response rule triggers
4. Tenant receives acknowledgment email within 24 hours

**Outcome:** Complaint acknowledged; SLA timer starts


## Use Case 3: Escalate High-Priority Repair (Vulnerable Tenant)
**Actor:** System (automated Flow)  
**Precondition:** High-priority Repair Case created for a vulnerable tenant  
**Steps:**
1. Case saved with Priority = High AND Contact.Vulnerability_Flag__c = true
2. Record-triggered Flow fires
3. Flow creates Task: "Call tenant within 2 hours" (assigned to Housing Officer queue)
4. Flow sends email alert to Housing Officers

**Outcome:** Safeguarding alert sent; task created; response time reduced


## Use Case 4: View Vulnerable Tenant Info (Restricted)
**Actor:** Housing Officer  
**Precondition:** Officer needs to review vulnerability details  
**Steps:**
1. Officer opens Contact record
2. Vulnerability_Flag__c and Vulnerability_Reason__c fields are visible (via permission set)
3. Officer reviews details and updates if needed

**Outcome:** Sensitive data visible only to authorized users


## Use Case 5: Weekly KPI Dashboard Review
**Actor:** Ops Manager  
**Precondition:** Monday morning ops meeting  
**Steps:**
1. Manager opens "Housing Ops KPIs" dashboard
2. Reviews:
   - Open Repairs by Priority
   - Repairs by Age (0–2d, 3–7d, 8–14d, 15+d)
   - Open Complaints by Stage
   - Cases with Vulnerable Tenants
3. Drills down into high-priority backlog
4. Exports data for leadership report

**Outcome:** Real-time visibility; data-driven decisions
