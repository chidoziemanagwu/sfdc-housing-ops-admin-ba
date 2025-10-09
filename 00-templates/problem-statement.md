## Problems
1. **Slow repairs triage** — Repairs agents manually log requests; no automated routing or prioritization
2. **Sensitive data access risk** — Vulnerability flags (mental health, disability, elderly) are visible to all staff; no field-level security
3. **Weak reporting** — Managers cannot see real-time KPIs (backlog, response times, complaint stages)
4. **Manual processes** — No automated alerts for high-priority repairs involving vulnerable tenants

## Goals
1. Reduce time-to-first-response for high-priority repairs by 50%
2. Implement field-level security for vulnerability data (restrict to Housing Officers only)
3. Provide real-time operational dashboards for Ops Managers
4. Automate safeguarding workflows (alerts + tasks for vulnerable tenants)

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

## Success Metrics
- 90% of high-priority repairs acknowledged within 2 hours
- Zero unauthorized access incidents to vulnerability data
- Backlog reduction: 20% within first month
- Data completeness: 95%+ for Property and Contact records
- User satisfaction: 4/5+ in post-deployment survey

## Constraints
- Synthetic data only (no real tenant data)
- No paid add-ons or AppExchange apps
- 10-day build timeline
- Dev Org limits (data storage, API calls)
