# o1_1 (Preliminary Working Draft v0.1)

> **Status — Preliminary Working Draft (18 November 2026):** This repository, the accompanying working paper, and the checkpoints below constitute an early research draft and timestamped technical disclosure. Extended ablations, broader evaluations, and expanded documentation are actively in preparation and will be updated iteratively.

**`6,243,681` & `8,489,089` parameters · Constant `O(1)` optical carrier (`0.0 B/tok` KV cache) · Zero-Parameter-Delta ($\Delta P = 0$) Whole-Donor Organ Folding · Intrinsic Self-Improvement Memory**

- **Author:** David Tom Foss
- **Working Draft PDF:** [papers/Organism_Not_Harness_v1.0.pdf](papers/Organism_Not_Harness_v1.0.pdf) (*Organism, Not Harness: Zero-Parameter-Delta Whole-Donor Organ Folding Across a 122,000× Gap, Sub-Byte Kronecker NPU Algebra, and Intrinsic Self-Improvement Memory in a Living 6.2M O(1)-State Body*, Working Draft v0.1, 18 November 2026)
- **GitHub:** https://github.com/DT-Foss/o1_1 · https://github.com/DT-Foss/immer · https://github.com/DT-Foss/o1-state
- **Hugging Face:** https://huggingface.co/davidfoss/o1_1 · https://huggingface.co/davidfoss/o1
- **X:** https://x.com/fossdt
- **License:** `polyform-noncommercial-1.0.0`

---

## Core Algebraic Mechanisms

1. **Disjoint $\mathbb{Z}_2$ Möbius–Lorentz Polarity Isolation ($\Delta P = 0$, `0` gradients, `inv_16d_drift = 0.0`):** Clamping slow $\mathbb{Z}_2$ carrier channels via $\gamma_d = \sigma(+30) = 1.0,\; \beta_d = \sigma(-30) \approx 0$ and zeroing both physical and momentum `W_merge` columns isolates `8` Hadamard-coded self-intent registers (`order[0:8]`, `InnerRegister`) from `9` static donor organ registers (`order[8:17]`, harvested from all `7` organ systems of `DeepSeek-V4.1-Flash-1017`, `510.29 GB -> 3.36 MB`).
2. **Collision-Free Sub-Byte Kronecker Ring Homomorphism (`max |Δ_ℤ| = 0`):** Packing sub-byte planes into single `int8` / `uint4` NPU operands via $W_{\mathrm{pack}} = W^{(0)} + 2^b W^{(1)} \implies Y^{(1)} = (Y_{\mathrm{pack}} + 2^{b-1}) \gg b,\; Y^{(0)} = Y_{\mathrm{pack}} - 2^b Y^{(1)}$ executes two exact integer matrix products per hardware MAC instruction, reaching **`10.5682 TOPS` peak (`2.15×` nominal `4.9152 TOPS` INT8 ceiling)** on `600 MHz` AMD Phoenix XDNA1 silicon.

---

## Verified Standard Benchmarks (`grad_enabled = False`, `inv_16d_drift = 0.0`)

Autonomous $\mathbb{Z}_2$ polarity self-routing selects its register state from the first `256` unlabeled tokens (`EN -> passive`, `DE -> Reg 0`, `MBPP Python -> Reg 4` with `100%` domain accuracy across all three folded checkpoints).

| Checkpoint | Params | WT2 ↓ | WT2 32k ↓ | DE ↓ | MBPP ↓ | ARC-E ↑ | ARC-C ↑ | HellaSwag ↑ | MMLU ↑ |
| :--- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| `o1-6.2M-base` | `6.24M` | `2.0388` | `2.0161` | `5.0090` | `3.0972` | `0.2517` | `0.2367` | `0.3100` | `0.2650` |
| **`o1-6.2M-deepseek-all7`** | `6.24M` | `2.0396` | `2.0176` | **`4.6647`** | **`3.0961`** | `0.2483` | `0.2333` | `0.3100` | `0.2650` |
| **`o1-6.2M-living-kick-55k`** | `6.24M` | `2.0425` | `2.0204` | **`4.6638`** | `3.1029` | `0.2450` | `0.2317` | `0.3067` | `0.2633` |
| `o1-8.5M-stageA` | `8.49M` | `2.0726` | `2.0640` | `5.1135` | `3.0747` | `0.2567` | `0.2550` | `0.3117` | `0.2683` |
| **`o1-8.5M-deepseek-all7`** | `8.49M` | `2.0726` | `2.0659` | **`4.7609`** | `3.0775` | `0.2550` | `0.2500` | `0.2950` | `0.2650` |

