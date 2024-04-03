+++
title = 'DevOps'
summary = 'Deployment details'
weight = 40
+++

## Azure Functions code
The code for the Azure Functions is pulled from blob storage. The archive creation and push to blob storage is done via a Github Action.

## Landing page (this) deployment
The landing page is hosted as a Cloudflare Pages project. The content is deployed on repo `push` via a [Github Action](https://github.com/muteheadlight/folio-hugo/blob/main/.github/workflows/publish.yml).