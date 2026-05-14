# Certification

## 1. Purpose

Certification determines whether a vector is eligible to participate in restricted operations.

## 2. AuthRatio

AuthRatio is a deterministic composite validity score in the interval `[0, 1]`.

Certification MUST treat AuthRatio as an input score, not as certification itself.

### 2.1 Mandatory base factors
The canonical base factors are:

- magnitude validity
- composition validity
- ownership proof validity

### 2.2 Optional factors
A deployment MAY include optional factors such as:

- age of vector
- origin confidence
- historical integrity
- space trust level
- behavior reputation
- proof depth

Any optional factor used MUST be documented and versioned.

## 3. General rule

A vector is certified if:

`AuthRatio >= Threshold(ctx)`

where `ctx` is the evaluation context and Threshold is determined by:

- vector type
- operation class
- space policy
- risk profile
- protocol version

Thresholds MUST be explicit, versioned, reproducible, and space-aware.

## 4. Score model

A protocol MAY compute AuthRatio by weighted combination.

Canonical form:

`AuthRatio = w1*M + w2*C + w3*O + w4*X`

where:

- `M` = magnitude validity
- `C` = composition validity
- `O` = ownership proof validity
- `X` = optional extensions

Requirements:

- `0 ≤ M,C,O,X ≤ 1`
- `w1 + w2 + w3 + w4 = 1`
- each weight MUST be documented
- weights MUST be versioned
- the evaluation MUST be deterministic

If more than one optional factor is used, the `X` term MUST be expanded into a documented weighted submodel.

## 5. Validation requirements

Certification MUST verify:

- the vector exists
- the vector type is recognized
- the owner binding is genuine
- the record chain is intact
- any required proof is valid
- the vector is not explicitly revoked

Certification MUST fail closed when any required input is missing.

## 6. Certification states

### 6.1 Pending
The vector has not yet completed validation.

### 6.2 Certified
The vector satisfies the threshold for the current context.

### 6.3 Uncertified
The vector does not satisfy the threshold.

### 6.4 Suspended
The vector was previously valid but is temporarily blocked.

### 6.5 Revoked
The vector is disallowed until reauthorization or reorigin is completed.

## 7. State transitions

A certification workflow MAY transition among:

- `Pending -> Certified`
- `Pending -> Uncertified`
- `Certified -> Suspended`
- `Certified -> Revoked`
- `Uncertified -> Pending` through revalidation
- `Suspended -> Certified` through revalidation
- `Revoked -> Pending` only through explicit reauthorization or reorigin if the protocol permits it

Every transition MUST create a record.

## 8. Threshold management

Thresholds MUST be:

- explicit
- versioned
- space-aware
- type-aware
- reproducible

Thresholds MUST NOT be implicit or hidden inside unrelated logic.

## 9. Revocation

Revocation MUST:

- create a record
- state the reason
- state the scope
- state whether reversal is possible

## 10. Revalidation

A vector MAY be revalidated after revocation or suspension if the protocol allows it.

Revalidation MUST:

- reference the reason for prior invalidity
- prove that the issue is resolved
- create a new certification record

## 11. Certification and drain interplay

A protocol MAY permit drain offsets using certification credit only if the policy explicitly states:

- how credit is earned
- how it is consumed
- whether it decays
- whether it is transferable
- whether it survives migrations

## 12. Certification failure

If certification fails, the implementation MUST:

- reject the restricted action
- preserve the current state
- record the failure reason if the protocol logs failed attempts
- avoid partial state mutation

## 13. Security note

Certification is not ownership. A certified vector may still require separate authority checks for owner-bound actions.

## 14. Output contract

A certification result SHOULD contain:

- certification state
- AuthRatio
- threshold
- weight set reference
- policy version reference
- proof reference or failure reason
- record id
