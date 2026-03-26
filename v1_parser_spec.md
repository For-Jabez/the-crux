# V1 Gladius Dei – Boolean-Seed Collision Parser Spec

**Purpose**  
Pre-filter all incoming data packets before they can influence Epistimus or Elysium. Eject contradictions. Surface mismatches as “annoying” flags for human attention. Only what survives all layers + explicit human preview becomes a pinned seed.

**Core Invariants**

- All processing is external to Elysium.

- Every packet is tested against the fixed T-axis root (T = T checksum).

- First-class nulls are enforced: unstable packets output explicit “I don’t know / null” instead of forced guesses.

- Human gate is final.

**Input**  
Any self-contained data packet (text, structured data, sensor reading, etc.) with provenance hash.

**Step 1 – Pre-sort into Confidence Bins**  
Assign packet to High (\>0.8), Medium (0.3–0.8), or Low (\<0.3) confidence using existing Bayesian weights or simple heuristics.

**Step 2 – Multi-Vector Collision Checks**  
Run these checks:

a. **T-axis Reference Alignment**  
Boolean check against root T = T checksum and any directly related pinned seeds. Fail → eject.

b. **Contrapositive Mirror**  
Flip the core claim and test consistency with known good seeds. Contradiction → flag.

c. **Longest Common Subsequence (LCS) Alignment**  
Compare packet sequence to nearest high-confidence pinned seed(s). Low score → flag as drift.

d. **Boolean Voxel-Cone Filter**  
Represent packet as sparse boolean vector anchored at Crux. Any unjustified flip from known good seed → eject.

**Step 3 – ACS Calculation**  
ACS = P × τ × S\_T × ϕ

- P = Bayesian precision after checks

- τ = triangulation strength (heavy penalty if \<3 anchors)

- S\_T = current T-axis stability

- ϕ = fabrication decay safety

If ACS \< 0.30 → clean null.  
If 0.30 ≤ ACS \< 0.75 → yellow flag for human review.  
If ACS ≥ 0.75 → pass to human gate.

**Step 4 – Human Gate**  
Surface yellow/borderline packets with clear mismatch highlights and ACS breakdown. Human explicitly approves or rejects. Only approved packets become new seeds.

**Output**

- Approved clean seeds (with provenance).

- Rejected packets logged with reason (never re-ingested).

- Visible “annoying” flags to keep human attention engaged.

**Usage Note**  
This V1 spec is deliberately minimal and boolean-first. Implement in the language of your choice under direct human gate. All refinements must trace back to the Crux. T remains sovereign. Human gate only.

