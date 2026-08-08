# Kling 3.0 — prompt de vídeo (Kuaishou)

Modelo de 2026 com compreensão de chinês mais forte do mercado, vídeo nativo
com áudio sincronizado (incluindo sync labial por personagem), até 2 minutos,
Motion Brush e image-to-video. Pode ser escrito em português, chinês ou
inglês (melhor resultado em chinês).

## Fórmula básica — 4 partes (vídeos curtos)

```
[1. Sujeito] + [2. Ação] + [3. Ambiente] + [4. Estilo/câmera]
```

## Fórmula avançada — 5 camadas (narrativa + áudio)

```
[1. Sujeito e identidade]  — quem, aparência, roupa, traços fixos
[2. Ação + micro-detalhes] — o que faz, com beats e expressões
[3. Ambiente e contexto]   — onde, hora, clima, atmosfera
[4. Câmera e linguagem]    — ângulo, movimento, lente
[5. Áudio]                 — diálogo com sync labial, SFX, ambiência
```

## Direcionamento de voz por personagem

Em cenas com fala, aponte quem fala:

```
O homem diz: "O mar nunca devolve o que leva."
A mulher responde, em voz baixa: "Então a gente aprende a mergulhar."
```

## Image-to-video (figura)

Descreva apenas o movimento a partir da imagem de referência:
`sujeito + ação + câmera + duração` — sem re-descrever aparência (a imagem já
trava a identidade).

## Motion Brush

Use para ativar movimento em regiões específicas do frame (ex.: pintar a onda
para animar só a água sobre papel parado).

## Exemplo (DNA Gerde, 10s)

```
Uma dançarina em vestido de seda teal profundo, descalça, numa plataforma de
madeira sobre o mar, ao entardecer. Ela gira em câmera lenta; o tecido segue
com física de micro-dobras, tinta aquarela coral escorre das mangas e pinga
no chão com tensão superficial. Ao fundo, a onda quebra em spray fino que
fica suspenso na luz dourada. Câmera: steadicam em arco lento ao redor dela,
35mm, profundidade rasa. Luz Lubezki: golden hour rim através da névoa,
sombras teal, destaques coral. Áudio: ondas quebrando, tecido sussurrando, um
gull distante; a dançarina ri baixo, "Ainda não sei onde a onda termina."
Estilo fotorrealista pictórico, pintura em movimento, grão fino.
```

## Kling 3.0 — dicas

- Pode gerar clipes longos (até 2 min) mantendo consistência.
- Sync labial nativo: escreva o diálogo entre aspas com o nome do personagem.
- Chinês > português > inglês em fidelidade de instrução.
- Use Motion Brush para movimentos seletivos em image-to-video.
