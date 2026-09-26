# Synthetic garment test assets

These assets were created specifically for the public workflow test. They are not client photographs or private model images.

| File | Purpose |
| --- | --- |
| `source.png` | Synthetic beige dress on a headless dressmaker mannequin, resized to 768 × 768 |
| `reference.png` | Synthetic forest-green garment reference, resized to 768 × 768 |
| `mask.png` | Binary clothing-area mask: white means edit, black means preserve |
| `source-masked.png` | Same source RGB with an alpha channel encoding the mask for ComfyUI LoadImage |
| `result.png` | Unretouched actual output from the documented local Qwen run |
| `test-api.json` | Submitted API-format graph, with test input names and mannequin-specific instruction |

The standalone `mask.png` is a visual aid. The public UI graph reads its mask from the source LoadImage node; use `source-masked.png` in that node, or load `source.png` and paint an equivalent mask in MaskEditor. ComfyUI's alpha convention means transparent pixels become the editable mask. The RGB pixels remain present underneath the alpha channel.

`test-api.json` is the server API representation, not the drag-and-drop UI workflow. For the visual editor, load [the public workflow](../workflows/low-budget/Qwen_Fashion_Edit_3060.json), supply these inputs, and use the test instruction below. The graph connections, model choices and sampler defaults are retained. Only input filenames, the instruction and output prefix differ.

## Test instruction

> Replace only the masked beige dress on the mannequin in picture 1 with the forest-green everyday dress in picture 2. Match the garment color, smooth cotton fabric, short sleeves, round neckline and waist seam. Preserve the mannequin, stand, lighting and background. Realistic fashion product photograph.

The mask was drawn as a polygon for this reproducible test. It is not automatic segmentation. This simplified mannequin case does not test face identity, hands, complex poses or realistic garment fit on a person.

See [validation](../docs/validation.md) for measured results and limitations, and [asset provenance](../ASSET-MANIFEST.md) for how the inputs were created.
