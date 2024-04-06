+++
title = 'Implementation Decisions'
summary = 'Specifics on why things were done in certain ways'
weight = 20
+++

## Azure Functions
### identity and networking
Using a `User assigned` identity requires the app configuration set for `AzureWebJobsStorage__credential`, `AzureWebJobsStorage__clientId`, and `WEBSITE_RUN_FROM_PACKAGE_BLOB_MI_RESOURCE_ID`. The `AzureWebJobsStorage*` settings are used to provide the identity for the runtime storage. The `WEBSITE_RUN_FROM_PACKAGE_BLOB_MI_RESOURCE_ID` provides the identity to pull the code archive from storage.

Since Function Apps on a consumption plan cannot not be tied to a VNET there are some complications around setting the IP rules for the storage account. When the Storage Account and Function App are in the same region, internal IPs (10.92.*.*) are used, and Storage Account IP rules do not allow for specifying internal IPs. Deployed Function Apps will have a dynamic set of outbound IPs assigned. However, the assigned outbound IPs are not used for retrieving the code package. In order to disable full public network access to the Storage Account the IPs for the `AzureCloud.canadaeast` service tag need to be allow listed.

While disabling full public networking adds another layer of defense, an eye should be kept on bandwidth charges as the traffic is now flowing out of the regions.
