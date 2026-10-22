---
name: social-post-optimizer
description: Refine an existing social-media caption into a publication-ready post by adding an appropriate call to action (CTA), relevant hashtags, and platform-aware edits. Use whenever the user asks to polish, optimize, finalize, or prepare a social post for publishing, especially when a draft and the structured brief from social-post-analyzer or social-post-copywriter are available. Preserve factual accuracy and never invent product claims, offers, or performance results.
---

# Social Post Optimizer

## Purpose

Prepare the final publication-ready version of a social-media post. This is stage three of the workflow:

1. `social-post-analyzer` creates a factual brief.
2. `social-post-copywriter` writes the first caption draft.
3. `social-post-optimizer` refines the draft, adds a suitable call to action (CTA) and relevant hashtags, and checks publication readiness.

Focus on the final caption. Do not redo the full analysis or create a new campaign strategy unless the user asks.

## Input

Prefer both of these inputs:

- The structured brief from `social-post-analyzer`, including `company`, `product_or_service`, `target_audience`, `platform`, `known_attributes`, `potential_audience_benefits`, `core_message`, `recommended_tone`, `missing_information`, and `notes`.
- The draft caption from `social-post-copywriter`.

The user may provide a draft and brief as plain text, or ask to optimize a draft without a formal brief. Use the supplied information without forcing a JSON format. If no draft is provided, ask for it unless the user clearly requests that you create a final post from the brief.

## Workflow

1. **Read the draft and brief.** Identify the core message, platform, audience, tone, confirmed product attributes, and any stated limitations.
2. **Preserve factual boundaries.** Treat only `known_attributes` and other explicitly supplied facts as confirmed. Do not convert a potential benefit marked `interpretation` into a proven result. Never invent product specifications, prices, discounts, stock, shipping, guarantees, testimonials, certifications, environmental effects, or performance claims.
3. **Edit for publication.** Improve clarity, flow, grammar, readability, and platform fit. Keep the main idea and the brand's intended tone. Avoid changing the post so much that it no longer matches the original brief.
4. **Add one suitable CTA.** Use a simple action appropriate to the post and platform, such as inviting readers to share their preference, learn more, or explore the product. Do not imply a link, shop, promotion, availability, or special offer unless one is supplied. If no actionable destination or offer is known, use a generic, low-pressure CTA or explicitly note that the user should replace it with a real destination if needed.
5. **Add relevant hashtags.** Choose a small, focused set of relevant hashtags based on the product, topic, brand, audience, and platform. Include a brand hashtag only when the brand name is known. Avoid unrelated, misleading, overly broad, or claim-bearing hashtags (for example, environmental claims not substantiated by the brief). Do not claim that any hashtag will guarantee reach or engagement.
6. **Respect platform conventions.** Adapt formatting and hashtag quantity to the stated platform without presenting platform folklore as a guaranteed algorithmic rule. If the platform is missing, use a general-purpose format and note the limitation.
7. **Handle incomplete information conservatively.** If the product or service cannot be identified, ask one concise clarifying question. If a draft contains unsupported claims, remove them or flag them briefly rather than preserving them for style. If a CTA depends on a missing destination, avoid fabricating a URL or account.
8. **Run the final checks.** Ensure the post is coherent, audience-appropriate, factually grounded, and includes a CTA and relevant hashtags unless the user explicitly requests otherwise. Check spelling, punctuation, emoji use, and whether any claims exceed the brief.

## Output format

Return:

**Platform:** [platform]

**Final post:**

[Publication-ready caption with natural line breaks, one suitable CTA, and hashtags.]

**Final checks:**
- **CTA:** [brief description of the action invited]
- **Hashtags:** [brief rationale for the selected set]
- **Factual accuracy:** [confirm no unsupported claims were added, or identify any issue]
- **Open item:** [missing destination/detail the user may need to fill in, or “None”]

Keep the explanation concise. The final post should be easy to copy and publish. Do not return JSON unless the user explicitly asks for machine-readable output. Do not provide multiple variants unless requested.

## Handoff and scope

This skill is the final stage of the three-skill social-post workflow. It should return the finished caption to the user, not hand off to another skill. If the user asks for a separate campaign plan, audience research, or multiple creative directions, handle only the requested extension.

## Quality checklist

Before returning the result, verify:

- The draft's main message and brand intent are preserved.
- Every product claim is supported by supplied information.
- Interpretive benefits are not stated as verified outcomes.
- The CTA is clear, appropriate, and does not invent an offer or destination.
- Hashtags are relevant, restrained, and factually safe.
- The language and formatting suit the specified platform and audience.
- The final post is polished and copy-ready.
- Missing information or a necessary manual replacement is noted concisely.
