# Seedance 2.0 — prompt de vídeo (Doubao / ByteDance)

## Fórmula avançada — 8 elementos

```
[1. Sujeito preciso] + [2. Detalhe de ação] + [3. Ambiente/cena] +
[4. Luz e tom] + [5. Câmera/movimento] + [6. Estilo visual] +
[7. Qualidade] + [8. Restrições]
```

1. **Sujeito preciso** — quem/o quê com especificidade (profissão, material,
   aparência).
2. **Ação detalhada** — movimentos, interações, expressões, transformações,
   com beats.
3. **Ambiente/cena** — local, hora, clima, atmosfera.
4. **Luz e tom** — direção + qualidade (receita de DP).
5. **Câmera/movimento** — ângulo + movimento + lente.
6. **Estilo visual** — photorealistic, painterly, arte, paleta.
7. **Qualidade** — high detail, micro-detail, natural.
8. **Restrições** — o que manter consistente (personagem verbatim, paleta,
   sem cortes).

## Duração

5 / 10 / 15 segundos. A ação deve caber no tempo.

## Storyboard multi-cena (seedance-storyboard)

Cada cena organizada em 4 dimensões:

```
[# Cena N]
- Câmera: ângulo + movimento + lente
- Sujeito e ação: quem + o que faz + expressão
- Posição/espaço: onde está no frame, mudanças de espaço
- Áudio: diálogo + SFX + ambiência
```

## Exemplo (DNA Gerde, 10s)

```
Uma mulher em vestido de seda perolado fica em uma costa rochosa escura ao
entardecer, cabelo molhado, descalça, respiração visível. Ela ergue o braço
direito devagar, como se pintasse o céu; tinta aquarela molhada brota das
pontas dos dedos em teal profundo e coral, com tensão superficial realista e
gota a gota. A tinta forma uma onda que congela em papel em camadas com
bordas desfiadas e se dissolve em faíscas de ciano neon. Câmera estática em
nível dos olhos, 35mm, profundidade rasa, a mulher centralizada, o oceano no
terço inferior. Luz natural dourada de trás através da névoa, sombras teal
frias, destaques coral quentes, grão de filme fino. Estilo fotorrealista
pictórico: pintura em movimento, textura de papel, aquarela com tooth visível,
paleta dramática teal #0B2B3B + coral #FF6B6B + neon ciano #00E5FF. Áudio:
ondas quebrando, vento, gulls distantes. Manter a mulher e a paleta idênticas
ao longo do clipe; sem cortes.
```

## Problemas comuns e correção (seedance-debugger)

| Sintoma | Causa provável | Correção |
|---|---|---|
| Rosto muda / gêmeos | ID não ancorado | Referência de imagem + bloco do sujeito verbatim |
| Estilo muda no meio | Estilo fraca | Paleta hex + textura assinatura repetida |
| Legenda/logo estranha | Prompt pediu texto | Restrição explícita: no text, no watermark |
| Salto no final da extensão | Final não congelado | Terminar cena em estado estável |
| Cores lavadas | Pouco contraste | Regra 2 dominantes + 1 neon + neutros |
