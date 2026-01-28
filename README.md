Monitor de Deterioração de Ativos – Ações Brasileiras
Visão Geral
Este projeto implementa um sistema de monitoramento defensivo de ações brasileiras, com foco na detecção de regimes persistentes de baixo desempenho.
O objetivo não é:

Prever preços
Recomendar operações automáticas
Fazer trading

O sistema atua como um sensor estatístico, apoiando decisões de manutenção, redução ou pausa de aportes em uma carteira de longo prazo.
O projeto foi desenvolvido para uso mensal real, com geração de relatórios em Excel e histórico acumulado.

Motivação
Investidores de longo prazo frequentemente enfrentam dois problemas:

Insistir em ativos que perderam força estrutural
Reagir emocionalmente a ruídos de curto prazo

Este projeto busca mitigar esses problemas ao:

Detectar deterioração relativa e persistente, não quedas pontuais
Comparar cada ativo consigo mesmo, evitando vieses entre ativos
Separar fraqueza idiossincrática de movimentos gerais do mercado


Escopo do Projeto

Ativos: Ações brasileiras (B3)
Frequência: Mensal
Horizonte: Longo prazo
Abordagem: Modelo por ativo individual
Usuário-alvo: Investidor pessoa física
Fonte de dados: Yahoo Finance

O que o projeto faz

Monitora desempenho relativo e persistente
Gera alertas estatísticos explicáveis
Produz relatórios mensais acionáveis

O que o projeto não faz

Não prevê preços futuros
Não estima retorno esperado
Não automatiza decisões
Não substitui análise fundamentalista


Metodologia (resumo)

Coleta de preços ajustados mensais
Cálculo de retornos mensais simples
Construção de métricas estatísticas:

Retornos acumulados (3 e 6 meses)
Volatilidade recente
Z-score absoluto (24 meses)
Z-score relativo ao Ibovespa (24 meses)


Definição de regime de baixo desempenho por persistência estatística
Uso de Machine Learning explicável (Regressão Logística) como escore auxiliar
Geração de relatório mensal e histórico acumulado

O racional completo das decisões metodológicas está documentado em PDF.
📄 Documentação conceitual: docs/Sistema_Deteccao_Deterioracao_Ativos.pdf



Estrutura do Repositório

monitor-deterioracao-ativos/
├── src/
│   └── monitor_carteira.py          # Script principal (uso mensal)
├── notebooks/
│   └── exploracao_modelo.ipynb      # Exploração, treino e validação
├── docs/
│   └── racional_projeto.pdf         # Fundamentação conceitual
├── modelos/
│   └── README.md                    # Explicação sobre modelos treinados
├── outputs/
│   └── exemplo_monitor.xlsx         # Exemplo de relatório gerado
├── README.md
├── requirements.txt
└── .gitignore

Modelos Treinados
Os arquivos de modelo treinado (.pkl) não são versionados neste repositório. Eles são gerados localmente a partir do notebook de treino (notebooks/exploracao_modelo.ipynb).
Essa decisão evita versionamento de binários e mantém o repositório focado em código, lógica e documentação.

Uso do Sistema (resumo)
O uso típico é mensal, após o fechamento do mês:

Atualizar a lista de ativos no script (se necessário)
Executar:

bash   python src/monitor_carteira.py

Analisar o arquivo Excel gerado:

Aba INÍCIO → Explicação do sistema
Aba RESUMO → Diagnóstico rápido
Aba DADOS → Métricas completas
Aba HISTÓRICO → Evolução mensal acumulada



O sistema foi projetado para uso simples e recorrente, sem necessidade de intervenção frequente.

Interpretação dos Resultados
IndicadorSignificadoLabel = 1Regime confirmado de baixo desempenho (persistente)Score (ML)Escore probabilístico que indica fragilidade estatística com base em padrões históricosDiagnósticoSíntese operacional: Normal / Atenção / Regime fraco

⚠️ O score não deve ser interpretado isoladamente, mas sim ao longo do tempo.


Limitações

O modelo depende exclusivamente de preços históricos
Eventos estruturais recentes podem não ser capturados imediatamente
O score é um auxílio à decisão, não uma verdade absoluta

Essas limitações são intencionais e coerentes com o caráter defensivo do projeto.

Autor
Alan Alves

Contato
galves.alan@gmail.com

Projeto pessoal para uso próprio, aprendizado contínuo e portfólio técnico.