## Background
Dr. Sarah runs a GP surgery with 5,000 registered patients. Currently, they use:
- Paper forms for patient registration
- Excel spreadsheet for appointment bookings
- Separate system for prescription requests
- Email for patient complaints

## Problem
- Receptionists spend 30 minutes per day searching for patient records across systems
- Double-bookings happen 10% of the time (no real-time view of appointments)
- Prescription requests get lost in email (avg response time: 5 days)
- No way to flag high-risk patients (diabetics, elderly, etc.)


## The Goal
**Build a Salesforce system to**:
1. Centralize patient records
2. Manage appointments
3. Track prescription requests
4. Flag high-risk patients



## Success Metrics
1. Add flags for high risk patients
2. Enable real time view of appointments to reduce double bookings
3. Centralise patient records and reduce tim spent on searching for records


## Scope (In)
- **Objects:** Account (Household), Contact (Tenant), Case (Repairs/Complaints), Custom Property object
- **Service Cloud:** Record types, queues, assignment rules, email templates
- **Automation:** Record-triggered Flow (safeguarding alerts), Screen Flow (guided intake)
- **Reporting:** 6–8 KPIs, operational dashboard
- **Security:** Profiles, permission sets, field-level security, sharing rules

## Scope (Out)
- Integration with external repair scheduling systems
- Mobile app development
- Payment processing
- Contract management