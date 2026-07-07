# PGP68: Physis Orrery / Epoch Registry - Authority Transfer and Initialisation

- Author(s): Physis DAO / Council Steward
- Start Date: 2026-07-07
- Category: Programmatic
- Governance Role: Council
- Original PGP Pull Request: TBD
- Tracking Issue: TBD
- Vote Requirements: Council

---

## Summary

This proposal accepts Physis DAO ownership of **Physis Orrery: Epoch Registry**, authorises the transfer of program upgrade authority from the temporary developer deployment wallet to the DAO-controlled Realms authority, and approves the initial mainnet execution path for the Epoch Registry. Once approved, the current upgrade authority will transfer program upgrade authority to the Physis DAO authority, after which the attached Realms Base64 instruction payloads may be executed to initialise the mainnet Epoch Registry, register the current Physis epoch, and activate it.

Program:

```text
physis_epoch_registry
````

Program ID:

```text
PHYcBRWd6mKATk3xo8oYi3d55BBHUc7kAN4kK91cJoE
```

Current temporary upgrade authority:

```text
wfSXjyiLAv2mmCyPBhgT5ZNaPtAenNjQ6jaanQpdJJm
```

Target DAO-controlled authority:

```text
6ZuPrCK472jw3ZjRBqa6PZQ1tyVvY5BuYfWS7GMq7hX8
```

Physis Realm:

```text
DsWWtZrqXBcqTTPoEyFH793Euq82r95CuXWTwqo3JZur
```

---

## Impact

* **Why Now:**
  Orrery Program 1 has been deployed to mainnet, verified, and prepared with public metadata. The next step is to move it out of temporary developer control and into DAO-controlled infrastructure before it becomes the canonical source for Physis epochs and downstream program coordination.

* **Opportunities:**
  This creates the foundation for future Physis governance, Foundry Rewards, PHY lock systems, PRIVÉ participation, and later ASTRALIS/SmartSpot operator coordination. The Epoch Registry becomes the first live on-chain component of the broader Orrery program suite.

* **Challenges:**
  The upgrade authority transfer cannot be executed directly by the DAO until the DAO is already the authority. Therefore, the current developer authority must perform the technical transfer after Council approval. This proposal records DAO acceptance and authorises the follow-on Realms execution instructions once the transfer is complete.

* **Future Vision:**
  Successful completion establishes the standard lifecycle for future Orrery programs: deploy, test, verify, publish metadata, transfer authority to DAO, and execute initialisation through Realms.

---

## Stakeholders

* **Affected Parties:**
  The Physis Council, PRIVÉ members, PHY stakeholders, ASTRALIS stakeholders, future Foundry participants, SmartSpot operators, Physis Labs, and any future system relying on canonical Physis epoch timing.

* **Engagement for Feedback:**
  This proposal should be reviewed by Council members before execution. Technical artifacts, program IDs, hashes, authority addresses, and execution payloads should be made available through the PGP repository, Realms proposal text, and Orrery documentation.

---

## Explanation

### Concept Introduction

The Physis Epoch Registry is the first public Orrery on-chain program. It provides the canonical Physis epoch clock and preserves the ASTRALIS 6-hour service epoch anchor.

It does not calculate rewards, lock PHY, process claims, manage PRIVÉ eligibility, or run ASTRALIS operator rewards. Those functions belong to later Orrery programs.

### Current Deployment State

Program name:

```text
physis_epoch_registry
```

Program ID:

```text
PHYcBRWd6mKATk3xo8oYi3d55BBHUc7kAN4kK91cJoE
```

ProgramData address:

```text
9qXAL9PRc9TuNW8Lk9CWyAaXHsga8gGcPZiwT4tuXUSU
```

Verified source repository:

```text
https://github.com/PhysisVerse/physis-orrery
```

Verified source commit:

```text
17f0fcb35601c8fc0537d952d5a5f224a8bd1310
```

Verification job:

```text
25cf187c-a3ad-499d-aeeb-ded0d6e1d4d7
```

Verified program hash:

```text
7d19d0556c0f081c7641a164a08c30f3991f8f7400eb8c2709ce5291a3fa46a8
```

Security metadata:

```text
Uploaded through Program Metadata.
```

Program Metadata IDL:

```text
Uploaded through Program Metadata as a public URL-backed IDL profile.
```

Mainnet registry state:

```text
Not initialized.
```

### Implementation Overview

This proposal has two execution phases.

#### Phase 1: DAO Acceptance and Upgrade Authority Transfer

The Council approves accepting upgrade authority for Orrery Program 1.

After the proposal passes, the current temporary upgrade authority signs the upgrade-authority transfer from:

```text
wfSXjyiLAv2mmCyPBhgT5ZNaPtAenNjQ6jaanQpdJJm
```

to:

```text
6ZuPrCK472jw3ZjRBqa6PZQ1tyVvY5BuYfWS7GMq7hX8
```

The transfer is executed by the current authority wallet because only the current upgrade authority can sign the transfer.

The expected command is:

```bash
solana program set-upgrade-authority \
  PHYcBRWd6mKATk3xo8oYi3d55BBHUc7kAN4kK91cJoE \
  --new-upgrade-authority 6ZuPrCK472jw3ZjRBqa6PZQ1tyVvY5BuYfWS7GMq7hX8 \
  --url "$HELIUS_MAINNET_RPC" \
  --keypair ~/.config/solana/id.json
