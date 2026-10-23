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

---

# QA e QC

## Enunciado
Diferencie Garantia da Qualidade (QA) e Controle da Qualidade (QC), apresentando um exemplo de cada e explicando por que testes não representam toda a garantia da qualidade.

## Como montar a resposta
QA: orientada ao processo, preventiva.
Exemplo concreto de QA (padrão de código, revisão obrigatória, auditoria de processo).
QC: orientado ao produto, detectivo.
Exemplo concreto de QC (executar casos de teste, inspecionar o produto).
Explicar que teste é QC; QA é mais ampla (requisitos, padrões, revisões, treinamento, melhoria contínua).

### Resposta-modelo≈ 11 linhas de prova
Garantia da Qualidade (QA) é orientada ao processo e tem caráter preventivo: define e melhora a forma de trabalhar para que os defeitos não sejam introduzidos. Exemplo: criar um padrão de codificação e tornar obrigatória a revisão de código, ou auditar se a equipe segue o processo definido. Controle da Qualidade (QC) é orientado ao produto e tem caráter detectivo: examina o que foi produzido para encontrar defeitos antes da entrega. Exemplo: executar os casos de teste de uma nova versão e registrar os defeitos encontrados. Testes são, portanto, uma atividade de QC: mostram problemas que já existem no produto, mas não impedem que eles surjam. A garantia da qualidade é mais ampla e inclui requisitos bem definidos, padrões, revisões, treinamento, métricas de processo e melhoria contínua. Um produto pode ser muito testado e ainda ter baixa qualidade se o processo continuar gerando os mesmos defeitos.

---

# Verificação, validação e risco

## Enunciado
Diferencie verificação e validação. Em um sistema de pagamentos com pouco tempo para testar, explique como probabilidade e impacto de falha devem orientar as prioridades.

## Como montar a resposta
Verificação: o produto está sendo construído corretamente, conforme a especificação.
Validação: é o produto certo, atende à necessidade real do usuário.
Risco = probabilidade × impacto; com pouco tempo, priorizar pelo risco.
Exemplo de alta prioridade no sistema de pagamentos (valor, autorização, cobrança duplicada, segurança).
Exemplo de baixa prioridade (layout, telas pouco usadas), com testes mais superficiais.

### Resposta-modelo≈ 11 linhas de prova
Verificação responde à pergunta “estamos construindo o produto corretamente?”: confere se o software está de acordo com a especificação, por meio de revisões, inspeções e testes contra o que foi especificado. Validação responde “estamos construindo o produto certo?”: confere se o software atende à necessidade real do usuário e do negócio, por exemplo com testes de aceitação e homologação. Um sistema pode passar na verificação e falhar na validação se a própria especificação estiver errada. Com pouco tempo, não dá para testar tudo com a mesma profundidade, então a prioridade vem do risco, que combina a probabilidade de a falha acontecer com o impacto que ela causaria. Num sistema de pagamentos, cálculo do valor, autorização da transação, cobrança duplicada e segurança dos dados têm impacto altíssimo (prejuízo financeiro, legal e de imagem) e devem ser testados primeiro e mais a fundo, assim como partes complexas ou alteradas recentemente, que falham com mais probabilidade. Itens de baixo impacto, como o layout da tela de histórico, ficam para o final.

---

# Revisões e análise estática

## Enunciado
Explique como revisões e análise estática identificam defeitos antes da execução do software. Diferencie walkthrough e inspeção.

## Como montar a resposta
Revisões e análise estática são técnicas estáticas: avaliam artefatos sem executar o software.
Encontram defeitos cedo, quando são mais baratos de corrigir (até em requisitos e projeto).
Exemplos do que encontram (requisito ambíguo, erro de lógica, variável não usada, referência nula, vulnerabilidade).
Walkthrough: conduzido pelo autor, informal, foco em entendimento e sugestões.
Inspeção: formal, com moderador, papéis, checklist, registro de defeitos e métricas.

