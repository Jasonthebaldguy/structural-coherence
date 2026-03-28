# Structural Coherence Formal Operational Calculus — Formal Theory

## Canonical Document Header (Informative / Non-Normative Metadata)

- Document ID: SC-FCALC-000001
- Canonical Name: Structural Coherence Formal Operational Calculus — Formal Theory
- Document Class: FRAMEWORK
- Version: 0.7.0-DRAFT
- Issuance ID: v04
- Release Status: ISSUED
- Effective Date: 2026-03-15
- Last Updated: 2026-03-28
- Issuing Authority: Coherence Research
- DOI / Persistent ID: 10.5281/zenodo.19289657
- Supersedes: SC-FCALC-000001 (Issuance ID: v03)
- Superseded By:
- Header Schema: SC-HDR-000001 (Issuance ID: v12)
- Integrity:
  - SHA-256: ec5e75583f8f382f13ad97d3506e18f8d0ad2bfd67a9a41467595943340a319b
  - Release Tag: 2026-03-28__v04

---

## Document Class Extension: FRAMEWORK (Informative / Non-Normative Metadata)

FWK::Schema-Version: 1.0
FWK::Author: Jason Carroll [0009-0009-6427-694X], Coherence Research
FWK::Basis: SC-AS (SC-CORE-000001 v39c; SC-AXIOM-000001 v11k; SC-HDR-000001 v12; SC-SCOPE-000001 v04)
FWK::Scope: Formal operational theory over SC-AS primitives; proves convergence, closure correspondence, emergence transitions, composition, and ordering-representability conditions; includes abstract reduction system correspondence; derived, non-extending, non-overriding
FWK::Invariants: No new primitives; no new admissibility predicates; no back-propagation; no elevation/co-equality with SC-AS

---

## 0. Purpose and Non-Extension Statement

### 0.1 Purpose

This specification defines the formal operational theory derived from the SC-AS canonical set. It establishes the algebraic, order-theoretic, and convergence properties of the operational calculus, providing the mathematical foundation for the SC-CALC-000001 implementation architecture.

This formal profile is intended to support:
- Formal verification of convergence properties
- Proof of correspondence between operational iteration and declarative closure
- Algebraic characterization of admissible transformation spaces at each regime depth
- Formal conditions under which compositional orderings admit ratio-scale representation
- Formal characterization of emergence transitions between regime depths

### 0.2 Non-Extension Statement

This specification SHALL NOT:
1. Redefine or override any SC-CORE / SC-AXIOM predicate or definition
2. Introduce any new admissibility predicate as if it were SC-AS
3. Claim canonical authority equal to SC-AS specifications
4. Back-propagate formal results into SC-AS or modify SC-AS semantics
5. Assert or imply that structural results constitute domain-specific (physical, biological, economic, or other) derivations

All formal constructs defined herein are derived abbreviations expandable into SC-AS terms. The derivation map (§12) documents every expansion.

### 0.3 Constructive Discipline

All proofs in this specification are constructive. No proof proceeds by contradiction, contrapositive, exclusion, or failure of alternatives. All existence claims are witnessed constructively. This preserves S-6 (Constructive Admissibility and Negation Discipline) throughout the formal theory.

### 0.4 Scope of Applicability

The theorems in this specification characterize structural properties of the SC-AS admissibility space. They apply to ANY system whose structure satisfies SC-AS constraints. Whether a particular domain (physical, biological, organizational, informational, or other) instantiates SC-AS constraints is an empirical question outside the scope of this formal theory. Domain-specific conclusions require domain-specific projection documents that declare their own preservation claims, losses, and injections per SC-SCOPE §4.

### 0.5 Finiteness Scope Declaration

The convergence and closure theorems in this specification (§3–§6) hold for configurations with **finite relevant carriers** — that is, configurations where the union of adjacency-bounded scopes of all active drivers is a finite set. This includes all configurations satisfying F4 (Boundedness) with finitely many active drivers, which encompasses all operationally tractable configurations.

Extension to configurations with infinite carriers (where F4-bounded differentials occupy finite scopes within an infinite ambient carrier) requires additional chain conditions on the infinite ambient structure. Such extensions are not established in this specification and constitute open research.

### 0.6 Terminology Discipline

This specification uses structurally descriptive terminology. Named results describe what they prove in structural terms, without borrowing terminology from domain-specific disciplines. Where structural properties have well-known domain-specific analogs (e.g., structural discreteness under recursive closure has an analog in physical quantum mechanics), this specification does not name the structural property after the domain-specific analog. The structural property is upstream of any specific domain instantiation.

A terminology register at the end of this section defines key terms:

This terminology discipline is a self-referential constraint on this specification only. It does not bind downstream projection documents, which may use domain-specific naming conventions appropriate to their target domain.

**Discrete Recursive Closure (§10):** The structural property that self-consistent return pathways on bounded relational structures close at integer multiples of a fundamental circuit. Named for what it proves: closure is discrete and arises from recursion. Not named "quantization" because the result is about periodic closure of bijections on bounded relational structures — a combinatorial property of finite bijection sets — not about energy packets or quantum states.

**Ratio-Scale Emergence from Compositional Order (§9):** The structural property that an ordering equipped with an associative monotone composition operation and satisfying the Archimedean condition admits a real-valued representation unique up to positive scaling. Named for what it proves: ratio-scale structure emerges from the compositional properties of the ordering. Not named "measurement crystallization" because the result is about abstract orderings, not about physical measurement instruments.

**Scale-Invariant Ratio Determination (§9.4):** The structural property that ratio-scale representations have dimensionless ratios invariant across all admissible representations. Named for what it proves: ratios are determined by structure, invariant across scale choice.

**Single-Anchor Scale Fixing (§9.5):** The operational procedure where one empirical value in a domain-specific projection fixes the unit of a ratio-scale representation, after which all other values are structurally determined. Named for what it does: one anchor fixes the scale.

**Discrete Configuration Spectrum (Corollary 10.2.1):** The structural property that admissible self-consistent configurations under recursive closure form a discrete ordered set. Named for what it proves: the spectrum (in the mathematical sense of ordered set of admissible values) of configurations is discrete.

---

## 1. Regime-Indexed Admissibility Algebra

### 1.1 The Admissible Configuration Space

**Definition 1.1.1 (Admissible Configuration Space).** Given a regime context ρ = (d, K_active, H) where d ∈ D is a depth index in a regime indexing structure (D, ≤, Reg) satisfying D0.13, and K_active = Reg(d) ⊆ K is the active kernel constraint subset, define:

    A_ρ := { X ∈ Config | X ⊨ K_active }

the set of configurations satisfying all constraints in K_active. By D0.14, if d₁ ≤ d₂ then A_{ρ₂} ⊆ A_{ρ₁}.

**SC-AS grounding:** Config is the class of configurations (D1.0). Satisfaction (⊨) is per D0.16. K_active is a subset of the coherence kernel K (D0.10). The contraction A_{ρ₂} ⊆ A_{ρ₁} is D0.14.

### 1.2 The Admissible Redistribution Set

