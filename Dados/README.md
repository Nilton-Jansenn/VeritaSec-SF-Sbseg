# Dados Experimentais

Este diretório reúne os conjuntos de dados utilizados para reproduzir os experimentos apresentados no artigo do VeritasSec submetido ao SBSeg 2026.

## Estrutura

### JuiceShop

Contém o projeto utilizado durante os experimentos e o relatório SARIF correspondente, empregado como entrada para o VeritasSec.

### Google-Gemini

Contém os resultados produzidos pelo VeritasSec utilizando modelos da família Google Gemini.

### OpenAI

Contém os resultados produzidos pelo VeritasSec utilizando modelos da OpenAI.

## Fluxo Experimental

```
Código-fonte (Juice Shop)
          │
          ▼
      Ferramenta SAST
          │
          ▼
      Relatório SARIF
          │
          ▼
       VeritasSec
          │
          ├────────► Google Gemini
          │
          └────────► OpenAI
                   │
                   ▼
      Relatórios • Gráficos • Métricas • SARIF Enriquecido
```
