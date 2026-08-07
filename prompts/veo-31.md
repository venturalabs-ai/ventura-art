# Veo 3.1 — prompt de vídeo (fórmula oficial Google)

## Fórmula 5 partes (mínimo obrigatório)

```
[Cinematography] + [Subject] + [Action] + [Context] + [Style & Ambiance]
```

## Fórmula 7 slots (versão campeã)

```
[Framing + Lens + Camera Movement]
[Subject detalhado — consistência verbatim]
[Action com timing/beats]
[Environment + Time + Weather]
[Lighting direction + quality]
[Audio: dialogue + SFX + ambient]
[Style + Color Palette + Film Stock]
```

## Regras de ouro

1. Diálogo **sem aspas**: `A woman says: We have to leave now.`
2. SFX rotulado: `SFX: thunder cracks`
3. Um único momento por prompt curto.
4. Negative prompts descritivos (substantivos, sem "no/don't").
5. Consistência de personagem via Reference Images + Character Sheets
   (Nano Banana → Character Sheet → Reference Images).

## Consistência de personagem (pipeline oficial)

1. Gere a Character Sheet no Nano Banana (mesmo personagem, múltiplas poses/
   expressões/ângulos).
2. Use as Reference Images nas cenas.
3. Descreva o personagem com as mesmas palavras em todos os prompts.

## Exemplo (DNA Gerde, 8s)

```
Close-up on a woman's hands, 35mm lens, slow push-in, eye-level, shallow
depth of field.

A woman in a pearl-white silk dress, wet black hair, barefoot — her hands
move as if painting the air.

She traces a slow arc with her right hand; wet watercolor pigment blooms from
her fingertips in teal and coral, following the motion, dripping with surface
tension before dispersing into neon cyan sparks.

Night on a dark rocky shore, light sea mist, cool blue hour, waves breaking
behind her.

Natural golden-hour rim light from behind, soft haze, warm coral highlights
against cool teal shadows.

Audio: waves crashing, wind through sea grass; she breathes softly.

Style: photorealistic painterly, painting in motion, layered paper texture,
wet watercolor wash, dramatic teal and coral palette, fine film grain,
anamorphic flare on the horizon.
```

## Extras

- Consistência de estilo: "in the style of `<IMAGE_REF_0>`".
- Extensões: iterar com uma mudança por vez ("same shot, switch to 85mm").
- Enriquecer briefs crus com Gemini antes de gerar.
