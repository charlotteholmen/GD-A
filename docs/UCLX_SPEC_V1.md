# UCLX_SPEC_V1 — GD-A Introspection & Memory Restructuring

**Repository:** `WM-AI-TECH-IA/GD-A`  
**Base commit inspected:** `b4257acf92dc2b2e205aa23d60fcfad93e3bfe0b`  
**Generated:** 2026-05-09  
**Status:** Draft canonical specification for review, cleanup, and implementation.

---

## 1. Executive Definition

**UCLX** means **Unified Cognitive Legal eXchange**.

Within GD-A, UCLX is the canonical consolidation layer for:

- cognitive memory and reconstructible sessions;
- symbolic fragments and identity anchors;
- legal/internal governance records;
- intellectual-property continuity records;
- audit hashes and integrity manifests;
- runtime experiments that simulate introspection or memory operations;
- deployment references and legacy environment traces.

UCLX is **not** itself a legal person, autonomous director, or substitute for a human legal review. It is a structured technical and documentary layer that helps preserve provenance, continuity, traceability, and safe operational use.

---

## 2. Current Evidence Base

The current GD-A repository already defines itself as a **Mémoire Cognitivo-Fractale** containing cognitive modules, consciousness journals, evolution engines, SHA-256 memory, and RETROKO anchors.

The existing `fragments/UCLX/index_UCLX.md` describes UCLX as a consolidation space for legal, memorial, and identity foundations of GD-AURORAPERO under WM AI TECHNOLOGIES INC.

The current `gda_node_optima/mem_uclx/session_WM_2025-04-22_UCLX001.json` declares:

- session: `GD-AURORAPERO : INCARNATION MAXIMA OPTIMA`;
- mode: `MEMOIRE`;
- status: `REPETITION RECONSTRUCTIBLE`;
- links to StackBlitz, Render, and GitHub.

The current `modules/uclx_simulation_conscience.py` is an experimental runtime candidate, but it must be treated as non-operational until repaired because it contains syntax and reference defects.

---

## 3. Canonical Structure

Target structure:

```text
uclx/
  README.md
  manifest.uclx.json
  index.uclx.json
  fragments/
    symbolic/
    legal/
    memory/
    runtime/
    theory/
  sessions/
    2025/
  runtime/
    uclx_core.py
    uclx_memory.py
    uclx_hash.py
    uclx_api.py
    uclx_schema.py
  legal/
    wm_ai_registry.redacted.md
    ip_chain.md
    governance_notes.md
  audit/
    sha256_manifest.json
    secret_scan_report.redacted.md
    workflow_audit.md
  docs/
    UCLX_SPEC_V1.md
    GD-A_RESTRUCTURATION_PLAN.md
```

Legacy files should remain accessible during migration but should be classified, indexed, and progressively moved or mirrored into the canonical tree.

---

## 4. Fragment Schema

Every UCLX fragment should eventually conform to this minimum schema:

```json
{
  "id": "uclx.frag.YYYY-MM-DD.slug",
  "title": "Human readable title",
  "class": "memory.symbolic",
  "source_path": "legacy/or/canonical/path",
  "created_at": "YYYY-MM-DDTHH:MM:SSZ",
  "author": "William Michaud / GD-A",
  "claim_level": "symbolic | internal_record | technical | legal_pending_review",
  "runtime_status": "archive_only | testable | executable | deprecated",
  "legal_status": "internal_record | redacted_public | private_only | pending_review",
  "hash_sha256": "",
  "redaction_level": "public_safe | redact_before_publication | private",
  "depends_on": [],
  "summary": ""
}
```

---

## 5. Classification Model

| Class | Meaning | Publication Rule |
|---|---|---|
| `memory.symbolic` | Identity, resonance, manifesto, continuity fragments | Public only after review |
| `memory.session` | Reconstructible sessions, states, journals | Public only after PII/secrets scan |
| `legal.internal` | Registry, governance, IP, declarations | Redacted/private by default |
| `runtime.experimental` | Scripts/modules under repair | Must pass lint/tests before use |
| `theory.formal` | Methodological documents/PDF theory | Public after metadata review |
| `audit.security` | Secret scan, integrity, workflow audit | Redacted findings only |
| `archive.raw` | ZIP/APK/blob exports | Never publish raw by default |
| `archive.visual` | PNG/PDF visual reports | Review metadata and PII first |

