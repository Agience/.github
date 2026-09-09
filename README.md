# Agience

> Information carries through space, and through time.
> **Entroptics** carries it through space. **Mantle** carries it through time.
> **Agience** is the one who is looking.

---

## Entroptics — the instrument

Look through a small opening and there is a limit to the detail you can see. That is why a cheap
telescope blurs. **Entroptics measures that limit for any ordered signal, and works it out from the
data itself, with nothing to tune.**

Almost every tool for this has a knob someone has to set by hand, and a setting that works on one
instrument is quietly wrong on the next. Entroptics has no knob. The resolution comes from the
signal. The threshold comes from the noise floor. The only external input is your own false-alarm
tolerance — and the system says precisely where that decision enters.

```bash
pip install entroptics        # the core needs only numpy
```

Independent. Open. Reproducible. Falsifiable — each one a checkable fact rather than a claim about
quality.

| repo | what it is |
|---|---|
| [`entroptics`](https://github.com/Agience/entroptics) | **the instrument.** Start here |
| [`entroptics-jlens`](https://github.com/Agience/entroptics-jlens) | Entroptics reads of the Jacobian lens — the machine-learning surface |
| [`entroptics-llm`](https://github.com/Agience/entroptics-llm) | inference and RAG: how many to keep, measured rather than set as a hyperparameter |
| [`entroptics-mass-gap`](https://github.com/Agience/entroptics-mass-gap) | the mass gap as a finite-aperture effect — paper, Lean 4 development, analysis code and figure data |

Validated on four independent carriers with no per-substrate tuning, and the governing mathematics is
machine-verified in Lean 4 / Mathlib, `sorry`-free.

---

## Agience — the platform

A model-free intelligence platform, and where Entroptics runs at scale. Signals cross a membrane,
condense into typed content, and every capability is a shareable, signed, content-addressed
artifact. **No model runs inside Agience** — nothing in the answer path is a trained weight, and that
rule covers remote APIs called with your own key.

### Run a node

```bash
curl -fsSL https://get.agience.ai/install.sh | sh     # macOS, Linux
```

```powershell
irm https://get.agience.ai/install.ps1 | iex          # Windows
```

Python 3.11+ is the only prerequisite. The installer builds a private virtualenv rather than touching
the interpreter you already have, generates your key material, and seeds the trust. Four services
come up on loopback: identity, the store, the gateway and the observation engine. Everything lands
under one directory; removing it removes the node and takes nothing else with it.

Prefer to read it first? The bootstrap is
[`install.sh`](https://github.com/Agience/agience-observe/blob/main/package/install/install.sh) — it
fetches [`agience-observe`](https://github.com/Agience/agience-observe) and runs its installer, which
you can equally do by hand.

### The pieces

| repo | what it is |
|---|---|
| [`agience-observe`](https://github.com/Agience/agience-observe) | **start here** — the installers, host packaging, seed corpora, backup and restore |
| [`agience-mantle`](https://github.com/Agience/agience-mantle) | **the substrate.** One SQLite file plus a filesystem CAS, opened in-process — no external database process to provision. Each artifact carries its own identity, version history and provenance inside it, so the audit trail *is* the data rather than a log beside it |
| [`agience-crystal`](https://github.com/Agience/agience-crystal) | **the signal guide.** Takes whatever arrives, works out what kind of thing it is, and routes it to whatever handles that kind |
| [`agience-chorus`](https://github.com/Agience/agience-chorus) | **the specialists.** Seven services, each holding the operators of one domain |
| [`agience-ember`](https://github.com/Agience/agience-ember) | **the local leaf.** Runs on your own machine, holds your data, answers from it directly, and reaches the wider network only when it has to |
| [`agience-origin`](https://github.com/Agience/agience-origin) | identity and authority |
| [`agience-prism-py`](https://github.com/Agience/agience-prism-py) | the wire protocol |
| [`agience-build`](https://github.com/Agience/agience-build) | the agent tooling for the workspace |

---

## Authorization is reachability

A traversal over containment edges from a principal's grants outward.

> **Reachability decides which keys are issued — it does not derive them.** A grant is not a rule the
> storage layer chooses to honour; it is what decides whether a key is handed out at all. The cell
> key itself is derived on demand and never stored, so there is nothing at rest to take.

Revocation is a single grant edit — nothing is re-encrypted and no key is rotated. It takes effect
within the verifier's memo TTL, 30 seconds by default and clamped to the earliest grant expiry.

Content is encrypted per principal with AES-256-GCM, and the AAD binds each ciphertext to its
`(principal, collection)` slot, so a blob written for one collection does not authenticate in
another.

Search can run over a blind-token encrypted index, so the storage layer performs the search without
reading it. **That index does not yet cover a whole corpus.** On our own reference store it covers
the lexicon and our own documents — a small fraction of the total — and everything else is served by
an ordinary plaintext lexical index. The encrypted-search property is real and its coverage is
partial; both halves travel together.

## Self-hosting

Self-host is at full parity with the hosted tier, at $0. Reads and search queries are unmetered.
Non-custodial in data, name, identity and money. Zero take rate on operator revenue, and a flat
facilitation fee rather than a percentage — commerce never gates your own data, export or backup
paths.

## License

Dual-tracked: AGPL-3.0 for the platform services, Apache-2.0 for the tooling, CC-BY-4.0 for the
documentation. Each repository carries its own `LICENSE` and `NOTICE`.

Commercial licensing and security reports: **connect@agience.ai** — please email rather than opening
a public issue for anything security-related.
