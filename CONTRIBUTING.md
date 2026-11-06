# Contributing

Thanks for helping make this guide better. This repository is a curated skill taxonomy: every link costs a
reader a click, so the bar for adding or changing one is deliberately high.

Two things define the quality bar here:

1. **Every resource is placed at a level.** Say which level it starts at (`[beginner]`, `[intermediate]`,
   `[advanced]`) and why it belongs there. A link with no reason gets sent back.
2. **Levels are described in behaviour, not titles.** No "3 years of experience" claims, no salary or
   outcome guarantees, no popularity metrics. If it cannot be observed, it does not go in.

## The ethics rule (non-negotiable)

This project is defensive-first and authorized-practice-only. It teaches security work inside the legal
frame: **only test systems you own or have explicit written permission to test.**

- No content that enables attacks on systems the reader is not authorised to test — no exploit code aimed at
  third-party software, no payloads, no credential dumps, no target lists, no evasion or bypass recipes, no
  cracked or licence-dodging copies of commercial tools.
- Hands-on resources must point at a lab that is designed to be attacked (a practice platform, an
  intentionally vulnerable application, a wargame) or at the reader's own infrastructure.
- Offensive topics appear only as authorized practice, and each section that contains them must keep its
  **Authorized testing only** note. Do not remove that line.
- Anything that treats curiosity, good intent or "white hat" framing as permission will be declined.

## Link rules

1. **Verify the link with `curl` before opening the pull request.** A link that works in your browser and
   fails under `curl` is not verified:

   ```bash
   curl -sIL -o /dev/null -w '%{http_code}\n' --max-time 25 \
     -A 'Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/124 Safari/537.36' \
     '<your-url>'
   ```

   `200` is what we ship. `403` usually means bot protection on a real page — if you keep it, say so in your
   pull request and confirm you opened it yourself. `404`, `410` and `451` links are dropped. Some hosts
   answer `HEAD` with `404` while `GET` returns `200` (`portswigger.net` does this under `/web-security/*`),
   so re-check any `404` with `curl -sL` before dropping the URL.
2. **No affiliate, referral or tracking links.** No `?ref=`, no coupon codes, no link shorteners.
3. **No paywalled-only resources** unless the entry itself says so, plainly ("paid exam voucher", "free tier
   with a paid option"). Free tiers and free-to-read material are preferred.
4. **Prefer primary sources**: official documentation, standards bodies (NIST, CISA, OWASP, MITRE, FIRST,
   CIS) and maintained open-source projects over listicles and SEO content.
5. **Ban your own invention.** No fabricated benchmarks, adoption numbers, "trusted by" claims, star counts
   or user counts — not in the README, not in a doc, not in a pull request description. If you cite a number,
   it must be measured locally and the method has to be in the same paragraph.

## Structural rules

- Keep the eight-skill structure. A new skill must replace or genuinely extend one; we are not growing this
  into a topic dump, and nine half-skills are worse than eight real ones.
- Every skill section keeps its four parts: **What proficiency looks like** (beginner / intermediate /
  advanced, three concrete levels), **Resources to move up a level** (5–10 verified links, each with a
  one-line reason and a level tag), the **You're on track when…** self-check, and — where offensive practice
  appears — the authorized-only note.
- Aim for 5–10 links per skill, at least one per level where an honest one exists.
- Do not duplicate the sequential pathway content from
  [`virtualtradrs/cybersecurity-roadmap`](https://github.com/virtualtradrs/cybersecurity-roadmap). This
  repository answers "what does this skill consist of and how do I know my level"; that one answers "what
  order do I learn it in".
- Check your own anchors before pushing. GitHub lowercases headings, drops punctuation and turns spaces into
  hyphens, so `## 3. Scripting and automation` is reachable as `#3-scripting-and-automation`.

## Pull requests

- One skill or one document per pull request where you can; explain what you added, at which level, and paste
  the `curl` output for each new link.
- Say explicitly what you removed, if anything, and why.
- Keep the tree clean: no editor backups, no scratch files, no data you cannot re-create.

## License

By contributing you agree that your contribution is licensed under the MIT License (see [LICENSE](LICENSE)).
