# Cybersecurity Skills — a skill-by-skill guide to what each one actually requires

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Links: hand-checked](https://img.shields.io/badge/links-hand--checked-brightgreen.svg)](#link-health)

**The goal of this repository:** *a curated, skill-by-skill guide to modern cybersecurity — what each core
skill actually requires, what beginner / intermediate / advanced looks like, and the best free or
low-cost resources to level up each one.*

Eight core skills. For each one: the three levels in concrete terms, the resources that actually move you
from one level to the next, and a self-check you can run against yourself today. Every link was checked
with `curl` before it was published, and the ones that need a lab are labelled as such.

## How this differs from the roadmap

This repository is a **taxonomy**, not a path. It answers *"what does this skill consist of, and how do I
know which level I am at?"*

- **This repo (`cybersecurity-skills`)** — one section per skill: the levels, the resources per level, a
  self-check. Jump to whichever skill your current role needs.
- **[`cybersecurity-roadmap`](https://github.com/virtualtradrs/cybersecurity-roadmap)** — *the order to
  learn these in*, stage by stage, from your first `tcpdump` to a first security job, with a "done when"
  test on each stage.

They are designed to be used together and neither replaces the other. If you are new and want a sequence,
start with the [roadmap](https://github.com/virtualtradrs/cybersecurity-roadmap) and use this repository
as the depth reference. If you already work in security and one area is holding you back, start here and
use the roadmap only to check that your gaps upstream are closed.

**What this is not:** a certification list, a ranking of people, a toolkit, or a promise of a job. Levels
describe *skill*, not years served or job titles — plenty of people hold a senior title and cannot read a
packet capture, and plenty of juniors can. Nothing here contains exploit code, payloads, target lists or
evasion recipes; offensive material appears only as **authorized practice** in deliberately vulnerable labs
you are entitled to attack (see the [ethics rule](CONTRIBUTING.md#the-ethics-rule-non-negotiable)).

---

## Contents

- [How to read the level tags](#how-to-read-the-level-tags)
- [Skills at a glance](#skills-at-a-glance)
- [1. Networking skills](#1-networking-skills)
- [2. Linux and systems administration](#2-linux-and-systems-administration)
- [3. Scripting and automation](#3-scripting-and-automation)
- [4. Security analysis and log triage](#4-security-analysis-and-log-triage)
- [5. Detection and monitoring](#5-detection-and-monitoring)
- [6. Cloud and infrastructure security](#6-cloud-and-infrastructure-security)
- [7. Application and web security](#7-application-and-web-security)
- [8. Professional skills](#8-professional-skills)
- [How to use this without lying to yourself](#how-to-use-this-without-lying-to-yourself)
- [Companion pages](#companion-pages)
- [Link health](#link-health)
- [Contributing](#contributing)

## How to read the level tags

Every resource is tagged with the level at which it starts being useful:

- **[beginner]** — usable before you understand the field. Gets you operational, not expert.
- **[intermediate]** — assumes you have done the beginner work and have a system to practise on.
- **[advanced]** — specialist depth; usually assumes a job, a lab or a serious home setup.
- **[lab]** — you type commands or click through a scenario. Reading it is not the exercise.
- **`(paid)`** — no meaningful free tier for that specific resource. Everything unmarked is free or
  free-to-read.

A tag describes where a resource *starts*, not what you become. No single resource makes anyone advanced;
advanced is the point where you can do the thing on an unfamiliar system without a walkthrough, and then
explain how you know you were right.

## Skills at a glance

| # | Skill | Why it matters | How the levels usually go |
|---|-------|----------------|---------------------------|
| 1 | [Networking skills](#1-networking-skills) | Every log line, alert and architecture decision is a network in disguise. If TCP, DNS and HTTP are fuzzy, everything downstream is guesswork. | Read the model → capture and read real traffic → reason about failure, latency and evasion |
| 2 | [Linux and systems administration](#2-linux-and-systems-administration) | Most servers, sensors, containers and cloud hosts you defend are Linux. You cannot detect what you cannot operate. | Commands → services, permissions and logs → hardening and live forensics |
| 3 | [Scripting and automation](#3-scripting-and-automation) | Security work is data work: parsing, enriching, deduplicating, automating the boring 90%. Manual triage does not scale and is not trusted. | A script that runs → a script that fails safely and is reviewed → a tool others depend on |
| 4 | [Security analysis and log triage](#4-security-analysis-and-log-triage) | The raw material of every decision: is this malicious, what happened, what do we do in the next hour? | Read one log type → correlate across sources → reconstruct a timeline and prove it |
| 5 | [Detection and monitoring](#5-detection-and-monitoring) | An alert nobody wrote is an incident nobody catches. Detection is an engineering discipline, not a dashboard. | Understand a good signal → write and test a rule → measure, tune and decommission at scale |
| 6 | [Cloud and infrastructure security](#6-cloud-and-infrastructure-security) | In modern estates the perimeter is an IAM policy and the firewall is a security group. Misconfiguration, not malware, is the usual headline. | Read provider docs → least-privilege design → multi-account guardrails as code |
| 7 | [Application and web security](#7-application-and-web-security) | Most breaches begin in an application, and security review of code is a job that very few people can actually do. | OWASP vocabulary and a lab → find real bugs in authorized targets → design and review systems that resist them |
| 8 | [Professional skills](#8-professional-skills) | A finding nobody understands changes nothing. Writing, reporting and ethics turn technical truth into decisions. | Write clearly → report under pressure → brief decision-makers and hold the ethical line |

**Levels are not a ladder you climb once.** Most working security people are intermediate in four of these
and beginner in three. That is normal. The point of the table is to stop you from calling yourself advanced
in something you have never done on a system you did not build.

---

## 1. Networking skills

Networking is the skill that makes the other seven readable. The test is not whether you can recite the
OSI model — it is whether you can look at a capture or an alert and say what happened, what should have
happened, and what the difference tells you.

### What proficiency looks like

**Beginner**
- Can explain, without notes, what happens between typing a URL and seeing a page: DNS resolution, TCP
  handshake, TLS handshake, HTTP request and response.
- Can read an IP address, a subnet mask and a CIDR block, and can tell from a log line which host talked to
  which on which port and protocol.
- Knows the difference between TCP and UDP and can give one security-relevant consequence of each.

**Intermediate**
- Can capture traffic with `tcpdump` or Wireshark on a host you own, filter it to the conversation you care
  about, and reconstruct what was requested and returned.
- Can explain a firewall rule set as intent (what should reach what), spot rules that are broader than the
  intent, and predict what a given rule will do to a specific packet.
- Reads a DNS or TLS log and recognises the shapes that deserve a second look: unusual query types, long
  TXT records, connections to a hostname that was registered days ago.

**Advanced**
- Can reason about a network at design level: segmentation, least-privilege egress, where to place sensors,
  what a flat network costs you during an incident, and how each choice affects what you can detect later.
- Can diagnose from packet data alone — asymmetric routing, MTU and fragmentation problems, retransmission
  storms — and can tell the difference between "broken", "slow" and "being interfered with".
- Knows the limits of your own visibility: which traffic never reaches your sensors (encrypted, out-of-band,
  east-west in a network you do not tap) and says so instead of implying full coverage.

### Resources to move up a level

- <https://skillsforall.com/course/networking-basics> — free vendor-neutral networking course; the honest
  starting point if "subnet" still makes you uneasy. [beginner]
- <https://www.netacad.com/courses/networking-basics> — free course with ungraded labs and Packet Tracer;
  practice building small topologies instead of only reading about them. [beginner]
- <https://www.practicalnetworking.net/> — the "packet traveling" series, the clearest free explanation of
  what actually happens to a packet as it leaves a host. [beginner]
- <https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview> — HTTP from the people who write browser
  docs; the request/response model you will read out of logs every day. [beginner]
- <https://www.wireshark.org/docs/wsug_html_chunked/> — the official Wireshark user guide; the filter
  language is the part worth learning properly. [beginner] [lab]
- <https://gitlab.com/wireshark/wireshark/-/wikis/SampleCaptures> — real capture files (including malware
  traffic samples) you can open offline and practise interpreting. [intermediate] [lab]
- <https://www.tcpdump.org/manpages/tcpdump.1.html> — the `tcpdump` man page; on any server you will have
  `tcpdump` and not a GUI, so learn the flags from the source. [intermediate]
- <https://www.rfc-editor.org/rfc/rfc9293.html> — the current TCP specification. Dense, and the definitive
  answer every time somebody's blog contradicts what your capture shows. [intermediate]
- <https://www.rfc-editor.org/rfc/rfc1035.html> — the DNS specification: record types, message format and
  why DNS is the control channel of so much malicious traffic. [intermediate]

> **Authorized testing only.** Packet capture, port scanning and traffic manipulation are only legitimate on
> systems you own or have written permission to test — a lab you built, a deliberately vulnerable target, or
> your own employer's systems under a signed scope. Intercepting traffic on a network you do not administer
> is not "research".

**You're on track when…** someone hands you a capture or a firewall rule set you have never seen and you can
describe the conversation, name the protocol at each step, and point at one thing that looks wrong — and you
can say which of your conclusions are certain and which are inference.

---

## 2. Linux and systems administration

You will defend Linux long before you defend anything exotic. Sysadmin skill is what lets you install a
sensor, read its logs, know when a service is lying to you, and preserve a machine's state instead of
destroying it while "investigating".

### What proficiency looks like

**Beginner**
- Comfortable on the command line: navigate the filesystem, read man pages, use `grep`, `find`, `awk`/`sed`
  well enough to answer a question about a file.
- Can explain users, groups, file permissions and `sudo`, and can tell why a world-writable script in
  `/tmp` is a problem without being told.
- Knows where logs live (`/var/log`, journald) and how to filter them with `journalctl`.

**Intermediate**
- Can run a service properly: write a systemd unit, understand its dependencies and restart behaviour, and
  read `systemctl status` output without guessing.
- Can explain processes and privilege from the kernel's point of view — real vs effective UID, capabilities,
  namespaces — and use that to say why a container breakout or a privesc path is possible.
- Can install and troubleshoot real software from packages, read the errors instead of pasting them
  somewhere, and know when a problem is the app, the OS or the network.

**Advanced**
- Can harden a host from a benchmark, and justify every deviation: which control you skipped, what risk that
  accepted, and what compensating control you added.
- Can do live triage on a running system without destroying evidence: capture volatile state in the right
  order, use `auditd`/`bpftrace`-class visibility, and keep a record of everything you ran.
- Understands kernel and userland persistence surfaces well enough to look for what *should not be there* —
  unusual units, cron entries, capabilities on binaries, LD_PRELOAD — rather than only patterns a scanner
  already knows.

### Resources to move up a level

- <https://ubuntu.com/tutorials/command-line-for-beginners> — a careful, free tour of the shell for people
  who have only used GUIs; no assumptions about prior Unix. [beginner]
- <https://github.com/jlevy/the-art-of-command-line> — a dense, practical collection of command-line habits
  and traps; skim it once, then return when a one-liner gets ugly. [beginner]
- <https://www.gnu.org/software/bash/manual/bash.html> — the authoritative bash manual; quoting, expansion
  and exit status are where most self-taught shell scripts are dangerously wrong. [intermediate]
- <https://man7.org/linux/man-pages/man7/capabilities.7.html> — Linux capabilities explained from the source;
  the mental model behind most container and privilege-escalation discussions. [intermediate] [advanced]
- <https://man7.org/linux/man-pages/man5/sshd_config.5.html> — every SSH daemon option, including the ones
  that decide whether your host is a target or a wall. [intermediate]
- <https://man7.org/linux/man-pages/man5/systemd.exec.5.html> — sandboxing and hardening directives for
  services (`ProtectSystem`, `PrivateTmp`, `NoNewPrivileges`). The most useful hardening page most admins
  never open. [advanced]
- <https://github.com/linux-audit/audit-documentation/wiki> — the auditd documentation project: rule syntax
  and what the kernel can actually tell you, which is the backbone of Linux detection. [advanced]
- <https://www.kernel.org/doc/html/latest/admin-guide/sysctl/index.html> — every tunable kernel parameter.
  Half of "hardening a Linux server" is knowing which handful of these matter. [advanced]
- <https://www.cisecurity.org/cis-benchmarks> — the CIS Benchmarks, free PDFs per distribution. Use them as a
  checklist, then write down why you deviated on any line. [intermediate]
- <https://csrc.nist.gov/pubs/sp/800/123/final> — NIST's guide to securing a general-purpose server; verbose,
  but it teaches you to think in control families rather than tips. [intermediate]

**You're on track when…** you are handed an unfamiliar Linux host and can find out what it is, what it
talks to, what runs on it and what would break it — from the terminal, from memory, with the man pages as
your only reference. If you would need to search for "how to check open ports", you are still beginner.

---

## 3. Scripting and automation

Everyone in security writes scripts. The difference between levels is not language features, it is whether
your script can be trusted by somebody else: does it fail loudly, refuse to destroy data, log what it did,
and survive review?

### What proficiency looks like

**Beginner**
- Can write a Python or bash script that reads a file, parses it (JSON, CSV or a log format), and prints or
  writes a result — and can run it again after a bug without asking for help.
- Uses arguments instead of editing the file to change the target, and can explain what `set -euo pipefail`
  prevents in bash.
- Handles the obvious failure: file missing, network call fails, empty input.

**Intermediate**
- Structures work so it can be re-run: idempotent steps, clear exit codes, logging to a file, no hard-coded
  secrets, credentials from environment or a secret store.
- Can consume an API responsibly — pagination, rate limits, retries with backoff, and validating the
  response instead of trusting it.
- Uses version control and a linter/formatter, writes tests for the parts that matter, and treats a
  code review comment as information rather than an insult.

**Advanced**
- Designs automation as a product: who runs it, what it does on a bad day, how it is scheduled and
  monitored, how failures are reported, how it is deprecated and removed.
- Can read unfamiliar code and spot security-relevant patterns — unsafe deserialisation, command injection,
  secrets in source, unbounded input — and can say what an attacker gains from each.
- Knows when *not* to automate: one-off glue that hides an operational problem is a liability, and a script
  nobody owns becomes an undocumented privileged process.

### Resources to move up a level

- <https://docs.python.org/3/tutorial/index.html> — the official Python tutorial. Boring, complete and the
  fastest route to code that does what it says. [beginner]
- <https://docs.python.org/3/howto/argparse.html> — turning a throwaway script into a command with real
  arguments, defaults and help text. [beginner]
- <https://peps.python.org/pep-0008/> — the style guide the rest of the ecosystem reads by; matching it makes
  your code reviewable. [intermediate]
- <https://docs.astral.sh/ruff/> — a fast linter and formatter; run it before every commit and stop arguing
  about style in review. [intermediate]
- <https://docs.pytest.org/en/stable/> — the standard Python test framework. One test that exercises your
  parser is worth more than a page of comments claiming it works. [intermediate]
- <https://google.github.io/styleguide/shellguide.html> — shell is where security scripts go wrong quietly;
  this guide is the antidote for quoting, error handling and exit codes. [intermediate]
- <https://cheatsheetseries.owasp.org/cheatsheets/Secrets_Management_Cheat_Sheet.html> — how to keep
  credentials out of scripts and repositories, and what to do after one leaks. [intermediate]
- <https://crontab.guru/> — a scheduler-expression explainer; pair it with a real cron or systemd timer so
  your automation runs when you are asleep. [beginner]
- <https://docs.github.com/en/actions> — scheduled, auditable automation in a repository: the practical way
  to publish recurring data work where others can see what it does. [intermediate] [advanced]
- <https://learn.microsoft.com/en-us/powershell/scripting/overview> — PowerShell is unavoidable in mixed
  estates; learn it once and stop treating Windows automation as somebody else's problem. [intermediate]

**You're on track when…** a colleague you have never met can take your script, run it against their own
data, get the same kind of result, and debug it from its own logs and errors — without a single question to
you. If only you can run it, you have written a personal habit, not automation.

---

## 4. Security analysis and log triage

This is the skill entry-level roles are actually hired for, and it is the one most often faked with tool
knowledge. Tools change; the ability to take an ambiguous pile of evidence and reach a defensible conclusion
does not.

### What proficiency looks like

**Beginner**
- Can read a single log source (auth logs, web access logs, EDR process events) and answer a specific
  question from it without help.
- Knows the difference between an indicator and a conclusion, and can describe what a suspicious event looks
  like in terms of the data rather than in terms of the tool that flagged it.
- Writes down what was checked and what was not; says "unknown" when the data does not support an answer.

**Intermediate**
- Correlates across sources — endpoint, authentication, network, cloud audit — and builds a timeline of a
  small incident with timestamps normalised to one timezone.
- Enriches before judging: what is this host, is it internet-facing, is this process signed, does this domain
  appear in threat intel, and what does the baseline say this system normally does.
- Triages realistically: recognises a benign-but-noisy pattern, closes it with a reason, and escalates when
  the evidence justifies it instead of when a tool says so.

**Advanced**
- Reconstructs an intrusion from partial telemetry, states the confidence level of each claim, and separates
  what the data proves from what is plausible narrative.
- Recognises when the answer is *missing data* — the log was rotated, the sensor was down, the field was not
  collected — and treats that gap as a finding in itself.
- Can brief a decision-maker on a live incident in two minutes: what we know, what we do not, what we are
  doing next, what we need from them.

### Resources to move up a level

- <https://attack.mitre.org/> — MITRE ATT&CK: the shared vocabulary for what an adversary is doing. Learn to
  map an observed event to a technique, not the other way round. [beginner]
- <https://www.first.org/cvss/> — CVSS, and more importantly its specification: what a score does and does
  not tell you about your exposure. [beginner]
- <https://zeltser.com/security-incident-log-review-checklist/> — a free incident log review checklist from
  SANS instructor Lenny Zeltser; use it as the structure of your first 50 triages. [beginner]
- <https://docs.splunk.com/Documentation/Splunk/latest/SearchTutorial/WelcometotheSearchTutorial> — the
  official Splunk search tutorial; the search language matters less than learning to ask questions of data in
  order. [beginner]
- <https://www.elastic.co/guide/en/kibana/current/kuery-query.html> — Kibana Query Language, so you can work
  in the other very common stack without re-learning the concept. [beginner]
- <https://github.com/logpai/loghub> — free real-world log datasets (HDFS, OpenSSH, Apache, Windows and
  more) to practise parsing and anomaly-hunting offline. [intermediate] [lab]
- <https://github.com/OTRF/Security-Datasets> — labelled datasets of simulated adversary activity mapped to
  ATT&CK: run your analysis against data where the answer is known. [intermediate] [lab]
- <https://www.malware-traffic-analysis.net/> — a long-running public archive of malicious traffic with
  write-ups; practise identifying the infection chain in a capture before reading the answer. [intermediate] [lab]
- <https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html> — the STIX 2.1 specification: how
  structured threat intelligence is represented, which is what makes it automatable. [advanced]
- <https://csrc.nist.gov/pubs/sp/800/61/r2/final> — NIST's incident handling guide; the vocabulary and
  phases your incident reports are expected to follow. [intermediate]

**You're on track when…** you are given an alert you have never seen, from a tool you do not use, and you can
reach "malicious / benign / insufficient data" with a written trail of queries, normalised timestamps, and one
clear statement of what would change your mind. Guessing right does not count.

---

## 5. Detection and monitoring

Detection is engineering: a rule is a small program with inputs, a false-positive rate and a maintenance
cost. The advanced part is not writing more rules, it is knowing which ones earn their place.

### What proficiency looks like

**Beginner**
- Can explain, for one alert, exactly what data it needs and what would make it fire — and what would make it
  fire for innocent reasons.
- Knows the shape of good evidence: fields that are actually populated, timestamps in a known timezone,
  process parents and command lines preserved.
- Understands that logs are a pipeline (source → transport → parser → storage → query) and can find where a
  missing event got lost.

**Intermediate**
- Writes maintainable detection logic (Sigma-style, or native to your platform) with documented intent,
  known false positives and a test case.
- Tests against real or labelled data before shipping — including a deliberate benign case — instead of
  waiting for production to tell you.
- Maps detections to ATT&CK to find coverage gaps, and can say which techniques you cannot currently see
  at all.

**Advanced**
- Runs detections like software: versioned, reviewed, tested, measured (true/false positive rate, time to
  detect) and periodically retired when they stop earning their cost.
- Designs the telemetry, not just the rule: knows that the decision to log a field is a detection decision
  made months earlier, and specifies what to collect for the threats that matter.
- Validates coverage with safe adversary emulation in your own environment, in writing and with approval, and
  records the gap between what the technique did and what the detection saw.

### Resources to move up a level

- <https://sigmahq.io/> — Sigma: a vendor-neutral rule format so what you write is not locked to one SIEM;
  the site explains the format and the tooling around it. [beginner]
- <https://github.com/SigmaHQ/sigma> — the Sigma rule repository itself; reading thousands of real rules is
  the fastest way to learn what a good rule looks like. [intermediate]
- <https://github.com/mitre-attack/attack-navigator> — ATT&CK Navigator: draw your coverage, and use the map
  to argue about priorities with evidence instead of opinion. [intermediate]
- <https://github.com/elastic/detection-rules> — production detection rules with test data and documented
  false positives; a good model for how to ship a rule responsibly. [intermediate]
- <https://www.elastic.co/guide/en/security/current/detection-engine-overview.html> — how a commercial
  detection engine actually consumes rules, alerts and exceptions. [intermediate]
- <https://docs.suricata.io/en/latest/> — Suricata: network IDS/IPS rules, protocol parsing and the honest
  limits of signature detection. [intermediate] [lab]
- <https://github.com/zeek/zeek> — Zeek turns packets into structured logs; the standard way to get network
  evidence you can actually query. [intermediate] [lab]
- <https://github.com/redcanaryco/atomic-red-team> — small, documented, safe tests of individual techniques
  so you can prove a detection fires rather than assume it. [advanced] [lab]
- <https://github.com/palantir/alerting-detection-strategy-framework> — how to prioritise what to detect at
  all, based on what would actually harm you. The thinking behind the rules. [advanced]
- <https://github.com/DataDog/stratus-red-team> — cloud adversary emulation with detonation, cleanup and
  recorded output: validation for cloud detections specifically. [advanced] [lab]

> **Authorized testing only.** Adversary emulation, atomic tests and red-team tooling belong in an
> environment you own or are contracted to test, with written approval and a rollback plan. Running them
> against systems or tenants you do not administer is unauthorized access, and it is also how people destroy
> the evidence they were trying to collect.

**You're on track when…** for any detection you own you can state what it detects, which real technique that
corresponds to, how often it fires benignly, and what test proves it still works — and when asked for the
gaps, you can name techniques you cannot see rather than claiming full coverage.

---

## 6. Cloud and infrastructure security

Cloud security punishes people who learned security before infrastructure became an API. Identity is the
perimeter, misconfiguration is the common incident, and the only sustainable answer is guardrails expressed
as code.

### What proficiency looks like

**Beginner**
- Knows the shared responsibility model for at least one provider and can say which of a given problem's
  causes are yours.
- Can explain identity objects — user, role, policy, trust — and why a wildcard action on a wildcard
  resource is usually a finding.
- Can read a storage bucket/container access setting and an inbound firewall rule and say whether the
  resource is exposed to the internet.

**Intermediate**
- Designs least-privilege access with scoped roles, no long-lived keys where temporary credentials are
  available, and can explain an access-denied error from the policy evaluation, not by trial and error.
- Enables and reads the audit trail (CloudTrail/Activity Log/audit logs), writes queries against it, and
  knows which events matter for detection.
- Hardens the fundamentals: encryption in transit and at rest, private networking paths, centralised logging,
  key rotation, and workload identity for CI systems rather than stored credentials.

**Advanced**
- Designs multi-account/multi-project estates with organisational policy as code: guardrails that make the
  insecure configuration impossible instead of merely detected later.
- Threat-models the control plane: what an attacker does with a stolen role versus a stolen key, what
  privilege-escalation paths exist between identities, and what your blast radius is per identity.
- Automates compliance and evidence: reproducible infrastructure, policy-as-code checks in the pipeline,
  drift detection, and an honest account of what your controls do not cover.

### Resources to move up a level

- <https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html> — AWS's own IAM best practices;
  read it as the design brief for every permission decision you make. [beginner]
- <https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html> — the Security Pillar of
  the Well-Architected Framework: architecture-level security, not click-ops tips. [intermediate]
- <https://learn.microsoft.com/en-us/azure/security/benchmarks/overview> — the Azure Security Benchmark: the
  control set Azure expects you to meet, and a useful checklist for any cloud. [intermediate]
- <https://cloud.google.com/docs/security> — Google Cloud's security documentation hub; the IAM and VPC
  material is written clearly enough to learn the concepts from. [beginner]
- <https://kubernetes.io/docs/concepts/security/> — the official Kubernetes security concepts; start here
  before any third-party hardening guide. [intermediate]
- <https://kubernetes.io/docs/concepts/security/secrets-good-practices/> — how Kubernetes secrets actually
  behave and why "put it in a Secret" is not encryption. [intermediate]
- <https://github.com/aquasecurity/kube-bench> — runs the CIS Kubernetes benchmark against a cluster and
  reports where you fail. [intermediate] [lab]
- <https://github.com/aquasecurity/trivy> — one scanner for container images, filesystems, IaC and
  dependencies; put it in CI, not in a quarterly report. [beginner] [intermediate]
- <https://github.com/bridgecrewio/checkov> — static analysis for Terraform, CloudFormation and Kubernetes
  manifests: catch the misconfiguration before it is deployed. [intermediate]
- <https://cloudsecurityalliance.org/artifacts/cloud-controls-matrix-v4> — the CSA Cloud Controls Matrix: a
  shared control vocabulary for cloud, useful when you need to answer "which control covers this?".
  [advanced] (paid membership unlocks extras — the published matrix is free to read)
- <https://csrc.nist.gov/pubs/sp/800/207/final> — NIST SP 800-207, zero trust architecture. The reference
  definition behind the marketing. [advanced]

**You're on track when…** you can be handed an unfamiliar cloud account and, within an hour, say which
identities can take what action on what resource, what is exposed to the internet, where the audit trail
goes, and what a compromised workload could reach next.

---

## 7. Application and web security

Application security is the skill with the widest gap between "has read about it" and "can do it". The
differentiator is not knowledge of the top-ten list — everyone has that — it is being able to find a real bug
in a system you are authorized to test, and to design and review systems so that class of bug stops
recurring.

### What proficiency looks like

**Beginner**
- Can explain the OWASP Top 10 categories with a concrete example of each, and name the root cause rather
  than the symptom (e.g. output encoding, not "XSS").
- Can read a HTTP request and response and identify where untrusted input enters and where it is reflected,
  stored or executed.
- Knows the difference between authentication, authorization and session management, and why confusing them
  is the source of most web bugs.

**Intermediate**
- Can find real vulnerabilities in a deliberately vulnerable application you are authorized to test —
  including one you did not find with a scanner — and write it up with reproduction steps and impact.
- Can read source code for security-relevant patterns: string-concatenated queries, unsafe
  deserialisation, missing authorization checks on endpoints, secrets in repositories.
- Can explain how to fix a class of bug and where in the lifecycle the fix belongs (design, library,
  framework, pipeline check) so it cannot come back.

**Advanced**
- Threat-models a system before it is built and gets the mitigations into the design; reviews APIs,
  authentication flows and authorization models and finds the broken assumptions between components.
- Builds the programme around it: secure defaults, reusable libraries, review gates, security requirements in
  tickets, and metrics that measure real risk reduction rather than number of findings.
- Judges severity honestly, in the context of the deployment — a critical CVSS in an unreachable internal
  service is not the same finding as a medium one in an internet-facing login.

### Resources to move up a level

- <https://owasp.org/www-project-top-ten/> — the OWASP Top 10: the shared vocabulary. Learn the categories,
  then read the CWEs behind them. [beginner]
- <https://cheatsheetseries.owasp.org/> — the OWASP Cheat Sheet Series: the practical "how do we actually
  implement this" reference. Bookmark the authentication, authorization and input-validation sheets.
  [beginner] [intermediate]
- <https://developer.mozilla.org/en-US/docs/Web/Security> — MDN's web security section: browser behaviour
  explained by the people documenting the platform. [beginner]
- <https://github.com/OWASP/owasp-vwad> — the OWASP Vulnerable Web Application Directory: a curated list of
  deliberately vulnerable applications to practise against legally. [beginner] [lab]
- <https://github.com/juice-shop/juice-shop> — OWASP Juice Shop: a modern, deliberately vulnerable app with
  a built-in progress system. The standard first target. [beginner] [lab]
- <https://portswigger.net/web-security> — PortSwigger's Web Security Academy: a large, genuinely free
  lab-backed curriculum covering every major vulnerability class. [beginner] [intermediate] [lab]
- <https://portswigger.net/web-security/learning-paths> — structured paths through the academy, so you
  practise in a sensible order instead of bouncing between topics. [intermediate] [lab]
- <https://cwe.mitre.org/top25/archive/2024/2024_cwe_top25.html> — the CWE Top 25 most dangerous software
  weaknesses, ranked from real vulnerability data; the root causes behind the symptoms. [intermediate]
- <https://owasp.org/www-project-web-security-testing-guide/> — the WSTG: the reference methodology for
  testing a web application, and a good template for your own test reports. [intermediate]
- <https://github.com/OWASP/API-Security> — the OWASP API Security Top 10: where modern applications actually
  break, and why authorization at object level is the recurring failure. [advanced]
- <https://owasp.org/www-project-application-security-verification-standard/> — ASVS: a requirements
  standard you can verify against, and the honest way to say what level of assurance an application has.
  [advanced]

> **Authorized testing only.** Every offensive technique here exists to be used against a deliberately
> vulnerable application, a lab you built, a bug-bounty programme whose rules define your scope, or a client
> system with signed written authorization. Testing without authorization is a crime in most jurisdictions
> regardless of intent, and "I was only checking" is not a defence. When you do test, stay inside the
> published scope: the out-of-scope host is usually the production one.

**You're on track when…** you can take an application you have never seen, find a real vulnerability in it
using your own reasoning, prove it with a minimal reproduction, explain the fix at the right layer — and
write it so a developer who does not like you still acts on it.

---

## 8. Professional skills

The most common reason good technical work fails is not technical. It is a report nobody read, a finding
written in a way that made an engineer defensive, a risk left unstated because it was uncomfortable, or a
boundary crossed because nobody wrote down what was authorized.

### What proficiency looks like

**Beginner**
- Writes short, structured updates: what happened, what it means, what you need, by when — with no filler and
  no unearned certainty.
- Separates observation from interpretation in writing, and names the confidence behind each.
- Reads a scope document or an authorization email and can say what is *not* permitted, not just what is.

**Intermediate**
- Writes incident reports and findings that survive review: reproducible steps, affected systems, honest
  impact, prioritised remediation, and clearly labelled assumptions.
- Explains technical risk to a non-technical decision-maker in their terms — cost, exposure, effort — without
  exaggerating and without softening a real risk into nothing.
- Handles the human part: says "I was wrong" or "I do not know" cleanly, gives feedback on someone's work
  without making it personal, and writes documentation that outlives their memory of the system.

**Advanced**
- Runs the conversation in a crisis: briefs executives under uncertainty, keeps an accurate record, and
  protects the integrity of the evidence while people above them want a conclusion earlier than the data
  supports.
- Sets and defends ethical lines in writing — scope, data handling, disclosure timelines, what the team will
  not do — and knows the escalation path when asked to cross one.
- Writes for the field, not just for one employer: internal standards, public research, mentoring, and
  contributions that other practitioners can build on.

### Resources to move up a level

- <https://www.plainlanguage.gov/guidelines/> — the US federal plain-language guidelines. Apply the "audience
  and purpose" sections to every incident report you write. [beginner]
- <https://www.isc2.org/ethics> — the (ISC)² code of ethics, free to read: the professional-conduct
  commitments that practitioners are held to, including the duty to disclose conflicts. [beginner]
- <https://learn.microsoft.com/en-us/style-guide/welcome/> — Microsoft's Writing Style Guide: concise,
  actionable rules for the interface and documentation writing you will be asked to produce. [intermediate]
- <https://developers.google.com/style> — Google's developer documentation style guide, with a strong
  "second person, active voice, no marketing" bias. A good counterweight to defensive writing. [intermediate]
- <https://sre.google/sre-book/postmortem-culture/> — blameless postmortem culture from the Google SRE book:
  the single most useful chapter for writing incident reviews that improve systems instead of assigning
  blame. [intermediate]
- <https://www.first.org/tlp/> — FIRST's Traffic Light Protocol 2.0: the standard for marking how sensitive
  information may be shared, used in every incident and threat-intel exchange. [intermediate]
- <https://www.nist.gov/cyberframework> — the NIST Cybersecurity Framework: the common language for
  describing risk posture to management, auditors and customers. [intermediate]
- <https://verizon.com/business/resources/reports/dbir/> — the annual Data Breach Investigations Report: free
  and long-running, and the model for evidence-based reporting rather than anecdote. [intermediate]
- <https://csrc.nist.gov/pubs/sp/800/181/r1/final> — NIST SP 800-181r1, the Workforce Framework for
  Cybersecurity Work (NICE): the standard vocabulary for tasks and skills per role, and a sober way to assess
  your own gaps. [advanced]

**You're on track when…** a report you wrote is acted on by someone who was not in the room, an engineer
whose code you criticized thanks you for the finding rather than defending it, and you have refused — in
writing — to do something that was out of scope or unethical.

---

## How to use this without lying to yourself

- **Pick two skills, not eight.** Rate yourself honestly in each, then spend a quarter on the one where the
  self-check fails. Breadth without a single defensible specialism is the standard junior profile.
- **Score on artifacts, not feelings.** "I could probably do it" is beginner. "Here is where I did it, with
  the output, and here is why the conclusion is sound" is intermediate or above.
- **Re-check every six months.** Level definitions do not move; you do, in both directions if a skill goes
  unused for a year.
- **One project can hit several skills.** A home lab where you collect logs, write a detection, break down a
  vulnerable app and write it up touches skills 2, 4, 5 and 7 at once, and gives you written evidence for
  all of them. See [From skills to evidence](docs/SKILLS-TO-EVIDENCE.md).
- **The gaps are the point.** Knowing that you are beginner in cloud while intermediate in detection is more
  useful than a score, because it tells you what the next quarter is for.

## Companion pages

- [Skill matrix for common security roles](docs/SKILL-MATRIX.md) — which of the eight skills each role leans
  on, and the level that is typically expected, so you can target a role rather than a topic list.
- [From skills to evidence](docs/SKILLS-TO-EVIDENCE.md) — how to demonstrate each skill with a real,
  reproducible artifact instead of a claim, including how to write it up honestly.

## Link health

Every external URL in this repository was checked with `curl` immediately before publication:

```bash
curl -sIL -o /dev/null -w '%{http_code}\n' --max-time 25 \
  -A 'Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/124 Safari/537.36' \
  '<url>'
```

Two documented exceptions, both of which answer `200` to a normal request:

- **`portswigger.net/web-security/*`** returns `404` to `HEAD` while returning `200` to `GET`. Both
  PortSwigger links here were re-verified with `curl -sL`, not dropped.
- **`docs.zeek.org`** rate-limits automated checks (HTTP 429), so the Zeek entry points at the project's
  GitHub repository instead, which resolves reliably.

`403` responses (bot protection on an ordinary page) and any other non-`200` result were not shipped.

## Contributing

Corrections, better primary sources and new labs are welcome — see [CONTRIBUTING.md](CONTRIBUTING.md). The
short version: verify the link with `curl`, no affiliate or referral links, label anything paid, keep the
defensive-first ethics rule, and do not invent numbers.

## License

MIT — see [LICENSE](LICENSE). Copyright (c) 2026 Virtual Traders.
