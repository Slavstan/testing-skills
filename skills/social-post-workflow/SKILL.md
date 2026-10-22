---
name: social-post-workflow
description: Orchestrate the analyzer, copywriter, and optimizer skills to create a fact-grounded, platform-appropriate social post from a short brief. Use when the user asks for an end-to-end social post or to run the social-post skills together.
---

# Social Post Workflow

## Purpose

Create one publication-ready social post by applying the three stage skills in order. Keep intermediate analysis, JSON, drafts, and handoff notes internal unless the user explicitly asks to see them.

## Required stage instructions

Read and follow all three files before processing the brief:

1. `../social-post-analyzer/SKILL.md` — extract facts and create the structured brief.
2. `../social-post-copywriter/SKILL.md` — write one draft from that brief.
3. `../social-post-optimizer/SKILL.md` — finalize the draft with platform-aware editing, a suitable CTA, hashtags, and final checks.

Resolve paths relative to this workflow's directory under `skills/`. If the environment can invoke named skills directly, invoke them in order. Otherwise, follow their files sequentially. Never claim that separate skills were independently executed if you only followed their instructions in one orchestrated run. If any required file is unavailable, say so briefly and do not claim full workflow execution; you may still help using the instructions that are available.

## Input handling

Accept ordinary text, structured fields, or a supplied draft. Use available information about:

- Company or brand
- Product or service
- Target audience
- Social platform
- Confirmed product facts and approved claims
- Optional campaign goal, existing draft, destination URL, offer, preferred CTA, and brand voice

Do not require JSON from the user. Normalize obvious spelling errors only when the intended meaning is clear; do not silently reinterpret ambiguous audience or product descriptions. If the product or service cannot be identified, ask one concise clarifying question. If audience or platform is missing, continue with a conservative general-purpose result when useful and disclose the limitation only if it materially affects the post.

## Execution contract

1. Read the stage instructions; do not edit skill files during an ordinary workflow run.
2. Run the analyzer internally and retain its valid JSON brief.
3. Give that brief to the copywriter and retain one draft.
4. Give the original brief and draft to the optimizer.
5. Check the optimizer's result against the user's original input. Remove or qualify unsupported claims, fabricated offers, fake links, testimonials, certifications, product specifications, and promises of reach or engagement.
6. Preserve the user's requested language, brand spelling, campaign goal, and any explicit constraints unless they conflict with factual accuracy or safety.
7. Do not turn inferred benefits into verified product claims. Treat a claim as confirmed only when supplied by the user or supported by a source the task explicitly authorizes and that was actually checked.
8. A CTA must be actionable without inventing a destination, availability, offer, or link. If a destination is missing, use a low-pressure generic CTA or state what should be supplied.
9. If a missing detail prevents a safe or useful result, ask one concise question. Otherwise, produce a conservative post and mention only material limitations.
10. This workflow creates copy only. Do not publish, schedule, message, or modify external accounts unless a suitable integration is available and the user explicitly requests that action.

## Final response

Default to the optimizer's output structure:

- **Platform**
- **Final post** with one suitable CTA and a small, relevant set of hashtags
- **Final checks** covering CTA, hashtags, factual accuracy, and any open item

If the user explicitly asks to see only the post/caption, return only the copy-ready post and omit the headings and checks. If the user asks for an audit or explanation, provide that separately without exposing intermediate stage outputs unless requested. Do not show analyzer JSON, the first draft, internal reasoning, or progress updates by default.

## Quality checklist

Before responding, verify:

- All three stages were applied in order, or any missing-file/tool limitation is disclosed accurately.
- The final copy matches the user's language, brand, audience, platform, and goal as far as the brief allows.
- Every factual product claim is grounded in supplied or actually verified information.
- CTA and hashtags are relevant and do not imply unsupported claims, offers, links, or guaranteed performance.
- The response follows the user's requested output mode: full final result or only the post.
- No external publishing action was taken without explicit authorization.
