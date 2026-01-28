# Monitor de Deterioração de Ativos – Ações Brasileiras

## Visão geral

Este projeto implementa um **sistema de monitoramento defensivo de ações brasileiras**, com foco na **detecção de regimes persistentes de baixo desempenho**.

O objetivo **não é**:
- prever preços  
- recomendar operações automáticas  
- fazer trading  

O sistema atua como um **sensor estatístico**, apoiando decisões de **manutenção, redução ou pausa de aportes** em uma carteira de longo prazo.

O projeto foi desenvolvido para **uso mensal real**, com geração de relatórios em Excel e histórico acumulado.

---

## Motivação

Investidores de longo prazo frequentemente enfrentam dois problemas:

- insistir em ativos que perderam força estrutural  
- reagir emocionalmente a ruídos de curto prazo  

Este projeto busca mitigar esses problemas ao:

- detectar **deterioração relativa e persistente**, não quedas pontuais  
- comparar cada ativo **consigo mesmo**, evitando vieses entre ativos  
- identificar quando a deterioração é específica do ativo e não apenas reflexo do mercado  

---

## Escopo do projeto

- **Ativos:** Ações brasileiras (B3)  
- **Frequência:** Mensal  
- **Horizonte:** Longo prazo  
- **Abordagem:** Modelo por ativo individual  
- **Usuário-alvo:** Investidor pessoa física  
- **Fonte de dados:** Yahoo Finance  

---

## O que o projeto faz

- Monitora desempenho relativo e persistente  
- Gera alertas estatísticos explicáveis  
- Produz relatórios mensais acionáveis  

---

## O que o projeto não faz

- Não prevê preços futuros  
- Não estima retorno esperado  
- Não automatiza decisões  
- Não substitui análise fundamentalista  

---

## Metodologia (resumo)

1. Coleta de preços ajustados mensais  
2. Cálculo de retornos mensais simples  
3. Construção de métricas estatísticas:
   - retornos acumulados (3 e 6 meses)  
   - volatilidade recente  
   - z-score absoluto (24 meses)  
   - z-score relativo ao Ibovespa (24 meses)  
4. Definição de regime de baixo desempenho por persistência estatística  
5. Uso de **Machine Learning explicável (Regressão Logística)** como escore auxiliar  
6. Geração de relatório mensal e histórico acumulado  

📄 **Documentação conceitual:**  
`docs/Sistema_Deteccao_Deterioracao_Ativos.docx`

---

## Estrutura do repositório


```text
monitor-deterioracao-ativos/
├── src/
│   └── monitor_carteira.py
├── notebooks/
│   └── exploracao_modelo.ipynb
├── docs/
│   └── Sistema_Deteccao_Deterioracao_Ativos.docx
├── modelos/
│   └── README.md
├── outputs/
│   └── exemplo_monitor.xlsx
├── README.md
├── requirements.txt
└── .gitignore

```

## Modelos treinados

Os arquivos de modelo treinado (.pkl) **não são versionados** neste repositório.

Eles são gerados localmente a partir do notebook de treino (notebooks/exploracao_modelo.ipynb).
Essa decisão evita versionamento de binários e mantém o repositório focado em código, lógica e documentação.

## Uso do sistema (resumo)

Uso típico mensal:

**1.** Atualizar a lista de ativos no script

**2.** Executar:

    'python src/monitor_carteira.py'


**3.** Analisar o Excel gerado:

    - INÍCIO → explicação do sistema

    - RESUMO → diagnóstico rápido

    - DADOS → métricas completas

    - HISTÓRICO → evolução mensal acumulada

## Interpretação dos resultados

**- Label = 1**
Regime confirmado de baixo desempenho

**- Score (ML)**
Escore probabilístico de fragilidade estatística

**Diagnóstico**
    Síntese operacional:

    - Normal

    - Atenção

    - Regime fraco

O score deve ser interpretado ao **longo do tempo**, não isoladamente.

## Limitações

O modelo utiliza apenas preços históricos

Eventos estruturais recentes podem não ser capturados imediatamente

O score é um **apoio à decisão**, não uma regra automática

## Autor

**Alan Alves**
**galves.alan@gmail.com**


Projeto pessoal para uso próprio, aprendizado contínuo e portfólio técnico.
