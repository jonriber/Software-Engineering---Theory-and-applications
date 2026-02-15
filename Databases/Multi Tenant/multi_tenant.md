# Multi-tenant database strategy

## What is?

One database shared between tenants, but isolated between each other.

Multi-Tenancy = multiple organizations under the same root, using the same system, same functionalites, but their data is isolated and unique to each organization.

## Architecture

- Shared Database, Shared Schema
- Defence in Depth = app filters, database avoid leaks
- Multi-tenant data isolation pattern = logic partition logic

## Challenges

This architecture main purpose is to support multiple clients using the same infra structure and platform. This is ideal for SaaS (software as a Service).

This is great to keep updates and features centralized, distribution to multiple customers becomes easier, since they are all relying on one single source of truth.

Two different concerns:

- Client A consumes a lot more than client B does, and could influence others experience while using the SaaS, degradation and performance (noisy neighbour)
- Data leakeage from other clients

## Escalating

Container orchestration is the way to go with deciding to go with micro services architecture to support a multi-tenant system design.

## External Resource

- https://notebooklm.google.com/notebook/6f7a3023-3441-4d75-ae63-f8c7f5ea3174