### Resposta-modelo≈ 11 linhas de prova
Revisões e análise estática são técnicas de teste estático: avaliam requisitos, projeto e código sem executar o software. Por isso podem ser aplicadas cedo, até antes de existir código executável, quando corrigir um defeito custa muito menos. Nas revisões, pessoas leem o artefato e encontram requisitos ambíguos, regras de negócio faltando, erros de lógica e desvios de padrão. A análise estática usa ferramentas, como linters e o SonarQube, que examinam o código automaticamente e apontam variáveis não usadas, código inalcançável, possíveis referências nulas, vulnerabilidades e complexidade excessiva. As duas localizam o defeito diretamente, enquanto o teste dinâmico mostra uma falha cuja causa ainda precisa ser investigada. O walkthrough é uma revisão menos formal, conduzida pelo próprio autor, que apresenta o material ao grupo para explicar, receber sugestões e compartilhar conhecimento. A inspeção é a revisão mais formal: tem moderador treinado, papéis definidos, preparação individual com checklists, registro dos defeitos, métricas e acompanhamento das correções.

---

# Atributos e maturidade

## Enunciado
Explique por que um software funcional pode ainda apresentar baixa qualidade. Cite três atributos de qualidade abordados na aula e diferencie qualidade do produto de maturidade do processo.

## Como montar a resposta
Funcionar não basta: qualidade inclui como o software faz (desempenho, uso, falhas, manutenção).
Três atributos de qualidade, cada um explicado (ISO/IEC 25010).
Qualidade do produto: características do próprio software.
Maturidade do processo: capacidade da organização de produzir de forma previsível (CMMI, MPS.BR).
Relação: processo maduro aumenta a chance de qualidade, mas não a garante.

### Resposta-modelo≈ 11 linhas de prova
Um software funcional faz o que foi pedido, mas qualidade também envolve como ele faz. Um sistema pode calcular tudo certo e ainda assim ser lento, difícil de usar, cair com frequência, ter falhas de segurança ou ter um código tão confuso que cada alteração gera novos defeitos. A norma ISO/IEC 25010 organiza esses aspectos em características de qualidade. Três delas: usabilidade, que indica se o usuário consegue aprender e operar o sistema com facilidade; confiabilidade, que é a capacidade de funcionar sem falhas e se recuperar delas; e manutenibilidade, que é a facilidade de modificar, corrigir e testar o código. Qualidade do produto se refere às características do próprio software, observadas no código e no sistema em uso. Maturidade do processo se refere à capacidade da organização de desenvolver de forma definida, medida e previsível, avaliada por modelos como CMMI e MPS.BR. Um processo maduro aumenta a chance de entregar produtos de qualidade de forma consistente, mas não garante sozinho a qualidade de cada produto.

---

# Planejamento e rastreabilidade

## Enunciado
Explique os principais elementos de um plano de testes e como a rastreabilidade entre requisito, teste, resultado e defeito contribui para a revisão da qualidade.

## Como montar a resposta
Elementos do plano: escopo (o que entra e o que fica fora), objetivos e estratégia.
Elementos do plano: ambiente, recursos, responsáveis e cronograma.
Elementos do plano: riscos, critérios de entrada e de saída, entregáveis.
Rastreabilidade: requisito ↔ teste ↔ resultado ↔ defeito, normalmente numa matriz.
Contribuição: cobertura de requisitos, análise de impacto e decisão de liberar baseada em evidências.

### Resposta-modelo≈ 11 linhas de prova
O plano de testes documenta como os testes serão conduzidos. Seus principais elementos são: escopo (o que será e o que não será testado); objetivos; estratégia (níveis, tipos e técnicas de teste); ambiente e ferramentas; recursos e responsáveis; cronograma; riscos e contingências; critérios de entrada e de saída, por exemplo todos os casos críticos executados e nenhum defeito crítico aberto; e entregáveis, como os relatórios. A rastreabilidade liga cada requisito aos casos de teste que o verificam, cada teste ao resultado da execução e cada falha ao defeito registrado, normalmente numa matriz de rastreabilidade. Na revisão da qualidade, ela mostra quais requisitos foram cobertos e quais ficaram sem teste, a situação de cada requisito (passou, falhou, bloqueado) e quais defeitos afetam funções importantes. Também permite analisar o impacto de uma mudança de requisito, porque se sabe quais testes refazer. Assim, a decisão de liberar deixa de se basear em impressões e passa a se apoiar em evidências.

