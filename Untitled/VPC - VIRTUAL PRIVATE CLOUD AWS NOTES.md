

### 1. ☁️ Amazon VPC

- A **logically isolated** virtual network within an AWS Region.
    
- Gives you full control over
    
    ,,, and.
    
- Every AWS account comes with a **default VPC** per Region — this project creates a **custom VPC** for better architectural control.
    
- Defined by an
    
    (e.g., `10.0.0.0/16` = 65,536 IPs).
    
- **Architecture significance:** VPC is the first decision in any AWS deployment — it determines network segmentation, security boundaries, and connectivity patterns.
    

---

### 2. 🥅 Subnets

- Subdivisions of a VPC, each mapped to a specific
    
    .
    
- **Private by default** — no internet connectivity until explicitly configured.
    
- **Public subnet** = subnet with a route table entry pointing `0.0.0.0/0` →
    
    + **auto-assign public IP enabled**.
    
- **Private subnet** = no route to an IGW; used for sensitive workloads (databases, internal services).
    
- Each subnet has its own
    
    , which must be a subset of the VPC CIDR (e.g., `10.0.1.0/24` = 256 IPs).
    
- **Design principle:** Separate public-facing resources (web servers) from backend resources (DBs) using different subnet types.
    

---

### 3. 🚪 Internet Gateway (IGW)

- A **horizontally scaled, redundant, highly available** VPC component — no bandwidth constraints or single point of failure.
    
- Enables bidirectional communication between VPC resources and the internet.
    
- **Two requirements** for internet access:
    
    1. IGW attached to the VPC.
        
    2. Subnet's
        
        has a route: `0.0.0.0/0 → igw-xxxxxx`.
        
- Performs
    
    (1:1) for instances with public IPv4 addresses.
    
- **Limit:** One IGW per VPC.
    

---

### 4. 🚏 CIDR Blocks & IP Addressing

- = Classless Inter-Domain Routing — method for allocating IP ranges.
    
- `/16` = 65,536 addresses (typical VPC), `/24` = 256 addresses (typical subnet).
    
- Smaller prefix number = larger network; larger prefix = smaller, more specific network.
    
- AWS reserves **5 IPs per subnet** (first 4 + last 1) for internal use.
    
- **Planning tip:** Choose non-overlapping CIDR blocks if you plan to use
    
    (Part 6).
    

---

### 5. 👤 IAM User (Prerequisite Best Practice)

- **Never use root** for day-to-day operations — use
    
    with least-privilege policies.
    
- Root is reserved for account-level tasks (billing, account closure).
    
- Compromised IAM user = limited blast radius vs. compromised root = full account takeover.
    

---

