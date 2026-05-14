# Records

## 1. Purpose

Records provide the immutable history of the protocol.

## 2. Record requirement

Every successful state change MUST create exactly one primary record. A failure MAY create a failure record if the protocol chooses to log rejected attempts, but failure records MUST be clearly distinguished from state-transition records.

## 3. Canonical record form

A record is logically defined as:

`R = (v_before, v_after, operation, parameters, certification, timestamp, proof)`

A practical implementation MAY add:
- `record_id`
- `space_id`
- `version`
- `initiator`
- `parent_record_ids`
- `signature`
- `hash`
- `nonce`
- `settlement_ref`

## 4. Required properties

A valid record MUST be:
- immutable
- time-ordered or hash-ordered
- machine-parseable
- uniquely identifiable
- replayable
- linked to the affected state

## 5. Serialization

Record serialization MUST be canonical.

A canonical serialization MUST:
- preserve field order,
- preserve number encoding rules,
- preserve string normalization,
- preserve hash inputs,
- avoid ambiguous representations.

## 6. Hashing

If hashes are used, the hash function MUST be versioned and declared.

A record hash SHOULD cover:
- the full canonical record content
- the protocol version
- the space identifier if relevant

## 7. Immutability model

Records are append-only.

A record MUST NOT be edited after commitment.

If correction is required, the protocol MUST append a new corrective record rather than overwrite history.

## 8. Parent linkage

Where relevant, records SHOULD reference parent records to establish causality.

Examples:
- transfer record linked to source wallet state
- reconstruction record linked to projection record
- migration record linked to source space record chain

## 9. Failure logging

If a system logs failed operations, the failure log MUST:
- distinguish rejection from success,
- not alter canonical state,
- record the reason for rejection,
- avoid ambiguity about whether value moved.

## 10. Replay

A valid chain of records MUST replay deterministically.

Replay rules:
- process records in their canonical order
- verify each precondition
- apply each transition
- compare resulting state against stored post-state

Any mismatch MUST be treated as invalid.

## 11. Record minimality

Records SHOULD include all data necessary for verification without leaking private keys or unnecessary sensitive data.

For backend storage, immutability enforcement, and on-disk record materialization details, implementation-specific behavior SHOULD be documented in `v-nodex` rather than being expanded here.

## 12. Privacy

Private key material MUST NOT appear in a record.

Sensitive metadata MAY be redacted, hashed, or committed by reference if the protocol supports it.

## 13. Cross-space records

For migrations and cross-space actions, records MUST preserve:
- source context
- destination context
- bridge or translation logic
- causal traceability

## 14. Educational note

The record stream is the protocol's memory. If the records are correct, the state can be reconstructed; if the records are incomplete, the system loses verifiability.

When readers need to understand how records are stored, persisted, or replayed at the implementation layer, they should follow the linked `v-nodex` documentation:
- [storage.md](https://github.com/vnetworkx/v-nodex/blob/main/docs/storage.md)
- [spatial-storage.md](https://github.com/vnetworkx/v-nodex/blob/main/docs/spatial-storage.md)
- [immutability.md](https://github.com/vnetworkx/v-nodex/blob/main/docs/immutability.md)