# Public visual assets

## Actual Qwen result

`examples/result.png` is the unretouched saved output of the local Qwen test on 2026-09-26, using only the synthetic inputs described below. It is not a separately generated concept image. ComfyUI workflow metadata embedding was disabled for the run. See [test instruction](examples/README.md) and [measured report](docs/validation.md).

## Synthetic validation inputs

The built-in OpenAI image-generation tool created two original images on 2026-09-26, without reference images, for the owner's requested local Qwen test. The test uses a headless mannequin and standalone garment, not a person or any private client asset. Copies were resized to 768 × 768 for the test. A deterministic polygon mask and alpha-bearing source were prepared locally; these are test data, not generated Qwen results.

Source generation prompt: Create a single photorealistic fashion studio test input, portrait 1024x1024. A headless neutral ivory dressmaker mannequin on a slim metal stand, wearing a plain beige knee-length short-sleeved dress, front view, centered, entire dress visible with generous background margin. The mannequin has no arms or legs, only torso and short neck. Warm light gray seamless studio background, even soft lighting. No person, no text, no logos, no collage. Original synthetic asset intended as input for a real local garment-edit workflow test. Dress silhouette simple, fabric smooth, no accessories.

Reference generation prompt: Generate one original synthetic product photograph for a garment reference in an AI editing test. Single plain forest-green short-sleeved knee-length A-line dress with round neckline, subtle fitted waist seam, smooth cotton fabric, no belt, no pockets, no patterns, no logos. Front view, flat lay neatly arranged symmetrically on a light ivory background, entire garment visible, centered with generous margins. Square composition, soft even studio lighting. No person, mannequin, hanger, text, collage or before-after comparison. One image only.

## fashion-tech-banner.png

Original technology-themed banner generated on 2026-09-26 using the built-in OpenAI image-generation tool, at the repository owner's request for a colorful premium front-page design. No input images or client assets were supplied. Generic image, mask, connected-shirt and garment icons illustrate the process; these are not official Qwen or ComfyUI logos and do not depict measured output.

Generation prompt: Create a premium wide technology banner for QWEN FASHION EDIT, midnight navy background, cyan/violet gradients and gold accents; large bespoke 3D shirt with workflow nodes plus source-image, paintbrush-mask and edited-garment icons. Title QWEN FASHION EDIT; subtitle LOCAL AI • COMFYUI • GARMENT EDITING; label EXPERIMENTAL WORKFLOW. No people, client photos, company logos, benchmark numbers or certification claims.

## fashion-edit-concept.png

- Created on 2026-09-26 using the built-in OpenAI image-generation tool at the repository owner's request for publication here.
- Original synthetic illustration: a fictional adult in a beige everyday dress and a forest-green dress, shown as a before/after concept.
- No reference photographs, client images, private model photographs or existing workflow outputs were supplied to the generator.
- Purpose: explain the intended garment transition on the README. It is not an output of the published Qwen graph, a measured demonstration or a product-fidelity claim.
- The image visibly says **AFTER CONCEPT** and **AI-generated illustration • Not a tested Qwen workflow output**. Retain that distinction when describing or reusing it.
- Source: generated specifically for this repository, with no third-party stock-photo source. The owner's requested publication is recorded here; no exclusivity or universal copyright eligibility is asserted for generated content.
- The image may retain generator provenance metadata. It contains no intentionally embedded ComfyUI workflow or client-image reference.

## Generation prompt

Use case: ads-marketing.
Asset type: premium wide GitHub README fashion workflow concept illustration.
Create one original polished photorealistic before-and-after diptych, landscape 1536x1024 or similar. No input reference images. Entirely fictional adult female fashion model, about 30, shown full length twice in exactly the same relaxed standing pose, hairstyle, face, proportions, shoes and neutral warm ivory studio background. Left panel wears a modest plain beige short-sleeved knee-length everyday dress. Right panel wears an elegant forest-green long-sleeved midi dress with subtle belt, realistic fabric, suitable for an everyday fashion catalogue. Fully clothed, professional neutral expression, no suggestive poses. Clear visible garment transformation, both panels equal size with generous margins. Refined editorial design: deep charcoal title band, muted gold accents, thin dividing rule, a tasteful small right arrow between the panels.
Exact heading: "QWEN FASHION EDIT".
Exact subtitle: "A visual guide to reference-led clothing edits".
Above left image: "BEFORE". Above right image: "AFTER CONCEPT".
Legible footer: "AI-generated illustration • Not a tested Qwen workflow output".
Critical: depict a fictional person created from scratch, no real person likeness, no client images, no logos or invented metrics. This is a conceptual illustration, not performance evidence. Make typography elegant, clear and accurately spelled.
