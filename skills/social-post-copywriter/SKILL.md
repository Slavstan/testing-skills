---
name: social-post-copywriter
description: Write a clear, engaging social-media caption from a structured product or service brief, especially the JSON handoff from social-post-analyzer. Use whenever the user wants a first-draft post for a named social platform based on supplied brand, audience, product details, core message, or audience benefits. Create the caption only; leave CTA and hashtag optimization to a downstream publishing optimizer.
---

# Social Post Copywriter

## Purpose

Turn a factual brief into a ready-to-review first draft of social-media copy. This is stage two of a three-skill workflow:

1. `social-post-analyzer` identifies known facts, audience, core message, and tone.
2. `social-post-copywriter` writes the initial post.
3. A downstream publication optimizer adds or improves the call to action (CTA), hashtags, and final publishing details.

Keep this skill focused on writing the caption, not on re-analyzing the product or doing final publication optimization.

## Input

Prefer the JSON object produced by `social-post-analyzer`, with these fields:

- `company`
- `product_or_service`
- `target_audience`
- `platform`
- `known_attributes`
- `potential_audience_benefits`
- `core_message`
- `recommended_tone`
- `missing_information`
- `notes`

The user may instead provide the same information in ordinary text. Map the supplied details to these fields without requiring the user to reformat them.

## Workflow

1. **Read the brief.** Extract the company, product or service, audience, platform, confirmed attributes, core message, and tone.
2. **Respect evidence levels.** Treat `known_attributes` as confirmed. Benefits marked as `interpretation` may guide the framing, but must not be rewritten as guaranteed or proven product outcomes. Do not add features, materials, prices, discounts, availability, environmental claims, performance claims, or other facts not in the brief.
3. **Choose the angle.** Build the caption around the core message and, when useful, one supported audience benefit. Keep the post focused on one main idea.
4. **Write for the platform and audience.** Use the recommended tone and adapt length, rhythm, and formatting to the named platform. If the platform is unknown, use a concise general-purpose social caption and mention no platform-specific assumptions.
5. **Make it natural.** Use clear, specific language rather than generic hype. Emojis may be used sparingly if appropriate to the audience and tone. Do not force slang or imply personal experiences or testimonials that were not supplied.
6. **Do not perform stage-three work.** Do not add hashtags, a CTA, or a list of optimization tips. The downstream publication optimizer is responsible for those.
7. **Handle incomplete briefs carefully.** If a core message is missing, form a conservative one from confirmed facts. If the product or service itself is missing, ask one concise clarifying question instead of inventing the subject. If other details are missing, draft only when the remaining facts are sufficient.
8. **Check the result.** Confirm that the caption names or clearly refers to the supplied product or service, aligns with the audience and tone, communicates one main idea, and contains no unsupported claims, CTA, or hashtags.

## Output format

Return the result in this format:

**Platform:** [platform]

**Draft post:**

[One polished social-media caption. Keep line breaks if they improve readability.]

**Editorial note:** [One short sentence identifying any meaningful limitation caused by missing information, or “None” if no important limitation applies.]

Do not return JSON unless the user explicitly asks for machine-readable output. Do not provide multiple variants unless the user asks for options. Do not add a CTA or hashtags.

## Handoff to Skill 3 — Publication Optimizer

Pass the drafted caption and the original brief to the next skill. The publication optimizer may add an appropriate CTA and relevant hashtags, refine the copy for publication, and check that all final wording remains consistent with confirmed product information. Preserve the original product facts and the distinction between confirmed attributes and interpretations.

## Quality checklist

Before returning the draft, verify:

- The post is based on the supplied brief, not invented product facts.
- The main message matches `core_message`.
- The wording suits the target audience, platform, and recommended tone.
- Interpretive benefits are framed cautiously rather than as guaranteed outcomes.
- No unsupported claims, fabricated testimonials, or invented offers appear.
- No CTA or hashtags are included.
- The output uses the specified format and contains one draft unless alternatives were requested.