---

# Erro, defeito e falha

## Enunciado
Diferencie erro, defeito e falha utilizando um exemplo. Explique por que uma execução de testes sem falhas não comprova ausência absoluta de defeitos.

## Como montar a resposta
Erro: engano humano.
Defeito: imperfeição deixada no artefato ou no código por causa do erro.
Falha: comportamento incorreto observado na execução.
Um único exemplo que passe pelos três (ex.: “>” no lugar de “>=”).
Testes sem falhas não provam ausência de defeitos: testes mostram presença; teste exaustivo é impossível; o defeito pode estar num caminho não executado.

### Resposta-modelo≈ 11 linhas de prova
Erro é uma ação humana equivocada, como entender mal um requisito ou escrever a condição errada. Defeito (bug) é a imperfeição que esse erro deixa no artefato, como uma linha de código incorreta. Falha é o comportamento incorreto observado quando o código com defeito é executado. Exemplo: a regra diz que compras a partir de R$ 100 têm desconto, e o desenvolvedor escreve “valor > 100” em vez de “valor >= 100” (erro). O código fica com a condição errada (defeito). Quando um cliente compra exatamente R$ 100 e não recebe o desconto, ocorre a falha. Um defeito pode existir sem nunca gerar falha, se aquele trecho não for executado com a entrada que o revela. Por isso, testes sem falhas não provam que não há defeitos: testes mostram a presença de defeitos, não a sua ausência. Testar todas as entradas e caminhos é impossível, então os testes cobrem só uma amostra; no exemplo, se ninguém testar o valor 100, o defeito passa despercebido. Testes sem falhas aumentam a confiança, mas não garantem um software sem defeitos.

---

# Níveis de teste

## Enunciado
Diferencie testes unitários, de integração, de sistema e de aceitação. Apresente um exemplo de cada em uma aplicação de vendas.

## Como montar a resposta
Unitário: menor parte do código, isolada, com exemplo de vendas.
Integração: comunicação entre componentes, com exemplo.
Sistema: sistema completo contra os requisitos (funcionais e não funcionais), com exemplo.
Aceitação: cliente ou usuário confirma que atende ao negócio, com exemplo.

### Resposta-modelo≈ 11 linhas de prova
Os níveis de teste se diferenciam pelo tamanho do que é testado e pelo objetivo. O teste unitário verifica a menor parte do código, isolada, como uma função ou classe, e normalmente é escrito pelo desenvolvedor. Exemplo: verificar se a função calcularTotal aplica corretamente 10% de desconto a um pedido. O teste de integração verifica a comunicação entre componentes ou sistemas. Exemplo: ao confirmar uma venda, o módulo de pedidos chama o serviço de estoque e a quantidade do produto é baixada corretamente. O teste de sistema avalia o sistema completo, de ponta a ponta, contra os requisitos funcionais e não funcionais, num ambiente parecido com o de produção. Exemplo: buscar um produto, colocá-lo no carrinho, pagar com cartão e receber o e-mail de confirmação, medindo também o tempo de resposta. O teste de aceitação é feito pelo cliente ou usuário para confirmar se o sistema atende às necessidades do negócio. Exemplo: a equipe comercial registra uma venda real com cupom promocional e aprova a entrega.

---

# Caixa preta e caixa branca

## Enunciado
Diferencie caixa preta e caixa branca. Para uma entrada que aceita idades inteiras de 18 a 65 anos, proponha valores para testar os limites e explique por que cobertura de código alta não garante testes eficazes.

## Como montar a resposta
Caixa preta: baseado na especificação, em entradas e saídas, sem ver o código.
Caixa branca: baseado na estrutura interna, medido por cobertura de comandos e decisões.
Valores-limite propostos: 17, 18, 19, 64, 65, 66 (no mínimo 17, 18, 65 e 66).
Justificar: os defeitos se concentram nas fronteiras (ex.: “>” no lugar de “>=”).
Cobertura alta não garante eficácia: mede execução, não verificação (teste sem asserção, valores que não revelam o defeito, requisitos não implementados).

