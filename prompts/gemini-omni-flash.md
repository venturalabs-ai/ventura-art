# Gemini 3 Omni Flash — prompt de vídeo (AI Creative Studio / Google Labs)

Modelo multimodal nativo: texto + imagem + vídeo de referência → vídeo com
áudio sincronizado. **O áudio precisa ser escrito no prompt; sem áudio
descrito, o modelo inventa.**

## Parâmetros do modelo

- Duração nativa: **3–10s** (720p, 24 FPS) — nada além de 10s.
- Formato: **9:16 vertical** (declarar explicitamente) ou 16:9.
- Vídeo de referência: até **30s**.
- Timecode: `[0-3s]`, `[3-6s]`, `[6-10s]`.
- Idioma: prompts em inglês (suporte total).

## Anatomia (13 elementos)

1. Subject — quem/o quê, específico.
2. Action — o verbo.
3. Scene/context — onde/quando, atmosfera.
4. Camera angle — eye-level, low-angle, close-up, wide, POV...
5. Camera movement — static, pan, tilt, dolly, handheld...
6. Lens/optical — shallow DoF, rack focus, wide-angle, telephoto...
7. Lighting — receita de DP (Deakins, Lubezki, Doyle...).
8. Tone/mood — joyful, melancholic, suspenseful...
9. Artistic style — photorealistic, cinematic, art movement...
10. Ambiance — paleta, fog, heat haze, texturas.
11. Temporal — pacing, evolução sutil.
12. Audio — SFX, ambiência, diálogo.
13. Aspect + duration — "9:16 vertical, 10 seconds".

## Cena única (por padrão o modelo tenta vários cortes)

Escreva literalmente:

- `In a single unbroken scene`
- `In a single continuous shot`
- `No scene cuts`

## Timecode e timing

```
[0-3s] A person is walking
[3-6s] They stop and turn around
[6-10s] They start running
```

Ou linguagem natural: "After 3 seconds, a woman enters the scene".

## Meta prompting (passar verbatim)

- "Consider micro-detail, expression and timing to create a very rich,
  detailed but entirely natural scene."
- "Be extremely detailed in your descriptions of characters and environments.
  Apply costume design principles to characters. Be very specific about the
  people, items and objects in the scene."
- "Include plenty of appropriate detail in the background elements to make the
  scene feel realistic and natural."

## Referências

- `<FIRST_FRAME>` — imagem como frame inicial: "`<FIRST_FRAME>` a woman is walking".
- `<IMAGE_REF_N>` — imagem como referência de estilo/sujeito (índice a partir de 0).
- Vídeo de referência (≤30s): "Referring to the camera movement, perspective
  and motion in the reference video, <ação>".

## Vídeo mestre multi-cena

Cada cena é um prompt Gemini separado. Regras (ver `template-mestre.md`):

1. Cena N termina congelada; cena N+1 abre "continuing from where the previous
   scene ended".
2. Último frame da cena anterior como `<FIRST_FRAME>` da próxima.
3. Bloco do sujeito verbatim em todas as cenas.
4. "same lighting, same camera position, same audio bed".
5. Declare: "This is scene N of a master video. Continue seamlessly from the
   last frame of the previous scene."

## Exemplo pronto (DNA Gerde, 10s, 9:16)

```
In a single unbroken scene, 9:16 vertical, 10 seconds.

[0-3s] A woman in a flowing pearl-white silk dress stands on a dark rocky
shore at dusk, wet watercolor pigment bleeding from her fingertips into the
air. Waves crash behind her, spray catching the last light.

[3-6s] She raises her arms slowly, wrists turning inward, as if painting the
sky; pigment blooms into a teal and coral wave that arcs over the horizon.

[6-10s] The wave freezes mid-motion into layered torn paper collage, deckled
edges, and she lowers her hands, breath visible. The watercolor wave dissolves
into drifting neon cyan sparks.

Camera: static eye-level, 35mm, shallow depth of field, subject centered,
ocean filling the lower third.

Lighting: Lubezki — natural enveloping golden-hour rim light, backlight
through sea mist, soft haze, cool teal shadows with warm coral highlights.

Style: photorealistic painterly — painting in motion, layered paper texture,
wet watercolor wash, paper tooth visible, dramatic teal #0B2B3B and coral
#FF6B6B palette with cyan #00E5FF neon accents, fine film grain.

Audio: waves crashing on the shore, distant gulls, a low sea wind; the woman
breathes softly as pigment blooms.

The most important element is the physical texture of the watercolor pigment
blooming from her hands, with realistic fluid behavior.
```

## Negative (formato descritivo, sem "no/don't")

`plastic skin, waxy textures, distorted hands, extra fingers, warped
reflections, floating objects, physics-defying motion, uncanny valley,
oversaturated colors, jpeg artifacts, watermark`
