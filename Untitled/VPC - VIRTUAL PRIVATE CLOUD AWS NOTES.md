

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

### 🏗️ What AWS Auto-Creates When You Create a VPC

ResourceCreated Automatically?Default Behavior**Route Table**✅ YesOnly has a local route (no internet access)**Network ACL**✅ YesAllows **ALL** inbound & outbound traffic**Security Group**✅ YesAllows all **outbound** traffic, allows **inbound only from same security groupDHCP Option Set**✅ YesProvides DNS and IP config to resources


PROJECT -2 


INBOUND (User → Your EC2 Instance):
1. 🌐 User sends request from their browser
2. 🚪 Internet Gateway lets traffic into the VPC
3. 🚏 Route Table directs traffic to the right subnet
4. 📋 Network ACL checks subnet-level inbound rules → ALLOWED
5. 🥅 Request enters the Public Subnet
6. 👮 Security Group checks resource-level inbound rules → ALLOWED
7. 💻 EC2 Instance processes the request

OUTBOUND (Response back to User):
8. 👮 Security Group auto-allows response (stateful!)
9. 📋 Network ACL checks outbound rules separately (stateless!)
10. 🚏 Route Table directs response to internet gateway
11. 🚪 Internet Gateway sends response to the internet
12. 🌐 User sees the website!


### Public EC2 Instance

A public instance is an EC2 instance launched in a public subnet. In your project, this is your **NextWork Public Server**.

- It sits in a subnet that has a route to an internet gateway, so it can communicate with the internet.
    
- It gets a **Public IPv4 address** — a globally unique address that lets it be reachable from the internet.
    
- You can connect to it directly using EC2 Instance Connect.
    
- **Use case:** Web servers, application servers — anything that needs to talk to the outside world.
    

### 🔒 Private EC2 Instance

A private instance is an EC2 instance launched in a private subnet. In your project, this is your **NextWork Private Server**.

- It sits in a subnet with **no route to an internet gateway**, so it **cannot** communicate directly with the internet.
    
- It only has a **Private IPv4 address** — no public IP, so it's invisible to the outside world.
    
- You **can't** connect to it directly from the internet. It can only communicate with other resources **inside your VPC**.
    
- **Use case:** Databases, backend servers — anything that holds sensitive data and shouldn't be exposed.