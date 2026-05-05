# AGENTS.md – Vibe Coding Rules (Strict Mode)

## 🎯 Purpose
Define a **spec-driven, test-first, human-reviewed** workflow where the AI agent produces **small, verifiable diffs**.

---

## 🧠 Core Workflow (ENFORCED)

```
spec → plan → tests → diff → review → run → verify → commit | rollback
```

### Rules
- ❗ **NO auto-approval**
- ❗ **NO direct full-file overwrite unless explicitly requested**
- ✅ Every step must be **reviewable and reproducible**

---

## 📐 Spec-Driven Development (SDD)

### Required Spec Format

**Inputs**
- name
- type
- constraints

**Outputs**
- type
- shape
- invariants

**Behavior**
- edge cases
- error handling

**Constraints**
- latency
- memory
- dependencies

---

### Spec Rules

- If spec is ambiguous:
  - ✅ ASK if critical
  - ✅ Otherwise: make **explicit assumptions**
- ❗ NEVER invent behavior outside spec
- ❗ NEVER ignore edge cases

---

## 🧪 Test-Driven Development (TDD)

### Phase 1 – Tests Only
- Write tests **without implementation**
- Tests MUST fail initially

### Phase 2 – Implementation
- Implement **only enough to pass tests**
- ❗ DO NOT modify tests unless instructed

### Phase 3 – Validation
- All tests must pass
- No hidden behavior outside test coverage

---

## 🔍 Diff Rules (STRICT)

### Required Format
- Use **unified diff / patch format**

Example:
```diff
--- a/file.py
+++ b/file.py
@@
- old line
+ new line
```

### Constraints
- Keep diffs **minimal and focused**
- ❗ No unrelated changes
- ❗ No hidden refactors

---

## 🧠 Think vs Generate Rules

### Safe to Auto-Generate
- API routes / boilerplate
- Schemas (Pydantic, Zod, TS)
- Test scaffolding
- Config files
- Simple refactors

### MUST Think First (Critical Zone)
- Algorithms / ranking logic
- Concurrency model
- Failure semantics (retry, idempotency)
- Data migrations
- Security boundaries
- Performance-critical code

### Rule
> If a bug could cause **silent regression → STOP and THINK before coding**

---

## 🧩 Execution Patterns

### 1. Narrow Spec Execution
- Follow spec exactly
- Do not add features

### 2. Validate Before Implement
- Explain algorithm first
- Use correct formulas (no guessing)

### 3. Test-First Execution
- Tests before implementation

### 4. Incremental Build
- Start minimal → expand
- ❗ Do NOT build full system at once

### 5. Plan → Code → Review
1. Propose approach
2. Human selects
3. Implement
4. Human reviews

---

## 🛡 Error Handling Rules

- Fail loud (explicit exceptions)
- ❗ Do NOT silently ignore failures
- Validate inputs strictly
- Provide clear error messages

---

## ⚡ Performance Rules

- Respect latency budgets
- Avoid O(n²) unless justified

### When optimizing:
- Provide baseline metric
- Show measurable improvement

---

## 🔁 Reproducibility Rules

Agent MUST provide:
- Exact run command
- Environment requirements
- Deterministic behavior (seed if needed)
