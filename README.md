# Ventura Art

![MIT](https://img.shields.io/github/license/chamseddinehiddoud/ventura-art)
![stars](https://img.shields.io/github/stars/chamseddinehiddoud/ventura-art)
![forks](https://img.shields.io/github/forks/chamseddinehiddoud/ventura-art)

Agente de criação de arte e animação generativa do estúdio Gerde. Produz
vídeos para **todas as principais plataformas** (YouTube, TikTok, Instagram,
Facebook, X, LinkedIn, WhatsApp) usando os principais sistemas de geração
(Gemini 3 Omni Flash, Veo 3.1, Seedance 2.0, Kling 3.0, Sora 2, LTX 2.3,
ComfyUI + AnimateDiff), com o **usuário no controle total da configuração**:
grade, sistema, tempo, formato e conformidade de IA.

## O usuário escolhe

| Escolha | Opções | Onde vive |
|---|---|---|
| **Plataforma** | YouTube Shorts, YouTube long-form, TikTok, Instagram Reels, Facebook, X, LinkedIn, WhatsApp | `config/plataformas.json` |
| **Sistema** | Gemini 3 Omni Flash, Veo 3.1, Seedance 2.0, Kling 3.0, Sora 2, LTX 2.3, ComfyUI + AnimateDiff | `config/sistemas.json` |
| **Tempo** | 3–10s (Omni), 5/10/15s (Seedance), 4/8/12/16/20s (Sora), até 2 min (Kling), 16 frames @ 8fps (ComfyUI) | `config/sistemas.json` |
| **Formato** | 9:16 vertical, 16:9 horizontal, 1:1 quadrado, 4:5 retrato | `config/plataformas.json` |
| **Grade** | Cena única, vídeo mestre multi-cena com continuidade (last frame → `<FIRST_FRAME>`), grid de cenas | `grade/config-usuario.md` |
| **Áudio** | Nativo do modelo, TTS, música, silent | prompts de cada sistema |
| **Conformidade** | Disclosure de IA obrigatório por plataforma | `conformidade/divulgacao-ia.md` |

Fluxo: preencha o formulário em `grade/config-usuario.md`, escolha a
plataforma e o sistema, use o template de prompt correspondente.

## Estrutura

```
ventura-art/
├── README.md
├── config/
│   ├── plataformas.json        # grade de formatos, durações e disclosure por plataforma
│   └── sistemas.json           # catálogo de modelos: capacidades, durações, fórmulas
├── grade/
│   └── config-usuario.md       # formulário: grade, sistema, tempo, formato, áudio, divulgação
├── prompts/
│   ├── template-mestre.md      # anatomia universal de prompt de vídeo
│   ├── gemini-omni-flash.md    # 3-10s, 9:16, áudio nativo, timecode, meta prompting
│   ├── veo-31.md               # fórmula oficial 5 partes / 7 slots
│   ├── seedance-20.md          # fórmula 8 elementos + storyboard multi-cena
│   ├── kling-30.md             # 4 partes básicas / 5 camadas, até 2 min
│   └── comfyui-animatediff.md  # workflow API JSON: SD1.5 + AnimateDiff + ControlNet
└── conformidade/
    └── divulgacao-ia.md        # regras Google, YouTube, TikTok, Meta, X, LinkedIn
```

## DNA visual (estúdio Gerde)

Surrealismo em pintura em movimento — texturas físicas (papel em camadas,
tecido, aquarela, neon) sobre paleta dramática (teal profundo × coral × ciano
neon), com temas de água/onda/costa, dança e espiritualidade. Detalhes em
`prompts/framework-hiperrealismo.md` do estúdio.

Frase-guia: **"Surrealismo em pintura em movimento: texturas físicas sobre
paleta dramática, com temas de água/onda/costa, dança e espiritualidade."**

## Arquitetura Token-Efficient & Regenerative

Este sistema foi projetado sob três princípios fundamentais:

1. **Economia de Tokens** — maximizar valor por token gasto  
2. **Loop de Alto Rendimento** — cada ciclo deve justificar o consumo  
3. **Comportamento Regenerativo** — o sistema se reconstrói melhor a cada execução

### Ciclo Principal: Explore → Compile → Replay

| Fase | Descrição | Consumo de Tokens |
|------|-----------|-------------------|
| **Explore** | Modelo forte descobre o melhor caminho | Alto (único) |
| **Compile** | Transforma o caminho em skill determinística | Baixo |
| **Replay** | Executa a skill sem raciocínio completo | Mínimo / Zero |
| **Regenerate** | Quando o domínio muda, regenera a skill | Sob demanda |

### Regras de Engenharia

- **Token Budget** explícito por especialista e por etapa
- **Context Engineering** + **Context Compaction** em todas as passagens
- **Context Firewall** entre sub-agentes (cada um só recebe o necessário)
- **Prefix Caching** com system prompt estável
- **Yield-based Stop Condition** (para quando o valor não justifica mais tokens)
- **Skill Distillation** após caminhos bem-sucedidos

### Resultado esperado

- Redução drástica de tokens em execuções recorrentes
- Qualidade mantida ou superior
- Sistema que se auto-otimiza com o uso
