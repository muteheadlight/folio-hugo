+++
archetype = "chapter"
title = "3. Resilience"
weight = 3
+++

With a Recovery Time Objective (RTO) of 1+ day(s) and in the interest of minimal cost, the majority of the design does not consider resilience options. The following can be considered to increase robustness of this solution.

### Event Grid
Event grid is regional, clones would need to be built in any target regions for DR or HA.

### Azure Functions
Azure Functions supports a zone-redundant deployment under a Premium App Plan.

Additionally, an active-passive multi-region deployment could be used for DR. Event grid triggered functions can exist in another region without adverse effects. Timer triggered functions must be disabled to prevent duplicate events being generated in the passive region. Enable the functions for DR but also consider the "failed" region may still have the functions enabled once available again.

### Storage Account
A zone-redundant deployment App Plan will require a ZRS storage account to support the Azure Functions.

Geo-redundant Storage (GRS) would be useful in a multi-region Azure Function deployment. Having the Azure Functions run from a package on the replicated Storage Account would eliminate needing to deploy the Azure Functions code in multiple regions, since it would be replicated automatically.
