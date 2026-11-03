# JobSpark Engineering Proof

**Kyle Spivey** · Forward-deployed systems builder  
Updated: November 3, 2026

This is the single public engineering evidence index for JobSpark.  
It is not a marketing document. Every section below links to concrete evidence of how the system is built, tested, deployed, and recovered.

[Live Demo (synthetic)](https://jobsparksystems.app/?demo=falcon) · [Product site](https://jobsparksystems.com) · [Profile README](https://github.com/SKYBEAMS/SKYBEAMS)

---

## What JobSpark is

JobSpark is a production operations system that coordinates a moving company’s work from intake through dispatch, field execution, contract closeout, history, and payroll around a single shared job record.

The engineering focus is controlled state, explicit transitions, recoverable side effects, and making uncertainty visible instead of silent.

Core principles:
- AI may propose; it does not independently overwrite canonical operational state
- Important changes go through explicit, validated commands
- Interrupted work can resume from recorded checkpoints without double-counting effects
- Missing or conflicting evidence becomes actionable work, not a silent failure

---

## Evidence Categories

Jump to a category:

1. [Deployment & Release Identity](#1-deployment--release-identity)
2. [Failure Modes & Recovery](#2-failure-modes--recovery)
3. [Financial Correctness](#3-financial-correctness)
4. [Authority & Security Boundaries](#4-authority--security-boundaries)
5. [Deterministic Lifecycle & State](#5-deterministic-lifecycle--state)
6. [Test & CI Evidence](#6-test--ci-evidence)
7. [Current Gaps & Honest Status](#7-current-gaps--honest-status)

---

### 1. Deployment & Release Identity

JobSpark is deployed. Frontend and API can ship on different schedules. Release identity is verified by commit SHA, not by assumption.

**What exists today**
- Required PR checks: build/integrity, browser workflow, frontend hooks, production-dependency API startup
- Render deploys the API from `main` on commit
- Vercel builds the frontend
- Public health and version probes exist to confirm the running SHA
- Documented release and rollback posture

**Key evidence**
- Live demo and product site are publicly reachable
- Deployment and ownership notes are maintained in the private repository and available on request

---

### 2. Failure Modes & Recovery

The system is designed so that interruptions, partial completion, and external failures do not silently corrupt operational or financial state.

**What is demonstrated**
- Durable closeout execution with recorded checkpoints
- Recovery workers that resume from the last completed stage
- Protection against double-counting payroll or duplicating side effects
- Explicit handling when state is missing or retry limits are reached (surfaces as attention items)
- Controlled drills for closeout interruption and restore scenarios (emulator-based)

**Design stance**
- Checkpoints + domain guards make replay safe
- External effects (messages, payroll writes) are tracked separately from internal progress
- Owner attention is required when automatic recovery is no longer safe

---

### 3. Financial Correctness

Payroll and ledger behavior is treated as high-stakes. The system prefers visible problems over silent incorrect completion.

**Current posture**
- Ledger rows and payroll runs are created through controlled commands
- Missing rates and incomplete evidence are intended to block or surface completion
- Idempotent aggregation is a core requirement (retries must not double-count hours)

**Known focus areas (November 2026)**
- Server-side enforcement that missing rates cannot reach a PAID state
- Correct attention-item resolution after rate corrections
- Completeness of revenue and workload queries under large history

These items are tracked as explicit findings and next work. Detailed audit notes are available on request.

---

### 4. Authority & Security Boundaries

Write authority is server-owned. The browser presents state and submits commands; it does not hold the final authority to mutate consequential records.

**Boundaries maintained**
- Workspace isolation
- Role-based guards on sensitive actions
- Explicit separation between browser writes and server-validated commands
- Storage and evidence handling rules
- Public demo runs in an isolated synthetic workspace with no customer data

Detailed authority and security reference documents live in the private repository and can be shared with serious reviewers.

---

### 5. Deterministic Lifecycle & State

Jobs move through an explicit lifecycle. Important transitions are commands, not free-form status changes.

**Key behaviors**
- Intake preserves source evidence before acceptance
- Scheduling and dispatch can be locked
- Customer-driven changes after lock become review items instead of silent mutations
- Closeout requires validated evidence and proceeds through checkpoints
- History and payroll are downstream of successful closeout stages

The public demo walks a synthetic job through the main path. Deeper state-machine and transition evidence is available on request.

---

### 6. Test & CI Evidence

The private repository maintains required CI checks and a substantial automated suite.

**Publicly summarized evidence**
- Multiple required CI jobs (build, browser, hooks, API startup)
- Browser journeys covering assignment, permissions, contract upload, office review, payroll/history, and correction paths
- Targeted suites for closeout integrity, concurrent assignment, customer change lifecycle, and communications recovery
- Emulator-based drills for recovery and restore behavior

Exact current counts, full test maps, and CI run links require private repository access and can be provided to reviewers.

---

### 7. Current Gaps & Honest Status

JobSpark is in active V1 hardening. The following remain open or only partially demonstrated:

- Full deployed acceptance of a complete live customer job (end-to-end financial + communications evidence)
- Independent verification of all production policies, IAM, and rollback artifacts
- Measured economic impact / unit economics
- Repeatable customer onboarding and operator handoff package
- Resolution of the specific financial correctness findings noted in section 3

The system demonstrates strong controlled-decision and recovery design. It does not yet claim formal pilot sign-off or production certification for an external operator.

---

## How to go deeper

| Audience | What to do |
|----------|------------|
| Resume / initial review | Read this page + try the [live demo](https://jobsparksystems.app/?demo=falcon) |
| Serious technical review | Request access to the private JobSpark repository and the detailed ownership / test / authority documents |
| Hiring conversation | I can walk through any section live, including recovery drills, state transitions, and financial correctness controls |

---

## Summary

JobSpark is a real, deployed system built around explicit operational state, guarded transitions, recoverable execution, and visible uncertainty.  
This page is the public index of that engineering work. Deeper source, tests, and internal review material are available to people who need them.

— Kyle Spivey  
[jobsparksystems.com](https://jobsparksystems.com) · [LinkedIn](https://www.linkedin.com/in/kylespivey1)
