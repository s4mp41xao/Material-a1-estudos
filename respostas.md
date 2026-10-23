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

---

# Automação segura

## Enunciado
Explique por que automatizar uma tarefa não garante qualidade. Cite três cuidados para tornar scripts de automação mais confiáveis e explique a função de cada um.

## Como montar a resposta
Explicar que a automação repete o processo, inclusive os erros, mais rápido e em escala.
Cuidado 1 com a sua função (ex.: tratamento de erros / fail fast).
Cuidado 2 com a sua função (ex.: idempotência).
Cuidado 3 com a sua função (ex.: versionar, revisar e registrar logs).
Bônus: segredos fora do script, validação de entradas, testar o próprio script.

### Resposta-modelo≈ 11 linhas de prova
Automatizar faz uma tarefa ser executada sempre do mesmo jeito e mais rápido. Se o procedimento estiver errado, a automação repete o erro em escala e com menos chance de alguém perceber: um script de deploy que apaga a pasta errada causa o mesmo estrago toda vez que roda. Por isso o script deve ser tratado como código de produção. Três cuidados: (1) tratamento de erros (fail fast): verificar o resultado de cada passo e parar com código de saída de erro quando algo falha, para que o pipeline não continue num estado inconsistente; (2) idempotência: rodar o script duas vezes deve dar o mesmo resultado que rodar uma vez (por exemplo, criar um diretório só se ele não existir), o que permite reexecutar com segurança depois de uma falha; (3) versionamento, revisão e logs: manter o script no repositório, revisado como qualquer código, e registrar o que cada execução fez, o que permite auditar, rastrear e reverter mudanças. Também não se deve deixar senhas escritas no script.

---

# Build reproduzível

## Enunciado
Um projeto compila na máquina de um desenvolvedor, mas falha no servidor de integração. Explique o conceito de build reproduzível e a importância de declarar as dependências e automatizar sua execução.

## Como montar a resposta
Definir build reproduzível: as mesmas entradas geram o mesmo resultado em qualquer ambiente.
Explicar a causa provável do caso: dependência implícita ou diferença de ambiente (“funciona na minha máquina”).
Importância de declarar as dependências com versões fixas (pom.xml, package.json com lockfile).
Importância de automatizar o build por script ou ferramenta (Maven, Gradle, npm), sem passos manuais.
Ligar com a confiabilidade da CI (ambiente limpo, resultado comparável).

### Resposta-modelo≈ 11 linhas de prova
Build reproduzível é aquele que, a partir do mesmo código-fonte e das mesmas entradas, gera o mesmo resultado em qualquer máquina e a qualquer momento. O caso descrito é o clássico “funciona na minha máquina”: o build depende de algo que só existe no computador do desenvolvedor, como uma biblioteca instalada à mão, outra versão do compilador ou do runtime, uma variável de ambiente ou um passo manual. O servidor de integração parte de um ambiente limpo e revela essa dependência implícita. Declarar as dependências com versões fixas (em pom.xml, package.json com lockfile ou requirements.txt) faz todo ambiente baixar exatamente as mesmas bibliotecas. Automatizar a execução com uma ferramenta de build (Maven, Gradle, npm) e, se possível, um container garante que os passos sejam sempre os mesmos, na mesma ordem, sem depender da memória de ninguém. Assim o resultado da CI passa a ser confiável e comparável entre ambientes.

---

# CI, entrega e deploy contínuos

## Enunciado
Diferencie Integração Contínua, Entrega Contínua e Deploy Contínuo, indicando o papel da decisão de liberação do software.

## Como montar a resposta
CI: integrar com frequência, com build e testes automatizados a cada mudança.
Entrega Contínua: software sempre pronto para produção, validado pelo pipeline.
Na Entrega Contínua a liberação em produção é uma decisão humana (de negócio).
Deploy Contínuo: toda mudança aprovada no pipeline vai para produção automaticamente.
Destacar que a diferença central é quem decide a liberação, e o que o deploy contínuo exige (testes confiáveis, monitoramento, rollback).

