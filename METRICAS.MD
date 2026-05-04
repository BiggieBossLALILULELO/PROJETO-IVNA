# 📊 Análise de Desempenho e Métricas Ágeis - EcoQuest

## 1️⃣ Cálculo da Velocity
A *Velocity* da equipe foi calculada somando os *Story Points* das histórias que atingiram 100% dos critérios de aceitação e foram movidas para a coluna "Done" (Concluído). Tarefas parciais não foram pontuadas, respeitando a regra do *Definition of Done* (DoD).

* **Sprint 1:**
  * **Planejado:** 10 pontos.
  * **Entregue:** 10 pontos.
  * **Histórias Concluídas:** US01 (3 pts), US02 (2 pts) e US03 (5 pts).
  * **Velocity Sprint 1:** **10 pontos.**

* **Sprint 2:**
  * **Planejado:** 11 pontos.
  * **Entregue:** 8 pontos.
  * **Histórias Concluídas:** US04 revisada com upload de fotos (5 pts) e US16 Painel de Admin (3 pts).
  * **Histórias Incompletas (Não pontuadas):** US05 Sistema de Nível (3 pts) - o front-end foi feito, mas a integração com o back-end não terminou a tempo.
  * **Velocity Sprint 2:** **8 pontos.**

---

## 2️⃣ Comparação entre Sprints
Analisando os dados, observamos uma **queda na Velocity de 10 para 8 pontos (redução de 20%)** entre a Sprint 1 e a Sprint 2.
Enquanto a Sprint 1 apresentou uma previsibilidade perfeita (100% de entrega do planejado), a Sprint 2 apresentou uma estabilidade menor, deixando uma história não finalizada ("rollover" da US05 para a Sprint 3).

---

## 3️⃣ Análise de Desempenho
A queda na *Velocity* da Sprint 2 não reflete necessariamente uma equipe mais lenta, mas sim o impacto de fatores técnicos e de mudança de escopo:

* **Mudança de Escopo e Complexidade:** A Sprint 2 absorveu a mudança obrigatória definida anteriormente (exigência de fotos para evitar trapaças). A integração com o Cloud Storage (AWS S3/Firebase) para suportar o upload de imagens se provou tecnicamente mais complexa do que apenas salvar textos no banco de dados.
* **Estimativas Imprecisas:** A equipe manteve a estimativa de 5 pontos para a US04, mas a inclusão dos Requisitos Não Funcionais (NFRs) de Segurança e Desempenho no processamento das fotos exigiu muito mais esforço invisível (refatoração de código). O valor real dessa tarefa deveria ter sido 8 pontos.
* **Dependências Técnicas (Gargalo):** Como a evolução de nível (US05) dependia de o sistema de XP (US04) estar 100% sem bugs, os desenvolvedores da US05 ficaram bloqueados por dois dias aguardando a finalização do serviço de upload.

---

## 4️⃣ Ações de Melhoria
Para estabilizar nossa *Velocity* e melhorar a previsibilidade nas próximas Sprints, o grupo adotará as seguintes medidas:

1. **Uso de Spikes Técnicos:** Antes de estimar e puxar histórias com tecnologias desconhecidas (como será o uso de mapas na US08), faremos um *Spike* (tarefa de pesquisa curta de 1 dia) para entender a tecnologia e dar uma estimativa de pontos mais realista.
2. **Considerar os NFRs nas Estimativas:** A partir da Sprint 3, os Requisitos Não Funcionais (como testes de carga e segurança) farão parte do *Definition of Done*. Histórias que mexem com dados sensíveis receberão pontuação extra na estimativa devido ao tempo necessário para testes.
3. **Limitar o WIP (Work In Progress):** Para evitar que uma história fique pronta apenas no front-end enquanto o back-end atrasa (como ocorreu na US05), vamos limitar a quantidade de cartões na coluna "In Progress". A equipe fará *Pair Programming* (programação em pares) para "atravessar" as histórias difíceis até o "Done" antes de puxar uma tarefa nova.
