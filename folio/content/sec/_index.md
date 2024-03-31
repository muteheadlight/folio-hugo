+++
archetype = "chapter"
title = "2. Security"
weight = 2
+++

## Secret Management
Secrets (health/fitness service credentials and oauth keys) are persisted in a Key Vault. Upon refreshing oauth credentials, the function should write the updated token back to the Key Vault. Where possible, once oauth is established, login credentials should be deleted from Key Vault. 

## Authentication & Authorizations
A managed identity with permissions to the Key Vault, Storage Account and Event Grid is assigned to the functions for another layer of protection

## Public networking
Public networking on Azure Functions, Storage Account, Event Grid, and Key Vault should be restricted to only allowing Azure trusted services.

## Private VNET & Private Endpoints
Since all the solution's components are Azure services, there isn't a need to implement a private VNET with private endpoints.

Additionally, the Azure Functions Consumption plan does not provide virtual network integration.