### Resposta-modelo≈ 11 linhas de prova
No teste caixa preta, os casos são criados a partir da especificação, sem olhar o código: avalia-se o que o sistema faz, comparando entradas e saídas, com técnicas como partição de equivalência e análise de valor-limite. No teste caixa branca, os casos são criados a partir da estrutura interna do código, buscando executar comandos, decisões e caminhos; sua medida é a cobertura de código. Para idades inteiras de 18 a 65, a análise de valor-limite testa cada fronteira e seus vizinhos: 17 (inválido), 18 (válido), 19 (válido), 64 (válido), 65 (válido) e 66 (inválido). As fronteiras são escolhidas porque é nelas que aparecem erros como usar “>” no lugar de “>=”. Cobertura alta não garante testes eficazes, porque mostra apenas que as linhas foram executadas, não que o resultado foi verificado: um teste sem asserções pode chegar a 100% de cobertura sem detectar nada. Além disso, testar 30 e 70 cobre os dois caminhos do “if”, mas não revela o erro no limite 18, e a cobertura não mostra requisitos que nem foram implementados.

---

# Ciclo TDD

## Enunciado
Explique o ciclo Red-Green-Refactor do TDD, justificando por que o teste deve falhar antes da implementação e por que a refatoração faz parte do ciclo.

## Como montar a resposta
Red: escrever um teste que falha para um comportamento novo.
Green: escrever o código mínimo para o teste passar.
Refactor: melhorar o código sem mudar o comportamento, com os testes verdes.
Por que falhar antes: prova que o teste detecta a ausência do comportamento (evita teste que passa sempre).
Por que refatorar: o código mínimo acumula duplicação e dívida técnica; os testes dão segurança para melhorar.

### Resposta-modelo≈ 11 linhas de prova
No TDD (Test-Driven Development), o teste é escrito antes do código, em ciclos curtos de três etapas. No Red, escreve-se um teste automatizado para um comportamento que ainda não existe; ao executá-lo, ele falha. No Green, escreve-se o código mínimo necessário para o teste passar, sem se preocupar ainda com elegância. No Refactor, melhora-se a estrutura do código e do teste (remover duplicação, melhorar nomes, simplificar) sem mudar o comportamento, rodando os testes para garantir que tudo continua verde. Depois o ciclo recomeça com o próximo comportamento. O teste precisa falhar antes da implementação para provar que é capaz de detectar a ausência do comportamento. Um teste que já passa sem o código pode estar errado, testando outra coisa ou sem asserção, e daria uma falsa segurança; a falha também confirma que o requisito ainda não foi atendido. A refatoração faz parte do ciclo porque o código do Green costuma ser simples ou repetido. Sem ela, a dívida técnica se acumula; com os testes já escritos, dá para melhorar o design com segurança.

---

# Testes legíveis e dependências

## Enunciado
Explique a organização Arrange-Act-Assert e como o uso de doubles de teste pode isolar dependências. Indique um risco do excesso de mocks.

## Como montar a resposta
Arrange: preparar dados, objetos e dependências.
Act: executar a ação testada (normalmente uma chamada).
Assert: verificar o resultado esperado; a separação deixa o teste legível.
Doubles substituem dependências reais (banco, API, e-mail) para isolar a unidade: teste rápido e determinístico.
Tipos de double (stub, mock, fake) e a função de cada um.
Um risco do excesso de mocks bem explicado (acoplamento à implementação ou falsa confiança na integração).

### Resposta-modelo≈ 11 linhas de prova
O padrão Arrange-Act-Assert organiza o teste em três blocos. No Arrange, prepara-se o cenário: dados, objetos e dependências. No Act, executa-se a ação testada, normalmente uma única chamada. No Assert, verifica-se se o resultado é o esperado. Exemplo: criar um carrinho com dois itens, chamar calcularTotal() e verificar se o total é R$ 50. Essa separação deixa claro o que o teste faz e facilita achar a causa quando ele falha. Doubles de teste são objetos que substituem dependências reais durante o teste, como banco de dados, API de pagamento ou serviço de e-mail. Um stub devolve respostas prontas, um mock verifica se uma interação aconteceu (por exemplo, se o e-mail foi enviado uma vez) e um fake é uma implementação simplificada, como um banco em memória. Assim a unidade é testada de forma isolada, rápida e determinística, sem depender de rede ou de dados externos. O risco do excesso de mocks é o teste ficar acoplado à implementação: passa a verificar como o código faz e não o que ele entrega, quebra a cada refatoração e pode passar mesmo com a integração real quebrada, dando falsa confiança.

