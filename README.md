# AWS Blue-Green Deployment with Application Load Balancer

## 🚀 Overview
Zero-downtime release management strategy using AWS Application Load Balancer (ALB) target group listener rules to seamlessly route production traffic from Blue (v1.0) to Green (v2.0) environments without changing application endpoints.

## 🏗️ Deployment Architecture
* **Custom VPC Configuration:** Custom VPC built with isolated subnets, Internet Gateway, route tables, and restricted Security Groups.
* **Blue Environment (v1.0):** Active production web application running Apache on Ubuntu EC2 instances.
* **Green Environment (v2.0):** Isolated staging environment hosting the upgraded software version.
* **ALB Listener Switching:** Traffic redirection handled dynamically at the load balancer layer by updating listener rules to point from `TG-Blue` to `TG-Green`.
* **Zero-Downtime Rollback:** Instant safety mechanism allowing continuous rollback to `TG-Blue` if unexpected errors are detected post-release.

## 🛠️ Tech Stack
* **Cloud Provider:** AWS (VPC, EC2, Application Load Balancer, Target Groups, Security Groups)
* **Web Server:** Apache HTTP Server
* **OS:** Ubuntu Linux

## ⚙️ Execution Steps
1. **Infrastructure Setup:** Provision Blue (v1.0) and Green (v2.0) EC2 instances within private subnets.
2. **Target Group Creation:** Configure isolated target groups (`TG-Blue` and `TG-Green`) with independent HTTP health checks.
3. **Stage & Test:** Verify Green (v2.0) functionality independently using direct target group health check routing.
4. **Traffic Cutover:** Update ALB listener rules to route 100% of production traffic to `TG-Green` seamlessly.
5. **Rollback Verification:** Test instant rollback capabilities by reverting ALB listener target rules back to `TG-Blue`.

## 👤 Author
* **Tushar Bhendarkar** — [LinkedIn](https://linkedin.com/in/tusharbhendarkar) | [GitHub](https://github.com/tusharbhendarkar30)
