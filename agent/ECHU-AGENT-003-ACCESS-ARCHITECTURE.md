# ECHU Agent — Access Architecture v1.0

**Status:** Proposed  
**Purpose:** define a safe path for connecting the ECHU Website Agent to WordPress/Avada without exposing credentials or granting unnecessary privileges.

## 1. Principle

GitHub is the documentation/version-control layer. It is **not** the live WordPress execution environment.

The Agent requires a separate execution path to inspect or modify WordPress.

The preferred architecture is:

**ChatGPT strategy → ECHU Agent → controlled WordPress access → WordPress/Avada**

with GitHub holding the Agent rules, specifications and technical records.

## 2. Access levels

### Level 0 — No site access
Planning and documentation only.

### Level 1 — Read-only
Agent can inspect WordPress/Avada configuration and pages but cannot modify production.

**This is the required first operational level.**

### Level 2 — Controlled edit
Agent can edit approved pages/components within a defined scope but cannot publish production changes.

### Level 3 — Publish
Agent can publish approved changes. This should remain restricted and should not be the default.

## 3. Least privilege

Grant only the permissions required for the current mission.

Do not use a shared administrator password simply because it is convenient.

Do not place WordPress passwords, application passwords, API keys, cookies, session tokens or other secrets in:

- GitHub files;
- task descriptions;
- screenshots;
- chat messages;
- public documentation.

## 4. Preferred execution methods

### Option A — Browser/Computer execution
A controlled browser/desktop execution environment allows the Agent to operate the WordPress administration interface and Avada visually.

This is particularly useful for:
- Avada Live Builder;
- visual templates;
- global options;
- responsive design inspection;
- workflows not exposed cleanly through an API.

The user should authenticate through the secure environment themselves when required. Credentials should not be copied into chat.

### Option B — WordPress API
An API-based integration can be used for structured operations where supported, such as approved content or metadata workflows.

API access should use the minimum required permissions and should not automatically imply administrator access.

### Option C — Hybrid
**Recommended target architecture:** use API for structured/automatable operations and controlled browser execution for Avada-specific visual operations.

The method used for each task must be recorded in the task report.

## 5. Environment separation

Preferred environments:

1. Development/staging — experimentation and testing.
2. Production — approved, tested changes only.

If staging does not exist, high-risk production work requires a verified backup/rollback path and explicit approval.

## 6. Production publishing gate

Production publication is an independent permission.

The Agent must be able to perform:

**Inspect → Plan → Edit → Test → Report**

without automatically being able to:

**Publish**.

Where the execution platform cannot technically separate edit and publish permissions, the workflow must compensate with an explicit human approval gate and a documented rollback method.

## 7. WordPress access model

Before granting access, determine the smallest WordPress role/capability set that supports the required mission.

Do not create a new administrator account unless there is a documented technical requirement.

If an application/API credential is used, it should:

- belong to a dedicated integration identity where appropriate;
- have limited scope;
- be revocable;
- never be committed to GitHub;
- be stored only in the secure credential mechanism of the execution environment.

## 8. First connection mission

The first connection must be **ECHU-AGENT-001 — Site Recon** in READ-ONLY mode.

Success means the Agent can inspect enough of the WordPress/Avada environment to produce:

- WordPress baseline;
- Avada baseline;
- page-builder map;
- plugin/dependency map;
- SEO baseline;
- performance baseline;
- backup/rollback status;
- custom-code inventory;
- access/risk findings.

No edits are permitted during the first connection.

## 9. Connection acceptance test

Before any real task, verify:

- Agent can access the intended WordPress environment;
- Agent can identify the correct site;
- Agent can distinguish production from staging;
- Agent cannot accidentally publish during read-only discovery;
- secrets are not exposed to the chat or repository;
- access can be revoked;
- the owner understands what the Agent can and cannot do.

## 10. Avada-specific rule

Because ECHU uses Avada, browser-level execution is important for visual work.

The Agent must not assume that an API operation is equivalent to an Avada Builder operation.

Before editing a page, it must verify the actual builder/template and the scope of global settings involved.

## 11. Access revocation

The owner must be able to revoke Agent access independently of GitHub documentation.

When an integration is no longer required:

1. disable/revoke the credential or connection;
2. verify access is actually gone;
3. retain only non-sensitive documentation of the change.

## 12. What ECHU must not do

- Do not send WordPress passwords to ChatGPT.
- Do not commit credentials to GitHub.
- Do not grant administrator access without a demonstrated need.
- Do not connect an unknown third-party automation service to production without reviewing its permissions.
- Do not allow an Agent to publish autonomously by default.
- Do not begin high-risk site modification before the read-only audit is complete.

## 13. Recommended rollout

### Phase 1
Read-only connection.

### Phase 2
Site Recon report.

### Phase 3
Compare Site Recon with existing Grok UX/benchmark findings.

### Phase 4
Create `ECHU-BUILD-SPEC-001`.

### Phase 5
Enable controlled edit for one low/medium-risk task.

### Phase 6
Run QA and owner review.

### Phase 7
Only after successful operation, consider a restricted publishing workflow.

## 14. Decision

For ECHU, the target architecture is **Hybrid Access**:

**Read-only browser inspection first → API where appropriate → controlled Avada browser execution → human publication gate.**

This architecture keeps the Agent useful without turning it into an unrestricted administrator.
