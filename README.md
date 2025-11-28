
AutoAssignOn – ServiceNow Auto Assignment Engine

AutoAssignOn is a ServiceNow scoped application that automatically assigns incidents based on real-time agent availability, SOW (Statement of Work) readiness, and login status.  
It ensures incidents are only routed to agents who are currently active, available, and part of the appropriate assignment group.

📦 Application: Autoassignon  
🧩 Scope: x_1876443_autoassi  
📄 Version: 1.0.0  
📝 Description: “Application to assign incidents on the basis of SOW availability”

---

🚀 Features

### 1. Intelligent Auto-Assignment Engine
The app determines the best-fit agent by checking:
- Assignment group membership  
- Login status (u_is_logged_in)  
- SOW availability (u_available_on_sow)  
- Recent activity via Last Seen timestamp  
- Notes (optional)

Code reference:
src/server/auto-assign-incident-script.js

---

2. Agent Status Tracking Table

Custom table: x_1876443_autoassi_u_agent_status

Fields:
- u_user
- u_is_logged_in
- u_available_on_sow
- u_last_seen
- u_notes

---

3. “Update My SOW Status” UI Action

A custom UI Action allowing users to update:
- Login status  
- SOW availability  
- Notes  
Also updates “Last Seen” automatically.

---

4. Cross-Scope Privileges Included
Includes permissions for:
- Reading Incident  
- Writing Incident  
- GlideRecord.setValue  

---

Architecture Overview

Incident Created → Business Rule Triggers  
→ auto-assign-incident-script.js executes  
→ Fetch agents logged in + available  
→ Select best agent  
→ Auto-assign incident  

---

Installation

### Option 1 — Import Update Set
1. Go to System Update Sets → Retrieved Update Sets
2. Upload Autoassignon.xml
3. Preview  
4. Commit  
5. Test  

---

Repository Structure

AutoAssignOn/  
│── src/server/auto-assign-incident-script.js  
│── update_sets/Autoassignon.xml  
│── docs/architecture-diagram.png (optional)  
└── README.md  

---

Technical Components
- Business rule script module  
- Scoped app metadata  
- Custom table dictionaries  
- UI Action  
- List layout  
- Cross-scope privileges  
- One API features  

---

Author
Developed by **Nishant**  
ServiceNow Administrator & Automation Enthusiast

