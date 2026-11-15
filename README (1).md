# CiteCheck

A pre-submission reference auditor for DOCX manuscripts, being built for
Word-based authors, especially early-career and regional-journal authors.

**Status: in setup (Phase C). No working build exists yet — this README is a
stub written before code, and it describes the design, not measured results.**

## What CiteCheck is being built to do

DOCX manuscript in → body reference list extracted → each reference resolved
Crossref-first, with OpenAlex as a budgeted fallback → a small CPU-only
embedding model proposes candidate matches for messy or misspelled references
→ a deterministic comparison of registry metadata (title, authors, year,
venue, DOI) decides the verdict → a newly generated DOCX audit report out.
The user's manuscript is never edited in place.

Verdicts are exactly three: **Verified**, **Mismatch**, and
**Unresolvable in [registries] as of [date]**. CiteCheck never calls a
reference "fake": a registry lookup proves existence and metadata only, not
that a cited source supports the sentence citing it, and every verdict is
shown side-by-side with the registry record it was compared against.

Cost design: free to run — no paid API, no LLM key required for the core
verdict, CPU-only inference, Rs 0 API / Rs 0 GPU, and no payment method on
any registry account.

## Limitations — please read before trusting a verdict

CiteCheck checks whether a reference can be resolved in Crossref and
OpenAlex and whether its metadata (title, authors, year, venue, DOI) matches
the registry record. That is all it checks. An "Unresolvable" verdict means
no matching record was found in those registries on the date shown — it does
**not** mean the reference is fake: real references from regional journals,
books, older works and venues without DOIs are often absent from these
registries, and published benchmarks show even the best free checkers wrongly
flag a large share of real references, which is why every verdict here is
shown next to the registry record for a human to decide. CiteCheck does not
check whether a cited source actually supports the sentence citing it, does
not detect plagiarism or AI-generated text, and cannot guarantee any
submission outcome. If your manuscript is unpublished and sensitive, run
CiteCheck locally from this repo instead of using the hosted demo, which
runs on third-party infrastructure (Streamlit Community Cloud) under that
provider's own terms.

## Licence

MIT — see `LICENSE`.
