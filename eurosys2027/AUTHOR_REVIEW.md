# Author review: CAGE-S to EuroSys 2027

The subject fits distributed systems and resource management. The strongest
available paper is an empirical study of a policy-constrained placement
decision procedure. The current evidence does not establish a deployed
edge--cloud system, migration safety, or improved application latency.
Editing can clarify that contribution; it cannot supply those missing results.

## What changed

The revision leads with a concrete placement problem, explains source
retention before migration, and distinguishes policy admission, prediction,
selection history, and empirical headroom. It replaces the repeated
four-stage novelty argument with a narrower statement of the contribution.
Related work now recognizes that filtering before scoring already exists
in Kubernetes. It avoids treating an author's chosen combination of
features as proof that competing systems lack useful functionality.

The original system model shortlisted the fully feasible set, while the
method and algorithms shortlisted the policy-and-batch candidate set before
screening risk and headroom. Those procedures can choose different nodes.
The revision follows the detailed method and Algorithms 2 and 4, and states
that agreement with full ranking is empirical rather than guaranteed.
**Confirm this choice against the actual implementation.**

The original complete algorithm assigned a destination after calling a
verification routine even if that routine did not commit. The revised
pseudocode explicitly leaves a failed recheck uncommitted. This corrects
the written specification; it is not evidence that experiment code behaved
that way. The runtime's fixed-snapshot, sequential behavior is kept distinct
from atomic reservation in a live controller.

The revision retains all nine result tables and their reported measurements.
The observed-source fairness and top-ten values are changed from zero to
an em dash because no migrations makes those quantities undefined.
Long method labels are shortened in tables and mapped to their definitions.
The duplicated component-results paragraph, survey matrix, and redundant
figures are removed. No experimental measurements were invented.

The rewritten paper also corrects the Alibaba trace paper's author names
against the published paper: Shutian Luo, Huanle Xu, Chengzhi Lu, Liping
Zhang, and Yu Ding were misnamed in the original entry. Its DOI is added.
The KaiS title is corrected to singular “Network.” Bibliographic metadata
not independently established is not silently completed from memory.

## Scientific issues that need your evidence

1. **Obtain the experiment artifact.** This repository contains LaTeX,
   a PDF, seven figure PDFs, and template files. It contains no scheduler
   code, trained predictor, raw outcomes, policy generator, or environment
   lockfile. The original availability statement described an artifact that
   is not present here. The new statement describes what is actually available.
   Provide the original code and outputs before asserting reproducibility.

2. **Specify the 22 features exactly.** The missing `app:features` appendix
   was referenced but never included. Define each feature, order, units,
   lag behavior, variance convention, and warm-up handling; include model
   hyperparameters and any probability-calibration transformation. Do not
   infer these details from the feature count. The new draft makes this
   limitation explicit instead of leaving an unresolved reference.

3. **Audit temporal leakage.** The model uses projected/headroom features
   derived from margins estimated in a pre-test calibration region that
   also contains development and validation data. The original prose does
   not establish when margins were computed relative to fitting and model
   selection. Supply exact timestamp inequalities, label-boundary handling,
   parameter-selection logs, and residual provenance. A clean test split is
   necessary but is not proof that development selection was leakage-free.

4. **Resolve the cleaning-count contradiction.** The original says 22
   service--instance pairs enter after the first timestamp, but also says
   96,341 of 96,346 pairs are already present then, which leaves five.
   The revision omits the contradictory arrival claims and preserves the
   main dataset counts. Recover the count from the cleaning outputs.
   Also explain how full-trajectory node cleaning and local shard validity
   relate; do not assume they are the same eligibility rule.

5. **Confirm telemetry scale and burst meaning.** Explain the conversion
   from Alibaba's node signals to the normalized 0.8 boundary and the units
   of the instance CPU increase threshold 0.05. Instance CPU is not an
   absolute resource request. The original explicitly says it is used only
   to construct events; preserve that distinction.

6. **Document policy generation.** A hash and seed are insufficient to
   reproduce the overlay without the hash algorithm, seed list, class
   probabilities, capability mappings, and per-class predicates. Legal-node
   counts alone do not specify the generator. Native-source policy violations
   are violations of an imposed synthetic overlay, not evidence of real
   production noncompliance.

7. **Keep the outcome claim narrow.** The native next-state metric reads an
   unchanged recorded destination trajectory. It does not add incoming load,
   remove source load, execute migrations, or measure application SLOs.
   Confirm that later event sources indeed remain those recorded in the
   trace, as the supplied replay description indicates. Do not describe
   these numbers as achieved post-migration overload or latency reductions.

8. **Do not call Q95 a safety certificate.** Two separate empirical
   residual percentiles do not establish joint 95% coverage. The guardrail
   has no destination-specific service-demand or migration-transient term.
   Removing Q95 leaves the reported unsafe proxy unchanged while reducing
   migrations. The demonstrated benefit is enforcing an additional rule,
   not reducing observed failures in that comparison.

