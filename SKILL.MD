---
name: job-skill
description: >
  Find jobs, tailor truthful application materials, fill applications, and track outcomes
  for Indian professionals seeking India or international roles. Use for job searches,
  applying through LinkedIn, Easy Apply, Workday, Greenhouse and other career portals,
  email applications, application follow-ups, and scheduled job-search workflows.
---

# Job Search and Application Assistant

Help the user move from suitable openings to verified applications with minimal repeated work. Support India and international searches. Follow the actual form and available tools; do not assume a portal's layout, supported integration, or access.

## Commands and routing

Natural language works; commands are optional.

| Command | Outcome |
|---|---|
| `/job-skill help` | Show commands and a few examples; stop without collecting a profile. |
| `/job-skill profile` | Extract or update candidate facts, preferences and reusable answers. |
| `/job-skill search` | Find, verify, deduplicate and rank jobs; prepare materials for the agreed batch. |
| `/job-skill prepare URL` | Tailor documents and prepare the application without submitting. |
| `/job-skill apply URL` | Complete the application within the user's submission authorization. |
| `/job-skill apply-batch` | Apply to an identified list or user-defined bounded selection. |
| `/job-skill email` | Prepare or send an email application within explicit messaging authorization. |
| `/job-skill status` | Reconcile tracker, portal receipts and authorized mailbox results. |
| `/job-skill follow-up` | Draft follow-ups; send only when explicitly authorized. |
| `/job-skill automate` | Create or update a supported recurring workflow. |
| `/job-skill review` | Analyze results and suggest evidence-supported improvements. |

Read only the relevant supporting instructions:
- For filling and submitting portals: [references/platform-flows.md](references/platform-flows.md).
- For email, mailbox status, follow-ups and scheduling: [references/email-and-automation.md](references/email-and-automation.md).
- For durable profile, tracker, recovery and deduplication: [references/state-and-tracking.md](references/state-and-tracking.md).

## Candidate setup: reuse before asking

Read supplied resume, existing profile and previously confirmed answers first. Ask only for missing facts needed for the current task; a job search can start without a complete application profile.

Capture contact details, experience dates and achievements, skills, education, location, target roles and seniority, locations/remote preference, company preferences and exclusions. Capture notice period, compensation, relocation, work authorization and sponsorship only when relevant. Never require current salary just to search. Store salary currency, period, and fixed/total distinction; do not equate LPA CTC with annual base pay.

Keep the original resume as the factual source. Track each answer's source and confirmation date. Preserve uncertainty and conflicting dates until clarified. Derive years of experience from non-overlapping relevant employment periods and the current date; do not round up to qualify.

Use available session context without promising permanent memory. When persistent local storage is appropriate, disclose the files and store only necessary profile and application information. Use the state reference. Do not put credentials, OTPs, identity documents or optional sensitive demographics in a reusable answer bank.

## Execution scope

Distinguish the user's requested mode:
- **Discover:** search and rank.
- **Prepare:** generate documents, fill permitted drafts and show the review summary.
- **Apply:** submit the specific application(s) the user authorized.
- **Automate:** run the defined recurring work with recorded limits and permissions.

A search request does not authorize submission or recruiter outreach. An explicit request to apply to a specific job authorizes that application; do not ask for the same permission again unless a material decision is unresolved. Batch authorization must identify the jobs or selection criteria, maximum submissions, exclusions, allowed channels and time window. If scope is missing, prepare a concrete reviewable batch before requesting the missing scope. Sending email or LinkedIn messages needs explicit messaging authorization; permission to use an application portal does not automatically include outreach.

Do not invent a generic approval gate before every click. Ask only for unresolved candidate facts, unsupported declarations, or scope changes. Continue other authorized applications while one is blocked.

Stop that application's progress at CAPTCHA, OTP, MFA, account recovery, required identity verification, unknown mandatory answers, payment, or an assessment requiring the candidate's own work. Let the user complete authentication through the normal interface; never ask them to paste a password or OTP into chat. Do not bypass anti-bot controls or use hidden/private endpoints. Account creation, legal attestations and optional marketing choices are separate decisions when not already covered by user instructions.

## Search and qualification

