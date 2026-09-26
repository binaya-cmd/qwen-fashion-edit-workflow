# Local AI Fashion & E-commerce Image Editing with ComfyUI

A local Qwen workflow for experimenting with everyday garment edits using a source photo, product reference and painted clothing mask.

**Status: experimental workflow starter.** The low-budget JSON is now included and structurally checked. End-to-end image generation, visual quality, peak memory and speed are not yet validated for this public graph. This project is independent of Qwen and ComfyUI.

## Start here

1. Read the [hardware guide](docs/hardware-guide.md).
2. Follow [installation](docs/installation.md) and obtain the exact files in [model downloads](docs/model-downloads.md).
3. Download [Qwen_Fashion_Edit_3060.json](workflows/low-budget/Qwen_Fashion_Edit_3060.json) using **Download raw file** and drag it into ComfyUI.
4. Follow the [workflow instructions](workflows/low-budget/README.md) to supply two images and paint a mask.
5. Review the output and consult [troubleshooting](docs/troubleshooting.md).

## What it does

The graph edits a painted garment region and composites it over the original source. Zero-mask areas retain source pixels; soft edges blend. Outputs keep the original dimensions, but the edited region is generated at a lower working resolution. Inspect fabric, seams, fit, logos, color and face consistency before using an output in a product listing.

## Setup paths

| Setup | Intended use | Status |
| --- | --- | --- |
| RTX 3060 12 GB | GGUF Q4_K_M, reduced working resolution and offloading | Experimental graph included; inference and performance untested |
| RTX A6000 / A40 48 GB | More memory headroom locally or on rented hardware | Comparison not benchmarked; cloud processing is remote |
| Larger-memory configurations | Evaluate after a measured need | Research only |

## Public scope

General fashion and e-commerce examples only. The public baseline uses generic prompts and placeholder input filenames. Client images, model weights, credentials, confidential prompts and proprietary paid workflows remain outside the repository and its history. No demo images are included. Model downloads and installation are manual.

The [pro folder](workflows/pro-placeholder/README.md) remains a documentation placeholder. External models and software retain their own licenses; original repository material is provided under the [MIT License](LICENSE).

## Next validation work

- [x] Add a public baseline graph and check its links and public-facing content.
- [ ] Complete a generation run with cleared demo assets.
- [ ] Record exact software/model revisions, peak VRAM/RAM and timings.
- [ ] Publish reviewed examples with an asset manifest.
- [ ] Compare a high-memory setup using the same inputs and settings.
