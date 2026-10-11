---
name: destiller
description: Use only when the user explicitly invokes destiller to compress a draft while preserving all material content.
argument-hint: "[--tight|--keep-tone] <draft text or file path>"
disable-model-invocation: true
---

# Destiller

Maximize useful information per word without omitting any material fact, decision, requirement, rationale, caveat, dependency, risk, or actionable recommendation.

## Input

The draft is, in order of precedence:
1. Text passed with the command.
2. A file path passed with the command: read that file.
3. Otherwise, the assistant's most recent message.

Flags (optional, before the draft):
- `--tight`: compress harder; drop examples and reasoning unless strictly needed for interpretation.
- `--keep-tone`: preserve the author's voice and register; compress structure and redundancy only.

Default: the shortest form that passes the verification below. No fixed ratio.

## Rules

- State each idea once; merge overlaps.
- Remove framing, repetition, transitions, recaps, redundant emphasis, obvious explanations, and inferable or low-information wording unless uniquely informative.
- Prefer direct sentences, compact bullets, labels, or tables.
- Use one representative example unless others add distinct information.
- Keep reasoning only when it affects interpretation or conclusions.

## Never rewrite

Keep verbatim: code, commands, file paths, URLs, identifiers, exact numbers and units, dates, quotations, proper names, and legal or contractual wording. Compress the prose around them, not them.

## Output

- Output only the compressed draft. No preamble, no commentary, no "here is the compressed version".
- Keep the original language.
- Keep the original format: markdown headings, lists, tables, and code blocks stay as they were. Reduce their content, not their kind.
- If a file path was given, output the compressed text in the response; do not overwrite the file unless asked.

## Verification

Before responding:
1. List every unique material claim in the draft (facts, decisions, requirements, rationale, caveats, dependencies, risks, recommendations).
2. Compress.
3. Check each listed claim against the output. Restore anything missing.
4. If you judged something non-material and dropped it, append one line: `Dropped: <items>` so the user can object. Omit the line when nothing was dropped.
