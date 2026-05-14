# Vector Network Documentation Set (v-docsx)

This directory contains the master documentation set for Vector Network, including the canonical protocol specification, state model, operational rules, certification rules, security rules, language references, SDK contracts, and supporting examples.

Vector Network is not described as a blockchain. It is a distinct decentralized vector ecosystem built around a deterministic kernel, immutable recordkeeping, and multidimensional state representation. The documents in this directory explain the system from different angles so that readers can move from high-level understanding to implementation detail without needing to already know the project.

## What this directory is for

This documentation set is intended to:

- explain what Vector Network is in plain language
- define the vector-based state model
- describe how transfers, drains, projections, and reconstructions work
- specify certification, AuthRatio, and validation rules
- define how immutable records are written and replayed
- describe security expectations for wallets, keys, signatures, and ownership
- provide formal notation for implementers and auditors
- document the language, SDK, and visualization layers built on top of the kernel
- provide direct cross-references to implementation-level documentation in `v-nodex` where storage, persistence, immutability, and runtime mechanics are explained

## Document map

- `SPEC.md` — master protocol rulebook and normative specification
- `GLOSSARY.md` — canonical terminology and field definitions
- `STATE_MODEL.md` — mathematical state model for vectors and vector spaces
- `CANONICAL_STATE_MODEL.md` — canonical state layout and state representation rules
- `OPERATIONS.md` — operational rules for transfer, projection, reconstruction, drain, and origin
- `OPERATIONS_FINITE_TRANSITIONS.md` — operation transition structure and state-machine flow details
- `CERTIFICATION.md` — certification, AuthRatio, validation, and rejection logic
- `AUTHRATIO.md` — AuthRatio scoring model, weighting, and validation factors
- `RECORDS.md` — immutable record format and event log requirements
- `SECURITY.md` — ownership, signatures, key handling, and threat controls
- `ERRORS.md` — protocol error classes and failure handling
- `GOVERNANCE.md` — versioning, upgrades, parameters, and compatibility rules
- `EXAMPLES.md` — worked examples and learning-oriented scenarios
- `FORMALISM.md` — formal notation, invariants, and proof obligations
- `VECTOR_LANGUAGE_SPEC.md` — language grammar, syntax, and execution rules
- `VECTOR_LANGUAGE_REFERENCE.md` — language reference material and usage notes
- `SDK_SPEC.md` — SDK architecture, interface expectations, and integration rules
- `SDK_FUNCTION_CONTRACTS.md` — callable SDK behavior and function-level contracts
- `VISUALIZATION_FRAMEWORK.md` — ledger views, state visualizations, and explorer concepts
- `v-nodex/docs/storage.md` — storage model, persistence rules, and record materialization
- `v-nodex/docs/spatial-storage.md` — spatial storage layout and vector-space persistence
- `v-nodex/docs/immutability.md` — immutability guarantees and append-only storage behavior

## Related implementation references

When a section in this documentation set mentions storage, persistence, retention, immutability, or on-disk layout, readers should jump to the corresponding `v-nodex` implementation documentation.

Suggested target references:

- [v-nodex storage documentation](https://github.com/vnetworkx/v-nodex/blob/main/docs/storage.md)
- [v-nodex spatial storage documentation](https://github.com/vnetworkx/v-nodex/blob/main/docs/spatial-storage.md)
- [v-nodex immutability documentation](https://github.com/vnetworkx/v-nodex/blob/main/docs/immutability.md)

## Recommended reading order

1. Read `SPEC.md` first for the canonical protocol overview.
2. Read `GLOSSARY.md` next so terms are interpreted consistently.
3. Read `STATE_MODEL.md` and `CANONICAL_STATE_MODEL.md` to understand how vector state is represented.
4. Read `OPERATIONS.md` and `OPERATIONS_FINITE_TRANSITIONS.md` to understand how state changes happen.
5. Read `CERTIFICATION.md` and `AUTHRATIO.md` to understand validation and restriction logic.
6. Read `RECORDS.md` to understand how immutable records are written.
7. Read `SECURITY.md`, `ERRORS.md`, and `GOVERNANCE.md` for practical protocol safety and maintenance rules.
8. Read `FORMALISM.md` for strict notation and invariants.
9. Read `EXAMPLES.md` and `experiments.py` for learning, testing, and experimentation.
10. Read `VECTOR_LANGUAGE_SPEC.md`, `VECTOR_LANGUAGE_REFERENCE.md`, `SDK_SPEC.md`, `SDK_FUNCTION_CONTRACTS.md`, and `VISUALIZATION_FRAMEWORK.md` for the higher layers built on top of the kernel.
11. Read the relevant `v-nodex` storage documentation when the topic involves persistence, record storage, storage layout, immutability, or runtime state materialization.

## Normative language

The words **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** are to be interpreted as normative requirements in the sense of a technical protocol specification.

## Naming convention

In this project, the prefix `v` is used to signal vector identity or vnetworkx identity. The suffix `x` is used to indicate a space, environment, or system layer. Depending on context, names such as `vNetworkx`, `v-networkx`, or related forms can refer to a vector-space-oriented implementation or subsystem of the broader Vector Network concept.

## File structure notes

Some documents in this directory overlap by design. That is intentional.

- `SPEC.md` is the canonical source of truth.
- Other files may restate parts of the spec in a more focused or more readable form.
- The language, SDK, visualization, and example documents are supporting layers rather than competing sources of truth.
- Reference code such as `experiments.py` is educational and experimental unless explicitly promoted into the canonical implementation.
- Implementation-specific storage behavior belongs in `v-nodex`, while this directory focuses on protocol rules and readable canonical documentation.

## Suggested use by audience

- New readers: start with `SPEC.md`, `GLOSSARY.md`, and `EXAMPLES.md`.
- Developers: focus on `OPERATIONS.md`, `RECORDS.md`, `SECURITY.md`, `SDK_SPEC.md`, and `SDK_FUNCTION_CONTRACTS.md`.
- Protocol designers: study `STATE_MODEL.md`, `CANONICAL_STATE_MODEL.md`, `CERTIFICATION.md`, `AUTHRATIO.md`, and `FORMALISM.md`.
- Tool builders: review `VECTOR_LANGUAGE_SPEC.md`, `VECTOR_LANGUAGE_REFERENCE.md`, and `VISUALIZATION_FRAMEWORK.md`.
- Maintainers: consult `GOVERNANCE.md` and `ERRORS.md` when changing protocol behavior.
- Implementers working on persistence or state backends: follow the linked `v-nodex` storage, spatial-storage, and immutability documentation alongside these protocol rules.

## Notes for contributors

When editing the documentation set:

- keep terminology consistent across files
- preserve the distinction between canonical rules and explanatory notes
- avoid introducing hidden assumptions into examples
- keep the kernel deterministic in every description of execution
- treat record generation as mandatory for successful state transitions
- keep wallet secrets out of shared state and public records
- add or update cross-references to `v-nodex` whenever storage, persistence, or immutability concepts are introduced