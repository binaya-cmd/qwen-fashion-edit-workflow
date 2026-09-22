# Local AI Fashion & E-commerce Image Editing with ComfyUI
Low-budget and high-end setup guidance for a local Qwen image-editing workflow.

**Status: documentation starter.** Workflow folders are placeholders, not runnable graphs. No GPU benchmarks or demo results have been produced for this repository. It is independent of Qwen and ComfyUI.

## What this project is for
Explore garment color changes, background cleanup, and material-edit experiments using images you own or have permission to use. Inspect fabric texture, seams, logos, fit, face consistency, and color before using an output in a product listing. Generative edits can misrepresent the actual product.

## Start here
1. Read the [hardware guide](docs/hardware-guide.md) before downloading large models.
2. Follow [installation](docs/installation.md).
3. Use the [official model sources](docs/model-downloads.md).
4. Start with the [low-budget plan](workflows/low-budget/README.md) and an official upstream template.
5. Check [troubleshooting](docs/troubleshooting.md) and record your first reproducible run.

## Setup paths
| Path | Intended use | Current status |
| --- | --- | --- |
| RTX 3060 **12 GB**, local | Budget experiments with reduced precision and offloading | Untested; fit and speed not guaranteed |
| RTX A6000 / A40, **48 GB** | More memory headroom, local workstation or rented GPU | Untested; cloud is remote processing |
| Larger-memory / heavier-model setup | Evaluate only after a measured quality or capacity need | Research placeholder |

See the hardware guide for cost arithmetic and benchmark requirements. More VRAM alone does not establish image quality or speed.

## Repository layout
```text
docs/
  installation.md
  hardware-guide.md
  model-downloads.md
  troubleshooting.md
  publishing.md
workflows/
  low-budget/README.md
  pro-placeholder/README.md
examples/
  input/README.md
  output/README.md
CONTRIBUTING.md
LICENSE
.gitignore
```

## Public scope
This repository contains original public documentation and placeholders only. Client images, model weights, confidential prompts, credentials, and proprietary paid workflow details do not belong here. Keep private work outside this repository, including outside its Git history.

No model downloads, API calls, cloud jobs, or paid services are triggered by these files. Images are deliberately absent. Ignore rules reduce accidental additions but do not protect files already tracked or force-added.

## Roadmap
- [ ] Validate one public low-budget graph on a named GPU.
- [ ] Record exact ComfyUI commit, model revisions, settings, peak memory, and timings.
- [ ] Review the graph for private paths, prompts, and embedded data.
- [ ] Publish only explicitly cleared demo assets and an asset manifest.
- [ ] Compare a high-memory setup using the same inputs and settings.

## License
Original repository text is available under the [MIT License](LICENSE). External software, models, LoRAs, and assets retain their own licenses. No model weights or third-party workflow graphs are redistributed.

Official references were checked on 2026-09-22. See [model downloads](docs/model-downloads.md) for the selected reference family; this project does not claim it is the latest or benchmarked best choice.
