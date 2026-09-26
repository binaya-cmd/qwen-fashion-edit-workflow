# Validation status and reproducible test plan

## Current evidence

| Check | Status | What it establishes |
| --- | --- | --- |
| JSON parsing and graph link consistency | Passed on 2026-09-26: 19 nodes, 27 typed connections | The exported structure is internally consistent |
| Public content review | Generic prompts and placeholder image names; no images or weights supplied | The published file is a public baseline |
| Earlier local setup validation | Baseline model files and graph inputs recognized; two input images absent | Setup recognition, not a generation result |
| Public graph end-to-end generation | Pending | No inference success claim yet |
| Visual quality and garment fidelity | Pending | No demonstrated accuracy claim yet |
| Timings, peak VRAM/RAM and hardware comparison | Pending | No performance numbers yet |

ComfyUI was not listening on local port 8188 during the documentation update on 2026-09-26. No image-generation job was run as part of that update.

## Test inputs

Use a newly created or explicitly cleared non-sensitive source image and everyday garment reference. Do not use client/model photographs from private work. Record the asset source, creator, permission/license, and any required attribution. Keep the originals outside this repository. Publishing demo assets is a separate step from using them in a local test.

## Procedure

1. Install the documented dependencies and select the exact files.
2. Load the exact public JSON and supply both test images.
3. Paint a nonempty clothing mask and save it. Keep details to preserve outside it.
4. Keep baseline defaults, record the actual dimensions and queue one run.
5. Confirm the run completes and saves an output. Check that the output is not simply unchanged because the mask was empty.
6. Compare zero-mask regions with the source and inspect the blended boundary. Review garment seams, texture, color, shape, hands and occlusion.
7. Measure cold load and warm runs separately. Record peak resources, failures and output acceptance criteria.
8. Update the results only with observed measurements. Keep a failure report if the run does not complete.

## Results template

Copy and complete this for a measured run; blank fields are not zero values.

```text
Test date:
Public workflow commit/hash:
OS / GPU / VRAM / system RAM:
Driver / Python / PyTorch:
ComfyUI commit / GGUF extension commit:
Model sources / revisions / SHA-256:
Asset provenance and permission:
Source / reference dimensions:
Working dimensions / mask method:
Seed / steps / CFG / sampler / scheduler / denoise:
Launch flags / offload behavior:
Cold load seconds:
Warm generation seconds (each run and median):
Peak VRAM / peak system RAM / measurement method:
Completed outputs / rejected outputs:
Garment fidelity and boundary findings:
Outside-mask comparison:
Errors or limitations:
Demo publication clearance:
```

A successful synthetic or simplified test establishes pipeline execution for those inputs. It does not by itself validate realistic garment transfer, broad compatibility or production readiness.