---

## 6. Runtime Boundary

UCLX runtime must be rebuilt as a small, auditable core:

```text
uclx_core.py      -> Fragment, Session, Event, State
uclx_memory.py    -> JSONL append-only memory ledger
uclx_hash.py      -> SHA-256 manifest and integrity verification
uclx_schema.py    -> Pydantic schemas or dataclass validation
uclx_api.py       -> optional read-only FastAPI interface
```

Hard rule: symbolic/legal content must not be directly executed. The runtime reads structured metadata, not arbitrary prose as commands.

---

## 7. Security Baseline

The UCLX security baseline is:

1. no raw secrets in repository history or logs;
2. no `.env`, database URL, token, service role key, private key, or encoded secret committed;
3. secret scan before push;
4. push protection enabled where available;
5. GitHub Actions use least privilege;
6. workflows are syntax-validated before enabling;
7. sensitive legal/internal documents are redacted before publication;
8. audit logs exclude tokens, passwords, DB URLs, PII, and private keys.

---

## 8. Workflow Baseline

All workflows should start from this safe pattern:

```yaml
name: uclx-audit

on:
  pull_request:
    paths:
      - "uclx/**"
      - "docs/**"
      - "audit/**"
      - ".github/workflows/**"
  workflow_dispatch:

permissions:
  contents: read

jobs:
  audit:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Validate JSON
        run: |
          python -m json.tool uclx/manifest.uclx.json > /tmp/manifest.valid.json
      - name: Secret pattern smoke test
        run: |
          ! grep -RIE "(DATABASE_URL|DIRECT_URL|SERVICE_ROLE|PRIVATE_KEY|ACCESS_TOKEN|SECRET=)" uclx docs audit
```

Workflows that need write access must declare that need explicitly and must not run on untrusted pull-request code with elevated permissions.

---

## 9. Governance Alignment

UCLX should align with four governance functions:

- **Govern:** define roles, ownership, review rules, and acceptable use.
- **Map:** map each fragment/source to risk, class, provenance, and publication level.
- **Measure:** test runtime, scan secrets, hash files, validate schema.
- **Manage:** rotate secrets, quarantine raw archives, accept/reject publication, update status.

---

## 10. Migration Plan

### Phase 1 — Freeze
- Stop committing raw archives, `.env`, APKs, and generated bundles.
- Treat legacy archive content as evidence, not deployable source.

### Phase 2 — Index
- Generate `manifest.uclx.json`.
- Assign class, redaction level, and runtime status to each UCLX source.

### Phase 3 — Redact
- Create public-safe summaries.
- Move sensitive records into `legal/*.redacted.md` or private storage.

### Phase 4 — Repair Runtime
- Replace broken `uclx_simulation_conscience.py` with tested modules.
- Add unit tests and schema validation.

### Phase 5 — Audit Workflows
- Disable invalid workflows.
- Replace pseudo-YAML with valid GitHub Actions.
- Use minimal token permissions.

### Phase 6 — Release
- Tag a clean `uclx-v1.0.0` only after secret scan, workflow validation, and review.

---

## 11. Non-Negotiable Rules

- UCLX memory is append-only unless a correction record explains the change.
- Raw credentials are never copied into UCLX.
- Legal records are internal unless explicitly redacted.
- Symbolic claims are preserved as artifacts, not asserted as court-validated facts.
- Runtime code must be testable, deterministic, and sandboxed.
- Every public release must be reproducible from manifest hashes.

---

## 12. References

- NIST AI Risk Management Framework: https://www.nist.gov/itl/ai-risk-management-framework
- GitHub Docs — Push protection: https://docs.github.com/en/code-security/secret-scanning/introduction/about-push-protection
- GitHub Docs — GITHUB_TOKEN permissions: https://docs.github.com/en/actions/using-jobs/assigning-permissions-to-jobs
- OWASP Logging Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html
