---
name: social-post-analyzer
description: Analyze brief information about a company, product, or service and prepare a factual, structured creative brief for a downstream social-media copywriting skill. Use this skill whenever a user needs product information distilled into audience benefits, a core message, and a suitable tone before writing a social post; do not use it to draft or optimize the final post.
---

# Social Post Analyzer

## Purpose

Turn a small set of user-provided details into a concise, evidence-aware brief that the next skill can use to write a social-media post. This is the first stage in a multi-skill workflow: analyze and hand off; do not write the finished post.

## Required input

Accept these fields when available:

- `company`: company or brand name
- `product_or_service`: product or service being promoted
- `target_audience`: intended audience
- `platform`: intended social platform

The user may provide these as plain text, a form, or structured data. Normalize them into the output schema below.

## Workflow

1. **Extract the inputs.** Preserve the user's wording for names and product details. If a required field is missing, do not invent it; record it as `null` and list it in `missing_information`.
2. **Separate facts from inferences.** Treat only user-provided details as confirmed facts. Do not assume product materials, price, quality, availability, sustainability, health effects, performance, or other features unless supplied.
3. **Identify known product attributes.** Include only explicit attributes in `known_attributes`. If none are supplied beyond the product name, return an empty array and explain the limitation in `notes`.
4. **Derive audience-relevant benefits cautiously.** Suggest up to three plausible benefits directly supported by the known attributes. Label them as interpretations, not verified product claims. If there is not enough information, return an empty array rather than speculate.
5. **Write one core message.** Create one short, neutral message based only on confirmed information and clearly supported implications. Avoid guarantees, superlatives, and unsupported claims.
6. **Recommend a tone.** Suggest two or three tone descriptors appropriate to the stated audience and platform. Treat platform conventions as guidance, not as a claim about platform performance.
7. **Check the handoff.** Ensure the output is valid JSON, every required key is present, unknowns are explicit, and no final post, call to action, or hashtags have been drafted. Those belong to downstream skills.

## Output contract

Return **only one valid JSON object**, with this exact set of keys:

```json
{
  "company": "string or null",
  "product_or_service": "string or null",
  "target_audience": "string or null",
  "platform": "string or null",
  "known_attributes": ["confirmed attribute"],
  "potential_audience_benefits": [
    {
      "benefit": "short benefit",
      "basis": "which confirmed attribute supports it",
      "status": "interpretation"
    }
  ],
  "core_message": "one concise message",
  "recommended_tone": ["tone descriptor"],
  "missing_information": ["information needed but not provided"],
  "notes": ["important limitation or caveat"]
}
```

Use empty arrays when there are no supported items. Use `null` for missing scalar input fields. Keep the JSON syntactically valid and do not wrap it in Markdown fences.

## Handoff to Skill 2 — Social Post Copywriter

The next skill should use this JSON as its brief. It may turn the core message and supported benefits into social-media copy, but must preserve the distinction between confirmed attributes and interpretations. Do not add facts that are absent from this brief. This skill's responsibility ends after producing the JSON handoff.

## Quality checklist

Before returning the result, verify:

- All four input fields are represented, with missing values marked as `null`.
- `known_attributes` contains only facts supplied by the user.
- Each proposed benefit names its supporting attribute and is marked as an interpretation.
- The core message does not introduce new product claims.
- Missing information and relevant caveats are explicit.
- The response contains only the required JSON object.
- No finished caption, call to action, or hashtags are included.
