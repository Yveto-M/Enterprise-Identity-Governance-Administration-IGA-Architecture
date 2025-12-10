# 🛡️ Enterprise Identity Governance & Administration (IGA) Architecture
### Automated Just-In-Time (JIT) Access & Lifecycle Management

## 🚀 Executive Summary
In modern Zero Trust environments, "Standing Access" (permanent permissions) is a primary vulnerability. To mitigate this, I architected an **Automated Governance Framework** using **Microsoft Entra ID Governance** (formerly Azure AD).

This project replaces manual ticket processing with a **Self-Service JIT Workflow** that allows IT personnel to request temporary, privileged access to sensitive Finance resources. The solution enforces **Segregation of Duties (SoD)**, mandates **Business Justification**, and executes a strict **7-Day Eviction Policy** to ensure Least Privilege compliance (NIST 800-53, AC-2).

---

## ⚡ Key Features Implemented
* **Segregation of Duties (SoD):** Access requests are strictly scoped to the "IT Team," preventing unauthorized departments (HR, Sales) from even seeing the package.
* **Just-In-Time (JIT) Access:** Permissions are hard-coded to expire after 7 days, eliminating privilege creep.
* **Audit-Ready Workflows:** Mandatory "Business Justification" capture for every request.
* **Human-in-the-Loop:** Automated provisioning is paused until a Manager/Admin explicitly approves the request.

---

## 📸 Architecture & Configuration

### Phase 1: Policy Definition (The "Gatekeeper")
I configured the **Access Package** to enforce strict entry requirements.
* **Requester Scope:** Limited specifically to the `IT Team` security group.
* **Approval:** Required (Single Stage).
* **Justification:** Mandatory.

<img width="468" height="685" alt="Requests tab showing-1" src="https://github.com/user-attachments/assets/ca7b7a61-f9c7-4f94-9c6a-c30fb53f03f2" />
*Figure 1: Configuring the "Requests" policy to restrict access to IT Team members only.*

---

### Phase 2: Lifecycle & Eviction (The "Time Bomb")
To prevent "Digital Hoarding," I implemented a rigid expiration policy.
* **Expiration:** 7 Days.
* **Access Reviews:** Enabled weekly to ensure ongoing compliance.

![Lifecycle Tab Configuration](Lifecycle tab showing-2.png)
*Figure 2: JIT Policy Settings showing the 7-day auto-expiration rule.*

---

## 🧪 Operational Workflow (User Experience)

### Step 1: Self-Service Request
The IT user (`Joseph Thomas`) logs into the MyAccess portal. The "Finance Audit" package is visible only because he is a verified member of the IT Team.

![My Access Portal](Screenshot 2025-12-10 135310.png)
*Figure 3: The targeted Access Package appearing in the user's portal.*

### Step 2: Audit Capture
The user must provide a valid business reason (`Urgent Audit for Ticket #999`) to proceed. This data is logged for future audits.

![Request Form](Self-Service Request Portal-3.png)
*Figure 4: Enforcing mandatory business justification before submission.*

### Step 3: Administrative Approval
The request triggers a notification to the Identity Administrator. Access is **not** granted until this approval step is completed.

![Approval Screen](JT-approved-4.png)
*Figure 5: The Administrator's view showing the successful approval of the request.*

---

## ✅ Verification & Results

### automated Provisioning
Immediately upon approval, the Entra ID Governance engine automatically injected the user into the `Finance Team` security group. No manual intervention was required.

![Finance Team Members](JT-added-finance-5.png)
*Figure 6: Verification that Joseph Thomas was added to the Finance Team group.*

### JIT Policy Enforcement
The system stamped a hard expiration date on the assignment. On **12/17/2025**, the user will be automatically removed, ensuring the environment returns to a secure state.

![Assignment Expiration](Entitlement management Assignments-6.png)
*Figure 7: The "Assignments" log proving the access is time-bound (Expires 12/16/2025).*

---

## 🏆 Project Outcome
* **Risk Reduction:** Reduced the attack surface by moving 100% of ad-hoc administrative access to a time-bound model.
* **Efficiency:** Reduced IT ticket resolution time by enabling self-service requests.
* **Compliance:** Achieved readiness for **NYS DFS Part 500** and **SOX** audits by ensuring all privileged access is documented, justified, and temporary.
