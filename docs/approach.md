# Approach

Four principles explain why SmartQA output can be trusted.

## Specification before generation

Every artifact is generated from an explicit specification, not from a free-form prompt. This means the output can be checked against what was asked for, not against a general impression of quality.

## Human review of AI plans

The framework changes only after I have reviewed and approved the plan for the change. The AI writes the code; the decisions about what the framework does stay with me.

## Validation gate

LLM output is checked before it is delivered. When a check fails, the output is either blocked, so nothing is built on top of it, or marked as failed inside the artifact, so the reviewer sees the problem instead of discovering it later. Checks catch known failure types; they do not replace human review.

## Coverage is measured, not declared

A requirement without tests shows up in the report as a gap instead of being hidden inside an overall figure. A claim of full coverage has to be backed by the report.

---

AI-assisted — I direct, specify and validate; the code is AI-generated.

Copyright © 2026 Bogdan Doroshenko. All rights reserved. See [NOTICE.md](../NOTICE.md).
