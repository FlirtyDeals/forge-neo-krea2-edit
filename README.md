# Krea 2 Identity Edit for Forge Neo

Forge Neo extension that lets the Krea 2 Identity Edit LoRA edit an existing photo (for example, change the clothes) while keeping the person's face.

This is a fork of [opparco/sd-forge-krea2-edit](https://github.com/opparco/sd-forge-krea2-edit). It includes the compatibility fixes from [pull request #5](https://github.com/opparco/sd-forge-krea2-edit/pull/5) by trcwebdesign for newer Forge Neo versions, plus one extra fix: the Qwen tap layers are passed to Forge as a list instead of a tuple.

## Requirements

- Forge Neo
- Krea 2 Raw or Turbo, with its Qwen3-VL text encoder and VAE
- The Identity Edit LoRA (not included, see below)

## Install

1. In Forge, open Extensions, then Install from URL, paste this repository's URL and install.
2. Restart Forge completely.

## Get the LoRA

Download [krea2_identity_edit_v1_2.safetensors](https://huggingface.co/conradlocke/krea2-identity-edit/resolve/main/krea2_identity_edit_v1_2.safetensors) (1.83 GB) and put it in `models/Lora`.

Model page: https://huggingface.co/conradlocke/krea2-identity-edit

The LoRA has its own license. Read it on the model page. It is not bundled in this repository.

## Use

1. Select Krea 2 Turbo (or Raw).
2. Go to the **txt2img** tab (not img2img).
3. Open the **Krea 2 Identity Edit** accordion and tick its checkbox.
4. Upload your photo into **Subject reference (required)**.
5. Write the edit as an instruction and add the LoRA tag:

```
Make both people wear white NASA-style spacesuits with helmets. Keep the person's identity and facial features. <lora:krea2_identity_edit_v1_2:1>
```

6. Generate.

## Recommended settings

| Setting | Value |
|---|---|
| Model | Krea 2 Turbo |
| Steps | 8 |
| CFG | 1 |
| Batch size | 1 |
| Size | same aspect ratio as the photo, 2 megapixels or less |
| Hires. fix | Off |
| Grounding resolution | 768 (lower follows the edit more, higher keeps the face more) |
| Reference boosts | 1 (off) |

For removals and other strong edits, use Krea 2 Raw with about 20 steps and CFG 3.

## Credits and license

- Original extension by [opparco](https://github.com/opparco/sd-forge-krea2-edit)
- Compatibility fixes from pull request #5 by trcwebdesign
- Adapted from [lbouaraba/comfyui-krea2edit](https://github.com/lbouaraba/comfyui-krea2edit)

Licensed under Apache-2.0, see `LICENSE` and `NOTICE`.
