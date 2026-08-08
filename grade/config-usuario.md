# Configuração do usuário — formulário de produção de vídeo

Preencha este formulário para cada vídeo. Ele define a **grade** (multi-cena ou
cena única), o **sistema** (modelo), o **tempo** (duração e ritmo), o
**formato** (proporção) e a **conformidade** (disclosure de IA). Depois de
preencher, use o template do sistema escolhido em `../prompts/`.

---

## 1. Plataforma de destino (uma ou mais)

- [ ] YouTube Shorts
- [ ] YouTube long-form
- [ ] TikTok
- [ ] Instagram Reels
- [ ] Facebook / Threads
- [ ] X (Twitter)
- [ ] LinkedIn
- [ ] WhatsApp Status

> Formato e duração máximos automáticos: veja `../config/plataformas.json`.

## 2. Formato (proporção)

- [ ] 9:16 vertical (1080x1920)
- [ ] 16:9 horizontal (1920x1080)
- [ ] 1:1 quadrado (1080x1080)
- [ ] 4:5 retrato (1080x1350)

## 3. Sistema (modelo de geração)

- [ ] Gemini 3 Omni Flash — 3-10s, áudio nativo, ref de vídeo ≤30s
- [ ] Veo 3.1 — 8s, 1080p, fórmula oficial Google
- [ ] Seedance 2.0 — 5/10/15s, 8 elementos, storyboard multi-cena
- [ ] Kling 3.0 — até 2 min, sync labial, chinês forte
- [ ] Sora 2 — 4-20s (API: 4/8/12/16/20), 720p/1080p
- [ ] LTX 2.3 — clipes 2-10s, open source
- [ ] ComfyUI + AnimateDiff — 16 frames @8fps, pipeline local Gerde

## 4. Tempo (duração e ritmo)

- [ ] Clipe único curto (3-10s)
- [ ] Clipe único médio (10-30s)
- [ ] Clipe único longo (30s+)
- [ ] **Vídeo mestre multi-cena** (2+ cenas de 10s com continuidade)

Ritmo:
- [ ] Lento e contemplativo (câmera parada, movimentos sutis)
- [ ] Médio (movimento constante, cortes suaves)
- [ ] Rápido (whip pan, cortes ritmados, hype)

## 5. Grade (estrutura do vídeo)

- [ ] **Cena única** — um take contínuo (`In a single unbroken scene`)
- [ ] **Vídeo mestre multi-cena** — cada cena é um prompt separado que continua
      do último frame da anterior (`<FIRST_FRAME>`), personagem verbatim,
      mesma luz/câmera/áudio entre cenas
- [ ] **Grid de formatos** — mesma cena renderizada em múltiplos formatos
      (9:16 para Shorts/TikTok + 16:9 para YouTube) para reutilização cross-platform

Se multi-cena, liste as cenas:

| # | Cena | Duração | Estado final (congelado) | Primeira ação da próxima |
|---|---|---|---|---|
| 1 | | 10s | | |
| 2 | | 10s | | |

## 6. Áudio

- [ ] Nativo do modelo (escrever no prompt: diálogo + SFX + ambiência)
- [ ] TTS / voz (ElevenLabs, Gemini TTS)
- [ ] Música (Lyria, biblioteca)
- [ ] Silêncio ambiente (room tone)

Diálogo (verbo + frase entre aspas): `She whispers, "..."`

## 7. Estilo (DNA Gerde)

- Textura assinatura: papel em camadas / tecido / aquarela / neon
- Paleta: 2 dominantes + 1 neon + neutros
  - Teal `#0B2B3B` | Azul-onda `#2E6E8E` | Ciano `#00E5FF` | Coral `#FF6B6B`
  - Carmim `#7A1F3D` | Perolado `#F4F1EA` | Meia-noite `#10162E` | Ouro `#C9A227`
- Diretor de fotografia: Deakins / Lubezki / Doyle / Khondji / van Hoytema
- Tema: água/onda/costa | dança | espiritualidade

## 8. Conformidade (obrigatório)

- [ ] Conteúdo dentro das políticas do Google (sem conteúdo proibido)
- [ ] Sem dados pessoais/biometria de terceiros
- [ ] Sem pessoas reais sem consentimento / figuras públicas sem disclaimer
- [ ] Disclosure de IA explícita para a plataforma escolhida (rótulo não removido)
- [ ] SynthID / C2PA preservados

---

## Saída (preenchido)

```
PLATAFORMA:   [TikTok + Instagram Reels]
FORMATO:      9:16 (1080x1920)
SISTEMA:      Gemini 3 Omni Flash
DURACAO:      10s, cena única
RITMO:        médio
GRADE:        cena única, um take
AUDIO:        nativo — ondas + gulls; voz: "..." 
ESTILO:       aquarela sobre teal profundo, luz Lubezki, tema costa
DISCLOSURE:   label IA (auto-label TikTok, AI info Meta)
```

Com esse bloco preenchido, vá ao template do sistema e gere o prompt final.
