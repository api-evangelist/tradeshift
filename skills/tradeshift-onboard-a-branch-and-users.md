---
name: Onboard a branch account and its users on Tradeshift
description: >-
  Create a child branch under a master account, add and role users, set tax registrations and legal-entity
  identifiers — the multi-entity onboarding path.
api: openapi/tradeshift-external-api-openapi.yml
generated: '2026-08-02'
method: generated
operations:
  - get-rest-external-account
  - get-rest-external-account-branches
  - put-rest-external-account-branches-new
  - get-rest-external-account-branches-companyid
  - get-rest-external-account-users
  - put-rest-external-account-users-userid
  - put-rest-external-account-users-userid-role
  - put-rest-external-account-users-userid-state
  - get-rest-external-account-taxes
  - put-rest-external-account-taxes
  - put-rest-external-legalentities-id
  - put-rest-external-legalentities-id-identifiers-identifier
  - put-rest-external-companies-companyaccountid-identifiers
  - get-rest-external-users-userid-branches
  - put-rest-external-users-userid-primarybranch-newgroupid
---

# Onboard a branch account and its users on Tradeshift

Base URL: `https://api.tradeshift.com/tradeshift`. Every request carries `X-Tradeshift-TenantId`.

Tradeshift supports a **two-level** hierarchy: a master branch with child branches. An account can be a master or a
child, never both. A user created in a master branch can switch between its children; a user created in a child
cannot switch out.

## Steps

1. **Confirm you are on the master.** `get-rest-external-account` and `get-rest-external-account-branches` — the
   latter lists the children. `get-rest-external-account-parent` tells you if you are already a child.

2. **Create the branch.** `put-rest-external-account-branches-new` —
   `PUT /rest/external/account/branches/new` with a body carrying `User` (with an `Id` UUID and a `Person.Email`),
   `CompanyAccount.Company` (name, country, identifiers) and `ParentCompanyAccountId`.
   - The branch is activated automatically and **no activation email is sent** on this endpoint.
   - `SendActivationEmail` and `From` are available on the request body.
   - Identifiers are `{scheme, value}` pairs, e.g. `{"scheme": "TS:ID", "value": "<uuid>"}`.

3. **Read it back.** `get-rest-external-account-branches-companyid`.

4. **Set the legal identity.** `put-rest-external-legalentities-id` and
   `put-rest-external-legalentities-id-identifiers-identifier` register the legal entity and its identifiers;
   `put-rest-external-companies-companyaccountid-identifiers` sets the company-account identifiers.
   `put-rest-external-legalentities-id-locations-locationid` sets locations.

5. **Set tax registrations.** `get-rest-external-account-taxes` / `put-rest-external-account-taxes`. Get this right
   before any document is issued — it drives e-invoicing compliance.

6. **Add and role users.** `get-rest-external-account-users` lists them;
   `put-rest-external-account-users-userid` updates a user;
   `put-rest-external-account-users-userid-role` sets the role;
   `put-rest-external-account-users-userid-state` activates or deactivates.
   `get-rest-external-users-userid-branches` shows which branches a user can reach and
   `put-rest-external-users-userid-primarybranch-newgroupid` sets their primary branch.

## Retry and idempotency rules

- Step 2 is idempotent through the identifier, not through a header: **the identifiers must not already exist**. A
  replay of the same request returns `400` with *"The tenant identifier proposed does already exist on the platform
  and no tenant nor user was created"* — which is the safe outcome, not a duplicate tenant. Generate the `User.Id`
  and the `TS:ID` identifier once and reuse them on every retry.
- Steps 4, 5 and 6 are all `PUT` on named resources and are safe to replay.

## Errors

- `400` — identifier collision (see above) or invalid body.
- `404` — *"User not found or out of company hierarchy"* — the user exists but not under this master branch.
- `403` — the feature is not available for this account.

Full catalog: `errors/tradeshift-problem-types.yml`.

## Events

`USER_STATE_CHANGED` fires when a user changes state — see `asyncapi/tradeshift-webhooks.yml`.
