# Hardware guide
These are planning paths, not tested minimum requirements or purchasing recommendations.

| Setup | VRAM | Use to evaluate | Constraints |
| --- | --- | --- | --- |
| RTX 3060 12 GB | 12 GB | Low-budget local edits | Quantization/offloading may be needed; CPU RAM and transfer time matter |
| RTX A6000 | 48 GB | Larger working sets on a workstation or rental | Full graph memory still needs measurement |
| NVIDIA A40 | 48 GB | Hosted/server GPU experiments | Server cooling and deployment differ from a desktop card |
| Higher-memory GPU | Model-dependent | Heavier precision or larger workloads after benchmarking | Higher cost does not guarantee better edits |

The RTX 3060 also has an 8 GB variant; confirm the actual card. Memory specifications: [NVIDIA RTX 3060](https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3060-3060ti/), [RTX A6000](https://www.nvidia.com/en-gb/products/workstations/quadro/rtx-a6000/), and [NVIDIA A40 reference](https://docs.nvidia.com/vgpu/sizing/virtual-workstation/latest/gpus-vws.html).

For initial planning, allow 32 GB system RAM on a budget workstation and consider 64 GB for substantial offloading. These are untested planning allowances, not guarantees. Check actual download sizes and reserve SSD space for all model components, temporary downloads, and outputs; 100 GB free is a starting allowance, not a measured requirement.

## Cost
No current hardware purchase prices or cloud rental quotes are asserted here. Compare an existing local machine before buying hardware. For rentals, obtain a live quote including storage, stopped-instance charges, taxes, and data transfer.

- Local incremental cost = wall power in kW × hours × electricity price per kWh.
- Cloud session cost = hourly GPU rate × billed hours + storage + transfer + taxes.
- Cost per accepted image = total session cost / number of outputs that pass review.

Illustrative arithmetic only: at an assumed USD 1/hour, a 30-minute billed session costs USD 0.50 before extras. This is not a provider quote. Downloads and setup may consume billed time.

## Speed and quality
There are no seconds-per-image claims yet. Measure cold loading separately from warm generation. Run the same input, graph, model, dimensions, batch, and settings on each setup; report several runs and the median. Record peak VRAM and system RAM, failures, and accepted output count.

Evaluate stitching, texture, shape, identity, logos, background edges, and product color. Do not label a setup "production ready" until it meets your own quality and cost criteria.
