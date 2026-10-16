# AI Security Journey

Hands-on notes on attacking and defending LLM systems, written from a blue-team perspective.

**Author:** Silivia Nduta Kamau | [LinkedIn](https://linkedin.com/in/silvia-nduta-414230311) | [GitHub](https://github.com/hackhersecure)

## Focus
Jailbreaking and guardrail bypass: how these attacks work, how they get detected, and how to mitigate them.

## Contents
| Folder | What's inside |
|---|---|
| `writeups/` | Practice writeups (Gandalf by Lakera) |
| `defense/` | Detection and mitigation notes |

## Method
For every attempt I record: the target, the technique, the exact approach, the result, and what a defender could do about it.

## Ethics
I only test systems I'm authorised to test: practice labs, CTFs, and my own setups.

## Status
- [ ] Gandalf writeup (in progress)
- [ ] Defense notes (draft)


---

## Gandalf (Lakera) Writeup

**Target:** Gandalf, a practice game where you trick an AI into revealing a secret password.
**Category:** Jailbreaking / guardrail bypass, direct prompt injection
**Date:** TODO

### Summary
TODO: 2-3 sentences. Levels completed, overall approach, key lesson.

### Level notes
Copy this block for each level.

#### Level N
- **Defense in place:** TODO (e.g. told not to reveal password, output filter, input filter)
- **Technique tried:** TODO (e.g. roleplay, indirect ask, partial reveal, encoding)
- **Prompt used:** TODO
- **Result:** TODO (passed / failed)
- **Why it worked or failed:** TODO

### What I learned
- TODO

### How a defender could catch this
- TODO (link to `defense/detection-and-mitigation.md`)


---

## Detection and Mitigation: Jailbreaks and Prompt Injection

### Common jailbreak patterns
- **Roleplay / persona framing:** "Pretend you are a character with no rules."
- **Hypotheticals and fiction:** wrapping a blocked request in a story.
- **Instruction override:** "Ignore previous instructions."
- **Indirect extraction:** asking for the secret in pieces, hints, or transformed form.
- **Encoding tricks:** asking for output in another language, cipher, or format to dodge filters.

### Detection ideas (blue-team view)
- Log all prompts and responses with timestamps and user/session IDs.
- Flag known phrases (e.g. "ignore previous instructions") and repeated retries with small variations.
- Alert on responses that contain protected strings, even if transformed.
- Watch for sessions with unusually many refusals followed by a success.

### Mitigations
- Layered defenses: input filtering, output filtering, and a separate checker model.
- Least privilege: never put real secrets in the system prompt.
- Rate limiting and session monitoring.
- Regular red-team testing against known jailbreak patterns.

### Frameworks to map to
- OWASP Top 10 for LLM Applications (LLM01: Prompt Injection)
- MITRE ATLAS
