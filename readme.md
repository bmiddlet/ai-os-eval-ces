# AI-OS eval.CES

**Dynamic Clinical Environment Simulator (CES) Evaluation Harness for the AI-OS / Performance‑Gated Autonomy (PGA) Framework**

---

## Overview

**AI‑OS eval.CES** provides a high‑fidelity, closed‑loop simulation environment for evaluating governed AI agents operating within complex clinical systems. It is designed to assess how the **AI‑OS / PGA Framework** performs when decisions alter patient trajectories, resource availability, workflow dynamics, and downstream uncertainty in real time.

Unlike static benchmark testing, eval.CES enables **systems‑level validation of autonomous decision governance** under realistic operational conditions.

This repository contains the experimental environment, scenario generators, metrics, and orchestration tools required to conduct reproducible CES‑based evaluations.

---

## Purpose

The primary goal of eval.CES is to evaluate the safety, effectiveness, and operational coherence of governed autonomy mechanisms, including:

- **Performance‑Gated Autonomy (PGA)** decision authorization
- **Shadow Mode** observation and learning behavior
- **Resource‑aware escalation** under constrained clinical capacity
- **Multi‑agent coordination and conflict resolution**
- **Temporal safety and latency sensitivity**
- **Outcome‑aware closed‑loop decision effects**

The platform supports both single‑agent and multi‑agent experiments across a range of clinical scenarios.

> **Important:** This repository does **not** implement the core AI‑OS/PGA engine. It evaluates it.

---

## Relationship to `rrwa_env`

The core AI‑OS / PGA kernel resides in the companion repository:

**`rrwa_env` — RRWA / PGA Framework and Engine**

`ai-os-eval-ces` imports the kernel as an external dependency via a stable adapter layer. This separation ensures:

- Clean architectural boundaries
- Independent versioning and release cycles
- Reproducible experiments pinned to specific kernel states
- Flexibility to evaluate multiple kernel variants
- Preservation of intellectual‑property controls

Conceptually:

```
rrwa_env        → Governing engine (AI‑OS / PGA)
ai-os-eval-ces  → Dynamic evaluation environment (CES)
```

---

## Architecture

At a high level, eval.CES simulates a clinical system in which governed AI agents operate.

```
Synthetic Cohort → CES Environment → Agent Proposal → PGA Authorization → Action → State Update → Outcome
```

Key design principles:

- Closed‑loop simulation of patient and system dynamics
- Explicit modeling of uncertainty and information flow
- Operational constraints (staffing, capacity, latency)
- Deterministic reproducibility via seeds and configuration
- Separation between environment, agents, and governance logic

---

## Repository Structure

```
src/eval_ces/
  ces_env/      Patient and hospital simulation engines
  agents/       Task‑specific agent implementations (e.g., medication reconciliation)
  eval/         Experiment runner, metrics, and reporting
  adapters/     Interfaces to the external PGA kernel

configs/        Scenario definitions and experiment parameters
scripts/        Utility and experiment scripts
notebooks/      Exploratory analysis (optional)
docs/           Protocols and architecture notes
```

### Component Roles

- **ces_env** — Simulates patient state, care processes, and resource dynamics
- **agents** — Generate task‑level proposals based on observations
- **eval** — Orchestrates trials and computes performance metrics
- **adapters** — Connects CES to the external governance kernel

---

## Installation (Local Development)

Recommended local layout:

```
~/Documents/AI-OS/
  rrwa_env/
  ai-os-eval-ces/
```

Create and activate a virtual environment inside `ai-os-eval-ces`:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
```

Install the CES package and the kernel dependency in editable mode:

```bash
pip install -e .
pip install -e ../rrwa_env
```

Verify linkage:

```bash
python -c "import rrwa_env; print(rrwa_env.__file__)"
```

---

## Reproducibility

Experiments are designed to be reproducible through:

- Fixed random seeds
- Version‑controlled configuration files
- Explicit scenario definitions
- Trace logging of environment state and decisions
- Pinning to specific kernel commits

Reproducibility artifacts are stored per experiment run.

---

## Intended Use Cases

- Evaluation of governed clinical AI agents
- Stress testing under operational constraints
- Comparative studies of autonomy policies
- Multi‑agent coordination research
- Safety validation prior to real‑world deployment

---

## Status

This repository is under active development and represents an experimental research platform.

Interfaces and internal structure may evolve as the AI‑OS / PGA program matures.

---

## Citation and Acknowledgment

If using this framework in research, please cite the associated AI‑OS / PGA publications when available.

---

## License

To be determined.

---

## Contact

Maintained as part of the AI‑OS research program.

