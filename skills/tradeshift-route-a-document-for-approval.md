---
name: Route a document for approval on Tradeshift
description: >-
  Create an assignment against a document, reassign it, comment on it, close it, and read the audit log — the
  accounts-payable approval loop.
api: openapi/tradeshift-external-api-openapi.yml
generated: '2026-08-02'
method: generated
operations:
  - get-rest-external-account-users
  - get-rest-external-usergroups
  - post-rest-external-assignments
  - get-rest-external-assignments
  - get-rest-external-assignments-id
  - patch-rest-external-assignments-id
  - put-rest-external-assignments-id-comment
  - post-rest-external-assignments-id-reassign-assigneeid
  - put-rest-external-assignments-id-close
  - get-rest-external-assignments-id-logs
  - get-rest-external-assignments-subjects-subjectid-logs
---

# Route a document for approval on Tradeshift

Base URL: `https://api.tradeshift.com/tradeshift`. Every request carries `X-Tradeshift-TenantId`.

An **assignment** is a work item bound to a subject — normally a document — and to an assignee (a user or a group).
It is the primitive behind AP approval flows on Tradeshift.

## Steps

1. **Resolve the assignee.** `get-rest-external-account-users` lists users in the account;
   `get-rest-external-usergroups` lists the account's groups. Assign to a group rather than an individual where the
   approver may change.

2. **Create the assignment.** `post-rest-external-assignments` — `POST /rest/external/assignments` with the subject
   (the document UUID) and the assignee.

3. **Track it.** `get-rest-external-assignments` lists assignments (filterable by `assigneeids`, `subjectid`,
   `subjectType`, `state`, `companyid`); `get-rest-external-assignments-id` reads one.

4. **Work it.**
   - `patch-rest-external-assignments-id` — partial update.
   - `put-rest-external-assignments-id-comment` — add a comment.
   - `post-rest-external-assignments-id-reassign-assigneeid` — reassign to another user or group.
   - `put-rest-external-assignments-assignees-from_assigneeid-reassignees-to_assigneeid` — bulk reassign every
     assignment from one assignee to another (use for leavers and out-of-office).

5. **Close it.** `put-rest-external-assignments-id-close`.

6. **Audit.** `get-rest-external-assignments-id-logs` for one assignment;
   `get-rest-external-assignments-subjects-subjectid-logs` for everything that happened to a subject.

## Auto-assignment

Rules that route documents automatically live under the documents API:
`get-rest-external-documents-assignments-users-userid-autoassign`,
`put-rest-external-documents-assignments-users-userid-autoassign-autoassigneeid-delegationtype-delegationtype`,
`delete-rest-external-documents-assignments-users-userid-autoassign-autoassigneeid`, and the
`.../companies/{companyid}/autoassignments` listing.

## Retry and idempotency rules

- `post-rest-external-assignments` is **not** idempotent. Before retrying a create, query
  `get-rest-external-assignments` filtered by `subjectid` to see whether the first attempt landed.
- `put-rest-external-assignments-id-close` is a `PUT` on a specific assignment and is safe to replay.
- Reassign is a POST; check `get-rest-external-assignments-id` before retrying.

## Errors

- `403` — *"Current user does not have access to assignment"* (5 operations declare this).
- `500` with `ErrorCode` `AbsentDefaultAssignee` or `InvalidDefaultAssignee` — the branch has no valid, active
  default assignee, or none of the supplied assignees are valid members of the current branch. **This is a
  configuration error you can fix**, not a transient failure: set a valid default assignee, or supply an assignee who
  is an active member of the branch, then retry.

Full catalog: `errors/tradeshift-problem-types.yml`.