```

After transfer, the program must be verified with:

```bash
solana program show PHYcBRWd6mKATk3xo8oYi3d55BBHUc7kAN4kK91cJoE \
  --url "$HELIUS_MAINNET_RPC"
```

Expected authority after transfer:

```text
6ZuPrCK472jw3ZjRBqa6PZQ1tyVvY5BuYfWS7GMq7hX8
```

#### Phase 2: Realms Execution of Epoch Registry Initialisation

After the authority transfer is confirmed, the attached Realms Base64 Encoded Instruction payloads may be executed.

The approved instruction sequence is:

```text
1. initialize_registry
2. register_epoch
3. activate_epoch
```

The mainnet registry should be initialized with:

```text
registry.realm =
DsWWtZrqXBcqTTPoEyFH793Euq82r95CuXWTwqo3JZur

registry.authority =
6ZuPrCK472jw3ZjRBqa6PZQ1tyVvY5BuYfWS7GMq7hX8
```

ASTRALIS service epoch constants:

```text
astralis_epoch_zero_ts = 1725148800
astralis_epoch_duration_seconds = 21600
```

Initial Physis epoch to register:

```text
epoch_id = 202602
physis_year = 2026
physis_quarter = 2
calendar_year = 2026
calendar_quarter = 3
start_ts = 1782864000
end_ts = 1790812799
```

### Practical Example

After approval and execution, downstream Physis programs will be able to reference a DAO-controlled Epoch Registry to determine the active Physis epoch. Future PHY lock programs, Foundry reward distributors, and governance participation systems can use this source of truth rather than maintaining separate timing logic.

### Addressing Corner Cases

* If the authority transfer is not visible on-chain, the attached initialization instructions must not be executed.
* If the registry is already initialized, duplicate initialization must be rejected.
* If the epoch is already registered, duplicate registration must be rejected.
* If the active epoch state does not match the expected epoch, execution should pause and be reviewed.
* If any address in the payload differs from the proposal text, the payload should not be executed.

---

## Pitfalls

* **Reasons for Hesitation:**
  Transferring upgrade authority is a major governance step. Once transferred, future upgrades require DAO governance. This reduces individual flexibility but increases decentralised control and accountability.

* **Potential Problems:**
  The main risk is executing the initialization payload before confirming that the DAO authority is the program authority and intended registry authority. Another risk is attaching a malformed Base64 instruction payload. Both risks are mitigated by pre-execution verification and transparent documentation of all addresses and instruction parameters.

---

## Rationale

* **Optimal Design Justification:**
  The chosen process is the cleanest governance path: the DAO first approves accepting authority, the current authority performs the technical transfer, and the DAO then executes registry initialization through Realms. This reflects the real signing requirements of Solana upgrade authority while still preserving DAO approval and public auditability.

* **Considered Alternatives:**
  One suggestion was to place the upgrade-authority transfer itself inside a Realms Base64 instruction proposal. That was rejected because the DAO cannot sign as the current developer upgrade authority before the authority transfer occurs.
  Another alternative was to initialize the registry from the developer wallet before handoff. That was rejected because production registry authority should not originate from a founder or developer wallet.

* **Consequences of Inaction:**
  If this proposal is not executed, Orrery Program 1 remains deployed but not DAO-owned and not operational as the canonical Physis epoch registry. Future Orrery programs would lack a formally governed epoch source.

---

## Queries

* **Pre-Merge Resolutions:**
  Council should confirm the target DAO-controlled authority address:

  ```text
  6ZuPrCK472jw3ZjRBqa6PZQ1tyVvY5BuYfWS7GMq7hX8
  ```

  Council should also confirm the final Base64 Encoded Instruction payloads before execution.

* **Post-Approval Developments:**
  After authority transfer and registry initialization, future proposals may add new Orrery programs such as the Persona / PRIVÉ Eligibility Registry, PHY Governance Lock, Foundry Rewards Distributor, and Circuit Breaker Program.

* **Future Considerations:**
  This proposal does not implement rewards, PHY locking, PRIVÉ eligibility, SmartSpot registration, operator rewards, or ASTRALIS leader rotation. It only establishes Program 1 and its initial DAO-controlled epoch state.

* **Dependencies and Timelines:**
  This proposal depends on:

  ```text
  1. Verified deployed program.
  2. Confirmed DAO authority target.
  3. Current upgrade authority signing the authority transfer after approval.
  4. Verified Realms Base64 instruction payloads.
  ```

---

## Deployment

### User Impact

There is no direct end-user action required. This is a protocol infrastructure proposal. Once executed, future Physis governance and reward systems can use the Epoch Registry as a canonical time source.

### Documentation Updates

The following documentation should be updated after execution:

```text
README.md
docs/PROGRAM_REGISTRY.md
docs/DEPLOYMENT.md
PGP proposal index
Realms proposal record
```

The final transaction signatures for the authority transfer and registry initialization should be appended to the relevant deployment notes.

### Compatibility Considerations

This proposal does not migrate existing users. It initializes a new canonical on-chain registry. Future programs should integrate against this registry rather than creating separate epoch timing logic.

### Reversibility

The authority transfer is reversible only through the new DAO-controlled authority. Once authority is transferred to the DAO, the developer account can no longer unilaterally upgrade or reclaim control.

Registry initialization is intended to be permanent. The registry includes pause/resume controls, but historical epoch boundaries should be treated as immutable.

### Migration Strategy

No user migration is required. Future Physis programs should be built against the DAO-controlled Epoch Registry.

---

## Metrics

* **Performance Indicators:**
  Not applicable for direct performance improvement. This proposal establishes governance-controlled infrastructure.

* **Stability Metrics:**
  Success is measured by:

  ```text
  Program authority equals DAO-controlled authority.
  Registry account is initialized.
  Current Physis epoch is registered.
  Current Physis epoch is active.
  Registry current_epoch points to the active PhysisEpoch account.
  ```

* **Complexity Reduction:**
  Future programs can reference a shared epoch registry rather than duplicating epoch logic.

* **User Acceptance:**
  Acceptance is measured by Council approval, successful authority transfer, successful Realms execution, and no unexpected registry state after execution.

* **ETL Reporting Needs:**
  Indexers should eventually track:

  ```text
  EpochRegistered events
  EpochActivated events
  EpochClosed events
  RegistryPaused events
  RegistryResumed events
  authority transfer transaction
  registry initialization transaction
  ```

---

## Execution Checklist

Before execution:

```text
[x] Confirm program ID.
[x] Confirm current upgrade authority.
[x] Confirm target DAO authority.
[x] Confirm verified program hash.
[x] Confirm Realms proposal approval.
[x] Confirm Base64 instruction payloads match this proposal.
```

Authority transfer:

```text
[x] Current upgrade authority transfers program upgrade authority to 6ZuPr...
[x] solana program show confirms new authority.
```

Realms execution:

```text
[ ] Execute initialize_registry instruction.
[ ] Execute register_epoch instruction.
[ ] Execute activate_epoch instruction.
[ ] Confirm registry status.
[ ] Confirm epoch status = 1 Active.
```

Final documentation:

```text
[ ] Record authority transfer signature.
[ ] Record registry initialization signature.
[ ] Record epoch registration signature.
[ ] Record epoch activation signature.
[ ] Update Orrery docs.
```

---

## Attached Realms Instructions

The following Base64 Encoded Instruction payloads are to be generated and attached separately after final payload review.

Approved instruction sequence:

```text
1. initialize_registry
2. register_epoch
3. activate_epoch
```

The payloads must use:

```text
Program:
PHYcBRWd6mKATk3xo8oYi3d55BBHUc7kAN4kK91cJoE

Realm:
DsWWtZrqXBcqTTPoEyFH793Euq82r95CuXWTwqo3JZur

Registry authority:
6ZuPrCK472jw3ZjRBqa6PZQ1tyVvY5BuYfWS7GMq7hX8

ASTRALIS epoch zero:
1725148800

ASTRALIS epoch duration:
21600

Initial epoch:
202602
```

The payloads must not be executed until `solana program show` confirms:

```text
Authority: 6ZuPrCK472jw3ZjRBqa6PZQ1tyVvY5BuYfWS7GMq7hX8
```

```
```
