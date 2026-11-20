# Examples

Excerpts from one SmartQA run on [Practice Software Testing](https://practicesoftwaretesting.com), a public demo shop built for testing practice. The page under test is a product page. Fields are trimmed and IDs are simplified; the wording is the framework's output.

## Requirement → Test cases

**R-1.** The 'Quantity' input field shall be visible and accept numeric values between 1 and 99 inclusive.

- The field SHALL NOT accept values less than 1.
- The field SHALL NOT accept values greater than 99.
- Given the 'Quantity' input field has a value of 1, When the 'Decrease quantity' button is clicked, Then the quantity value SHALL remain 1.

**T-1.** Verify 'Quantity' input field accepts valid numeric values (BVA/EP)

| Value | Expected outcome |
|---|---|
| 1 | Accepted |
| 50 | Accepted |
| 99 | Accepted |

**T-2 (Negative).** Verify 'Quantity' input field rejects invalid numeric values (BVA/EP)

| Value | Expected outcome |
|---|---|
| 0 | Rejected (below min) |
| 100 | Rejected (above max) |
| -5 | Rejected (below min) |
| "abc" | Rejected (invalid format) |

The page did not show the exact error message, so the test case does not guess it: *"displaying appropriate (exact criteria TBD — verify with client) validation feedback."*

## Traceability row

| Requirement | Test cases | Status |
|---|---|---|
| R-1 | T-1, T-2 and 5 more (7 in total) | Covered |

## Coverage gap (from the quality report)

> **'Add to Favourites' Success for Authenticated Users**: R-2 covers the unauthorized scenario, but there is no positive requirement for successfully adding a product to favourites when a user is logged in. — Fix: add REQ

The quality report reviews the requirement set for scenarios that no requirement covers. Here it found that a feature had a requirement only for its negative path.

## Caught LLM fabrication

In review, requirements from an earlier version of the framework turned out to contain thresholds that appeared nowhere in the input:

> "page loads within 2 seconds"
> "email confirmation within 5 minutes"

The values looked plausible but had no source on the page, and one had already been copied into a test case assertion. Generation is now told to mark such values as unknown instead of inventing them; in later runs they appear like the note in T-2 above: *"exact criteria TBD — verify with client"*. This is guidance to the model, not a hard check, so review still matters.

**Reason in one line:** invented value with no source in the input.

---

Copyright © 2026 Bogdan Doroshenko. All rights reserved. See [NOTICE.md](../NOTICE.md).
