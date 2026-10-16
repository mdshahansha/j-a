# Job Skill

A reusable job-search and application assistant for Indian professionals seeking roles in India or internationally.

## What it supports

- Find, verify, rank and deduplicate job listings.
- Tailor resumes and cover letters using truthful candidate information.
- Fill applications through LinkedIn Easy Apply, Workday, Greenhouse and other career portals.
- Follow LinkedIn external application links to the correct employer portal.
- Draft or send explicitly authorized email applications and follow-ups.
- Track confirmations, responses, interviews, assessments and next actions.
- Configure recurring searches and bounded application workflows when supported by the host.

The skill contains instructions, not a standalone application. Browser control, email access, document generation and scheduling depend on the tools available in your assistant environment.

## Files

```text
job-skill/
├── SKILL.md
├── README.md
└── references/
    ├── platform-flows.md
    ├── email-and-automation.md
    └── state-and-tracking.md
```

- [SKILL.md](SKILL.md): commands, candidate setup, search, materials and the shared application workflow.
- [Platform flows](references/platform-flows.md): LinkedIn, Easy Apply, Workday, Greenhouse and other portals.
- [Email and automation](references/email-and-automation.md): email applications, mailbox tracking, follow-ups and recurring runs.
- [State and tracking](references/state-and-tracking.md): profile storage, application records, deduplication and interrupted-submission recovery.

## Setup

1. Extract the package and keep the `job-skill` folder intact.
2. Place that folder in your assistant's configured skills directory. For a standard personal Codex setup, this is `$CODEX_HOME/skills`, or `~/.codex/skills` when `CODEX_HOME` is unset.
3. Make the skill available using your host's normal skill discovery or reload process.
4. Invoke `/job-skill help` or ask the assistant to use the job-skill instructions. Slash-command handling depends on the host; these commands describe the skill's workflows rather than registering executable commands.
5. Provide your resume and target roles/locations. Connect browser, email or scheduling tools only as needed.

This package has not installed itself, connected accounts, created a schedule or submitted applications.

## Quick start

Start with a resume and a concrete request:

> Use job-skill. Find backend engineer roles in Bengaluru or Remote India, posted within seven days. Prepare the top five matches. My notice period is 30 days.

For one application:

> Apply to this job: [job URL]. Use my confirmed profile and a tailored resume. Ask me only for missing mandatory answers.

For preparation without submission:

> Prepare my application for [job URL], including the resume and screening answers. Stop before submission.

For email:

> Draft an email application for this role to [verified recipient address]. Attach my tailored resume. Do not send it yet.

Replace bracketed examples with real details. Missing addresses, candidate facts and permissions are never inferred from placeholders.

## Commands

| Command | Purpose |
|---|---|
| `/job-skill help` | Show capabilities and examples. |
| `/job-skill profile` | Extract or update candidate facts and preferences. |
| `/job-skill search` | Find, rank and prepare an agreed batch of matches. |
| `/job-skill prepare URL` | Prepare documents and application answers without submitting. |
| `/job-skill apply URL` | Complete the specified authorized application. |
| `/job-skill apply-batch` | Process an identified list or a bounded selection. |
| `/job-skill email` | Prepare or send an email application within explicit authorization. |
| `/job-skill status` | Check tracked applications and authorized response sources. |
| `/job-skill follow-up` | Prepare follow-ups; send only when authorized. |
| `/job-skill automate` | Create or update a supported recurring workflow. |
| `/job-skill review` | Review results and suggest improvements. |

Natural-language requests work too.

## Platform behavior

| Channel | Main checks |
|---|---|
| LinkedIn | Identify Easy Apply versus an external destination; preserve both source and employer job IDs. |
| Easy Apply | Validate contact details, selected resume, experience answers and each review step. |
| Workday | Use the correct employer tenant; repair resume parsing errors and verify employment/education dates. |
| Greenhouse | Verify employer and job, required uploads, custom questions and consent choices. |
| Other portals | Inspect the actual form and use the shared application transaction. |
| Email | Verify recipient, sender, attachments and messaging authorization; record the sent message result. |

“Greenocean” in the original request was interpreted as Greenhouse. If a different platform is intended, the assistant should identify the actual destination before applying.

## Candidate information

The assistant reuses your resume and confirmed answers, asking only for missing facts relevant to the current task. Useful information includes:

- Contact details and portfolio/LinkedIn links.
- Employment, education, skills and supported achievements.
- Target roles, locations, seniority and exclusions.
- Notice period, relocation preference and salary expectations when needed.
- Country-specific work authorization and sponsorship requirements.

Salary answers retain currency, payment period and fixed-versus-total compensation meaning. A general experience total is not reused as experience with every individual technology.

Persistent storage depends on your environment and the agreed working location. The skill does not guarantee permanent memory. Passwords, OTPs and session cookies do not belong in the candidate profile or tracker.

## Submission and messaging scope

- Searching prepares results; it does not authorize submissions or outreach.
- Asking to apply to a specific job authorizes that application when required facts are known.
- A batch needs a list or selection criteria, submission limit, allowed channels, exclusions and time window.
- Sending email or LinkedIn messages requires explicit messaging authorization.
- Existing authorization is reused; the assistant should not ask for the same permission at every step.

Unknown mandatory answers, authentication challenges and unsupported declarations pause the affected application. Other authorized jobs can continue. Complete login, CAPTCHA, OTP and MFA through the normal interface.

## Recurring automation

Specify the timezone, time, cadence, filters and preparation limit. Example:

> Search every weekday at 10 PM Asia/Kolkata for backend roles in Bengaluru or Remote India. Prepare up to five new matches. Do not submit applications. Notify me when there are useful new matches or required actions.

Unattended submissions additionally require explicit standing authorization, allowed channels, eligibility criteria, per-run/day limits and an end date or duration. Email sending needs its own explicit authorization. A scheduled run may still need your help signing in.

The assistant must use a supported scheduler and confirm successful configuration before saying an automation is active.

## Tracking and recovery

The tracker distinguishes prepared documents, filled drafts, verified submissions, sent emails, blockers and ambiguous attempts. Email sent does not mean employer acknowledgment.

Before retrying an uncertain submission or email send, the assistant checks portal history or Sent mail. A timeout is recorded as unverified rather than triggering a blind duplicate. The same employer requisition found on multiple boards should produce one application record with multiple discovery sources.

No response remains pending; it is not automatically treated as rejection. Mailbox updates must match the correct requisition or thread before changing an outcome.

## Documents and fit scores

Resumes use supported facts and readable formatting. Missing skills stay visible as gaps; the assistant must not invent tools, metrics, credentials or experience to improve a match.

Fit scores are explanatory estimates, not hiring probabilities or employer ATS scores. Without a requested batch size, the default is to prepare the top five eligible verified matches and list additional matches separately.

## Validation

Package metadata, reference links, text encoding and archive contents were checked during creation. The bundled skill validator could not run because PyYAML was unavailable. No live application, email send, account connection or scheduled run was tested or performed.
