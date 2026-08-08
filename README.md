# Ventura Art

[![License](https://img.shields.io/github/license/venturalabs-ai/ventura-art)](LICENSE)
[![Stars](https://img.shields.io/github/stars/venturalabs-ai/ventura-art)](https://github.com/venturalabs-ai/ventura-art/stargazers)
[![Forks](https://img.shields.io/github/forks/venturalabs-ai/ventura-art)](https://github.com/venturalabs-ai/ventura-art/forks)

Framework de prompts, configuração e documentação para **arte, vídeo e animação generativa com IA**, com foco em consistência, controle de formato e adaptação entre plataformas.

## Objetivo

Centralizar decisões que normalmente ficam espalhadas entre prompts: plataforma, modelo, duração, proporção, áudio, continuidade de cenas e requisitos de divulgação de conteúdo gerado por IA.

## Estrutura

```text
ventura-art/
├── README.md
├── LICENSE
├── config/
│   ├── plataformas.json
│   └── sistemas.json
├── grade/
│   └── config-usuario.md
├── prompts/
│   ├── template-mestre.md
│   ├── gemini-omni-flash.md
│   ├── veo-31.md
│   ├── seedance-20.md
│   ├── kling-30.md
│   └── comfyui-animatediff.md
└── conformidade/
    └── divulgacao-ia.md
```

## Fluxo de uso

```text
1. Defina plataforma e formato.
2. Escolha o sistema/modelo de geração.
3. Defina duração, áudio e estrutura de cenas.
4. Use o template correspondente.
5. Valide continuidade, legibilidade e disclosure antes da publicação.
```

## Continuidade entre cenas

Para produções multi-cena, trate como requisitos explícitos:

- identidade do personagem;
- figurino e proporções;
- direção de luz;
- lente e linguagem de câmera;
- posição de objetos principais;
- transição do último frame para o primeiro frame da cena seguinte.

## Conformidade

As regras de plataformas e modelos mudam com frequência. O material em `conformidade/` deve ser tratado como referência operacional e revisado antes de campanhas ou publicações importantes.

## Modelos e marcas

Nomes de modelos e plataformas são utilizados apenas para identificar compatibilidade de workflow e formato. Este projeto não implica parceria, certificação ou afiliação com os respectivos fornecedores.

## Arquitetura de eficiência

**Explore → Compile → Replay → Regenerate**

Prompts bem-sucedidos podem ser convertidos em templates reutilizáveis para reduzir retrabalho e manter consistência entre produções.

## Status

Repositório de **framework, prompts e documentação**. Não é um motor próprio de geração de vídeo; a renderização é executada pelas plataformas e modelos escolhidos pelo usuário.

## Licença

MIT — consulte [LICENSE](LICENSE).

## Autor

Wemerson Mota de Oliveira — Ventura Labs AI

[GitHub](https://github.com/venturalabs-ai) · [LinkedIn](https://www.linkedin.com/in/wemerson-mota-de-oliveira-81aa8226/)
