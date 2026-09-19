# CAGE-S Overleaf manuscript

This project uses the Elsevier CAS double-column template supplied by the user.

## Upload and compile

1. In Overleaf, choose **New Project -> Upload Project** and upload the ZIP.
2. Set the main file to `main.tex`.
3. Use **pdfLaTeX**. The project includes the required CAS class, style, and bibliography style.
4. The default build is anonymized. To compile the author version, edit `main.tex` and replace:

   `\anonymizedtrue`

   with:

   `\anonymizedfalse`

5. Complete `author_info.tex` before compiling the author version.

## Scope of the current manuscript

The paper is intentionally framed as a trace-driven evaluation using the Alibaba `MSResource_0` shard. It does not require a live Kubernetes/KubeEdge testbed or an additional Alibaba shard. The manuscript therefore makes no causal claim about post-migration response time, migration downtime, end-to-end orchestration latency, or universal cross-shard generalization.

## Remaining placeholders

Search the project for `TBD`. The remaining markers concern only information that must be verified before submission:

- exact timing hardware and thread settings;
- artifact URL or archival DOI;
- author emails, affiliations, and CRediT roles.

Do not replace a TBD field with an estimated or remembered value.

## Current evidence included

The manuscript contains the completed Alibaba `MSResource_0` trace evaluation, temporal model metrics, ten internal baselines and ablations, a 20,000-replicate paired timestamp-cluster bootstrap, 30-seed policy robustness, destination-capacity sensitivity, and online-core latency.

The phrase **native next-state unsafe proxy** is deliberate. It must not be changed to post-migration outcome, causal effect, achieved SLA improvement, or measured live-cluster benefit.

## Main files

- `main.tex`: complete manuscript entry point
- `author_info.tex`: author-version front matter
- `sections/`: manuscript sections
- `references.bib`: bibliography
- `figures/`: figures generated from validated replay outputs
