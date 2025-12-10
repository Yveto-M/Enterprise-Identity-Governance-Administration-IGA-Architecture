# 🛡️ Enterprise Identity Governance & Administration (IGA) Architecture
### Automated Just-In-Time (JIT) Access & Lifecycle Management

## 🚀 Executive Summary
In modern Zero Trust environments, "Standing Access" (permanent permissions) is a primary vulnerability. To mitigate this, I architected an **Automated Governance Framework** using **Microsoft Entra ID Governance**.

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

<img width="468" height="685" alt="Requests tab showing-1" src="https://github.com/user-attachments/assets/e7973ab8-37b4-49f6-a79d-425d52f34f66" />

*Figure 1: Configuring the "Requests" policy to restrict access to IT Team members only.*

---

### Phase 2: Lifecycle & Eviction (The "Time Bomb")
To prevent "Digital Hoarding," I implemented a rigid expiration policy.
* **Expiration:** 7 Days.
* **Access Reviews:** Enabled weekly to ensure ongoing compliance.

<img width="639" height="602" alt="Lifecycle tab showing-2" src="https://github.com/user-attachments/assets/fcaba44c-1e80-4a4c-8220-efd029bd9ddc" />

*Figure 2: JIT Policy Settings showing the 7-day auto-expiration rule.*

---

## 🧪 Operational Workflow (User Experience)

### Step 1: Self-Service Request & Audit Capture
The IT user (`Joseph Thomas`) logs into the MyAccess portal. He must provide a valid business reason (`Urgent Audit for Ticket #999`) to proceed. This data is logged for future audits.

<img width="490" height="456" alt="Self-Service Request Portal-3" src="https://github.com/user-attachments/assets/4cd9473d-ed8c-462c-bb29-e056f45a799e" />

*Figure 3: Enforcing mandatory business justification before submission.*

### Step 2: Administrative Approval
The request triggers a notification to the Identity Administrator. Access is **not** granted until this approval step is completed.

<img width="796" height="357" alt="JT-approved-4" src="https://github.com/user-attachments/assets/7bd2ab57-a40c-496e-afe4-79645cd4173c" />

*Figure 4: The Administrator's view showing the successful approval of the request.*

---

## ✅ Verification & Results

### Automated Provisioning
Immediately upon approval, the Entra ID Governance engine automatically injected the user into the `Finance Team` security group. No manual intervention was required.

<img width="768" height="457" alt="JT-added-finance-5" src="https://github.com/user-attachments/assets/2cc5ecbe-7583-4b8e-a5b6-3cee65d06643" />

*Figure 5: Verification that Joseph Thomas was added to the Finance Team group.*

### JIT Policy Enforcement
The system stamped a hard expiration date on the assignment. On **12/16/2025**, the user will be automatically removed, ensuring the environment returns to a secure state.

<img width="867" height="318" alt="Entitlement management  Assignments-6" src="https://github.com/user-attachments/assets/e9e62928-a044-413e-9676-dc22ca8ea979" />

*Figure 6: The "Assignments" log proving the access is time-bound (Expires 12/16/2025).*

---

## 🏆 Project Outcome
* **Risk Reduction:** Reduced the attack surface by moving 100% of ad-hoc administrative access to a time-bound model.
* **Efficiency:** Reduced IT ticket resolution time by enabling self-service requests.
* **Compliance:** Achieved readiness for **NYS DFS Part 500** and **SOX** audits by ensuring all privileged access is documented, justified, and temporary.
