---
name: social-post-workflow
description: Run the complete three-stage social-media publishing workflow from a short user brief: analyze the facts, write a first caption, optimize it with a CTA and hashtags, and show the user only the final result. Use when the user asks to create a social post end to end or to run the social-post skills together.
---

# Social Post Workflow

## Purpose

Orchestrate the three existing skills as one end-to-end task and return only the final publication-ready result. Do not expose intermediate analysis JSON, first-draft copy, or internal handoff notes unless the user explicitly requests them.

## Skills to run, in order

1. `social-post-analyzer` — read `../social-post-analyzer/SKILL.md` and follow its instructions to produce a factual brief.
2. `social-post-copywriter` — read `../social-post-copywriter/SKILL.md` and follow its instructions using the brief from stage 1 to produce a first caption.
3. `social-post-optimizer` — read `../social-post-optimizer/SKILL.md` and follow its instructions using both the original brief and the draft from stage 2 to create the final post.

Resolve these paths relative to this workflow's directory under `skills/`. If the environment provides a mechanism for invoking named skills directly, invoke the named skill at each stage. Otherwise, follow the relevant `SKILL.md` instructions in sequence as part of this workflow. Do not claim that separate skills were independently executed if the environment only supports following their instructions in one orchestrated run.

## User input

Accept ordinary text or structured fields. Collect what is available:

- Company or brand
- Product or service
- Target audience
- Social platform
- Known product facts or approved claims
- Optional draft, campaign goal, link, offer, or CTA preference

Do not force JSON input. If the product or service cannot be identified, ask one concise clarifying question before proceeding. If audience or platform is missing but a conservative useful result is possible, continue and note the limitation only if it matters to the final result.

## Execution contract

1. Read the three stage instructions before running the pipeline. Do not edit their files as part of an ordinary workflow run.
2. Run stage 1 internally. Preserve its JSON brief as internal workflow data.
3. Pass that brief to stage 2. Keep the resulting draft as internal workflow data.
4. Pass both the original brief and stage-2 draft to stage 3.
5. Validate the final post against the original user input and brief. Remove any unsupported product claims, fabricated offers, fake links, fabricated testimonials, and claims of guaranteed reach or engagement.
6. Show the user only stage 3's final output. Do not include stage 1 JSON, stage 2 draft, internal reasoning, or progress updates.
7. If a required detail is missing and prevents a safe or useful final post, ask one concise question instead of fabricating it. Otherwise finish with a conservative result and note a material limitation in the final output.
8. Do not publish, schedule, or post to an external account. This workflow creates copy only unless a separately authorized publishing integration is explicitly available and the user requests that action.

## Final response

Use the output format defined by `social-post-optimizer/SKILL.md`:

- Platform
- Final post, including a suitable CTA and relevant hashtags
- Concise final checks for CTA, hashtags, factual accuracy, and any open item

The final post should be easy to copy and publish. Do not add an explanation of the three internal stages. Do not show intermediate results.

## Quality checklist

Before returning the answer, confirm:

- All three stages were applied in the prescribed order, or any environment limitation was handled transparently.
- The final post is grounded in facts provided by the user.
- The CTA does not invent a destination, offer, or availability.
- Hashtags are relevant and do not introduce unsupported claims.
- The only user-visible content is the final result, unless clarification is required.
