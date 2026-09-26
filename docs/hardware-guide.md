# Hardware and operating costs

## Understand the setup paths

The table describes options to evaluate, not measured performance or purchasing recommendations. Only the experimental budget JSON is supplied. One cold synthetic mannequin run on RTX 3060 12 GB is documented in [validation](validation.md); a separate [fictional-adult party-dress run](human-validation.md) is also documented. No repeated or comparative benchmark is available.

| Path | What it means here | Why evaluate it | Main tradeoff | Evidence today |
| --- | --- | --- | --- | --- |
| RTX 3060 12 GB, local | Q4_K_M GGUF model, historical 0.5 MP working image, one image and low-VRAM launch | Experiment on an existing desktop | Limited VRAM; offloading can consume system RAM and time | One synthetic run completed in about 11m 40s including loading; visible edge limitations |
| RTX A6000 / A40 48 GB | Test the same inputs on a machine with more VRAM | Investigate capacity limits or different precision/resolution | Purchase or rental cost; complete graph still needs memory measurement | No comparison benchmark |
| Larger-memory / heavier-model configuration | Separately select compatible model, precision and runtime | Investigate a specific unmet quality or capacity need | More resource use and setup complexity | Research only; no additional graph supplied |

VRAM is GPU memory; system RAM is separate. A GPU model name alone does not establish compatibility: the RTX 3060 has different memory variants. Check your actual card. Hardware references: [RTX 3060 specifications](https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3060-3060ti/), [RTX A6000](https://www.nvidia.com/en-gb/products/workstations/quadro/rtx-a6000/), [NVIDIA A40 reference](https://docs.nvidia.com/vgpu/sizing/virtual-workstation/latest/gpus-vws.html).

The measured local setup used 32 GB system RAM; sampled whole-system use reached 30.75 GiB with other applications open. That is context, not a validated minimum. Offloading, image dimensions, other applications and model loading affect RAM usage. Check model download sizes and reserve space for all components, temporary downloads and outputs. There is no measured disk-space requirement for a complete clean installation yet.

## Why use quantization?

The supplied graph uses `qwen-image-edit-2511-Q4_K_M.gguf` with `UnetLoaderGGUF`. Quantization reduces weight precision. It can reduce storage and model memory requirements, but quality and speed must be measured with the complete workflow. Encoder, VAE, activations and images also consume resources; model file size is not the same as peak VRAM.

The upstream BF16 model uses a different loader path and is not a drop-in filename change. Do not mix model families or add an acceleration LoRA without using its matching settings. The public graph currently uses 40 steps and no LoRA.

## Local versus cloud

| Question | Your local machine | Rented GPU machine |
| --- | --- | --- |
| Where are images processed? | On your machine with the supplied local graph | On the remote rented machine |
| What do you pay for? | Hardware ownership, electricity and storage | Billed GPU time plus any storage, transfer and other charges |
| Initial setup | Install and download once, then maintain | May require repeated setup unless storage persists |
| Main constraint | Your installed GPU/RAM and available time | Provider availability, billing rules and remote data handling |

A cloud GPU is optional. Do not rent one just because the table lists it. First define the problem: insufficient memory, unacceptable measured time, or a clearly specified experiment.

## Cost arithmetic, not price promises

No live GPU purchase prices or rental quotes are asserted here. Obtain a current provider quote and check minimum billing, storage while stopped, taxes and transfer costs.

- Local incremental electricity = wall power in kilowatts × run hours × electricity price per kWh.
- Cloud session = hourly rate × billed hours + storage + transfer + taxes.
- Cost per accepted image = total relevant session cost ÷ number of outputs passing review.

For illustration only, a machine averaging 0.30 kW for two hours at an assumed 8 currency units/kWh uses 4.8 currency units of electricity. This excludes hardware ownership and editing labor. At a hypothetical rental rate of USD 1/hour, 30 billed minutes costs USD 0.50 before extras. Neither example is a measured runtime, a local tariff, or a provider quote.

Include failed attempts and rejected images when evaluating practical cost. A low cost per generated image may still mean a high cost per usable result. Downloads and setup can consume billed rental time.

## How to compare fairly

Use the same cleared source image, reference image, mask, prompt, model, working dimensions, seed and sampler settings. If changing model precision, report that as a different configuration rather than attributing every difference to the GPU.

Measure cold model loading separately from warm generation. Record several runs, the median, peak VRAM and system RAM, failures and accepted output count. More VRAM alone establishes neither better image fidelity nor a specific speedup. Use the [validation template](validation.md) before publishing comparison claims.

The current main download uses 1 MP / 40 steps and a detail reference, so the historical 20-step timing above is not its runtime estimate. See the [quality experiment](quality-validation.md) for a measured, more demanding crop test.
