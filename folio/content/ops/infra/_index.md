+++
title = 'Infrastructure'
summary = 'IaaS components and architecture'
weight = 10
+++

![arch](/images/arch.png)

## components
Azure Functions (timer trigger) - Collects fitness/health data from various services  
Event Grid - Message distribution and event-driven component integration  
Azure Functions (event grid trigger) - Process events and forward formatted fitness/health data to various services  
Storage Account - Holds external package with Function app code (needed by Azure Functions)  
Key Vault - Holds login credentials and oauth keys for various fitness/health services