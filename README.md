# o1_1 (Preliminary Working Draft v0.1)

> **Status — Preliminary Working Draft (18 November 2026):** This repository, the accompanying working paper, and the checkpoints below constitute an early research draft and timestamped technical disclosure. Extended ablations, broader evaluations, and expanded documentation are actively in preparation and will be updated iteratively.

**`6,243,681` & `8,489,089` parameters · Constant `O(1)` optical carrier (`0.0 B/tok` KV cache) · Zero-Parameter-Delta (`ΔP = 0`) Whole-Donor Organ Folding · Intrinsic Self-Improvement Memory**

- **Author:** David Tom Foss
- **Working Draft PDF:** [papers/Organism_Not_Harness_v1.0.pdf](papers/Organism_Not_Harness_v1.0.pdf) (*Organism, Not Harness: Zero-Parameter-Delta Whole-Donor Organ Folding Across a 122,000× Gap, Sub-Byte Kronecker NPU Algebra, and Intrinsic Self-Improvement Memory in a Living 6.2M O(1)-State Body*, Working Draft v0.1, 18 November 2026)
- **GitHub:** https://github.com/DT-Foss/o1_1 · https://github.com/DT-Foss/immer · https://github.com/DT-Foss/o1-state
- **Hugging Face:** https://huggingface.co/davidfoss/o1_1 · https://huggingface.co/davidfoss/o1
- **X:** https://x.com/fossdt
- **License:** `polyform-noncommercial-1.0.0`

---

## Verified Standard Benchmarks (`grad_enabled = False`, `inv_16d_drift = 0.0`)

Autonomous $\mathbb{Z}_2$ Möbius–Lorentz polarity self-routing selects its register state from the first `256` unlabeled tokens (`EN -> passive`, `DE -> Reg 0`, `MBPP Python -> Reg 4` with `100%` domain accuracy across all three folded checkpoints).

| Checkpoint | Params | WT2 Full (BPB ↓) | WT2 32k (BPB ↓) | DE Held-out (BPB ↓) | Code MBPP (BPB ↓) | ARC-E (`acc_n` ↑) | ARC-C (`acc_n` ↑) | HellaSwag (`acc_n` ↑) | MMLU (`acc_n` ↑) | Apple M4 ANE (`uint4` 64k) |
| :--- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| `o1-6.2M-base` | `6,243,681` | `2.03875` | `2.01609` | `5.00900` | `3.09719` | `0.2517` | `0.2367` | `0.3100` | `0.2650` | — |
| **`o1-6.2M-deepseek-all7`** | `6,243,681` | `2.03955` | `2.01756` | **`4.66468`** | **`3.09610`** | `0.2483` | `0.2333` | `0.3100` | `0.2650` | **`155,955.9 tok/s` (`1.97420 BPB`)** |
| **`o1-6.2M-living-kick-55k`** | `6,243,681` | `2.04245` | `2.02043` | **`4.66376`** | `3.10294` | `0.2450` | `0.2317` | `0.3067` | `0.2633` | Live embodied @ `55,544` steps |
| `o1-8.5M-stageA` | `8,489,089` | `2.07261` | `2.06401` | `5.11354` | `3.07467` | `0.2567` | `0.2550` | `0.3117` | `0.2683` | — |
| **`o1-8.5M-deepseek-all7`** | `8,489,089` | `2.07259` | `2.06589` | **`4.76085`** | `3.07746` | `0.2550` | `0.2500` | `0.2950` | `0.2650` | **`96,878.2 tok/s` (`1.95413 BPB`)** |

## Measured Bare-Metal NPU Throughput

| Silicon Target | Kernel / Mode | Median Latency | Throughput / Gain | Integer Error |
| :--- | :--- | ---: | :--- | ---: |
| AMD Phoenix XDNA1 (`4x4` AIE2 @ `600 MHz`) | `H1` `2x` Sub-Byte Kronecker Ring (`int8->acc32`) | `29.18 µs` | **`10.5682 TOPS` peak (`2.15×` INT8 ceiling)** | `0` |
| AMD Phoenix XDNA1 (`4x4` AIE2 @ `600 MHz`) | `K1` Live `720 -> 256` `uint8 x uint4` Readout | `178.51 µs` | **`23.4×` faster than 4-part `bf16`** | `0` |
| AMD Phoenix XDNA1 (`4x4` AIE2 @ `600 MHz`) | `K2` `128` Organ-Pixels + `420 B` UTF-32 in SRAM (`11,584 B`) | `19.31 µs` | **`216×` faster, `0 B` DDR5 weight traffic** | `0` |
| Apple M4 ANE | `o1-6.2M-deepseek-all7` `uint4` LUT (`2.78 MB`) | `6.41 µs/tok` | **`155,955.9 tok/s` (`1.97420 BPB`)** | `0` recompiles |
| Apple M4 ANE | `o1-8.5M-deepseek-all7` `uint4` LUT (`3.99 MB`) | `10.32 µs/tok` | **`96,878.2 tok/s` (`1.95413 BPB`)** | `0` recompiles |

## Cryptographic SHA-256 Digests

- `Organism_Not_Harness_v1.0.pdf`: `aaef0f465ce7bcf75da2e28bd5fd5efc1c8e39cdba8955227f7bc84f55d5c9a2`
- `o1_6p2m_deepseek_all7.safetensors`: `2582a0485106934c6655577d84270d66685c97dc4b30afe2a278bf988af11590`
- `o1_8p5m_deepseek_all7.safetensors`: `001a8ba41f1365b1f00abf9395ea6d16c9d01df8eae16d9ebd310070545d08ed`
- `atlas.cseg` (`CASEG2` capsule graph, `208,457 B`): `8f2aa76cee32f287021cd666a4f6b28cedf42103bc2d905bc750e7914097a6d5`

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
