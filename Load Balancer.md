# ⚖️ AWS Load Balancer

## 📍 What is It?

A **Load Balancer** distributes **incoming traffic** across multiple EC2 instances to maximize **availability**, improve **performance**, and ensure your application handles requests efficiently.

---

## 🍽️ Real-World Analogy

Imagine a **busy restaurant (your app)** with multiple **waiters (EC2 instances)**. A **host (Load Balancer)** directs customers (incoming traffic) to the available waiters, preventing overload and ensuring fast service.

---

## 🔧 Types of Load Balancers

| Type                        | Protocols     | Use Case Example                                      |
|-----------------------------|---------------|-------------------------------------------------------|
| **ALB (Application)**       | HTTP/HTTPS    | Routes traffic to web app’s login page                |
| **NLB (Network)**           | TCP/UDP       | Ideal for low-latency apps (e.g., real-time gaming)   |
| **GLB (Gateway)**           | Layer 3       | Integrates third-party firewalls or security tools    |

> ✅ Example:  
**Netflix** uses Application Load Balancers (ALBs) to efficiently distribute streaming requests worldwide, ensuring a smooth playback experience even during peak hours.


## 🧠 Key Benefits

- Ensures **high availability** by rerouting traffic during instance failures  
- Enhances **performance** by balancing user load  
- Supports **autoscaling** and improves fault tolerance  
- Provides **SSL termination** for secure application delivery (ALB)

---

## 📈 Architecture Hint

For most web applications:
- Use an **ALB** in front of your EC2 instances
- Associate the ALB with a **Target Group**
- Configure **Health Checks** for resilience
- Pair with **Auto Scaling Groups** for elastic load handling



