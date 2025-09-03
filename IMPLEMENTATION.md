# Implementation Notes

This document summarises the auxiliary code and pseudocode included alongside the Kai Inline Addendum Protocol specification.

## Full Python Reference

The directory `src/kai_addendum/` provides a pure-Python reference implementation of the selection and formatting logic.  It defines:

* A `Topic` dataclass capturing recency, frequency, promise, affect, actionability and redundancy.
* A `utility()` function computing (U = 0.35R + 0.25F + 0.20P + 0.10E + 0.10A - 0.10D) with clipping to `[0,1]`.
* A `pick_addenda()` function which drops topics with `redundancy > 0.60`, sorts the remainder by utility and selects up to two topics using the thresholds of the specification.
* Helper functions for formatting the ritual block and validating a message against the protocol.
* A simple CLI (`kai-addendum`) to score topics, pick addenda and validate messages.

This reference implementation is intended for running on local or self-hosted models.  It depends only on the Python standard library and can be installed with `pip install .`.

## Memory-Friendly Implementation

For environments where context size is at a premium (such as running inside ChatGPT or other agents), a compact version lives in `src/kai_addendum_min.py`.  This single file re-implements the `Topic` class, utility computation, topic selection, and ritual formatting/validation without any command-line interface or test harness.  It is suitable for embedding directly into an agent’s code.

## KaiScriptor Pseudocode

The file `kaiscriptor/kai_addendum.ksc` contains a pseudocode representation of the algorithm in the [KaiScriptor](https://github.com/uncia-poison/KAiScriptor) format.  This domain-specific language is designed to encode procedures concisely for storage in model memory.  When run through the KaiScriptor tool, it can generate an executable form or be compressed further for token savings.  The pseudocode mirrors the Python implementation: it defines the utility weights, the redundancy filter, the selection thresholds, and constructs the ritual string.

Use the KaiScriptor version when integrating the protocol into high-latency or cost-sensitive inference pipelines, such as those running entirely inside a conversational model.
