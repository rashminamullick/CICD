# CICD
# Git + SSH + CI/CD Preparation
![alt text](<image/CICD Pipeline picture.png>)
* Why this was done

* This setup was created to prepare the application for a real CI/CD pipeline using Jenkins.
* Instead of manually copying files, running tests by hand, or deploying code directly, the goal was to automate the full process from code change to deployment.

* GitHub was used as the single source of truth, and SSH authentication was set up so Jenkins can securely access the repository without using passwords or personal credentials.

* This approach reflects how modern software teams work in industry, where automation, security, and reliability are essential.

## Benefits of doing it this way
1. Automation and consistency

* By committing only the application source code and excluding node_modules, Jenkins can install dependencies fresh on every run.
### This ensures:

* The same process runs every time

* No “works on my machine” problems

* Fewer human errors

2. Strong security

* SSH keys were used instead of usernames and passwords.
* This means:

  * No credentials are stored in scripts

  * Access can be revoked instantly if needed

  * Jenkins can authenticate securely and independently

1. Clean and professional repository

* The repository contains:

  * Only source code

  * Configuration files

* Tests

  * Large or sensitive files are excluded.
* This keeps the repository:

  * Lightweight

  * Secure

  * Easy to maintain

1. Early detection of problems

* Because the application includes test files, Jenkins can run tests automatically before deployment.
This allows issues to be caught early, before broken code reaches production.

* Problems and challenges faced
2. SSH configuration complexity

* Setting up SSH authentication required careful handling of:

  * Key generation

  * SSH agent configuration

  * GitHub key registration

  * SSH config files


## Business value and future value
1. Saves time and money

* Automation reduces:

* Manual testing time

* Manual deployment errors

* Developer effort

* This allows teams to focus on building features instead of fixing avoidable issues.

2. Improves reliability

* Automated testing and controlled deployment reduce the risk of:

* Broken releases

* Downtime

* Customer-facing issues

* Reliable systems protect business reputation.

3. Scales with team growth

* As teams grow, manual processes do not scale.
* This setup allows:

  * Multiple developers to work safely

  * Jenkins to handle builds and deployments automatically

  * Consistent quality regardless of team size

1. Industry-ready skills

* This approach mirrors real DevOps workflows used in companies.
  * It demonstrates skills in:

  * Git and GitHub

  * Secure authentication

  * CI/CD concepts

  * Jenkins automation

  * Cloud-ready deployment practices

# Job 3 – Continuous Delivery (CD) Deployment

## Overview

This document explains **Job 3**, the *Continuous Delivery (CD)* stage of the pipeline. The focus of this job is the **final delivery of approved changes to the live environment** in a way that is safe, repeatable, and reliable.

The purpose of Job 3 is **not** to build or test the application, but to **deliver a version that is already known to work** into production with minimal risk and minimal disruption.

---

## What Job 3 Does

Job 3 is responsible for:

* Taking a fully tested and approved version of the application
* Delivering it to a live EC2 instance
* Restarting the application safely so users see the update
* Doing this **automatically and consistently**, without manual steps

This job runs **only after Job 2 completes successfully**, ensuring that unfinished or broken work can never reach customers.

---

## Why Job 3 Is Important

In many organisations, the final delivery step is where most problems happen. It often:

* Relies on manual actions
* Depends on one person knowing the correct steps
* Causes stress during releases
* Increases the risk of outages and mistakes

Job 3 removes these risks by turning delivery into a **routine, predictable process**.

---

## Business Problems Solved

### Reducing Release Stress

Releasing updates no longer feels like a high-risk event. The process is automatic and repeatable, so the business can release changes with confidence.

### Eliminating Bottlenecks

The delivery process does not depend on a single person being available. The knowledge is built into the system itself.

### Protecting Live Services

Only work that has already been tested and approved is allowed to go live, reducing the chance of outages or customer impact.

---

## Business Benefits

### Speed

Updates can reach customers much faster. Once work is ready, it can be delivered without delay.

### Reliability

The same steps happen every time, which makes the outcome predictable and reduces human error.

### Reduced Risk

Manual mistakes are removed from the process, protecting the company’s reputation and service availability.

### Business Continuity

The delivery process is documented and automated, so it remains within the business even if team members change.

---

## How Job 3 Fits Into the Pipeline

* **Job 1** checks new changes
* **Job 2** confirms the changes are ready
* **Job 3** delivers those approved changes to users
![alt text](image/job2image9.png)
This separation ensures that delivery is safe and controlled.

---

## Security and Safety Considerations

* Secure access is used to connect to the live environment
* No direct changes are made manually on the production server
* Only approved pipeline jobs are allowed to deploy

This approach reduces risk and keeps the live environment stable.

---

## Evidence of Success

The success of Job 3 is confirmed by:

* A successful pipeline run
* The application running correctly after deployment
* Users being able to access the updated service

*(Screenshot placeholders can be added here)*

---

## Why This Matters to the Business

Job 3 ensures that:

* Updates can be released safely
* Downtime is minimised
* Teams can move faster without increasing risk
* The business can scale without relying on manual processes

The result is a **calm, predictable delivery process** that supports growth rather than slowing it down.

---

## Personal Reflection

This task demonstrates my ability to:

* Take ownership of the delivery stage
* Think beyond technical tasks and focus on business impact
* Build systems that are safe, reliable, and easy to operate

My goal is to make delivery *boring* in the best possible way — predictable, stress-free, and safe for both the business and its customers.

---

## Conclusion

Job 3 completes the pipeline by safely delivering approved work to customers. By automating this final step, the business gains speed, reliability, and confidence, while reducing risk and operational stress.

#### Job 3 Final Results as Console Output:
![alt text](<image/job3image6 - Copy.png>)
#### Open in Browser:
![alt text](<image/job3image12 - Copy.png>)