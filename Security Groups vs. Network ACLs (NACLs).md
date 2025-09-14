# 🔐 AWS Security Groups vs. Network ACLs (NACLs)

## 🛡️ Security Groups

### 📍 What is it?
A **stateful firewall** at the EC2 instance level that manages **inbound and outbound** traffic.

### ☕ Real-World Analogy
Think of a **coffee shop (EC2 instance)** with a **bouncer (Security Group)** at the entrance:
- The bouncer only lets in customers (traffic) on the approved list (e.g., HTTP on port 80).
- Once inside, you can leave without being checked again. _(Stateful behavior)_

### ✅ Rules
- Supports only **"Allow"** rules  
- Example: Allow port `22` for SSH access.

### 📌 Applied To
- **Specific EC2 instances**

---

## 🚪 Network ACLs (NACLs)

### 📍 What is it?
A **stateless firewall** that filters traffic **entering and leaving a subnet**.

### 🏘️ Real-World Analogy
Picture a **gated community (subnet)** with a **security gate (NACL)**:
- Incoming and outgoing vehicles (traffic) are checked against a list.
- You need explicit permission to **enter and exit**, even if previously allowed in. _(Stateless behavior)_

### ✅ Rules
- Supports both **"Allow"** and **"Deny"** rules  
- Example: Deny port `23` (Telnet) to block insecure access.

### 📌 Applied To
- **All EC2 instances within a subnet**

---

## 🔄 Key Differences

| Feature             | Security Groups                 | Network ACLs (NACLs)            |
|---------------------|----------------------------------|----------------------------------|
| Level               | Instance-level                  | Subnet-level                    |
| Type                | Stateful                        | Stateless                       |
| Rule Support        | Only Allow                      | Allow and Deny                  |
| Applied To          | Specific EC2 Instances          | All instances in a subnet       |


