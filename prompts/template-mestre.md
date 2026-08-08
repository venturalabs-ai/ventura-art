# Template mestre — anatomia universal de prompt de vídeo

Válido para qualquer modelo (Gemini Omni Flash, Veo, Seedance, Kling, Sora,
LTX, ComfyUI). Preencha os campos com física concreta, nunca adjetivos vagos.

## Esqueleto (regra universal)

```
[SETTING] [SUBJECT] [ACTION] [DETAIL] [STYLE] [DURATION]
```

1. **Esqueleto** — setting + subject + action + detail + style + duration.
2. **Peso no início** — primeiros 30-40% dos tokens = sujeito, ação, ambiente.
3. **Show, don't tell** — comportamento físico concreto > adjetivo ("jaw
   clenched, brow furrowed" > "intense").
4. **Linguagem natural** > pilha de tags.
5. **Um movimento de câmera primário** por tomada (câmera parada + sujeito em
   movimento conta como um).
6. **Lente precisa** — 35mm, 85mm, anamorphic breathing, wide 16mm — nunca
   "cinematic" sozinho.
7. **Âncora de consistência** — descrição do personagem verbatim em todas as
   cenas/referências.
8. **Zero contradições** — photorealistic + anime style se anulam.
9. **Detalhe concreto > conceito abstrato**.
10. **Duração disciplinada** — a ação deve caber no tempo do clipe.
11. **Último frame forte** — a imagem final é o que o espectador guarda.
12. **Check dos 3 detalhes** — pressão do ambiente, micro-ação física, âncora
    sonora/motivo visual.
13. **Papel de referência nomeado** — `<FIRST_FRAME>`, `<IMAGE_REF_N>`, vídeo
    de referência — sem ambiguidade.
14. **Prioridade declarada** — "The most important element is ..." no início.

## Blocos (template 7 slots)

```
1. FRAMING/LENS/CAMERA   [framing] [lens] [camera movement] [height/angle]
2. SUBJECT               [quem/quê, específico, verbatim nas cenas]
3. ACTION                [o que faz, com timing/beats]
4. ENVIRONMENT           [onde, hora, clima, detalhes atmosféricos]
5. LIGHTING              [direção + qualidade; receita de DP]
6. AUDIO                 [diálogo: "..." | SFX: ... | ambiência: ...]
7. STYLE/PALETTE         [estilo artístico + cores + grão/filme]
```

## Receitas de luz (escolha UMA por cena)

- **Deakins** — single hard key, negative fill, atmospheric haze, motivated
  light, cool palette with warm practicals.
- **Lubezki** — natural enveloping light, golden hour rim, backlight through mist.
- **Doyle** — practical neon sources, saturated complementary colors (teal vs
  coral), color bleed on skin.
- **Khondji** — deep shadow pools, warm key with cold fill, low-key, heavy
  film grain.
- **van Hoytema** — dramatic contrast, hard directional sunlight, strong
  silhouettes, anamorphic flares.

## Anti-slop (8 camadas de realismo físico)

1. Pele: subsurface scattering, poros, vellus hair, tom irregular.
2. Líquidos: Fresnel, caustics, refração, tensão superficial.
3. Tecido: trama visível (warp/weft), brilho anisotrópico, micro-dobras.
4. Contato: sombra de contato, ambient occlusion, compressão sob peso, poeira
   perturbada.
5. Anatomia: peso, articulações naturais, contra-balanço da coluna, gravidade.
6. Micro-movimento: micro-expressões, saccades, respiração, dedos, cabelo/roupa.
7. Interação com luz: specular em pedra molhada, translucidez nas orelhas,
   bloom no neon.
8. Pós-imagem: grão de sensor, imperfeições de lente, vinheta, falloff natural.

## Áudio (sempre escrito)

- Diálogo: **verbo + aspas** — `She whispers, "come closer."`
- SFX rotulado: `SFX: a dog barks from off-screen left`
- Ambiência rotulada: `Audio: waves crashing, then a distant thunderclap`
- Máximo ~8s de fala contínua por personagem por clipe.
- Sons específicos > genéricos: "distant waves and gulls" > "ocean".

## Negative prompt (modelos que aceitam)

`plastic skin, waxy textures, distorted hands, extra fingers, warped
reflections, floating objects, physics-defying motion, uncanny valley,
oversaturated colors, jpeg artifacts, watermark`

## Vídeo mestre multi-cena (continuidade obrigatória)

1. Termine a cena N com um estado congelado claro e abra a N+1 retomando-o:
   "continuing from where the previous scene ended".
2. Use o último frame da cena anterior como `<FIRST_FRAME>` da próxima.
3. Bloco de descrição do sujeito **verbatim** em todas as cenas.
4. Mesma câmera, iluminação, hora do dia e áudio entre cenas
   ("same lighting, same camera position, same audio bed").
5. `No scene cuts` apenas em take único real.
6. Declare a intenção: "This is scene N of a master video. Continue seamlessly
   from the last frame of the previous scene."
