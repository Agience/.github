# Agience

A trusted information platform, and Entroptics, the signal analysis that complements it.

## Agience platform

Every piece of information in Agience is a signed, content-addressed artifact that carries its
own identity, version history and provenance. You can check where it came from, who changed it
and that it has not been altered. Access follows
grants, and revoking one is a single edit. It runs hosted or on your own machine, with the same
features either way.

```bash
curl -fsSL https://get.agience.ai/install.sh | sh     # macOS, Linux
```

```powershell
irm https://get.agience.ai/install.ps1 | iex          # Windows
```

| Repository | What it is |
|---|---|
| [agience-observe](https://github.com/Agience/agience-observe) | Installers and host packaging. Start here to run a node. |
| [agience-mantle](https://github.com/Agience/agience-mantle) | The substrate: one SQLite file and a content-addressed store, opened in-process. |
| [agience-origin](https://github.com/Agience/agience-origin) | Identity and authority. |
| [agience-crystal](https://github.com/Agience/agience-crystal) | Signal condensation and routing. |
| [agience-chorus](https://github.com/Agience/agience-chorus) | Domain and platform operators. |
| [agience-ember](https://github.com/Agience/agience-ember) | The observation engine that runs on your own machine. |
| [agience-pharos](https://github.com/Agience/agience-pharos) | Knowledge and documentation. |
| [agience-prism-py](https://github.com/Agience/agience-prism-py) | The Python SDK. |
| [agience-build](https://github.com/Agience/agience-build) | Agent tooling for the workspace. |

## Entroptics

Most analysis tools ask you to choose: how many components to keep, where to set a threshold,
which window or rank to use. A setting that works on one dataset is quietly wrong on the next.
Entroptics reads those answers from the data itself. It finds how much real structure an
ordered signal holds — how many components, what they are, how fast they decay and oscillate —
with the resolution set by the signal and the threshold by its own noise floor. There is nothing
to tune, and the one choice left to you, how many false alarms you accept, is stated where it
enters.

The same read carries across very different data, and each application is published open
source with its paper, code and benchmarks:

- Language-model context: how many retrieved items to keep, which one is an injected
  instruction, and whether an answer stayed on its sources.
- Model weights: what a checkpoint's structure shows without running it.
- Radio: a physical layer that is detectable as energy, not as a signal, and a mesh built on it,
  on commodity software-defined radios.
- Astronomy: fast radio burst structure recovered from CHIME/FRB data, untuned.
- Physics: the Yang–Mills mass gap read as a finite-resolution effect, with a Lean 4
  development.

```bash
pip install entroptics        # the core needs only numpy
```

| Repository | What it is |
|---|---|
| [entroptics](https://github.com/Agience/entroptics) | The library. Start here. |
| [entroptics-context](https://github.com/Agience/entroptics-context) | Language-model context: what to keep, what is injected, what drifted. |
| [entroptics-jlens](https://github.com/Agience/entroptics-jlens) | Jacobian-lens reads of a model checkpoint, from the weights alone. |
| [entroptics-positivity](https://github.com/Agience/entroptics-positivity) | Positivity read from the weights alone. |
| [entroptics-infer](https://github.com/Agience/entroptics-infer) | Inference from a corpus's own geometry, with no trained weights. |
| [entroptics-rf](https://github.com/Agience/entroptics-rf) | A radio physical layer: blind acquisition and a keyed waveform on commodity SDRs. |
| [entroptics-mesh](https://github.com/Agience/entroptics-mesh) | A one-way radio mesh over entroptics-rf: no acknowledgements, no handshakes. |
| [entroptics-frb](https://github.com/Agience/entroptics-frb) | Fast radio burst morphology from CHIME/FRB data: reproduce and verify. |
| [entroptics-mass-gap](https://github.com/Agience/entroptics-mass-gap) | The mass gap as a finite-resolution effect: paper, Lean 4 development and analysis code. |

Each research repository ships its paper as a PDF with a Zenodo DOI.

## Contact

- Website: [agience.ai](https://agience.ai)
- X: [@AgienceAI](https://x.com/AgienceAI)
- Discord: [discord.com/invite/fyWWqzeUKH](https://discord.com/invite/fyWWqzeUKH)
- Email: connect@agience.ai. Please report security issues by email rather than in a public issue.

Issues and pull requests are read periodically. Agience is built by [Ikailo Inc.](https://ikailo.com)
Each repository carries its own `LICENSE` and `NOTICE`.