### Resposta-modelo≈ 11 linhas de prova
As três práticas formam uma sequência, e cada uma depende da anterior. Na Integração Contínua, os desenvolvedores integram o código com frequência e cada integração gera build e testes automatizados; o foco é detectar cedo problemas de integração. Na Entrega Contínua, o pipeline vai além: o artefato aprovado passa por ambientes de teste e homologação e fica sempre pronto para ir à produção, mas a liberação depende de uma decisão humana, normalmente de negócio (quando lançar e para quem), executada com um clique. No Deploy Contínuo essa decisão manual deixa de existir: toda mudança que passa em todas as etapas do pipeline é implantada em produção automaticamente. A diferença central está na decisão de liberação: na entrega contínua ela é manual e separada da parte técnica; no deploy contínuo ela passa para os critérios automáticos do pipeline, o que exige testes muito confiáveis, gates de qualidade, monitoramento e rollback rápido.

---

# Gates de qualidade

## Enunciado
Um pipeline está verde, mas uma análise encontrou violações críticas. Explique o que são gates de qualidade e proponha dois critérios que deveriam impedir a progressão de uma mudança.

## Como montar a resposta
Definir gate de qualidade: ponto de controle com critérios objetivos que bloqueia a etapa seguinte.
Explicar o caso: a análise não era critério obrigatório do pipeline e virou só relatório; verde não significa qualidade.
Critério 1 mensurável (ex.: zero bugs ou vulnerabilidades críticas ou bloqueantes).
Critério 2 mensurável (ex.: cobertura mínima no código novo e 100% dos testes passando).
Critérios automáticos, conhecidos pela equipe e aplicados a toda mudança.

### Resposta-modelo≈ 11 linhas de prova
Gates de qualidade são pontos de controle no pipeline com critérios objetivos e mensuráveis que uma mudança precisa atender para avançar à etapa seguinte. Se um critério não é atendido, o gate falha e a mudança é bloqueada. A situação mostra que o pipeline verde só indica que as etapas configuradas passaram. A análise encontrou violações críticas, mas o resultado dela não estava ligado a um gate obrigatório e serviu apenas como relatório. Ou seja, verde não significa qualidade se os critérios certos não fizerem parte do pipeline. Dois critérios que deveriam barrar a mudança: (1) nenhum bug ou vulnerabilidade de severidade crítica ou bloqueante na análise estática e de segurança (por exemplo, no SonarQube ou num scanner de dependências); (2) cobertura mínima de testes no código novo, por exemplo 80%, com 100% dos testes passando. Esses critérios devem ser automáticos, conhecidos pela equipe e aplicados a toda mudança.

---

# Observabilidade e métricas

## Enunciado
Explique como logs, métricas e alertas ajudam a avaliar a qualidade após o deploy. Cite dois indicadores que podem orientar ações de melhoria.

## Como montar a resposta
Explicar que a qualidade continua sendo avaliada em produção, no uso real.
Papel dos logs: eventos detalhados para investigar a causa de uma falha.
Papel das métricas: valores ao longo do tempo, tendências, comparação antes e depois do deploy.
Papel dos alertas: avisar quando um limite é ultrapassado, para reagir rápido.
Dois indicadores, cada um com a ação de melhoria que ele orienta.

### Resposta-modelo≈ 11 linhas de prova
Depois do deploy, a qualidade precisa ser acompanhada no uso real, porque muitos problemas só aparecem com usuários, dados e carga de produção. Os logs registram eventos detalhados, como erros, exceções e requisições, e permitem investigar a causa de uma falha. As métricas são valores numéricos coletados ao longo do tempo, como tempo de resposta, uso de recursos e quantidade de erros; mostram tendências e permitem comparar o sistema antes e depois de cada deploy. Os alertas monitoram essas métricas e avisam a equipe quando um limite é ultrapassado, para que ela aja antes que o problema atinja muitos usuários. Juntos, fecham o ciclo de feedback do DevOps. Dois indicadores: (1) taxa de erros, como o percentual de respostas HTTP 5xx: se sobe logo após um deploy, indica regressão e pode justificar um rollback; (2) taxa de falha de mudanças (métrica DORA), o percentual de deploys que causam incidentes: se é alta, orienta reforçar testes e gates. O MTTR, tempo médio de recuperação, também serve.