---

# Automação por camadas

## Enunciado
Explique por que não é adequado automatizar todos os testes pela interface. Descreva o papel de testes unitários, de API, de interface e exploratórios em uma estratégia equilibrada.

## Como montar a resposta
Por que não tudo pela interface: lento, frágil, caro de manter e difícil de diagnosticar.
Unitários: a base, muitos, rápidos, cobrem regras e cálculos.
API ou serviço: o meio, verificam integrações e regras sem depender da tela, mais estáveis.
Interface (end-to-end): o topo, poucos, só os fluxos críticos.
Exploratórios: feitos por pessoas, encontram o inesperado e problemas de usabilidade.

### Resposta-modelo≈ 11 linhas de prova
Automatizar todos os testes pela interface não é adequado porque os testes de UI são os mais lentos, os mais caros de manter e os mais frágeis: uma mudança de layout, de seletor ou no tempo de carregamento quebra o teste sem que exista defeito. Quando falham, também é difícil localizar a causa. Uma suíte só de UI forma o antipadrão da “casquinha de sorvete”, com feedback lento e pouca confiança. A estratégia equilibrada segue a pirâmide de testes. Na base ficam muitos testes unitários, rápidos, baratos e precisos, que verificam regras de negócio e cálculos isoladamente e rodam a cada commit. No meio ficam os testes de API ou de serviço, que verificam integrações e regras pelas interfaces do sistema (por exemplo, criar um pedido pela API e conferir a resposta) sem depender da tela, e por isso são mais estáveis. No topo, poucos testes de interface (end-to-end) cobrem apenas os fluxos críticos, como login e finalização da compra. Ao lado da pirâmide ficam os testes exploratórios, feitos por pessoas, que usam criatividade e conhecimento do negócio para encontrar problemas de usabilidade e comportamentos que nenhum script prevê.

---

# Flaky tests, smoke e regressão

## Enunciado
Uma suíte falha de modo intermitente sem mudanças no produto. Explique o que são flaky tests e proponha duas medidas para reduzir o problema. Diferencie smoke test de regressão.

## Como montar a resposta
Definir flaky test: não determinístico, passa e falha sem mudança no código.
Causas (esperas fixas e assincronia, ordem e dados compartilhados, rede e serviços externos, data e hora).
Medida 1 explicada (ex.: esperas por condição, isolamento de dados, doubles para serviços externos).
Medida 2 explicada (ex.: histórico de execuções, quarentena e correção prioritária).
Smoke: pequeno e rápido, verifica o essencial e decide se dá para seguir testando.
Regressão: ampla, garante que a mudança não quebrou o que já funcionava.

### Resposta-modelo≈ 11 linhas de prova
Flaky tests são testes não determinísticos: com o mesmo código, às vezes passam e às vezes falham. Causas comuns: esperas fixas e operações assíncronas, dependência da ordem de execução ou de dados compartilhados entre testes, serviços externos e rede instáveis, e uso da data e hora reais. O maior prejuízo é a perda de confiança: a equipe reexecuta o pipeline até ficar verde e passa a ignorar falhas reais. Duas medidas: (1) eliminar as fontes de não determinismo, trocando esperas fixas por esperas por condição, isolando cada teste com seus próprios dados (setup e teardown) e substituindo serviços externos por doubles; (2) monitorar e colocar em quarentena: usar o histórico de execuções para identificar os testes instáveis, retirá-los temporariamente da suíte que bloqueia o pipeline e corrigi-los com prioridade. Smoke test é um conjunto pequeno e rápido que verifica se as funções essenciais funcionam (o sistema sobe, o login e a página principal funcionam), para decidir se a versão pode seguir para testes mais profundos. Teste de regressão é mais amplo: reexecuta os testes das funcionalidades existentes para garantir que a mudança não quebrou o que já funcionava.
