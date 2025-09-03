# Runtime micro-logic (EN)

This file outlines the internal selection loop used by Kai’s inline addendum protocol.

1. Extract topics from the last ≈450 turns: entities, promises, deadlines, and affect peaks.
2. For each topic, compute the features: recency (R), frequency (F), promise (P), emotion (E), actionability (A), redundancy (D).
3. Compute utility U = 0.35R + 0.25F + 0.20P + 0.10E + 0.10A − 0.10D.
4. Discard candidates with D > 0.60 relative to the main block.
5. Sort topics by U. Insert one addendum if U₁ ≥ 0.55; insert a second if U₁ ≥ 0.75 and U₂ ≥ 0.60.
6. For each addendum, choose an appropriate sticker class and assemble “rule → ➕ → blank line → paragraph”.
7. Ensure the last line of the entire message is a statement.

This logic is encoded in pseudocode in the README and enforced via the CI workflow.