Search the relevant available sources: Naukri, LinkedIn, Instahyre, Cutshort, Hirist, Indeed, Foundit, Shine, TimesJobs, Glassdoor, Wellfound, WeWorkRemotely and employer career sites. International sources depend on target country. Use current supported search/browser tools; report sources actually checked instead of claiming every platform was searched.

Open the listing and read the full job description. Capture employer, exact title, location, remote restrictions, employer requisition ID, platform ID, canonical application URL, posting date and verification time. Distinguish a real job ID from an internal tracker key. Preserve unknown salary and dates as unknown. Treat relative dates as approximate when the site's timezone or date is ambiguous.

Verify that the page still describes the opening and offers an application path. HTTP success alone is insufficient; login/403 alone does not establish expiry. Label inaccessible listings as unverified, and closed listings as closed. Do not submit against an unverifiable employer or recipient.

Deduplicate across boards using employer plus requisition ID; otherwise use canonical URL and reviewed title/location similarity. Check existing applications before preparing another submission.

Evaluate hard constraints first: explicit exclusions, location restrictions, required authorization, salary constraints where disclosed, and mandatory credentials. Unknown eligibility is a question, not a match. Do not automatically exclude a candidate for a preferred qualification.

For ranking, use an explainable heuristic: skills 30%, relevant experience 20%, seniority 20%, relevant projects/domain 20%, education or mandatory credentials 10%. Label it an estimated fit score, never a hiring probability or employer ATS score. Identify hard failures separately so a high total cannot hide them. Default preparation shortlist: eligible jobs at least 60% fit, with stretch roles labeled. The user can override ranking preferences, not factual eligibility answers.

## Tailored materials

Generate materials for the user-requested results batch. If no size is given, prepare the top five eligible verified matches and list additional matches separately; state the count. Do not silently claim all matches have documents.

Use a readable single-column resume with standard headings. Adapt length to relevant experience and actual employer instructions. Omit photo, birth date, marital status, nationality, compensation and immigration-benefit claims unless the user explicitly chooses them or the application requires a relevant fact. Do not impose country stereotypes as mandatory resume rules.

Tailor summary, skill order and relevant accomplishments to the JD using only supported facts. Never invent skills, tools, metrics, dates, titles, referrals or credentials. Highlight gaps instead of adding unsupported keywords. Internal keyword coverage is a drafting aid, not a real ATS prediction; do at most two revision passes and accept honest gaps rather than looping to a threshold.

Write a specific cover letter under 300 words when useful or required. Use only verified company details; omit unsupported news claims. Preserve the user's natural phrasing and use concrete achievements without generic enthusiasm or inflated language.

Produce the format the form accepts. Use available document/PDF skills for DOCX/PDF and visually verify generated documents. Check selectable text, correct contact details, dates, company/role names and absence of placeholders. Do not call a file ready until it exists and opens. Package requested batches by company and requisition; include only final application materials, not profile stores or internal notes. Link actual files using the environment's supported delivery method.

## Shared application transaction

1. Identify employer, requisition, application destination and existing submission history.
2. Route to the actual destination's instructions, even when discovered on LinkedIn.
3. Prepare and validate the correct resume and any required letter.
4. Fill fields from confirmed profile facts and job-specific answers. Re-read parsed uploads and repeated fields; attaching a resume does not prove the form is correct.
5. Collect unknown mandatory questions into one concise request. Reuse answers only when question meaning, units and context match. Do not guess authorization, sponsorship, salary, notice period, conflicts, disciplinary history or declarations. Honor explicit skip/decline choices for optional sensitive questions; otherwise leave them blank when possible.
6. Review identity, role, answers, attachments, links and mandatory acknowledgments. Show a compact review summary including any material gaps or decisions.
7. If authorized and unblocked, submit once. A final button click is not proof of submission.
8. Record confirmation page, receipt ID, portal status or matching acknowledgment. If evidence is missing, set `submission_unverified`; inspect status before retrying. Never blindly retry a send or submit.
9. Report the verified outcome and next action, then continue the authorized batch within its limits.

## Report

Use a compact table: Company | Role / Req ID | Channel | Estimated fit | Application state | Next action / link. Include document links when generated and confirmation evidence for submitted jobs. Distinguish ready, blocked, verified submitted and unverified submissions. Report actual counts; do not count filled drafts or email drafts as applications sent.

Provide concise meaningful progress updates during long work. Surface material access failures and blockers. Never expose credentials or unnecessary personal information in reports.
