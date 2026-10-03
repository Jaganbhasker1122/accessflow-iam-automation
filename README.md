# AccessFlow — IAM Authorization Automation

A lightweight n8n workflow that demonstrates how an access request can be validated, mapped to a role, evaluated against a simple authorization policy, and recorded as an audit event.

## Workflow

`Webhook → Validate Request → Role/Permission Mapping → Authorization Decision → Audit Log → Response`

## What it demonstrates

- Access request intake through a webhook
- Basic role-based access control (RBAC)
- Authentication/authorization concepts
- Automated authorization decisions
- Audit logging
- REST/webhook-based workflow automation

## Example use case

A user requests access to a resource with a requested role such as `developer`, `analyst`, or `viewer`. The workflow checks the role against a small policy map, returns an `APPROVED` or `DENIED` decision, and creates an audit record.

## Example request

```json
{
  "user": "jagan",
  "department": "engineering",
  "requested_role": "developer",
  "resource": "github-repository"
}
```

## n8n setup

1. Import `workflow/accessflow.json` into n8n.
2. Open the workflow and review the Webhook node.
3. Activate the workflow and copy the production webhook URL.
4. Send the example request from `examples/access-request.json`.
5. Review the authorization response and execution log.

## Important

This is a learning/demo IAM automation. It does not connect to a real enterprise identity provider or provision real permissions. Extend the policy map and connect it to a sandbox/mock API before using it for demonstrations.

## Suggested extensions

- Connect a mock IAM REST API
- Add an approval step
- Store audit events in Google Sheets/PostgreSQL
- Add Slack/email approval notifications
- Add an AI-assisted explanation of authorization decisions
