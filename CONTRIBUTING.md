## Contributing

The Kai Inline Addendum Protocol remains defined by its specification in `README.md`.  The code under `src/` is a non-normative reference implementation.  If you modify thresholds, formulas, or the selection ritual, please update the documentation and add or adjust tests under `tests/`.

When submitting a change:

* Keep code, documentation and pseudocode in **English**.
* Add unit tests for new behaviour or bug fixes (see `tests/test_protocol.py`).
* Do not adjust the utility formula or thresholds without prior discussion.
* Run `ruff` and `pytest` locally before opening a pull request.

For memory-constrained use cases or in-chat agents, prefer the mini implementation (`src/kai_addendum_min.py`) or the KaiScriptor pseudocode (`kaiscriptor/kai_addendum.ksc`).
