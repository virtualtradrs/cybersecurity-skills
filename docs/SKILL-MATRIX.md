# Skill matrix for common security roles

This page maps the eight skills in the [main guide](../README.md) onto the roles people actually hire for.
It exists so you can target a role instead of collecting topics: the same eight skills appear in every
security job, but the *weights* differ a lot, and so does the level expected on day one.

**How to read it.** `●●●` = the role leans on this skill daily and an interview will test it; `●●○` = expected
and used regularly, but you can grow into it; `●○○` = useful context, rarely the deciding factor;
`○○○` = not part of the role. Levels are *typical expectations for someone doing the job*, not requirements
for getting hired — most people are promoted into the second and third columns.

## The matrix

| Skill | SOC analyst | Detection engineer | Security engineer (infra) | Cloud security engineer | AppSec engineer | Incident responder |
|-------|:-----------:|:------------------:|:-------------------------:|:----------------------:|:---------------:|:------------------:|
| 1. [Networking](../README.md#1-networking-skills) | ●●● | ●●● | ●●● | ●●○ | ●●○ | ●●● |
| 2. [Linux and systems administration](../README.md#2-linux-and-systems-administration) | ●●● | ●●● | ●●● | ●●● | ●○○ | ●●● |
| 3. [Scripting and automation](../README.md#3-scripting-and-automation) | ●●○ | ●●● | ●●● | ●●● | ●●● | ●●○ |
| 4. [Security analysis and log triage](../README.md#4-security-analysis-and-log-triage) | ●●● | ●●● | ●●○ | ●●○ | ●○○ | ●●● |
| 5. [Detection and monitoring](../README.md#5-detection-and-monitoring) | ●●● | ●●● | ●●○ | ●●○ | ○○○ | ●●○ |
| 6. [Cloud and infrastructure security](../README.md#6-cloud-and-infrastructure-security) | ●●○ | ●●○ | ●●● | ●●● | ●●○ | ●●● |
| 7. [Application and web security](../README.md#7-application-and-web-security) | ●○○ | ●○○ | ●●○ | ●●○ | ●●● | ●●○ |
| 8. [Professional skills](../README.md#8-professional-skills) | ●●● | ●●○ | ●●○ | ●●○ | ●●● | ●●● |

| Skill | Threat intel analyst | GRC / security analyst | Security architect | Penetration tester (authorized) |
|-------|:-------------------:|:----------------------:|:-----------------:|:------------------------------:|
| 1. [Networking](../README.md#1-networking-skills) | ●●○ | ●○○ | ●●● | ●●● |
| 2. [Linux and systems administration](../README.md#2-linux-and-systems-administration) | ●●○ | ●○○ | ●●● | ●●● |
| 3. [Scripting and automation](../README.md#3-scripting-and-automation) | ●●● | ●○○ | ●●○ | ●●● |
| 4. [Security analysis and log triage](../README.md#4-security-analysis-and-log-triage) | ●●● | ●●○ | ●●○ | ●●○ |
| 5. [Detection and monitoring](../README.md#5-detection-and-monitoring) | ●●○ | ●○○ | ●●○ | ●○○ |
| 6. [Cloud and infrastructure security](../README.md#6-cloud-and-infrastructure-security) | ●○○ | ●●○ | ●●● | ●●○ |
| 7. [Application and web security](../README.md#7-application-and-web-security) | ●○○ | ●○○ | ●●○ | ●●● |
| 8. [Professional skills](../README.md#8-professional-skills) | ●●● | ●●● | ●●● | ●●● |

## What each role is really asked for

**SOC analyst (Tier 1 → Tier 2).** The job is triage under time pressure. Expect a first shift built on
skills 4 and 5 with skill 1 underneath them: recognise the alert, decide, document, escalate or close. Tier 2
adds correlation across sources and the beginning of rule tuning. Deep networking is the usual differentiator,
because it decides whether you can explain an alert rather than just label it.

**Detection engineer.** Skills 3, 4 and 5 combined: you write logic, you test it, you measure it, you retire
it. The distinguishing ability is not writing a rule, it is proving a rule works and knowing what it misses —
which needs networking and systems depth to know what is even observable.

**Security engineer (infrastructure).** Skills 2, 6 and 1 at a design level: segmentation, identity,
hardening, logging pipelines, and the automation (skill 3) that keeps all of it reproducible. This role is
where "I read the benchmark" and "I can justify deviating from it" separate.

**Cloud security engineer.** Skill 6 first, with skills 3 and 2 as the working hands: policy as code, IAM
reasoning, container and IaC scanning in pipelines, and the audit-trail queries that let you answer what
happened.

**Application security engineer.** Skill 7 with skill 3 (you will read and occasionally write code) and
skill 8 (your findings only count if developers act on them). Breadth in 1 and 6 helps because most real
findings live at the seam between the app, its deployment and its identity.

**Incident responder.** Skills 1, 2, 4 and 8 at speed: reconstruct what happened, preserve evidence, brief
people while it is still happening. Detection (5) tells you it happened; response is about the analysis and
the writing.

**Threat intel analyst.** Skills 3 and 4 to turn feeds into structured, queryable intelligence (STIX,
enrichment pipelines), with skill 8 for how it is marked and shared (TLP) and skill 1 for the network
behaviour that makes an indicator meaningful rather than just a string.

**GRC / security analyst.** Skill 8 heavily, with 6 and 4 enough to argue from evidence. The failure mode of
this role is copying a framework into a spreadsheet; the skill is translating controls into what a specific
team must actually do.

**Security architect.** Every skill at a design level, and skill 8 most of all — architecture is a
communication job. Expect interviews to be system design, not trivia.

**Penetration tester (authorized engagements only).** Skills 7, 1, 2 and 3 in combination, with skill 8
carrying more weight than most candidates expect: scope discipline, evidence handling and report quality are
what clients buy, and out-of-scope testing ends careers.

## How to use the matrix

1. Pick one role. Read its row, not the whole table.
2. Score yourself honestly using the self-checks in each skill section of the [main guide](../README.md).
3. Take the two skills where the role weight is `●●●` and your own level is lowest. That is your next quarter.
4. Borrow the [evidence page](SKILLS-TO-EVIDENCE.md) to produce one artifact per skill so the claim is
   checkable.

## What this matrix is not

- **Not a job description.** Real postings vary by industry and company size; a "cloud security engineer" at a
  ten-person startup and at a bank share a title and almost nothing else.
- **Not a ranking.** A dot is not a score of worth or a prediction of salary, and no column here is a promise
  of employability.
- **Not exhaustive.** Roles like malware analyst, forensics examiner, identity engineer and security
  researcher exist and lean differently again — write your own column using the same eight skills.
