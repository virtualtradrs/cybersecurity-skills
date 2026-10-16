# From skills to evidence

A claim of skill is worth what someone can check. This page gives, for each of the eight skills in the
[main guide](../README.md), one artifact you can actually produce, the test that tells you it is finished, and
how to write it up so a stranger can reproduce it.

The rule underneath all of it: **write down what you did, show the output, and state the limits.** A modest
artifact with honest boundaries beats an ambitious claim with none.

## What every write-up should contain

Five short sections, in this order. If a section has nothing in it, say so — an empty section is information.

1. **Question.** What were you trying to find out, and in one sentence why it interested you.
2. **Setup.** The system, versions, data and scope — enough that someone else can rebuild it. State the
   authorization: your own machine, a practice target, or a signed engagement (then keep it anonymised).
3. **What you did.** The commands and queries, in order, with the output that mattered. Not a tutorial —
   your trail.
4. **What you concluded, and how sure you are.** Separate what the data proves from what you infer.
5. **What is missing.** What you could not see, what you did not test, what would change the conclusion.

### Non-negotiables

- **Redact before you publish.** No real credentials, hostnames, customer data, internal IP ranges, employee
  names or client identifiers. If you cannot redact it convincingly, do not publish it.
- **No invented numbers.** If you say "87% of alerts were benign", your own data and the counting method
  belong in the same document. Otherwise leave it out.
- **Label practice as practice.** Lab work is evidence of *your ability to do the work*, not of production
  experience. Say "in my lab" and say it plainly.
- **Keep the failures.** A section on what did not work is the most credible part of the write-up, and the
  most useful for the next person reading it.

## One artifact per skill

| Skill | Artifact that proves it | It is finished when… |
|-------|-------------------------|----------------------|
| 1. [Networking](../README.md#1-networking-skills) | A short capture analysis: take one conversation from a test machine or a public capture file, and explain each protocol step plus one anomaly | You can name the anomaly, show the packets that support it, and say what you cannot tell from this capture |
| 2. [Linux and systems administration](../README.md#2-linux-and-systems-administration) | A hardened host build: a small VM or container, a benchmark applied, with your deviations justified | The build is reproducible from a script or config file you wrote, and every deviation from the benchmark has a reason |
| 3. [Scripting and automation](../README.md#3-scripting-and-automation) | A log-parsing tool with tests: input, output, error handling, a README and a scheduled run | Someone else can install and run it from your README alone, and it fails loudly on bad input |
| 4. [Security analysis and log triage](../README.md#4-security-analysis-and-log-triage) | A triage report on a labelled public dataset or capture, where the answer is known | Your timeline is normalised to one timezone, each claim cites the evidence, and you state what you could not determine |
| 5. [Detection and monitoring](../README.md#5-detection-and-monitoring) | One detection rule plus its test: rule, mapping to a technique, one true positive and one documented benign case | You have run the rule against real or labelled data and reported both outcomes, not just the hit |
| 6. [Cloud and infrastructure security](../README.md#6-cloud-and-infrastructure-security) | A guardrail in a free-tier account: infrastructure as code with a policy check that fails the build on a misconfiguration | The insecure version demonstrably fails and the fixed version passes, both shown in the same document |
| 7. [Application and web security](../README.md#7-application-and-web-security) | A finding against a deliberately vulnerable app you are authorized to test, written up as a report | Reproduction steps are minimal, impact is stated for the real deployment context, and the fix is proposed at the right layer |
| 8. [Professional skills](../README.md#8-professional-skills) | A polished report or a postmortem of a lab incident, written for a reader who was not present | Someone unfamiliar with the work can act on it without asking you a question, and it contains no unearned certainty |

## Turning artifacts into a portfolio

- **One artifact beats five sketches.** Two well-documented artifacts, each with their limitations stated,
  read better than eight half-finished repositories.
- **Name the repository for the question, not the technology.** `auth-log-anomaly-report` tells a reader
  something; `security-stuff` does not.
- **Put the honest summary at the top of the README.** What it does, what it does not do, what it is not a
  substitute for. Readers trust the limits more than the features.
- **Link the skills explicitly.** One line in the README — "this exercises log parsing (skill 3) and detection
  testing (skill 5)" — helps a reviewer see the point without reading everything.
- **Keep the raw evidence where it is allowed to be public**, and say where the rest lives if it cannot be.
- **Do not pad for activity.** A commit that adds nothing is worse than an empty week; nobody reading your
  work is counting commits.
- **Do not copy a walkthrough and call it yours.** Cite what you learned from, then extend it with something
  you found yourself. The extension is the evidence.

## What does not count as evidence

- A certificate alone — it is evidence you studied, and useful as a filter, but it does not show you can do
  the work.
- A list of tools you have heard of, or a lab you started and never finished.
- An exploit someone else wrote, run once against a target you did not have permission to touch.
- A write-up with no output, no scope and no limits — which is most of them.
- Any number you cannot reproduce from your own data.
