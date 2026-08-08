# ComfyUI + AnimateDiff — workflow API (pipeline local Gerde)

Pipeline oficial do estúdio Gerde, 5 estágios:
**ComfyUI** (geração) → **revisão de frames/seed** → **Topaz Video AI**
(upscale) → **After Effects** (texturas) → **export final**.

## Config padrão de animação

| Parâmetro | Valor |
|---|---|
| Resolução | 512×768 (9:16) ou 768×512 (16:9) |
| Frames | 16 @ 8fps (≈2s por batch) |
| Motion model | `mm_sd_v15_v2.ckpt` (motion_scale 1.0) |
| Context | length 16, stride 16, overlap 0 |
| KSampler | steps 20–30, cfg 6–7, euler/normal, denoise 1.0 |
| ControlNet OpenPose | strength 0.85 |
| ControlNet Depth | strength 0.7 |
| Save | mp4, yuv420p, fps 8 |

## Regras críticas do formato API

1. **Um link sempre resolve para a 1ª saída do nó produtor.**
2. `CheckpointLoaderSimple` expõe apenas MODEL como 1ª saída → CLIP e VAE
   vêm de loaders dedicados (`CLIPLoader` type `stable_diffusion`,
   `VAELoader`).
3. `LoadImage` expõe IMAGE como 1ª saída (MASK é 2ª) → máscaras exigem
   `LoadImageMask`.
4. Prefira `ControlNetApply` (positive, negative, control_net, image,
   strength).
5. Valores de strings são literais (prompts, `"euler"`, `"mp4"`), não links.

## Nós verificados (AnimateDiff)

- `ADE_AnimateDiffLoaderWithContext` — model, model_name
  (`mm_sd_v15_v2.ckpt`), beta_schedule (`sqrt`), fps, motion_scale,
  context_length, context_stride, context_overlap
- `LoadImagesFromDir` (WAS) — directory, image_load_cap, start_index
  (frames de pose de entrada)
- `ControlNetLoader` — `control_v11p_sd15_openpose.pth`,
  `control_v11f1p_sd15_depth.pth`
- `EmptyLatentImage` — width, height, batch_size (= nº de frames)
- `KSampler` — seed, steps, cfg, sampler_name, scheduler, denoise, model,
  positive, negative, latent_image
- `CLIPTextEncode` — clip, text
- `VAEDecode` — samples, vae
- `SaveVideo` — images, filename_prefix, fps, format (`mp4`), pix_fmt
  (`yuv420p`)

## Estrutura do JSON (formato API)

```json
{
  "1": { "class_type": "CheckpointLoaderSimple", "inputs": { "ckpt_name": "*.safetensors" } },
  "2": { "class_type": "CLIPLoader", "inputs": { "clip_name": "*.safetensors", "type": "stable_diffusion" } },
  "3": { "class_type": "VAELoader", "inputs": { "vae_name": "*.safetensors" } },
  "4": { "class_type": "CLIPTextEncode", "inputs": { "clip": ["2", 0], "text": "PROMPT" } },
  "5": { "class_type": "CLIPTextEncode", "inputs": { "clip": ["2", 0], "text": "NEGATIVE" } },
  "6": { "class_type": "EmptyLatentImage", "inputs": { "width": 512, "height": 768, "batch_size": 16 } },
  "7": { "class_type": "ADE_AnimateDiffLoaderWithContext", "inputs": { "model": ["1", 0], "model_name": "mm_sd_v15_v2.ckpt", "beta_schedule": "sqrt", "fps": 8, "motion_scale": 1.0, "context_length": 16, "context_stride": 16, "context_overlap": 0 } },
  "8": { "class_type": "ControlNetLoader", "inputs": { "control_net_name": "control_v11p_sd15_openpose.pth" } },
  "9": { "class_type": "LoadImagesFromDir", "inputs": { "directory": "pose_frames", "image_load_cap": 16, "start_index": 0 } },
  "10": { "class_type": "ControlNetApply", "inputs": { "positive": ["4", 0], "negative": ["5", 0], "control_net": ["8", 0], "image": ["9", 0], "strength": 0.85 } },
  "11": { "class_type": "KSampler", "inputs": { "seed": 12345, "steps": 24, "cfg": 6.5, "sampler_name": "euler", "scheduler": "normal", "denoise": 1.0, "model": ["7", 0], "positive": ["10", 0], "negative": ["10", 1], "latent_image": ["6", 0] } },
  "12": { "class_type": "VAEDecode", "inputs": { "samples": ["11", 0], "vae": ["3", 0] } },
  "13": { "class_type": "SaveVideo", "inputs": { "images": ["12", 0], "filename_prefix": "gerde_onda", "fps": 8, "format": "mp4", "pix_fmt": "yuv420p" } }
}
```

> Arquivos de referência validados: biblioteca `gerde-workflows` (16 JSONs)
> e o gerador `generate-workflows.js`.

## Prompt de geração (EN)

```
A dancer in a deep teal silk dress on a dark rocky shore at dusk, wet
watercolor pigment blooming from her fingertips, layered torn paper collage
texture, deckled edges, painting in motion, wet watercolor wash, paper tooth
visible, dramatic teal and coral palette with cyan neon accents, volumetric
golden light through mist, waves crashing, cinematic, film grain
```

Negative padrão: `blurry, low quality, distorted, deformed, watermark, text,
extra limbs, oversaturated, flat lighting, jpeg artifacts`

## Pós (Topaz + After Effects)

1. Topaz Video AI — Proteus 2x/4x (geral); Iris (textura papel/tecido);
   motion deblur ativo em dança; tiling off; preserve original colors;
   export ProRes 422.
2. After Effects — texturas com Multiply/Overlay 15–30%; glow neon (Saber)
   em ciano/coral; máscara com leve posterize; split tone
   (teal/sombra + coral/luz); vinheta meia-noite; grain fino.
3. Export final — paleta e texturas unificadas.
