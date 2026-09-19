# Document validation

Checked September 19, 2026.

| Check | Result |
|---|---|
| Compilation | Successful with Tectonic 0.17.0 and its bundled acmart 1.83 |
| Length | 10 PDF pages; technical material ends on page 9; references start on page 9 |
| Page size | US Letter, 612 × 792 PDF points |
| Layout | Two columns; configured 7 × 9-inch body; 0.34-inch gap |
| Typography | 10 TeX-point body, captions, tables, and references; 12-point leading; ordinary mathematical subscripts use script size |
| Grayscale | Black text, equations, and tables; no color-dependent encoding |
| Page numbering | Present on every page |
| Cross-references | Every source reference has a defined label; no unresolved PDF markers |
| Bibliography | Every cited key exists; 13 cited entries |
| Result fidelity | All nine result tables compared against original LaTeX; numerical measurements preserved |
| Explicit correction | Four zero fairness/share cells for no-migration controls replaced with undefined markers |
| Anonymization | No author name, public CAGE-S name, or identifying project URL in the PDF; PDF author metadata empty |
| Visual inspection | All 10 pages rendered and inspected for clipping, overlap, readability, and pagination |
| Original preservation | No tracked original file modified; revision is a separate directory on local branch eurosys-2027-revision |
| Research reproduction | Not performed: experiment code, model, and raw measurements are absent |

TeX emits underfull-line warnings, a nonfatal 2.38-point vertical-box
warning during bibliography output, and bibliography completeness warnings
for some original entries. The rendered pages show no clipping or overlap.
The build does not certify missing bibliographic metadata or scientific
claims. A different TeX installation may change line breaks; rebuild and
inspect the PDF again after edits.

The reviewer PDF contains an AI-assistance disclosure. The author notes
and source package are not themselves anonymous research artifacts.
