# Vector Network Documentation

This repository contains the canonical documentation set for Vector Network.

It covers the protocol specification, state model, formal rules, operational behavior, certification logic, security guidance, language reference material, SDK contracts, and supporting examples. The documents are arranged so readers can move from overview to implementation detail without needing prior context.

Vector Network is not described as a blockchain. It is a decentralized vector system built around a deterministic kernel, immutable recordkeeping, and multidimensional state representation.

## What this repository is for

Use this repository to:

- understand Vector Network in plain language
- learn the vector-based state model
- review transfers, drains, projections, and reconstructions
- understand certification, AuthRatio, and validation rules
- see how immutable records are written and replayed
- review security expectations for wallets, keys, signatures, and ownership
- find formal notation for implementers and auditors
- navigate the language, SDK, and visualization layers built on the kernel

## Repository layout

- `README.md` — entry point for the documentation repository
- `SECURITY.md` — security policy and reporting guidance
- `experiments.py` — reference experiments and exploratory code
- `MANIFEST.json` — repository manifest and document inventory

### `docs/overview/`
- [`INTRODUCTION.md`](https://github.com/vnetworkx/docs/blob/main/overview/INTRODUCTION.md) — starting point for new readers
- [`CONCEPT_MAP.md`](https://github.com/vnetworkx/docs/blob/main/overview/CONCEPT_MAP.md) — high-level map of the system
- [`OVERVIEW.md`](https://github.com/vnetworkx/docs/blob/main/overview/OVERVIEW.md) — reference links and related resources

### `docs/core/`
- [`SPEC.md`](https://github.com/vnetworkx/docs/blob/main/core/SPEC.md) — canonical protocol specification
- [`FORMALISM.md`](https://github.com/vnetworkx/docs/blob/main/core/FORMALISM.md) — notation, invariants, and proof obligations
- [`STATE_MODEL.md`](https://github.com/vnetworkx/docs/blob/main/core/STATE_MODEL.md) — mathematical state model
- [`CANONICAL_STATE_MODEL.md`](https://github.com/vnetworkx/docs/blob/main/core/CANONICAL_STATE_MODEL.md) — canonical representation rules

### `docs/operations/`
- [`OPERATIONS.md`](https://github.com/vnetworkx/docs/blob/main/operations/OPERATIONS.md) — operational rules
- [`OPERATIONS_FINITE_TRANSITIONS.md`](https://github.com/vnetworkx/docs/blob/main/operations/OPERATIONS_FINITE_TRANSITIONS.md) — transition flow details
- [`ERRORS.md`](https://github.com/vnetworkx/docs/blob/main/operations/ERRORS.md) — error classes and failure handling

### `docs/governance/`
- [`CERTIFICATION.md`](https://github.com/vnetworkx/docs/blob/main/governance/CERTIFICATION.md) — certification and rejection logic
- [`AUTHRATIO.md`](https://github.com/vnetworkx/docs/blob/main/governance/AUTHRATIO.md) — AuthRatio scoring and validation factors
- [`GOVERNANCE.md`](https://github.com/vnetworkx/docs/blob/main/governance/GOVERNANCE.md) — versioning, upgrades, and compatibility rules

### `docs/reference/`
- [`GLOSSARY.md`](https://github.com/vnetworkx/docs/blob/main/reference/GLOSSARY.md) — terminology and field definitions
- [`RECORDS.md`](https://github.com/vnetworkx/docs/blob/main/reference/RECORDS.md) — immutable record format and event log requirements
- [`EXAMPLES.md`](https://github.com/vnetworkx/docs/blob/main/reference/EXAMPLES.md) — worked examples
- [`VISUALIZATION_FRAMEWORK.md`](https://github.com/vnetworkx/docs/blob/main/reference/VISUALIZATION_FRAMEWORK.md) — ledger views and explorer concepts

### `docs/language/`
- [`VECTOR_LANGUAGE_SPEC.md`](https://github.com/vnetworkx/docs/blob/main/language/VECTOR_LANGUAGE_SPEC.md) — language grammar and execution rules

### `docs/sdk/`
- [`SDK_SPEC.md`](https://github.com/vnetworkx/docs/blob/main/sdk/SDK_SPEC.md) — SDK architecture and integration rules
- [`SDK_FUNCTION_CONTRACTS.md`](https://github.com/vnetworkx/docs/blob/main/sdk/SDK_FUNCTION_CONTRACTS.md) — function-level contracts

## Recommended reading order

1. [`docs/overview/QUICK_START.md`](https://github.com/vnetworkx/docs/blob/main/overview/QUICK_START.md)
2. [`docs/overview/CONCEPT_MAP.md`](https://github.com/vnetworkx/docs/blob/main/overview/CONCEPT_MAP.md)
3. [`docs/core/SPEC.md`](https://github.com/vnetworkx/docs/blob/main/core/SPEC.md)
4. [`docs/reference/GLOSSARY.md`](https://github.com/vnetworkx/docs/blob/main/reference/GLOSSARY.md)
5. [`docs/core/STATE_MODEL.md`](https://github.com/vnetworkx/docs/blob/main/core/STATE_MODEL.md)
6. [`docs/operations/OPERATIONS.md`](https://github.com/vnetworkx/docs/blob/main/operations/OPERATIONS.md)
7. [`docs/governance/CERTIFICATION.md`](https://github.com/vnetworkx/docs/blob/main/governance/CERTIFICATION.md)
8. [`docs/reference/RECORDS.md`](https://github.com/vnetworkx/docs/blob/main/reference/RECORDS.md)
9. [`SECURITY.md`](https://github.com/vnetworkx/docs/blob/main/SECURITY.md)
10. [`docs/core/FORMALISM.md`](https://github.com/vnetworkx/docs/blob/main/core/FORMALISM.md)

## Source of truth

- `docs/core/SPEC.md` is the canonical source of truth.
- Supporting documents may restate, explain, or specialize the spec.
- `experiments.py` is educational unless promoted into canonical implementation.
- Implementation-specific storage behavior belongs in `v-nodex`.

## Notes for contributors

- keep terminology consistent
- preserve the distinction between canonical rules and explanatory notes
- avoid hidden assumptions in examples
- keep the kernel deterministic
- treat record generation as mandatory for successful state transitions
- keep wallet secrets out of shared state and public records
- update cross-references when storage, persistence, or immutability concepts are introduced
