# Integração Contínua

## Enunciado
Explique o que é Integração Contínua (CI) e cite duas práticas importantes para que ela contribua para a qualidade do software.

## Como montar a resposta
Definir CI: integrar as alterações ao repositório principal com frequência (várias vezes ao dia).
Dizer que cada integração dispara build e testes automatizados.
Explicar o objetivo: detectar problemas de integração cedo, com feedback rápido.
Prática 1 explicada e ligada à qualidade (ex.: testes automatizados a cada commit).
Prática 2 explicada e ligada à qualidade (ex.: corrigir o build quebrado na hora, commits pequenos).

### Resposta-modelo≈ 11 linhas de prova
Integração Contínua (CI) é a prática de integrar as alterações de cada desenvolvedor ao repositório principal com frequência, várias vezes ao dia. Cada integração dispara automaticamente o build e a execução dos testes. O objetivo é descobrir problemas de integração logo depois que surgem, quando ainda são pequenos e baratos de corrigir, em vez de acumulá-los para o fim do projeto. Duas práticas importantes: (1) build e testes automatizados a cada commit: o servidor de CI compila e testa toda mudança do mesmo jeito, sem depender de passos manuais, e avisa a equipe em minutos se algo quebrou; (2) corrigir imediatamente o build quebrado e trabalhar com commits pequenos: quando o pipeline falha, restaurá-lo é prioridade da equipe, e mudanças pequenas facilitam encontrar a causa. Com isso o software se mantém sempre integrado e testado, e o feedback rápido evita que defeitos se acumulem.

---

# DevOps e responsabilidade pela qualidade

## Enunciado
Uma equipe afirma que adotar uma ferramenta de automação é suficiente para implantar DevOps. Explique por que essa afirmação é incompleta e como desenvolvimento, QA e operações devem participar da qualidade.

## Como montar a resposta
Afirmar que DevOps é cultura + práticas + ferramentas, e não só ferramenta.
Mostrar o problema: automação com equipes em silos só acelera a entrega de problemas.
Papel do desenvolvimento (testes automatizados, revisão de código, correção rápida).
Papel do QA desde os requisitos (critérios de aceitação, riscos, estratégia de testes).
Papel de operações (monitoramento, logs, feedback de produção, requisitos de implantação).
Fechar com a responsabilidade compartilhada pela qualidade e objetivos comuns.

### Resposta-modelo≈ 11 linhas de prova
A afirmação é incompleta porque DevOps não é uma ferramenta: é uma combinação de cultura, práticas e ferramentas. A automação é só um dos pilares; o modelo CALMS cita também Cultura, Lean, Medição e Compartilhamento. Uma equipe pode ter um pipeline automatizado e continuar trabalhando em silos, com o desenvolvimento passando o código para o QA e o QA passando para operações. Nesse caso, a ferramenta apenas entrega problemas mais rápido. Em DevOps a qualidade é responsabilidade compartilhada. O desenvolvimento escreve testes automatizados, participa de revisões de código e corrige falhas rapidamente. O QA atua desde os requisitos, ajudando a definir critérios de aceitação, riscos e a estratégia de testes, e não só testando no fim. Operações contribui com requisitos de implantação, monitoramento, logs e informações sobre o comportamento em produção, que voltam como feedback para o time. Com objetivos e métricas comuns e comunicação contínua, a automação passa a apoiar um processo colaborativo.

---

# Fluxo de valor e gargalos

## Enunciado
Uma alteração fica pronta em duas horas, mas espera cinco dias por aprovação. Explique como o mapeamento do fluxo de valor ajuda a identificar o problema e proponha duas melhorias.

## Como montar a resposta
Definir o mapeamento do fluxo de valor: etapas do pedido até a produção, com tempo de trabalho e tempo de espera de cada uma.
Aplicar ao caso: 2 h de trabalho num lead time de mais de 5 dias; a espera domina.
Identificar a aprovação como gargalo (desperdício de espera, na visão Lean).
Melhoria 1 que reduza a espera (ex.: automatizar a aprovação com gates de qualidade).
Melhoria 2 que reduza a espera (ex.: mudanças menores, prazo máximo e rodízio de revisores).
Bônus: medir de novo o lead time para confirmar o ganho.

### Resposta-modelo≈ 11 linhas de prova
O mapeamento do fluxo de valor (Value Stream Mapping) desenha todas as etapas que uma mudança percorre, do pedido até a produção, registrando em cada uma o tempo de trabalho efetivo e o tempo de espera. No caso, o mapa mostra cerca de 2 horas de trabalho para um lead time de mais de 5 dias (120 horas): menos de 2% do tempo agrega valor. O restante é espera, um desperdício na visão Lean, e a etapa de aprovação aparece como o gargalo. Sem o mapa, a equipe poderia tentar acelerar a codificação, que não é o problema. Duas melhorias: (1) automatizar a aprovação com gates de qualidade no pipeline (testes, análise estática, segurança), deixando a aprovação manual só para mudanças de alto risco; (2) trabalhar com mudanças menores e definir um prazo máximo para revisões, com revisores em rodízio, para que nenhum pedido fique parado na fila. Depois, medir o lead time de novo para confirmar o ganho.

