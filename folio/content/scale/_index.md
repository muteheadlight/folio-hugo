+++
archetype = "chapter"
title = "Scalability"
weight = 4
+++

The expected workload on the solution is a handful of events each week.

Limits to consider
* Event Grid publish rate: 5000 64 KB events per second
* Azure Function Consumption Plan scales up to 100 instances. Additionally, potential for additional latency as Consumption Plan can scale to 0 on idle leading to latency from a cold start.
* Storage Account request max: 20,000 requests per second.
