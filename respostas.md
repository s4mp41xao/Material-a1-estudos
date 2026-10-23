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
