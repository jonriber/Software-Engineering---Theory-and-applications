# Authorization Theory - Architecture lecture

This is an entry point to authorization topic in software engineering. I will first address it with analogies and then start getting deeper.

![alt text](image.png)

## Analogy

Authorization is access control to a `castle`

There are 3 fundamental questions:
- Who are you? - Authentication
- Are you allowed to come in? - Authorization
- How far can you go once inside the castle? - Detailed Authorization

So, `authentication` is to show identity, and `authorization` is power decision.

## Classic authentication models

### ACL - Access Control List

Analogy:

- A notebook stuck at the front door saying: `Jon may come in. Mary may come in. Peter may not`

Each resource has its own list of access.

Structure
- resource --> allowed list of users

Pros:
- Very specific control

Cons:
- Does not scale 

Key topic: `control is based on resource`

### RBAC - Role based access control

Analogy:
- in a castle, there are required roles
- king
- General
- Soldier
- Chef

I do not need to list every soldier, instead I can only state that soldiers are allowed to stay at the entrance.

Structure:
- User --> Role --> permissions

Pros:
- simple
- Scalable
- easy

Cons
- Role explosion

Key topic: `control is based on org function`

### ABAC - Attribute-based access control

Analogy: 
- the castle gate keeper does not check only the role.
- he also asks if the person is:
- a general?
- is this part of the castle belongs to his unit?
- If that time slot is correct for him to work?

This means that the decision for authorization comes after checking several attributes.

Structure:
- Permission = function(user, resource, context)

Pros:
- flexible
- real modeling

Cons:
- if not well designed, can lead to spread if-then-else
- hard to audit

Key topic: `control is based on properties and relationships`

### PBAC - Policy based Access Control

Analogy:
- Instead of the gate keeper deciding, there is a book of rules
- Policy 17 = Soldiers might enter the gate at any time

Decisions are very explicit and testable

Structure:
- declared policies ---> gate decide

### MAC - Mandatory Access Control

Analogy:
- clasification based on
- public
- confidential
- secret
- top-secret

### ReBAC - Relationship-based Access Control

Subtype of ABAC

Analogy:
- You may come in because you are the son of the king

Based on entity relationships

Very common on social networks

## Decision

A decision to be made needs 4 different things:
- Subject (Who)
- Action (What)
- Resource (On what)
- Context (When, where, state)

Formal definition
```javascript
isAllowed(subject, action, resource, context) -> boolean
```

Those 4 questions needs to be answered or the system will break.

## Architecture

Where does Authorization lives on a very mature system?

Never:
- frontend
- mixed in on SQL
- spread across services

Ideally:
- Policy Layer
- Before domain logic
- independent of transportation layer