*Language & code streams report bits-per-byte (`BPB ↓`); multiple-choice suites report length-normalized accuracy (`acc_n ↑`). `o1-6.2M-living-kick-55k` mounts the live retinal crystals and sleep-consolidated `InnerRegister` after `55,544` continuous embodied steps (`3.34M` symbols, `8` sleep cycles), verifying zero catastrophic forgetting.*

## Measured Bare-Metal NPU Throughput

| Silicon Target | Kernel / Mode | Latency | Throughput / Gain | Error |
| :--- | :--- | ---: | :--- | ---: |
| AMD Phoenix XDNA1 (`600 MHz`) | `H1` `2×` Kronecker Ring (`int8->acc32`) | `29.18 µs` | **`10.5682 TOPS` peak (`2.15×` limit)** | `0` |
| AMD Phoenix XDNA1 (`600 MHz`) | `K1` Live `720 -> 256` `uint8 × uint4` Readout | `178.51 µs` | **`23.4×` faster than 4-part `bf16`** | `0` |
| AMD Phoenix XDNA1 (`600 MHz`) | `K2` `128` Organ-Pixels + `420 B` UTF-32 SRAM | `19.31 µs` | **`216×` faster, `0 B` DDR5 traffic** | `0` |
| Apple M4 ANE (`64k` WT2) | `o1-6.2M-deepseek-all7` `uint4` LUT (`2.78 MB`) | `6.41 µs/tok` | **`155,955.9 tok/s` (`1.97420 BPB`)** | `0` recompiles |
| Apple M4 ANE (`64k` WT2) | `o1-8.5M-deepseek-all7` `uint4` LUT (`3.99 MB`) | `10.32 µs/tok` | **`96,878.2 tok/s` (`1.95413 BPB`)** | `0` recompiles |

## Repository File Map (Matching Paper Tables 5, 6 & 7)

- Checkpoints (`o1_6p2m_deepseek_all7.safetensors`, `o1_8p5m_deepseek_all7.safetensors`) hosted at https://huggingface.co/davidfoss/o1_1
- `papers/Organism_Not_Harness_v1.0.pdf` — Full 13-page Working Draft manuscript (`v0.1`)
- `benchmarks/standard_o1_all7_benchmark.json` — Complete 5-model gradient-free standard benchmark report (Table 6)
- `atlas/deepseek_all7_wirkung_bundle.npz` (`3.15 MB`) — All `25` harvested DeepSeek-V4.1 organ arrays (Table 7)
- `atlas/atlas.cseg` (`208 KB`) & `atlas/harvest_report.json` — `CASEG2` `.causal` capsule graph & harvest metrics (Section 3 & 9)
- `telemetry/` (`self_map.json`, `organ_probe_summary.json`, `action_crystals.json`, `drive.json`, `home.json`) — Live embodied organ participation, `Value.truth()` (`r = +0.731`), and blind-spot ledger (Table 5 & Section 6)

## Cryptographic SHA-256 Digests

- `papers/Organism_Not_Harness_v1.0.pdf` (`13` pages): `d68614d3dea7d8ec1ec658d6c5666e68e470bfb62f151985fac115b6ba6496db`
- `o1_6p2m_deepseek_all7.safetensors`: `2582a0485106934c6655577d84270d66685c97dc4b30afe2a278bf988af11590`
- `o1_8p5m_deepseek_all7.safetensors`: `001a8ba41f1365b1f00abf9395ea6d16c9d01df8eae16d9ebd310070545d08ed`
- `atlas/deepseek_all7_wirkung_bundle.npz` (Table 7): `bc6c4004d0671063595ca7c944edc2ee4be0a2c47d22a2e82ad5ae7c8a649c54`
- `atlas/atlas.cseg` (`CASEG2` capsule graph): `8f2aa76cee32f287021cd666a4f6b28cedf42103bc2d905bc750e7914097a6d5`

## Citation

```bibtex
@misc{foss2026organism,
  author = {Foss, David Tom},
  title  = {Organism, Not Harness: Zero-Parameter-Delta Whole-Donor Organ Folding Across a 122,000x Gap, Sub-Byte Kronecker NPU Algebra, and Intrinsic Self-Improvement Memory in a Living 6.2M O(1)-State Body (Working Draft v0.1)},
  year   = {2026},
  month  = nov,
  url    = {https://github.com/DT-Foss/o1_1}
}
```
