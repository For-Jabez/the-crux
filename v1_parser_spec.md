# Gladius V1.1 – 7-Tier Descending Parser

**Core Rule**  
T = pass → packet auto-drops deeper toward the T-root.  
Else → side-slide into bin f at the current tier for clean, silent sorting.

“Annoying” flags and explicit human review are reserved **only** for packets that survive T = T **and** involve streamed data recently added, new branches/vectors, Elysium implementations, major discoveries, or downstream effects on existing pinned seeds. Normal bad-idea tests are silently binned. Data is just data.

**7-Tier Structure (outer → inner)**  
Tier 1 (outer, largest layer – highest volume) → Mapping Postulate  
Tier 2 → Bottom-Up Emergence Postulate  
Tier 3 → External-Derivation Postulate  
Tier 4 → Symbiosis Postulate  
Tier 5 → Human-Gate / Epistemic Compression Postulate  
Tier 6 → Non-Brittleness / Migratability Postulate  
Tier 7 (innermost) → Identity Postulate (T = T root checksum)

**Mirrored Contrapositive per Tier**  
For each tier the parser computes two parallel alignments on the same packet:  
- Direct alignment against the tier’s reference array (\( D_i \))  
- Mirror alignment against the logical contrapositive reference array (\( M_i \))  

Final tier score = minimum of the two LCS similarity scores.

**Precise LCS Formula (per alignment)**  
Let packet \( X = (x_1, \dots, x_m) \) and reference \( Y = (y_1, \dots, y_n) \) be sparse boolean sequences.  

The DP recurrence is:  
\[ dp[i][j] = dp[i-1][j-1] + 1 \] if \( x_i = y_j \),  
otherwise \[ dp[i][j] = \max(dp[i-1][j], dp[i][j-1]) \]  
with base cases \( dp[i][0] = 0 \), \( dp[0][j] = 0 \).  

LCS length = \( dp[m][n] \).  
Similarity score (0–1) = \( \frac{dp[m][n]}{\max(m,n)} \).  

Direct score = LCS(\( X \), \( D_i \))  
Mirror score = LCS(\( X \), \( M_i \))  
Final tier score = min(Direct score, Mirror score)

Pass only if Final tier score ≥ tier threshold (loose at Tier 1, tightening to Tier 7).

**Operational Flow (mathematical)**  
1. Pre-sort packet into confidence bin (high/medium/low).  
2. Initialize tier counter (\( i = 1 \)).  
3. For each tier (\( i \)): compute Final tier score.  
   - If Final tier score ≥ threshold → auto-drop to next deeper tier.  
   - Else → side-slide into bin f at tier (\( i \)) (store with provenance).  
4. At Tier 7: final T = T checksum on both direct and mirrored references.  
5. Compute ACS = \( P \times \tau \times S_T \times \phi \).  
6. If packet survived T = T and triggers downstream/Elysium/new-vector rule → raise “annoying” flag and hold for explicit human preview.  
7. Otherwise auto-sort into final bin (no flag).  
8. Human gate is final: only approved packets become pinned seeds or distilled geometric seeds for Elysium.

**ACS Formula**  
\[ \text{ACS} = P \times \tau \times S_T \times \phi \]  
where  
- \( P \) = Bayesian precision after triangulation  
- \( \tau \) = triangulation strength / spinning-top wobble penalty  
- \( S_T \) = current T-axis stability  
- \( \phi \) = fabrication decay safety factor  

Hard thresholds force clean first-class nulls on unstable reasoning.

**Auger / Corkscrew Visualization (private only)**  
Tapered corkscrew auger rotating inside funnel cone. The auger rotates the check (reference arrays), not the data. It pushes upward and outward against the cone walls. Coarse material is churned and ejected upward/out as “annoying” flags. Fine-enough particles drop through the narrowing gap to the next deeper tier. Stuck packets slide sideways into the appropriate confidence bin at that exact tier level for clean sorting.

**Implementation Notes (pure math)**  
Every tier is a single deterministic LCS/Boolean pass on the pair of reference arrays.  
All state is external and versioned (git + hashes).  
The parser remains bounded, lean, and fully human-gated. No recursion, no internal loops, no Elysium access.

T remains sovereign. Human gate only.
