# 06 — Printer Deployment

## What Was Built and Why

For this section, I deployed a printer and assigned it the right. Although it is a simple and straightforward access requirement, it is also a useful place to practice the same least-privilege and group-based access patterns that is used everywhere else within the project. 

A printer was added via **Print Management** as a centrally managed shared resource, rather than installed locally on individual machines. This keeps driver updates, queue management, and availability controlled from one place, instead of needing to be configured separately on every workstation that needs it.

![Printer added in Print Management](./screenshots/printer-management.png)


The permission on the printer was scoped to **Print only**, and granted to members of `SG-HR-Users`. Also, the print permission is deliberately the only permission that has been granted. Both **Manage Documents** (which would let users to view and manage other people's queued print jobs) and **Manage Printer** (which would let them change the printer settings or drivers) were both deliberately left off for two reasons.

- **Queue visibility can leak sensitive information** - For example, in a scenario where the HR staff is printing out payroll for all the staff within the company. If provided with access, every staff member would be able to see job names, manage their queue entry, or infer what the contents of the document are, which could be an issue. Thus, scoping to Print-only lets the staff print their own documents while also not having the ability to view or touch anyone else's job within the queue. 
- **Printer drivers are an attack surface that can be exploited** - Manage Printer permission also includes the ability to install or change printer drivers, and a driver-level vulnerability in Windows Print Spooler is a genuine and widely documented attack vector. Thus, keeping the capabilities limited to actual IT Administrators closes off the overall risk involved with every user having access to printers

- 
![Printer Security tab showing SG-HR-Users with Print-only permission](./screenshots/printer-permissions.png)

---

## Key Lessons Learned

- **Printer permissions follow the same group-based pattern as file shares, not a separate system.** Having already built the HR share around `SG-HR-Users`, applying the same group here meant access could be reasoned about consistently across different resource types, rather than re-deciding the approach each time.
- **The three printer permission levels (Print, Manage Documents, Manage Printer) map to genuinely different risks**, and it's worth being deliberate about which one a group actually needs rather than defaulting to the broadest option that happens to work.