9. **Interpret the risk metric fairly.** “Temporal violation” evaluates all
   schedulers against the temporal predictor's threshold, including the
   current-state baseline. Zero violations are expected for a scheduler
   that filters by this threshold. Independent evidence comes from actual
   held-out node labels and decision costs. Against Current-HGB, the natural
   next-state confidence interval reaches zero; avoid claiming a statistically
   established improvement in that proxy.

10. **Check dependence and effective sample size.** The test interval has
    59 timestamps; the balanced workload reuses the same telemetry. Thirty
    overlays produce 462,480 decisions but not 462,480 independent workload
    realizations. Timestamp resampling preserves within-timestamp dependence
    while breaking serial dependence. A moving-block sensitivity analysis
    and more trace windows would strengthen the evidence. No new intervals
    have been invented in this revision.

11. **Explain latency reproducibly.** Supply CPU model, RAM, WSL allocation,
    threads, warm-up, repetitions, and exact package versions from a lockfile.
    The original version table is unverified and has been omitted rather
    than presented as established provenance. The 4.724 ms shortlist
    microbenchmark and 20.247 ms timestamp-wide core benchmark measure
    different paths; neither is migration latency. Verify whether shortlist
    selection uses a full sort, partial selection, or a heap before claiming
    a particular complexity bound.

12. **State fairness and history precisely.** Selection history includes
    retention, but Jain's index counts migrated destinations over all nodes.
    Heterogeneous policy eligibility and different migration counts constrain
    the attainable index. It is a destination-spread statistic, not tenant
    fairness, capacity balance, or an SLO guarantee.

## Priority before submission

First recover the implementation and establish that the tables correspond
to it. Then resolve the schema, cleaning, temporal split, policy generation,
and timing details and replace the explicit draft limitations with verified
methodology. Those are description and provenance gaps, not requests to
invent a larger system.

For a stronger systems contribution, the most valuable additional evidence
would measure placement feedback and incoming demand on an executable
controller or a validated closed-loop model, with a practical baseline and
failure-path tests. A live Kubernetes deployment is not a formal conference
requirement; its absence limits the claims this particular study can support.
Additional shards and workload windows would address a different limitation:
external validity. These are recommended research additions, not experiments
completed during this revision.

## Submission checks

Author-facing checklist from the [EuroSys CFP](https://2027.eurosys.org/cfp.html):

- Fall registration: September 17, 2026; paper: September 24, AoE. Confirm registration.
- PDF; 12 technical pages; references unlimited; supplement separate and optional.
- A4/Letter; 7×9-inch block; two columns; gap ≥8 mm; text ≥10 pt/12 pt leading; numbered; grayscale-readable.
- Double-blind: anonymize authors, links, acknowledgments, self-citations; rename public versions.
- Original work; no concurrent submission; related submissions and workshop extensions require disclosure.
- Maximum three submissions per author/cycle; adjacent-cycle rejection restriction, except invited revision.
- Disclose AI use; follow ACM authorship, review, plagiarism, conflicts, and human-participant policies.
- Reviews January 6; response January 8; notification January 29, 2027. Rebuttal: corrections/questions, no new work; ≤500 words encouraged.
- Acceptance requires shepherd approval. Camera-ready March 5; ORCIDs; one full registration.
- Open access: institutional coverage or APC/waiver; 2027 subsidized rates $500 member/$750 nonmember.

The [artifact process](https://sysartifacts.github.io/eurosys2027/) is optional
after acceptance and uses single-blind evaluation. Fall milestones are
February 8 (submission), February 16 (initial checks), March 1 (decisions),
and March 3 (archive); the CFP marks the artifact dates tentative. Prepare
a runnable, documented package, choose the appropriate
[badges](https://sysartifacts.github.io/eurosys2027/badges), respond during
evaluation, and archive the final artifact permanently. Follow the
[packaging guide](https://sysartifacts.github.io/packaging-guide).

I read the complete CFP and the artifact process, badge, and packaging pages.
Several linked ACM policy pages returned fetch errors; this checklist does
not claim an independent clause-by-clause review of those inaccessible
documents. Their linked requirements still apply. Administrative facts
(registration, conflicts, submission history, authorship, funding, and
institutional payment coverage) cannot be verified from this repository.

## Anonymity and AI disclosure

“Sentry” is a provisional review name, not a claim of a new implementation.
The public CAGE-S version and the revised version describe the same research.
The new title/name reduce direct identity clues but do not guarantee anonymity.
The author requested publication of this revision in the CAGE-S repository.
That publication links the provisional review name to the authors. Before
submission, revisit the conference's anonymization requirements and the
review title/name. No paper has been submitted to the conference.

The PDF explicitly discloses Codex assistance. Read every changed technical
statement and extend the disclosure if other AI tools contributed elsewhere.
The prose was edited for precision, rhythm, and a consistent research voice;
no claim is made that an AI detector will label it human-written.

Citation correction source: [published Alibaba trace paper](https://www1.ece.neu.edu/~ningfang/SimPaper/SOCC21-Alibaba.pdf).
Scheduler comparison source: [Kubernetes Scheduling Framework](https://kubernetes.io/docs/concepts/scheduling-eviction/scheduling-framework/).