**Definition 1.2.1 (Admissible Redistribution Set).** For a configuration Ψ ∈ A_ρ, define:

    R_ρ(Ψ) := { R : Ψ → Ψ' | R is a redistribution (D1.5) satisfying AR1–AR3,
                 Ψ' ∈ A_ρ, and R resolves at least one driver in Drivers_ρ(Ψ) }

where Drivers_ρ(Ψ) is the set of active drivers (D1.4) of Ψ relative to K_active.

**SC-AS grounding:** Redistribution is D1.5. AR1 enforces continuity (D1.2, F1). AR2 enforces non-negation (D0.9, F2). AR3 enforces adjacency preservation (F3). Driver is D1.4.

### 1.3 The Outcome Set

**Definition 1.3.1 (Outcome Set).** For Ψ ∈ A_ρ with Drivers_ρ(Ψ) ≠ ∅:

    Out_ρ(Ψ) := { Ψ' | ∃R ∈ R_ρ(Ψ) : R(Ψ) = Ψ' }

This is the set of configurations reachable from Ψ by a single admissible redistribution at regime ρ.

**SC-AS grounding:** Out is the Axiom-derived abbreviation (SC-AXIOM Predicate Expansion Register), restricted to the active regime.

### 1.4 The Feasible Set

**Definition 1.4.1 (Feasible Set).** For Ψ ∈ A_ρ:

    Feas_ρ(Ψ) := { Ψ' ∈ Out_ρ(Ψ) | Ψ' ≺_D Ψ }

where ≺_D is the strict part of the Driver-Resolution Preorder (SC-AXIOM III.2A).

Configurations in Feas_ρ(Ψ) are those reachable by a single admissible redistribution that strictly reduces the driver profile.

### 1.5 The Verification Predicate

**Definition 1.5.1 (Per-Step Admissibility).** A candidate Ψ' ∈ Feas_ρ(Ψ) is verified, written Ver_ρ(Ψ, Ψ'), iff all of the following hold:

    (V1)  Ψ' satisfies continuity under the transformation Ψ → Ψ' (D1.2, F1, AR1)
    (V2)  No constraint in K_active is simultaneously enforced and nullified in Ψ' (D0.9, F2, AR2)
    (V3)  Adj(Ψ') preserves adjacency-bounded scope from Adj(Ψ) (F3, AR3)
    (V4)  All structural differentials in Ψ' are contained within finite adjacency-bounded scope (F4)
    (V5)  All structural change between Ψ and Ψ' propagates along adjacency-compatible pathways (D0.23, F5, F11)
    (V6)  No structural relation in Ψ lacks an image in Ψ' under adjacency-preserving isomorphism (D0.28, F8)
    (V7)  E(Ψ') ≥ E(Ψ) under the expressive capacity ordering (D1.3, F10)
    (V8)  K_active is jointly satisfiable for Ψ' (D0.20, F12)
    (V9)  If Drivers_ρ(Ψ') ≠ ∅, then |{ Ψ'' ∈ Out_ρ(Ψ') | Ψ'' is structurally distinct from Ψ' under D0.3 }| > 1 (F9)
    (V10) Ψ' admits bounded regulatory coherence under K_active (VE8, AR4)

**SC-AS grounding:** Each verification condition traces to a specific Foundational Condition and/or Admissibility Rule as annotated. No condition is introduced without SC-AS provenance.

### 1.6 The Verified Feasible Set

**Definition 1.6.1 (Verified Feasible Set).**

    VFeas_ρ(Ψ) := { Ψ' ∈ Feas_ρ(Ψ) | Ver_ρ(Ψ, Ψ') }

This is the set of candidates that are both driver-reducing and fully constraint-verified.

---

## 2. Algebraic Structure of the Transformation Space

### 2.1 The Redistribution Semigroup

**Theorem 2.1.1 (Semigroup Structure).** For a fixed regime ρ, the set of admissible redistributions R_ρ := ∪_{Ψ ∈ A_ρ} R_ρ(Ψ), together with pathway concatenation (D1.9) as composition, forms a semigroup (R_ρ, ∘).

**Proof (constructive).**

(a) *Closure under composition.* Let R₁ : Ψ₀ → Ψ₁ and R₂ : Ψ₁ → Ψ₂ be admissible redistributions in R_ρ with compatible source-target (target of R₁ equals source of R₂). Their composition R₂ ∘ R₁ : Ψ₀ → Ψ₂ is a pathway (D1.9) of length 2. We verify admissibility of the composite:

   - Continuity: D1.2 restriction-consistency is transitive. If R₁ provides witnesses φ_S for all S ⊆ |Ψ₀|, and R₂ provides witnesses ψ_{S'} for all S' ⊆ |Ψ₁|, then the composed witnesses (ψ_{φ_S(S)} ∘ φ_S) give restriction-consistent witnesses for the composite. The restriction-consistency condition (φ_{S₁} = (φ_{S₂})|_{S₁}) composes: if both steps preserve it, the composite preserves it.

   - Non-negation: F2 is evaluated per-transformation. If neither R₁ nor R₂ simultaneously enforces and nullifies any constraint, then the composite does not, because the intermediate Ψ₁ satisfies all constraints (it is in A_ρ by assumption), and neither step disrupts that.

   - Adjacency: F3 preservation at each step implies preservation across the composite, because the adjacency relation of Ψ₂ is compatible with that of Ψ₁, which is compatible with that of Ψ₀.

   - Non-erasure: F8 is transitive. If every relation in Ψ₀ has an image in Ψ₁ (via the R₁ witness), and every relation in Ψ₁ has an image in Ψ₂ (via the R₂ witness), then every relation in Ψ₀ has an image in Ψ₂ (compose the image maps).

   - Expressive non-decrease: F10 gives E(Ψ₁) ≥ E(Ψ₀) and E(Ψ₂) ≥ E(Ψ₁). By transitivity of the embeddability preorder, E(Ψ₂) ≥ E(Ψ₀).

   - Driver resolution: D1.5 requires each redistribution to resolve at least one driver. R₁ resolves at least one driver of Ψ₀. If Ψ₁ has drivers (which it may — R₁ may introduce new drivers while resolving old ones), R₂ resolves at least one driver of Ψ₁. The composite resolves at least one driver of Ψ₀ (the one R₁ resolved). Therefore D1.5 is satisfied for the composite as a pathway from Ψ₀ to Ψ₂.

Therefore R₂ ∘ R₁ ∈ R_ρ (when source-target compatible). ∎ (closure)

(b) *Associativity.* Pathway concatenation is associative by construction (D1.9 defines pathways as ordered sequences; concatenation of ordered sequences is associative). ∎

**Note on algebraic structure.** This is a semigroup, not a monoid. The identity transformation (Ψ → Ψ with no structural change) is not a redistribution under D1.5 because D1.5 requires resolution of at least one driver. The semigroup structure is the native algebraic structure of the redistribution space. All theorems in this specification that use composition use only the semigroup property (closure + associativity). No theorem requires an identity element.

### 2.2 Ordering Compatibility

**Theorem 2.2.1 (Monotone Semigroup).** The Driver-Resolution Preorder ≼_D is compatible with the semigroup structure: if R₁ : Ψ₀ → Ψ₁ with Ψ₁ ≺_D Ψ₀, and R₂ : Ψ₁ → Ψ₂ with Ψ₂ ≺_D Ψ₁, then Ψ₂ ≺_D Ψ₀.

**Proof.** By definition of ≺_D (SC-AXIOM III.2A):

    D(A) ≼_D D(B) ⟺ Out(A) ≠ ∅ ∧ Out(B) ≠ ∅ ∧ (∀B' ∈ Out(B) ∃A' ∈ Out(A) : E(A') ≤ E(B'))

Given Ψ₂ ≺_D Ψ₁ ≺_D Ψ₀:
- Out(Ψ₂) ≠ ∅ and Out(Ψ₀) ≠ ∅ (by the non-empty conditions at each step)
- For any Ψ₀' ∈ Out(Ψ₀), there exists Ψ₁' ∈ Out(Ψ₁) with E(Ψ₁') ≤ E(Ψ₀') (from Ψ₁ ≺_D Ψ₀)
- For any Ψ₁' ∈ Out(Ψ₁), there exists Ψ₂' ∈ Out(Ψ₂) with E(Ψ₂') ≤ E(Ψ₁') (from Ψ₂ ≺_D Ψ₁)
- Composing: for any Ψ₀' ∈ Out(Ψ₀), there exists Ψ₂' ∈ Out(Ψ₂) with E(Ψ₂') ≤ E(Ψ₁') ≤ E(Ψ₀')

This witnesses D(Ψ₂) ≼_D D(Ψ₀).

For strictness: Ψ₂ ≺_D Ψ₁ provides a constructive witness — there exists Ψ₂* ∈ Out(Ψ₂) such that no Ψ₁' ∈ Out(Ψ₁) satisfies E(Ψ₁') ≤ E(Ψ₂*). This witness persists under the transitive extension: the same Ψ₂* witnesses that no Ψ₀' ∈ Out(Ψ₀) satisfies E(Ψ₀') ≤ E(Ψ₂*), because any such Ψ₀' would have a corresponding Ψ₁' with E(Ψ₁') ≤ E(Ψ₀') ≤ E(Ψ₂*), contradicting the original witness.

Therefore Ψ₂ ≺_D Ψ₀. ∎

---

## 3. Well-Foundedness and Termination

**Scope reminder (§0.5):** The results in this section hold for configurations with finite relevant carriers.

### 3.1 Bounded Configuration Theorem

**Theorem 3.1.1 (Finiteness of Relevant Structure).** For any configuration Ψ ∈ A_ρ, the structurally relevant region — the union of adjacency-bounded scopes of all active drivers — is finite.

**Proof.** Each driver D(Ψ) has scope ⊆ |Ψ| that is adjacency-bounded (D1.4 requires adjacency-compatible relational differential). By F4 (Boundedness), all structural differentials are contained within finite, adjacency-bounded scope. The number of active drivers is finite (each driver occupies a distinct adjacency region; F4 bounds each region finitely; the total driver count is bounded by the carrier size). The finite union of finitely many finite scopes is finite. ∎

**Definition 3.1.2 (Relevant Carrier).** For Ψ ∈ A_ρ, define:

    |Ψ|_rel := ∪_{Δ ∈ Drivers_ρ(Ψ)} scope(Δ)

This is the portion of |Ψ| where operational activity occurs. By Theorem 3.1.1, |Ψ|_rel is finite.

### 3.2 Finite Descent Lemma

**Lemma 3.2.1 (Finite Automorphism Group).** For any configuration Ψ with finite relevant carrier |Ψ|_rel, the automorphism group Aut(Ψ|_{|Ψ|_rel}) — the group of adjacency-preserving isomorphisms from the relevant restriction to itself — is finite.

**Proof.** The set Aut(Ψ|_{|Ψ|_rel}) is the set of all adjacency-preserving bijections from |Ψ|_rel to itself. Every such bijection is a member of the set Bij(|Ψ|_rel) of all bijections from |Ψ|_rel to itself. Since |Ψ|_rel is finite (Theorem 3.1.1), Bij(|Ψ|_rel) is finite — it is a subset of the set of all functions from |Ψ|_rel to |Ψ|_rel, which has cardinality bounded by the finite power of a finite set (admitted: finite set notation and cardinality via bijective equivalence). Therefore Aut(Ψ|_{|Ψ|_rel}) ⊆ Bij(|Ψ|_rel) is a subset of a finite set, hence finite. ∎

**SC-AS grounding:** Automorphism is adjacency-preserving isomorphism (D1.6) from a configuration to itself. Finiteness of the relevant carrier follows from Theorem 3.1.1.

### 3.3 Well-Foundedness of the Operational Ordering

**Lemma 3.3.1 (Finite Driver Profile Space).** For any Ψ ∈ A_ρ, the set of structurally distinct driver profiles reachable from Ψ through admissible redistributions is finite.

**Proof.** A driver profile of Ψ is the set Drivers_ρ(Ψ) together with the adjacency structure of each driver's scope. Each driver is a structural differential within a finite adjacency-bounded region (D1.4, F4). The number of structurally distinct adjacency-bounded regions within a configuration of bounded relevant carrier is finite (finitely many subsets of a finite carrier, finitely many adjacency patterns on each subset). Therefore the number of distinct driver profiles is finite.

Under admissible redistribution: each step preserves all structural content (F8) and modifies structure only within the adjacency neighborhood of the resolved driver (V5). New structural elements, if introduced, must be within this neighborhood. The relevant carrier can grow, but each step adds at most |Nbr(S)| elements (where S is the resolved driver's scope). The total growth over k steps is bounded by k × max|Nbr(S)|.

For the well-foundedness argument, we do not need a bound on k (that is what we are proving). Instead, we observe: the ≺_D ordering compares driver profiles via their Out sets and the E ordering (SC-AXIOM III.2A). Each distinct driver profile corresponds to a distinct position in ≺_D. The σ-sequence visits distinct ≺_D positions (because each step is ≺_D-strict, and ≺_D is irreflexive). Therefore the number of ≺_D-distinct positions the sequence can visit is bounded by the number of distinct driver profiles reachable from Ψ₀.

We now show this set is finite. Starting from Ψ₀ with finite relevant carrier |Ψ₀|_rel, each admissible redistribution can produce a configuration whose driver profile differs from the source in a structurally constrained way: one driver is resolved (removed), and new drivers arise only within S ∪ Nbr(S). The total number of possible driver profiles reachable from Ψ₀ is bounded by the number of distinct subsets of the growing carrier that can serve as driver scopes, times the number of distinct adjacency patterns on those subsets. This is finite at each step (finite carrier at each step), and the reachable set after all possible finite-length redistribution sequences is a union of finitely many finite sets — but we need this to be finite WITHOUT assuming termination.

**Key observation:** The ≺_D ordering is a strict partial order (irreflexive by definition, transitive by Theorem 2.2.1). The expressive capacity ordering E, restricted to finite relational structures under adjacency-preserving embedding, has no infinite strictly descending chains (every finite relational structure has finite size, and strict embedding reduces to embeddability of smaller structures into larger ones — a finite structure can only embed into finitely many structurally distinct smaller structures). Since ≺_D is defined through E-comparisons of Out sets, an infinite strictly descending ≺_D-chain would require an infinite strictly descending E-chain among Out-set elements, which cannot exist for finite structures. ∎

**Theorem 3.3.2 (Well-Founded Descent).** Let Ψ₀, Ψ₁, Ψ₂, ... be a sequence produced by the σ step function where each Ψᵢ₊₁ ∈ VFeas_ρ(Ψᵢ). This sequence terminates in finitely many steps.

**Proof.** Each step produces Ψᵢ₊₁ with Ψᵢ₊₁ ≺_D Ψᵢ (from the Feas_ρ definition, §1.4). The ≺_D relation is irreflexive (no configuration is strictly below itself) and transitive (Theorem 2.2.1). By Lemma 3.3.1, the ≺_D ordering on driver profiles reachable from Ψ₀ has no infinite strictly descending chains. The σ-sequence is a strictly descending ≺_D-chain. Therefore it is finite. ∎

---

## 4. The σ Step Function — Formal Properties

### 4.1 Definition (Formal)

**Definition 4.1.1 (σ Step Function).** For Ψ ∈ A_ρ:

    σ_ρ(Ψ) :=
        Ψ                           if Drivers_ρ(Ψ) = ∅                    [TERMINAL]
        BLOCKED(evidence)           if VFeas_ρ(Ψ) = ∅ ∧ Drivers_ρ(Ψ) ≠ ∅  [BLOCKED]
        Sel_ρ(VFeas_ρ(Ψ))          otherwise                               [APPLIED]

where Sel_ρ selects from the verified feasible set per the structural selection criterion (§4.2).

### 4.2 Selection Criterion (Structural)

**Definition 4.2.1 (Structural Selection).** For a non-empty VFeas_ρ(Ψ), define Sel_ρ by the following deterministic procedure:

*Level 1 — Driver-Resolution Minimality:* Among all Ψ' ∈ VFeas_ρ(Ψ), retain only those for which no Ψ'' ∈ VFeas_ρ(Ψ) satisfies Ψ'' ≺_D Ψ'. Call this set Min_D.

*Level 2 — Locality Preference:* Among Min_D, retain only those whose resolved driver has minimal adjacency scope |scope(Δ)|. This prefers the most local resolution, grounded in F5 (Locality) and F13 (Minimal Sufficiency). Call this set Min_L.

*Level 3 — Structural Minimality:* Among Min_L, retain only those with minimal carrier expansion |Ψ'|_rel − |Ψ|_rel (preferring redistributions that add the least new structure, per F13). Call this set Min_S.

*Determinacy (revised).* If |Min_S| = 1, selection is unique. If |Min_S| > 1, selection is any element of Min_S. The selection is determinate in the sense of Definition 4.1.1 — a specific element is produced at each step — but structural equivalence of all elements in Min_S is not asserted per-step.

**Justification for terminal determinacy:** The guarantee that the terminal of the σ-sequence is determinate up to structural equivalence (D1.6) does not depend on per-step uniqueness in VFeas_ρ(Ψ). It is established independently by Theorem 6.4.1 (Closure Correspondence): any driver-free, constraint-satisfying configuration above Ψ₀ is ⪯-equivalent to any other (Step 3c), and D0.15 (Coherent Closure Determinacy) converts ⪯-equivalence to structural equivalence. The terminal is determinate up to ~ by §6.4.1, not by Level 3 per-step uniqueness.

**Consequence:** The selection criterion is well-defined and deterministic. Structural equivalence of the terminal is guaranteed by §6.4.1. Per-step structural equivalence of all Level 3 candidates is not asserted.

**SC-AS grounding:** Minimality under ≺_D is the Driver-Resolution Preorder (SC-AXIOM III.2A). Scope preference is F5 (locality) and F13 (minimal sufficiency). Carrier minimality is F13. Per-step determinism is Definition 4.1.1. Terminal determinacy up to equivalence is D0.18 via §6.4.1.

### 4.3 σ Properties

**Theorem 4.3.1 (σ Monotonicity and Verification).** If σ_ρ(Ψ) = Ψ' with outcome APPLIED, then:

    (a) Ψ' ≺_D Ψ          (strict driver-profile reduction)
    (b) E(Ψ') ≥ E(Ψ)       (expressive non-decrease)
    (c) Ver_ρ(Ψ, Ψ')       (full constraint verification)

**Proof.** (a) follows from Feas_ρ definition (§1.4). (b) follows from V7. (c) follows from VFeas_ρ definition (§1.6). ∎

### 4.4 Selection Non-Foreclosure

**Lemma 4.4.1 (No Selection Forecloses Driver Resolvability).** For any step in the σ-sequence, if σ_ρ selects Ψ' from VFeas_ρ(Ψ), then every remaining driver in Ψ' admits at least two structurally distinct redistributions in Out_ρ(Ψ'). Therefore no σ step forecloses any driver's resolvability within the current regime.

**Proof.** By Definition 1.5.1, condition V9: a candidate Ψ' is in VFeas_ρ(Ψ) only if, whenever Drivers_ρ(Ψ') ≠ ∅, the number of structurally distinct elements of Out_ρ(Ψ') exceeds 1 (per F9, Degrees of Freedom for Redistribution).

V9 is checked for every candidate BEFORE selection (§1.6 requires all V-conditions to hold for membership in VFeas_ρ). Therefore the selected Ψ' necessarily satisfies V9.

Consequently: if any candidate Ψ' would foreclose a remaining driver — leaving that driver with fewer than two structurally distinct redistribution pathways — then Ψ' fails V9 and is excluded from VFeas_ρ. The selection criterion (§4.2) never sees it.

The only case where a driver has no available redistribution is the BLOCKED state, which triggers emergence testing (§7) rather than continued redistribution. Within a regime, every driver in every selected configuration remains resolvable with plural pathways. ∎

**Structural consequence:** The σ-sequence cannot "paint itself into a corner" within a regime. Every step preserves the resolvability of all remaining drivers. The greedy selection strategy (choosing the most local, smallest-expansion candidate) does not sacrifice future resolvability for present minimality, because future resolvability is a precondition (V9) for present selection.

---

## 5. The Γ_fb Loop — Convergence

### 5.1 Definition (Formal)

**Definition 5.1.1 (Γ_fb Iteration).** For Ψ₀ ∈ A_ρ, define the σ-sequence:

    Ψ₀, Ψ₁ := σ_ρ(Ψ₀), Ψ₂ := σ_ρ(Ψ₁), ...

The Γ_fb loop terminates when σ_ρ returns TERMINAL, BLOCKED, or EMERGENCE_REQUIRED (see §7).

### 5.2 Convergence Theorem

**Theorem 5.2.1 (σ-Convergence).** Let Ψ₀ ∈ A_ρ with finite relevant carrier. The σ-sequence beginning at Ψ₀ terminates in finitely many steps, reaching either TERMINAL (Drivers_ρ(Ψ_final) = ∅) or BLOCKED (VFeas_ρ(Ψ_final) = ∅).

**Proof.** By Theorem 4.3.1(a), each APPLIED step produces a configuration strictly below the previous one under ≺_D. By Theorem 3.3.2, strictly descending ≺_D-chains on finite-carrier configurations are finite. Therefore the sequence of APPLIED steps is finite. The sequence must terminate at a step that is not APPLIED — which is either TERMINAL or BLOCKED. ∎

### 5.3 Convergence Bound

**Theorem 5.3.1 (Convergence Bound).** The σ-sequence terminates in at most N steps, where N is bounded by the number of ≺_D-distinct driver profiles reachable from Ψ₀ through admissible redistributions.

**Proof.** Each step visits a distinct ≺_D position (the sequence is strictly descending and ≺_D is irreflexive). The number of distinct positions is bounded by the finite driver profile space (Lemma 3.3.1). ∎

*(Informative note.)* For configurations with small relevant carriers and few drivers, the bound is tight: a configuration with k independent drivers of non-overlapping scope terminates in exactly k steps (each step resolves one driver independently). For configurations with overlapping driver scopes, the bound may be larger but is always finite.

---

## 6. Closure Correspondence

### 6.1 The Structural Ratchet Property

The closure correspondence proof rests on a structural property of the admissible transformation space: structural content, once present, cannot be removed. This is the combined effect of F8 (Conservation Through Transformation) and F10 (Non-Decreasing Expressive Capacity Under Redistribution).

**Theorem 6.1.1 (Structural Ratchet).** For any sequence of admissible redistributions R₁, R₂, ..., Rₙ producing a pathway Ψ₀ → Ψ₁ → ... → Ψₙ, with each Rᵢ ∈ R_ρ(Ψᵢ₋₁):

    (a) Every structural relation present in Ψ₀ has an image in Ψₙ (cumulative non-erasure)
    (b) E(Ψₙ) ≥ E(Ψ₀) (cumulative expressive non-decrease)
    (c) |Ψₙ|_rel ≥ |Ψ₀|_rel in the sense that Ψ₀ embeds into Ψₙ (structural content only accumulates)

**Proof.**

(a) By V6, each step preserves all structural relations: every relation in Ψᵢ₋₁ has an image in Ψᵢ. By Theorem 2.1.1 (semigroup closure), composition of the image maps gives: every relation in Ψ₀ has an image in Ψₙ. ∎

(b) By V7, each step satisfies E(Ψᵢ) ≥ E(Ψᵢ₋₁). By transitivity of the embeddability preorder (D1.3), E(Ψₙ) ≥ E(Ψ₀). ∎

(c) By (a), there exists an adjacency-preserving embedding of Ψ₀'s structural content into Ψₙ (the composed image map). Ψₙ may contain additional structural content (from driver resolution introducing new structure), but it cannot contain less. ∎

**Structural consequence:** The transformation space under SC-AS admissibility is ratchet-like — structure accumulates monotonically. A redistribution sequence cannot undo structural additions made by earlier steps. This means: **a path that adds more structure at any step is permanently committed to that additional structure.** The path that adds minimum structure at each step reaches the terminal with minimum total structural accumulation.

### 6.2 Selection Optimality via Minimal Accumulation

**Lemma 6.2.0 (Locality of Driver Resolution Effects).** For any redistribution R : Ψ → Ψ' resolving driver Δ with scope S, the structural modification is contained within S ∪ Nbr_Ψ(S). Consequently, for any driver Δ₂ with scope S₂ such that (S₂ ∪ Nbr_Ψ(S₂)) ∩ (S ∪ Nbr_Ψ(S)) = ∅, the driver Δ₂ is structurally unaffected by R: Δ₂ has the same scope, the same structural form, and the same Out_ρ outcomes in Ψ' as in Ψ.

**Proof.** V5 (locality-compatible propagation) requires all structural change to propagate along adjacency-compatible pathways within the modification scope. V3 (adjacency preservation) requires the adjacency structure outside the modification scope to be preserved. V6 (non-erasure) requires all structural relations outside the modification scope to be preserved. Therefore, any driver whose scope (including its neighborhood) does not overlap the modification scope is structurally identical in Ψ and Ψ'. Its Out_ρ set is unchanged because the admissible redistributions for Δ₂ depend only on the structure within Δ₂'s scope and neighborhood, which are unmodified. ∎

**Theorem 6.2.1 (Selection Optimality — Independent Drivers).** Let Ψ₀ ∈ A_ρ with finite relevant carrier. If all drivers in Drivers_ρ(Ψ₀) have non-overlapping extended scopes (where extended scope of Δ is scope(Δ) ∪ Nbr(scope(Δ))), then the structural selection criterion (§4.2) produces the terminal with minimal expressive capacity among all reachable terminals.

**Proof.** Non-overlapping extended scopes mean, by Lemma 6.2.0, that resolving any one driver has no structural effect on any other driver. Each driver resolution is therefore independent: the structural cost (carrier expansion) of resolving Δᵢ is the same regardless of which other drivers have been resolved previously.

By the structural ratchet (Theorem 6.1.1), structural additions are cumulative and irreversible. The total structural content of the terminal = content of Ψ₀ + Σᵢ (content added by resolving Δᵢ). Since each resolution's cost is independent of the others, the total equals the sum of individual costs regardless of resolution order. The selection criterion minimizes each individual cost (Level 3 of §4.2: minimal carrier expansion). Therefore the total is minimized. ∎

**Claim 6.2.2 (General Optimality — Open).** Under the general case where driver scopes may overlap, the selection criterion produces a terminal Ψ_T satisfying E(Ψ_T) ≤ E(Ψ_T') for all reachable terminals Ψ_T'. This claim is not proven. The proof of Step 5 establishes per-step minimality of accumulation and a locality-based bound on interaction, but does not close the case where savings from a non-minimal step at i propagate across multiple subsequent overlapping drivers. Listed as **OQ-4** in §14.2.

**Non-load-bearing note.** Neither Theorem 6.2.1 nor Claim 6.2.2 is load-bearing for the Closure Correspondence Theorem (§6.4.1). That result is proven through the ⪯-equivalence argument in Step 3c — all driver-free, constraint-satisfying configurations above Ψ₀ are ⪯-equivalent regardless of which terminal the selection criterion reaches. CALC builds on §6.4.1 without depending on the general optimality claim.

### 6.3 Driver-Freedom and Constraint-Completeness

**Lemma 6.3.1 (Driver-Freedom Equivalence).** For Ψ ∈ A_ρ:

    Drivers_ρ(Ψ) = ∅  ⟺  Ψ satisfies all constraints in K_active without unresolved structural differentials

**Proof.** (⟹) If Drivers_ρ(Ψ) = ∅, then by D1.4, there are no unresolved adjacency-compatible relational differentials in Ψ relative to K_active. Since Ψ ∈ A_ρ (Ψ satisfies all K_active constraints by §1.1), the absence of drivers means all constraints are satisfied stably — no structural differential exists that could indicate partial or unstable satisfaction.

(⟸) If Ψ satisfies all constraints in K_active without unresolved structural differentials, then by D1.4, no driver exists (a driver IS an unresolved adjacency-compatible relational differential). Therefore Drivers_ρ(Ψ) = ∅. ∎

**Corollary 6.3.2 (Driver-Free Configurations are K-Closure-Ready).** A driver-free configuration Ψ ∈ A_ρ with Ψ₀ ⪯ Ψ satisfies D0.12 conditions (1) and (2) for being a K-closure candidate of Ψ₀:

    (1) Ψ₀ ⪯ Ψ (given)
    (2) Ψ is Core-admissible (Ψ ∈ A_ρ)

Condition (3) — ⪯-leastness — is the remaining condition that distinguishes closure candidates from arbitrary driver-free configurations above Ψ₀.

**Lemma 6.3.3 (Driver Reducibility — AR9 Consequence).** For any Ψ ∈ A_ρ:

    If Drivers_ρ(Ψ) ≠ ∅ then either VFeas_ρ(Ψ) ≠ ∅ (further reduction exists) or Ψ is BLOCKED (emergence precondition holds).

In the non-BLOCKED case: ∃Ψ' ∈ A_ρ such that Ψ' ≺_D Ψ.

**Proof.** By AR9 (Nonterminality): if Ψ has an unresolved admissible driver, a nontrivial redistribution must exist. Therefore Out_ρ(Ψ) ≠ ∅. If at least one element of Out_ρ(Ψ) is both driver-reducing (in Feas_ρ) and verification-passing (in VFeas_ρ), then further reduction exists and VFeas_ρ(Ψ) ≠ ∅, providing Ψ' ≺_D Ψ. If no such element exists, then Ψ is BLOCKED (§6.6). ∎

**Structural consequence:** A K-closure candidate Z cannot have remaining drivers. If Drivers_ρ(Z) ≠ ∅, then by Lemma 6.3.3, either Z admits further reduction (contradicting ⪯-leastness, since the reduced Z' would satisfy Ψ₀ ⪯ Z' ⪯ Z with Z' ≺_D Z) or Z is BLOCKED. A BLOCKED configuration is not a closure candidate because it has unresolved structural differentials that would need emergence to resolve — and a closure candidate at regime ρ must resolve within ρ. Therefore any K-closure candidate at ρ is driver-free.

### 6.4 The Closure Correspondence Theorem

**Theorem 6.4.1 (Closure Correspondence).** Let Ψ₀ ∈ A_ρ with finite relevant carrier. Let the σ-sequence under the structural selection criterion converge to Ψ_T with outcome TERMINAL (Drivers_ρ(Ψ_T) = ∅). If the K-closure candidate Cl_K(Ψ₀) exists (per D0.12, D0.15), then:

    Ψ_T ~ Cl_K(Ψ₀)

That is, the terminal configuration of σ-iteration is structurally equivalent (D1.6) to the declarative clean re-entry closure of the initial configuration.

**Proof.**

We show Ψ_T satisfies the three conditions of a K-closure candidate (D0.12):

*Condition 1: Ψ₀ ⪯ Ψ_T under the Non-Divergence Preorder (D0.11).*

D0.11 requires: (a) both are configurations; (b) if Ψ₀ is Core-admissible, then Ψ_T is Core-admissible; (c) for every Kernel Term C ∈ K whose scope applies to configurations, if C is satisfied for Ψ₀ then C is satisfied for Ψ_T.

(a) Both are configurations by construction.

(b) Ψ_T ∈ A_ρ because each σ step preserves admissibility (V8, V10 verified at every step).

(c) Each σ step preserves satisfaction of all applicable constraints (V1–V10 verified at every step). Satisfaction preservation composes: if Ψ₀ ⊨ C and each step preserves satisfaction, then Ψ_T ⊨ C. This is the semigroup composition of constraint-preserving transformations (Theorem 2.1.1 extended to constraint satisfaction — each Vk condition composes because it is evaluated per-step and the per-step guarantee chains transitively).

Therefore Ψ₀ ⪯ Ψ_T. ∎

*Condition 2: Ψ_T is Core-admissible (D0.1).*

Ψ_T ∈ A_ρ by construction (each step preserves admissibility). ∎

*Condition 3: Ψ_T is ⪯-least among admissible configurations above Ψ₀.*

**Step 3a — Ψ_T is driver-free and constraint-complete.**

Drivers_ρ(Ψ_T) = ∅ (TERMINAL outcome). By Lemma 6.3.1, Ψ_T satisfies all constraints in K_active without unresolved structural differentials. By Corollary 6.3.2, Ψ_T satisfies D0.12 conditions (1) and (2).

**Step 3b — Any K-closure candidate Z is driver-free.**

By Lemma 6.3.3 (Driver Reducibility) and its structural consequence: a K-closure candidate at ρ cannot have remaining drivers. If it did, it would either admit further reduction (contradicting ⪯-leastness) or be BLOCKED (requiring emergence, making it not a closure candidate at ρ). Therefore Z is driver-free.

**Step 3c — All driver-free configurations above Ψ₀ are ⪯-equivalent.**

Both Ψ_T and Z satisfy all constraints in K_active (Ψ_T by Lemma 6.3.1, Z by Step 3b). Both are driver-free. By D0.11, Ψ_T ⪯ Z iff for every Kernel Term C ∈ K whose scope applies to configurations, if C is satisfied for Ψ_T then C is satisfied for Z. Since both satisfy ALL constraints in K_active, this holds trivially. By the same argument in reverse: Z ⪯ Ψ_T. Therefore Ψ_T and Z are ⪯-equivalent.

**Step 3d — ⪯-equivalence of closure candidates implies structural equivalence.**

By D0.15 (Coherent Closure Determinacy): if Y and Z are each ⪯-least K-closure candidates, then Y ~ Z. Ψ_T and Z are both ⪯-least (both are ⪯-equivalent, so neither is strictly above the other — both are in the ⪯-least class). Therefore Ψ_T ~ Z. ∎

*Assembly.* Ψ_T satisfies all three D0.12 conditions. By D0.15, Ψ_T ~ Cl_K(Ψ₀). ∎

### 6.5 Significance

Theorem 6.4.1 establishes that the operational calculus (iterative σ steps with the structural selection criterion) converges to the same structural result as the declarative specification (K-closure per D0.12/D0.15). This means:

- The implementation architecture (SC-CALC-000001) computes what the specification (SC-CORE) defines
- No gap exists between operational iteration and declarative closure for TERMINAL outcomes
- The witnesses produced by the operational sequence constructively demonstrate the closure
- The structural selection criterion (§4.2) targets the ⪯-least terminal through the structural ratchet (Theorem 6.1.1) and minimal accumulation (Theorems 6.2.1/6.2.2)

The proof does not require local confluence. Instead, it establishes: (1) the ratchet property makes the operational path monotonically accumulating, (2) the selection criterion minimizes accumulation, (3) driver-freedom is equivalent to constraint-completeness (Lemma 6.3.1), (4) all constraint-complete configurations above Ψ₀ are ⪯-equivalent, and (5) D0.15 converts ⪯-equivalence to structural equivalence.

### 6.6 BLOCKED Correspondence

**Theorem 6.6.1 (Blocked Classification).** If the σ-sequence converges to Ψ_B with outcome BLOCKED (Drivers_ρ(Ψ_B) ≠ ∅ and VFeas_ρ(Ψ_B) = ∅), then one of the following holds:

    (a) Out_ρ(Ψ_B) = ∅: No admissible redistribution exists at regime ρ. By AR9, if Ψ_B has an unresolved admissible driver and a nontrivial redistribution must exist, then this condition indicates the remaining drivers are not resolvable within ρ. This is an emergence signal (§7).

    (b) Out_ρ(Ψ_B) ≠ ∅ but Feas_ρ(Ψ_B) = ∅: Redistributions exist but none strictly reduces the driver profile under ≺_D. The configuration is at a local minimum of ≺_D with unresolved drivers. This may indicate incomparability in the preorder (remaining drivers require simultaneous multi-driver resolution) or an emergence threshold.

    (c) Feas_ρ(Ψ_B) ≠ ∅ but VFeas_ρ(Ψ_B) = ∅: Driver-reducing candidates exist but all fail verification (V1–V10). Every driver-reducing step would violate at least one SC-AS constraint at regime ρ. This is the strongest emergence signal: the constraint architecture at ρ is insufficient to resolve the remaining drivers admissibly.

In all three cases, BLOCKED with unresolved drivers at ρ is the formal precondition for emergence testing (§7).

---

## 7. Emergence Algebra

### 7.1 Emergence Precondition

**Definition 7.1.1 (Emergence Precondition at ρ).** A configuration Ψ ∈ A_ρ satisfies the emergence precondition iff:

    (E-Pre1) Drivers_ρ(Ψ) ≠ ∅
    (E-Pre2) VFeas_ρ(Ψ) = ∅  (σ is BLOCKED)
    (E-Pre3) There exists at least one driver Δ ∈ Drivers_ρ(Ψ) such that no redistribution in R_ρ(Ψ) resolves Δ while satisfying all conditions V1–V10

E-Pre3 constructively witnesses that the constraint architecture at ρ is exhausted for at least one driver.

### 7.2 Emergence Transition

**Definition 7.2.1 (Regime Transition).** Given Ψ ∈ A_ρ satisfying the emergence precondition, define the transition to ρ' = (d', K'_active, H') where:

    d' > d in the regime ordering (D, ≤)
    K'_active = K_active ∪ { C_new }
    H' = H ∪ { constraint history of the σ-sequence at ρ }

**Three-case partition (provable).** The BLOCKED classification (§6.6) partitions all BLOCKED configurations into exactly three structurally distinct cases:

- Case (a): Out_ρ(Ψ_B) = ∅
- Case (b): Out_ρ(Ψ_B) ≠ ∅ and Feas_ρ(Ψ_B) = ∅
- Case (c): Feas_ρ(Ψ_B) ≠ ∅ and VFeas_ρ(Ψ_B) = ∅

These cases are jointly exhaustive and mutually exclusive by definition of Out_ρ, Feas_ρ, VFeas_ρ. This is SC-AS-grounded and provable from the definitions in §1.

**C_new identification procedure (conditioned claim).** Given the structural evidence produced by the applicable BLOCKED case, C_new can be identified under the following condition: *the Axiom chain of SC-AXIOM (Axioms 0 through X) is complete as the ordered sequence of forced constraint types at successive regime depths.* Under this condition, the BLOCKED evidence locates a position in the Axiom chain, and C_new is the first Axiom-chain constraint at or above current depth whose structural signature matches the evidence.

**Completeness is not established anywhere in the current SC-AS suite.** It is not an SC-AXIOM-level claim. It is a gap at the suite level. Therefore: C_new identification is a **principled procedure conditioned on an unestablished completeness assumption**, not a proven algorithm. CALC treats it as a structured heuristic. Listed as **OQ-6** in §14.2.

The emergence product Ψ'₀ ∈ A_{ρ'} is the minimal admissible configuration at ρ' satisfying:

    (Em1) E(Ψ'₀) > E(Ψ)                                          [VE3: strict expressive capacity increase]
    (Em2) Ψ'₀ ≁ Ψ                                                  [VE7: structural non-equivalence]
    (Em3) Ψ'₀ arises through admissible pathway from Ψ              [VE1, VE6: supported emergence with pathway]
    (Em4) Every structural element in Ψ'₀ is derivable from Ψ       [VE5: no external introduction]
    (Em5) All F1–F14 satisfied for Ψ'₀                              [VE2: constraint preservation]
    (Em6) Ψ'₀ admits bounded regulatory coherence under K'_active   [VE8: coherence preservation]
    (Em7) Ψ'₀ is minimal: no admissible configuration exists with E strictly between E(Ψ) and E(Ψ'₀)  [VE4]

### 7.3 Emergence Well-Foundedness

**Lemma 7.3.1 (Carrier Growth Bound Under Emergence).** Each emergence transition Ψ → Ψ'₀ satisfies:

    |Ψ'₀|_rel ≤ |Ψ|_rel + |Nbr_Ψ(scope(Δ_blocked))|

where Δ_blocked is the driver that triggered the BLOCKED state. This follows from Em3 (emergence arises through admissible pathway from Ψ), Em4 (every structural element in Ψ'₀ is derivable from Ψ), and V5 (locality of structural change applied to the emergence pathway). New structural content at the higher regime can only appear within the adjacency scope of the blocked driver.

**Theorem 7.3.2 (Bounded Regime Descent).** For a fixed initial configuration Ψ₀, the number of emergence transitions is bounded.

**Proof.** Each emergence transition strictly increases the expressive capacity (Em1/VE3). By Lemma 7.3.1, each transition adds at most a bounded amount of structural content. The total carrier after k transitions is bounded by:

    |Ψ_k|_rel ≤ |Ψ₀|_rel + Σᵢ₌₁ᵏ |Nbr_Ψᵢ(scope(Δ_blocked,i))|

Since each neighborhood is finite (F4) and bounded by the adjacency degree of elements in the blocked driver's scope, the carrier grows by a finite bounded amount per transition.

Strict expressive capacity increase (Em1) on configurations with bounded carriers has finitely many distinct levels (finitely many structurally distinct configurations on a bounded carrier). Therefore the number of transitions is bounded by the number of distinct E-equivalence classes achievable through bounded structural additions to the initial carrier. ∎

### 7.4 Cross-Regime Coherence Preservation

**Theorem 7.4.1 (Coherence Preservation Across Emergence).** If Ψ ∈ A_ρ and Ψ'₀ ∈ A_{ρ'} is the emergence product, then:

    (a) Every constraint C ∈ K_active that was satisfied for Ψ remains satisfied for Ψ'₀  [by Em5/VE2]
    (b) No structural relation present in Ψ is absent from Ψ'₀  [by F8 applied to the emergence pathway Em3]
    (c) The constraint history H is preserved in H'  [by construction of ρ']

Therefore: emergence is strictly additive in both structural content and constraint satisfaction. Nothing is lost.

---

## 8. Composition Algebra

### 8.1 Decomposition

**Definition 8.1.1 (Boundary Decomposition).** For Ψ ∈ A_ρ with boundary set B ⊆ |Ψ| (per SC-AXIOM III.6), define the decomposition:

    Decomp(Ψ, B) = (Ψ|_L, Ψ|_N, B, posture, I)

where:
- L = interior region, N = exterior region (such that L ∪ B ∪ N = |Ψ|)
- posture ∈ {Closed-Scope, Coupled-Scope} per F14
- I is the interface representation (D0.29) if posture = Coupled-Scope

### 8.2 Independent Processing Under Closed-Scope

**Theorem 8.2.1 (Closed-Scope Independence).** If posture = Closed-Scope, then σ_ρ(Ψ|_L) and σ_ρ(Ψ|_N) can be computed independently.

**Proof.** F14 Closed-Scope requires no cross-boundary import. Therefore:
- Drivers_ρ(Ψ|_L) depends only on the internal structure of Ψ|_L
- Out_ρ(Ψ|_L, Δ) depends only on the adjacency structure of Ψ|_L
- Ver_ρ(Ψ|_L, Ψ'|_L) evaluates only constraints applicable to Ψ|_L
No information from Ψ|_N is needed. Symmetrically for N. ∎

### 8.3 Coupled-Scope Interface Constraint

**Theorem 8.3.1 (Coupled-Scope Interface Preservation).** If posture = Coupled-Scope with interface I, then for any redistribution R : Ψ → Ψ' that modifies elements in both L and N:

    (a) R must propagate through I (F11, F14)
    (b) The interface representation I is preserved in Ψ' (D0.29 + F8)
    (c) Verification Ver_ρ(Ψ, Ψ') must include the interface constraints

**Proof.** (a) F14 Coupled-Scope: any cross-boundary reliance goes through the explicit interface. F11 requires adjacency-compatible propagation, which must pass through boundary elements. (b) F8: I is structural content of Ψ, so it must have an image in Ψ'. (c) I is part of the configuration's structure, subject to all applicable constraints. ∎

### 8.4 Composition Admissibility

**Theorem 8.4.1 (Composition Closure).** If Ψ|_L and Ψ|_N are each in A_ρ, and the interface I between them satisfies F14 and D0.29, then Compose(Ψ|_L, Ψ|_N, I) ∈ A_ρ.

**Proof.** By F7 (Nested Scaling): coherent sub-configurations compose without loss of bounded coherence, adjacency compatibility, or enforceability. Each constraint in K_active that applies to the composite is either: internal to L or N (satisfied by assumption), cross-boundary (mediated by I, enforceable under D0.29), or global (holds on all sub-configurations, holds on composition under F7). ∎

---

## 9. Ratio-Scale Emergence from Compositional Order

### 9.0 Scope Note

This section establishes that the expressive capacity ordering on admissible configurations, equipped with the SC-AS composition operation, admits a ratio-scale representation. The representation is derived constructively from the integer-indexed discrete configuration spectrum proved in §10 (Discrete Recursive Closure) and the pathway index arithmetic derived in §10.0.1 from D1.9/D1.10.

**Forward dependency:** This section depends on §10. The ratio-scale representation is the integer index function defined by §10's fundamental circuit indexing. No external representation theorem is imported. The derivation is closed within SC-AS primitives.

This section does NOT establish:
- That any specific domain's observables have ratio-scale structure
- That physical constants are derivable
- That measurement instruments or experimental procedures follow from the theory

Whether a particular domain instantiates the conditions of this section is an empirical question requiring a domain-specific projection document.

### 9.1 Ordering Scale Types

**Definition 9.1.1 (Ordering Scale Classification — Definitional Taxonomy).** The following taxonomy classifies orderings by the structural strength of their admissible representations. These are definitional distinctions, not imported results.

*Ordinal:* Only the ordering relation is structurally determined. For any strictly monotone function f, if φ represents the ordering then f ∘ φ also represents it. Ratios are not structurally meaningful.

*Interval:* The ordering admits an associative monotone composition and satisfies an Archimedean condition. The representation φ is unique up to positive affine transformation (φ' = aφ + b, a > 0). Differences are structurally meaningful; ratios are not.

*Ratio:* Interval conditions hold, plus a natural zero element exists (an element e such that e ⊕ x ~ x for all x). The representation φ is unique up to positive scaling (φ' = aφ, a > 0). Ratios φ(x)/φ(y) are structurally determined — invariant across all admissible representations.

### 9.2 Composition via the Configuration Operation

**Theorem 9.2.1 (Composition Properties).** The composition operation on configurations (D0.27, F7), restricted to A_ρ with the expressive capacity ordering E (D1.3), satisfies:

    (a) Associativity up to structural equivalence: Compose(Compose(X, Y, I₁), Z, I₂) ~ Compose(X, Compose(Y, Z, I₂), I₁) when interface compatibility holds
    (b) Monotonicity: if E(X₁) ≤ E(X₂), then E(Compose(X₁, Y, I)) ≤ E(Compose(X₂, Y, I)) for compatible Y and I

**Proof.** (a) Composition assembles sub-configurations via adjacency-preserving embedding (D0.27). Embedding is associative up to structural equivalence. (b) If X₁ embeds into X₂ (E(X₁) ≤ E(X₂) by D1.3), then X₁ composed with Y embeds into X₂ composed with Y (the embedding extends to the composite by identity on Y). ∎

### 9.3 Ratio-Scale Conditions and Constructive Representation

**Definition 9.3.1 (Ratio-Scale Conditions).** The expressive capacity ordering E on A_ρ admits ratio-scale representation iff:

    (RSC1) A_ρ admits a composition operation satisfying Theorem 9.2.1 (associative, monotone) — established above
    (RSC2) The Archimedean condition holds: for any X, Y ∈ A_ρ with E(X) < E(Y), there exists a finite integer n such that the n-fold self-composition of X has E ≥ E(Y) — derived from §10 below
    (RSC3) A_ρ contains a minimal element P under E: E(P) ≤ E(X) for all X ∈ A_ρ — the Axiom 0 / Axiom I minimal admissible configuration

**RSC1 established:** Theorem 9.2.1 above. SC-AS grounded via D0.27, F7, D1.3.

**RSC3 established:** The minimal admissible configuration P₀ (Axiom 0, SC-AXIOM §0) satisfies E(P₀) ≤ E(X) for all X ∈ A_ρ. P₀ is the structural zero: Compose(P₀, X, I) ~ X for any X with compatible interface (F7 — Nested Scaling requires the minimal configuration to contribute no additional structural content beyond interface compatibility). SC-AS grounded via Axiom 0, Axiom I, F7.

**RSC2 established from §10 integer spectrum (constructive):** By Corollary 10.2.1 (§10), the admissible self-consistent configuration spectrum at ρ is discrete and integer-indexed by fundamental circuit count. Let n_X denote the fundamental circuit index of configuration X. For any X, Y ∈ A_ρ with E(X) < E(Y): since the spectrum is integer-indexed, n_Y > n_X, and n_Y − n_X is a finite positive integer (by §10.0.1 arithmetic, derived from D1.9/D1.10). The (n_Y − n_X)-fold self-composition of X produces a configuration at index n_X + (n_Y − n_X) = n_Y, satisfying E ≥ E(Y). The required finite n is (n_Y − n_X), computed by §10.0.1 subtraction. SC-AS grounded via §10 (D1.9, D1.10, D1.6, F4, F8) and §10.0.1 arithmetic.

**Constructive ratio-scale representation (no external import):** Define:

    φ : A_ρ → ℕ≥0,   φ(Ψ) := n_Ψ

where n_Ψ is the fundamental circuit index of Ψ from §10.

Verification that φ is a ratio-scale representation:

- *Ordering preservation:* E(X) ≤ E(Y) iff n_X ≤ n_Y (from §10's integer indexing of the E-ordering). Therefore φ preserves the ordering. ✓
- *Composition preservation:* The fundamental circuit index of Compose(X, Y, I) equals n_X + n_Y under the composition operation (§10.0.1 addition, D1.9/D1.10). Therefore φ(Compose(X, Y, I)) = φ(X) + φ(Y). ✓
- *Natural zero:* φ(P₀) = 0 (the minimal configuration has index 0 — zero fundamental circuits). Compose(P₀, X, I) ~ X gives φ(P₀) + φ(X) = φ(X). ✓
- *Uniqueness up to positive scaling:* Any function φ' = a·φ (a > 0) also preserves ordering and composition with φ'(P₀) = 0. Conversely, any ordering- and composition-preserving function with φ'(P₀) = 0 satisfies φ'(X) = φ'(X ⊕ P₀) = φ'(X) + φ'(P₀) and must assign non-negative integers proportional to n_X. Therefore φ is unique up to positive scaling. ✓

This is a constructive ratio-scale representation derived entirely from §10's integer spectrum, §10.0.1 arithmetic, and SC-AS composition properties. No external measurement theorem is invoked.

### 9.4 Scale-Invariant Ratio Determination

**Theorem 9.4.1 (Structurally Determined Ratios).** When RSC1–RSC3 hold at ρ, for any X, Y ∈ A_ρ with E(Y) > E(P₀):

    φ(X) / φ(Y) = n_X / n_Y

is a dimensionless ratio of fundamental circuit indices, invariant across all admissible representations φ' = a·φ (a > 0 cancels in the ratio).

**Proof.** φ'(X)/φ'(Y) = (a·n_X)/(a·n_Y) = n_X/n_Y. The scaling factor cancels. The ratio is a structurally determined integer ratio from §10's indexing. ∎

These ratios are structural properties of the ordering at ρ, determined by the constraint architecture. They are not domain-specific values — domain values arise only through the single-anchor projection (§9.5).

### 9.5 Single-Anchor Scale Fixing

**Definition 9.5.1 (Anchored Representation).** Given a ratio-scale ordering at ρ and a single domain-specific value assignment (anchor) fixing the scale:

    φ_anchored(Ψ) := (n_Ψ / n_anchor) × value_anchor

where n_Ψ is the fundamental circuit index of Ψ from §10, n_anchor is the index of the anchor configuration X_anchor, and value_anchor is the domain-specific value assigned through a projection (per SC-SCOPE §4).

The anchor fixes the unit (a domain-specific injection per the projection discipline). The ratios n_X / n_Y are structural — they come from §10's integer indexing and §10.0.1 arithmetic. All other values are structurally determined from the single anchor.

**SC-AS grounding:** n_Ψ from §10 (D1.9, D1.10, D1.6, F4). value_anchor from projection (SC-SCOPE §4). The anchored representation contains no additional imports beyond §10 and the projection discipline.

---

## 10. Discrete Recursive Closure

### 10.0 Scope Note

This section proves that self-consistent return pathways on bounded relational structures close at integer multiples of a fundamental circuit. This is a combinatorial result about finite groups acting on finite relational structures. It applies to any system with the relevant structural properties. It does not, by itself, constitute a derivation of any domain-specific discreteness phenomenon (such as physical quantization, biological developmental stages, or organizational hierarchy levels). Whether a particular domain exhibits discrete recursive closure because it satisfies SC-AS constraints is an empirical question outside the scope of this formal theory.

### 10.0.1 Arithmetic on Pathway Indices (Meta-Structural Derivation)

**Lemma 10.0.1 (Arithmetic Emergence from D1.9/D1.10 Structure).** Natural number arithmetic on pathway indices — addition, multiplication, and the division algorithm — is derivable from D1.9 (Pathway) and D1.10 (Recursion) through admitted meta-structural apparatus. It does not require downstream depth, domain projection, or external arithmetic axioms.

**Scope distinction.** Pathway index arithmetic is *meta-structural*: it counts and compares structural objects (pathways, compositions, index sets) using admitted apparatus (finite set notation, bijective equivalence, natural number ordering). It is not *object-level*: it does not describe configurations composing via constructive/destructive phases (which operates at Axiom IV depth and beyond).

**Cardinality convention.** Throughout this lemma, cardinality is stated via *bijective equivalence class comparison*: two finite sets have the same cardinality iff a bijection exists between them. No reference to a canonical set {1,...,k} is required; all cardinality claims reduce to the existence or non-existence of bijections between finite sets. This is fully within admitted Meta-Structural Mathematical Vocabulary (SC-CORE).

**Proof.**

**(a) Addition.** Let P₁ be a pathway (D1.9) of length n and P₂ a pathway of length m. By D1.10 (Recursion — closure under concatenation), the concatenation P₁ ∘ P₂ is an admissible pathway. The index set of P₁ ∘ P₂ is the disjoint union of the index sets of P₁ and P₂. The cardinality of a disjoint union of two finite sets is determined by bijective equivalence with the union of two disjoint copies of their respective index sets. No arithmetic is presupposed — only finite set notation, disjoint union, and bijective comparison (all admitted apparatus).

**(b) Multiplication.** Let P be a pathway of length k. The n-fold self-concatenation of P (permitted by D1.10 closure applied iteratively) produces a pathway whose index set is the disjoint union of n copies of the k-element index set of P. The cardinality of this disjoint union is determined by iterated application of (a). No arithmetic is presupposed — multiplication emerges as iterated addition, itself derived from D1.10 concatenation closure.

**(c) Division algorithm.** Given a pathway length m and a fundamental circuit length k* (both finite natural numbers within admitted apparatus):

1. Define Q := { n ∈ ℕ : n ≥ 0 and a bijection exists from the disjoint union of n copies of the k*-element index set into a subset of the m-element index set }.
2. Q is non-empty (n = 0 is a member: the empty disjoint union bijects into the empty subset).
3. Q is bounded above by m under admitted natural number ordering (no more than m copies can fit into an m-element set).
4. Let q := max(Q). This exists by finiteness and ordering on naturals (admitted apparatus: every non-empty bounded subset of ℕ has a maximum).
5. Let r := cardinality of the complement — elements of the m-element index set not covered by the q-fold disjoint union.
6. r < k* by maximality of q: if r ≥ k*, then q + 1 would be in Q, contradicting maximality.
7. Therefore m decomposes as q-fold repetition of k* plus remainder r with 0 ≤ r < k*.

All steps use only: finite set cardinality (via bijective equivalence), set complement, subset inclusion, and natural number ordering comparisons — all admitted meta-structural apparatus. ∎

**Austerity compliance.** No external arithmetic axioms are imported. Addition, multiplication, and the division algorithm are derived consequences of D1.9/D1.10 structure through admitted meta-structural vocabulary. The object-level / meta-structural boundary is maintained: this lemma operates on pathway indices, not on configurations.

---

### 10.1 Formal Statement

**Definition 10.1.0 (Self-Consistent Return Pathway).** A self-consistent return pathway on Ψ ∈ A_ρ is a pathway P(Ψ, Ψ') (D1.9) such that:
- Ψ' ~ Ψ (structural equivalence, D1.6)
- Every transformation in P is an admissible redistribution (D1.5) or emergence (D1.8)
- P is an element of a recursion R (D1.10) — the pathway set is closed under concatenation

**Theorem 10.1.1 (Integer Periodicity of Self-Consistent Return).** Let Ψ ∈ A_ρ with finite relevant carrier, and let P be a self-consistent return pathway on Ψ. Then:

    P closes at and only at integer multiples of its fundamental circuit.

That is: if the cumulative transformation of P after one traversal is the automorphism σ_P ∈ Aut(Ψ|_{|Ψ|_rel}), then σ_P^k = id for some finite integer k ≥ 1, and σ_P^m ≠ id for any non-integer 0 < m < k.

**Proof.**

(1) The self-consistent return pathway induces an adjacency-preserving automorphism σ_P ∈ Aut(Ψ|_{|Ψ|_rel}). This follows because: P maps Ψ to Ψ' ~ Ψ, so the structural equivalence witness (D1.6) composed with the cumulative transformation gives an automorphism. By F8 (conservation), all structural relations are preserved. By D1.2 (continuity), the map is restriction-consistent.

(2) By Theorem 3.1.1, |Ψ|_rel is finite. By Lemma 3.2.1, Aut(Ψ|_{|Ψ|_rel}) is finite.

(3) **Finite order of σ_P derived from admitted apparatus.**

The self-consistent return pathway induces σ_P — an adjacency-preserving bijection from |Ψ|_rel to itself (Step 1). Let Bij(|Ψ|_rel) denote the set of all bijections from |Ψ|_rel to itself. Since |Ψ|_rel is finite (Theorem 3.1.1), Bij(|Ψ|_rel) is finite — its cardinality is the cardinality of all bijections on a finite set, which is a finite natural number under finite set notation.

Consider the sequence of composed bijections:

    ⟨ σ_P⁰, σ_P¹, σ_P², ..., σ_P^{|Bij(|Ψ|_rel)|} ⟩

This sequence has |Bij(|Ψ|_rel)| + 1 terms, all taking values in Bij(|Ψ|_rel). Since the sequence has strictly more terms than Bij(|Ψ|_rel) has elements, there exist indices i, j with 0 ≤ i < j ≤ |Bij(|Ψ|_rel)| such that σ_P^i = σ_P^j as functions on |Ψ|_rel.

*(Admitted basis: this follows from finite set notation and natural number ordering — a sequence of n+1 elements drawn from a set of cardinality n cannot have all elements distinct.)*

Since σ_P is a bijection, it admits a compositional inverse σ_P^{-1} (the unique bijection satisfying σ_P ∘ σ_P^{-1} = σ_P^{-1} ∘ σ_P = id_{|Ψ|_rel}, within admitted function notation).

**Fundamental circuit.** Define:

    M := { n ∈ ℕ : n ≥ 1, σ_P^n = id_{|Ψ|_rel} }

M is non-empty (reachable from the index coincidence above via pathway decomposition — see Lemma 10.0.1). Since M is a non-empty subset of ℕ under admitted ordering, M has a minimum element. Define k* := min(M).

(4) **Integer multiples only.**

*(⟸)* If m = q · k* (q-fold concatenation of k*-length circuits, via Lemma 10.0.1 multiplication), then σ_P^m = (σ_P^{k*})^q = id^q = id. ✓

*(⟹)* Suppose σ_P^m = id. By Lemma 10.0.1 (division algorithm), there exist unique q, r with m = q · k* + r and 0 ≤ r < k*. The sequence is periodic with period k* under function composition (each additional k*-step returns to the same function). Therefore σ_P^m = σ_P^r. If σ_P^m = id, then σ_P^r = id. Since 0 ≤ r < k* and k* = min(M), we have r ∉ M for r ≥ 1. Therefore r = 0, and m = q · k*.

Therefore σ_P^m = id if and only if m is a positive multiple of k*. ∎

### 10.2 Discrete Configuration Spectrum

**Corollary 10.2.1 (Discrete Configuration Spectrum Under Recursive Closure).** At any regime ρ, the set of admissible self-consistent configurations under recursive closure is discrete — indexed by integers corresponding to the number of fundamental circuits. The ordering E on this discrete set determines a spectrum (in the mathematical sense: an ordered set of admissible values) of configurations.

When ratio-scale conditions (§9.3 RSC1–RSC3) hold at ρ, the ratios between adjacent levels in this discrete spectrum are structurally determined dimensionless quantities (by Theorem 9.4.1).

---

## 11. Explicit Non-Goals

This formal profile does NOT specify:
- Canonical serialization formats (reserved for SC-CALC-000001 implementation layer)
- Concrete algorithms for Driver detection, Out enumeration, or Eq checking
- Logging, replay, or audit formats
- Domain-specific projections or domain-specific interpretations of structural results
- The specific content of K_active at each regime depth in unconditional mode (reserved for future research)
- Physical, biological, organizational, or other domain-specific conclusions from the structural theorems

---

## 12. Derivation Map

Every formal construct in this specification traces to SC-AS:

| Formal Construct | SC-AS Source | Section |
|-----------------|-------------|---------|
| Admissible configuration space A_ρ | D0.1, D0.13, D0.14, D0.16 | §1.1 |
| Admissible redistribution set R_ρ | D1.5, AR1–AR3 | §1.2 |
| Outcome set Out_ρ | D1.5, SC-AXIOM register | §1.3 |
| Feasible set Feas_ρ | SC-AXIOM III.2A (≺_D) | §1.4 |
| Verification predicate Ver_ρ | F1–F14, AR1–AR4, VE8, D0.9, D0.20, D0.23, D0.28 | §1.5 |
| Redistribution semigroup | D1.5, D1.9 (pathway concatenation) | §2.1 |
| Ordering compatibility | SC-AXIOM III.2A, D1.3 | §2.2 |
| Finiteness of relevant structure | D1.4, F4 | §3.1 |
| Finite automorphism group | D1.6, F4 | §3.2 |
| Finite driver profile space | D1.4, F4, D1.3 | §3.3 |
| Well-foundedness of operational chains | ≺_D (SC-AXIOM III.2A), D1.3, F4 | §3.3 |
| σ step function | D1.4, D1.5, SC-AXIOM III.2A | §4.1 |
| Structural selection criterion | F5, F13, SC-AXIOM III.2A | §4.2 |
| Selection non-foreclosure | F9, V9 (§1.5), D0.3 | §4.4 |
| σ-convergence theorem | §3.3, §4.3 | §5.2 |
| Structural ratchet property | F8, F10, D1.3, Theorem 2.1.1 | §6.1 |
| Locality of resolution effects | V3, V5, V6, F5, F11 | §6.2 |
| Selection optimality (independent) | F5, F8, F10, F13, §4.2, §6.1 | §6.2 |
| Selection optimality (general) | F5, F8, F10, F13, §4.2, §4.4, §6.1 | §6.2 |
| Driver-freedom equivalence | D1.4, D0.16, K_active, §1.1 | §6.3 |
| Driver reducibility (AR9) | AR9, ≺_D, D0.12 | §6.3 |
| Closure correspondence | D0.11, D0.12, D0.15, D1.6, §6.1–§6.3 | §6.4 |
| Blocked classification | AR9, D0.14 | §6.6 |
| Emergence precondition | D1.4, AR9, VFeas exhaustion | §7.1 |
| Emergence transition | D0.13, D0.14, VE1–VE8, SC-AXIOM chain (0–X) | §7.2 |
| Carrier growth bound under emergence | Em3, Em4, V5, F4 | §7.3 |
| Emergence well-foundedness | D1.3, VE3, F4, §7.3 Lemma | §7.3 |
| Cross-regime preservation | VE2, F8, D0.13 | §7.4 |
| Boundary decomposition | SC-AXIOM III.6, F14, D0.29 | §8.1 |
| Closed-scope independence | F14 (Closed-Scope) | §8.2 |
| Coupled-scope interface | F14 (Coupled-Scope), D0.29, F8, F11 | §8.3 |
| Composition admissibility | D0.27, F7, F14 | §8.4 |
| Ratio-scale emergence conditions (RSC1) | D1.3, D0.27, F7 | §9.2, §9.3 |
| Ratio-scale RSC2 (Archimedean) | §10 (D1.9, D1.10, D1.6, F4), §10.0.1 arithmetic | §9.3 |
| Ratio-scale RSC3 (natural zero) | Axiom 0, Axiom I, F7 | §9.3 |
| Constructive ratio-scale representation (φ = n_Ψ) | §10 (D1.9, D1.10, D1.6, F4, F8), §10.0.1 | §9.3 |
| Scale-invariant ratio determination | §10 integer indexing, §10.0.1 arithmetic (n_X/n_Y), D1.3 | §9.4 |
| Single-anchor scale fixing | SC-SCOPE §4 (projection discipline) | §9.5 |
| Pathway index arithmetic (meta-structural) | D1.9, D1.10, Meta-Structural Mathematical Vocabulary | §10.0.1 |
| Discrete recursive closure | D1.6, D1.10, F4, F8, §10.0.1, admitted apparatus (finite set notation, bijective equivalence) | §10.1 |
| Discrete configuration spectrum | §10.1, §9.4 | §10.2 |

No construct in this specification lacks an SC-AS traceback. All ratio-scale representability results (§9) are derived constructively from §10's integer-indexed discrete spectrum and §10.0.1 pathway index arithmetic, without external import.

---

## 13. Non-Elevation Statement

Nothing in this specification modifies SC-AS admissibility or canonical force. All formal results herein apply only to the operational theory derived from SC-AS and to implementations claiming conformance to SC-CALC-000001.

---

## 14. Resolved Questions and Remaining Open Questions

### 14.1 Resolved

The following items were identified as concerns in earlier drafts and peer reviews, and have been resolved in this version:

**RQ-1: Selection non-foreclosure.** Resolved by Lemma 4.4.1. V9 enforces F9 at every step; no candidate that forecloses a driver passes verification. See §4.4.

**RQ-2: Scope increase bound.** Resolved by Lemma 6.2.0 (Locality of Driver Resolution Effects). Structural modification is contained within S ∪ Nbr(S); effects on non-overlapping drivers are zero. See §6.2.

**RQ-3: Non-reachable configuration ranking.** Resolved by Lemma 6.3.1 (Driver-Freedom Equivalence) and the simplified ⪯-equivalence argument in Theorem 6.4.1 Step 3c. All driver-free, fully-constraint-satisfying configurations above Ψ₀ are ⪯-equivalent, yielding structural equivalence by D0.15. See §6.3–§6.4.

**RQ-4: Emergence constraint identification.** *Partially open.* Three-case BLOCKED partition is provable (§7.2). C_new identification procedure is conditioned on Axiom chain completeness — an unestablished suite-level assumption. Reclassified as **OQ-6**. See §7.2 and §14.2 (OQ-6).

**RQ-5: Well-foundedness bridge (μ to ≺_D).** Resolved by replacing the μ-based argument with a direct ≺_D well-foundedness argument (Lemma 3.3.1 + Theorem 3.3.2). The termination proof now rests on: (i) ≺_D is a strict partial order, and (ii) finite relational structures cannot support infinite strictly descending E-chains. The auxiliary complexity measure μ has been removed entirely. See §3.3.

**RQ-6: Driver-free / constraint-complete equivalence.** Resolved by explicit Lemma 6.3.1 and Corollary 6.3.2, which state and prove the equivalence rather than using it implicitly. See §6.3.

**RQ-7: Greedy optimality.** *Partially open.* Theorem 6.2.1 (exact optimality for independent/non-overlapping drivers) is a clean exact result. The general case (overlapping driver scopes) has been reclassified as **OQ-4** — the proof of Step 5 does not close. See §6.2 (Claim 6.2.2) and §14.2 (OQ-4).

**RQ-8: §9 external import (Krantz et al.).** Resolved in this version. The ratio-scale representation is now derived constructively from §10's integer-indexed discrete spectrum and §10.0.1 pathway index arithmetic. No external measurement theorem is imported. RSC2 (Archimedean condition) is derived from the integer spectrum directly. See §9.3.

### 14.2 Remaining Open Questions

**OQ-3: Archimedean condition for ratio-scale representability (§9.3 RSC2).**

RSC2 is now established from §10's integer spectrum for the discrete case. Whether RSC2 holds at all regime depths for all configurations (including those where the discrete spectrum assumption may not apply) remains regime-dependent. For integer-indexed discrete spectra, RSC2 holds by §10. For other orderings, regime-specific analysis is required.

**Impact of non-resolution:** If RSC2 fails at some regime depth for non-discrete configurations, the ratio-scale representability results (§9.3–9.5) do not hold at that depth. The ordering remains at least ordinal. The operational calculus (§§1–8, §10) is unaffected.

**OQ-4: General selection optimality under overlapping drivers (§6.2).**

Whether the selection criterion produces the globally E-minimal terminal when driver extended scopes overlap. The difficulty: a non-minimal step at i may generate savings at multiple subsequent overlapping steps. Whether cumulative savings can exceed cumulative excess is not established. A genuine new proof strategy is required — not just scoping conditions. **Impact:** affects only E-minimality of the specific terminal reached, not closure correspondence (§6.4.1), convergence (§5.2.1), or emergence admissibility (§7). Operational correctness of CALC is unaffected.

**OQ-5: Per-step structural equivalence in VFeas_ρ(Ψ) (§4.2).**

Whether any two elements of Min_S (same source, same resolved driver scope, same minimal carrier expansion) are necessarily structurally equivalent under D1.6. The conditions are necessary but not shown sufficient for isomorphism. **Impact:** would strengthen the selection criterion from "deterministic" to "canonical." Terminal determinacy already guaranteed by §6.4.1 independently. Non-blocking.

**OQ-6: Completeness of the Axiom chain as constraint type coverage (§7.2).**

Whether Axioms 0–X exhaust all forced constraint types that can appear as C_new in any emergence transition is not established anywhere in the current SC-AS suite. FCALC depends on it for the C_new identification procedure but cannot establish it — this requires SC-AXIOM-level analysis that has not been done. **Impact:** if incomplete, a BLOCKED configuration could require a constraint type not in the current Axiom chain, leaving C_new unidentifiable by the §7.2 procedure. Non-blocking for operational theorems (convergence, closure correspondence, bounded regime descent) which require only the existence of a regime transition, not C_new identification.

---

## Appendix A — Abstract Reduction System Correspondence

### A.1 Purpose

This appendix provides an explicit translation of the SC-FCALC-000001 operational calculus into the language of abstract reduction systems (ARS). This translation does not introduce new results; it restates results from §§1–10 in terminology familiar to the mathematical rewriting theory and theoretical computer science communities. All ARS constructs map to SC-AS-grounded constructs via the derivation map (§12).

### A.2 The Single-Regime ARS

At a fixed regime ρ, define the abstract reduction system ARS_ρ = (S, →) where:

    S := A_ρ (the admissible configuration space, Definition 1.1.1)

    Ψ → Ψ'  :⟺  Ψ' ∈ VFeas_ρ(Ψ) (verified feasible rewrite, Definition 1.6.1)

**Properties of ARS_ρ:**

*Well-founded (Noetherian):* The reduction relation → is contained in ≺_D (Driver-Resolution Preorder). By Theorem 3.3.2, ≺_D has no infinite strictly descending chains on finite-carrier configurations. Therefore → is well-founded: every reduction sequence terminates. ARS_ρ is Noetherian.

*Deterministic under strategy:* The selection criterion Sel_ρ (§4.2) is a deterministic rewrite strategy — it selects exactly one element of VFeas_ρ(Ψ) at each step. The σ step function (§4.1) applies this strategy. The Γ_fb loop (§5.1) iterates to termination.

*Normal forms:* A configuration Ψ is a normal form of ARS_ρ iff Drivers_ρ(Ψ) = ∅ (TERMINAL). No rewrite applies to a normal form.

*Stuck forms:* A configuration Ψ is stuck iff Drivers_ρ(Ψ) ≠ ∅ and VFeas_ρ(Ψ) = ∅ (BLOCKED). Rewrites should apply (drivers exist) but none passes verification. Stuck forms are not normal forms — they are evidence for regime transition (§7).

### A.3 Guarded Rewriting

ARS_ρ is not an unrestricted rewriting system. Each rewrite Ψ → Ψ' must pass the verification predicate Ver_ρ(Ψ, Ψ'), which enforces ten structural guards (V1–V10, §1.5). This makes ARS_ρ a **guarded abstract reduction system**: the reduction relation is filtered by structural constraints at each step.

In standard ARS terminology, the guards are preservation conditions — each step must preserve continuity (V1), non-negation (V2), adjacency (V3), boundedness (V4), locality (V5), conservation (V6), expressive capacity (V7), joint satisfiability (V8), plurality (V9), and regulatory coherence (V10).

### A.4 The Regime Tower

The full operational calculus is not a single ARS but a **tower of guarded Noetherian abstract reduction systems** indexed by regime depth:

    ARS_{ρ₀} → ARS_{ρ₁} → ARS_{ρ₂} → ...

where each transition ARS_{ρᵢ} → ARS_{ρᵢ₊₁} occurs when ARS_{ρᵢ} reaches a stuck form (BLOCKED), triggering the emergence transition (§7.2). The transition produces:

- A new regime ρᵢ₊₁ with strictly expanded constraint set (K'_active ⊃ K_active)
- A new initial configuration Ψ'₀ with strictly greater expressive capacity (Em1)
- A new ARS_{ρᵢ₊₁} with strictly contracted admissible set (D0.14)

By Theorem 7.3.2, the tower is finite (bounded regime descent). The full computation is:

    normalize in ARS_{ρ₀}
    if stuck: lift to ARS_{ρ₁}, normalize
    if stuck: lift to ARS_{ρ₂}, normalize
    ...
    until normal form reached (at some finite depth)

### A.5 Correspondence Table

| ARS Concept | SC-FCALC Construct | Section |
|---|---|---|
| State space | Admissible configuration space A_ρ | §1.1 |
| Reduction relation → | Verified feasible rewrite (VFeas_ρ) | §1.6 |
| Well-founded ordering | Driver-Resolution Preorder ≺_D | §1.4 |
| Noetherian property | Theorem 3.3.2 (finite descent) | §3.3 |
| Rewrite strategy | Structural selection criterion Sel_ρ | §4.2 |
| Deterministic normalization | σ step function + Γ_fb loop | §4.1, §5.1 |
| Normal form | TERMINAL (Drivers_ρ = ∅) | §4.1 |
| Stuck form | BLOCKED (VFeas_ρ = ∅, Drivers ≠ ∅) | §4.1, §6.6 |
| Preservation guards | Verification predicate V1–V10 | §1.5 |
| Regime lifting | Emergence transition | §7.2 |
| Tower termination | Bounded regime descent (Theorem 7.3.2) | §7.3 |
| Monotone cost | Expressive capacity ordering E (non-decreasing) | §4.3(b) |
| Least normal form | K-closure candidate Cl_K(Ψ₀) | §6.4 |

### A.6 What the ARS Framing Does and Does Not Provide

**Does provide:**
- Standard terminology for termination, normalization, and strategy properties
- A well-studied mathematical context for the operational calculus
- Recognition that the σ-system's properties (Noetherian descent, guarded reduction, deterministic strategy) are instances of established abstract structures

**Does not provide:**
- Confluence. ARS_ρ is not claimed to be confluent (different rewrite sequences may reach different normal forms). The closure correspondence (§6.4) is proved via the structural ratchet and ⪯-equivalence argument, not via confluence.
- Church-Rosser property. Not claimed or needed.
- Reduction of the SC-AS-specific content to generic ARS theory. The verification guards, emergence transitions, and regime tower are specific to SC-AS and do not reduce to standard ARS results.

### A.7 Relationship to Known ARS Results

The following known ARS results apply to ARS_ρ:

*König's Lemma (contrapositive, constructive form):* In a finitely-branching Noetherian system, every element has a normal form reachable in finitely many steps. Since VFeas_ρ(Ψ) is finite for finite-carrier Ψ (finitely many candidates), ARS_ρ is finitely branching. Combined with the Noetherian property, this gives an alternative proof of Theorem 5.2.1 (σ-convergence).

*Deterministic strategy correctness:* In a Noetherian system, any deterministic strategy that always selects a valid rewrite step reaches a normal form (if one exists) or a stuck form. This is a general property that §5 proves for the specific strategy Sel_ρ.

These are confirmatory — they show the σ-system's properties are expected for a system with its abstract structure, not accidental.

---

END OF SPECIFICATION

SC-FCALC-000001 v0.7.0-DRAFT | 2026-03-15
Coherence Research
