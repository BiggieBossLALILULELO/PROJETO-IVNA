# 🚀 Relatório da Sprint 1 - EcoQuest

## 1️⃣ Objetivo da Sprint
Estabelecer a infraestrutura inicial do projeto e entregar o fluxo básico de acesso do usuário. O objetivo principal é permitir que um usuário crie uma conta, faça login no sistema e visualize a tela principal com a listagem de missões sustentáveis ativas.

---

## 2️⃣ Backlog da Sprint
As histórias abaixo foram movidas da coluna "Backlog" para a coluna "Done" (Concluído) ao longo desta Sprint:
* **US01:** `[Autenticação] Registro de novo usuário`
* **US02:** `[Autenticação] Login na plataforma`
* **US03:** `[Missões] Listagem de missões sustentáveis ativas`

---

## 3️⃣ Estimativas
Para esta Sprint, a equipe utilizou a técnica de **Story Points** (baseada na sequência de Fibonacci: 1, 2, 3, 5, 8...), medindo a complexidade e o esforço de cada tarefa:
* **US01 (Registro): 3 pontos** (Exige criação do banco de dados inicial e formulário).
* **US02 (Login): 2 pontos** (Aproveita a conexão do banco já feita no registro).
* **US03 (Listagem de Missões): 5 pontos** (Mais complexa, exige criar a interface da tela principal e puxar os dados do banco).
* **Total da Sprint:** 10 Story Points.

---

## 4️⃣ Registro das Daily Scrums
*Resumo das reuniões diárias de alinhamento da equipe:*

* **Daily 01 (06/04/2026):**
  * **O que foi feito:** Configuração do repositório no GitHub e planejamento da Sprint.
  * **O que será feito:** Desenhar a interface da tela de cadastro e iniciar a configuração do Banco de Dados.
  * **Impedimentos:** Nenhum.

* **Daily 02 (07/04/2026):**
  * **O que foi feito:** Banco de dados configurado e tela de cadastro (US01) finalizada no front-end.
  * **O que será feito:** Integrar o cadastro com o banco (back-end) e iniciar a tela de Login (US02).
  * **Impedimentos:** Dificuldade com um erro de CORS na comunicação entre front-end e back-end (resolvido após pesquisa).

* **Daily 03 (08/04/2026):**
  * **O que foi feito:** Erro de integração resolvido. US01 e US02 100% concluídas.
  * **O que será feito:** Iniciar a criação dos cartões de missão (US03) e preencher o banco com dados falsos (mock data) para testar a listagem.
  * **Impedimentos:** Atraso leve por problema de conexão de um dos membros, compensado com pareamento de código (Pair Programming).

---

## 5️⃣ Incremento da Sprint
Ao final desta Sprint, o incremento gerado é um **Protótipo Funcional Básico (MVP inicial)**. 
O sistema agora possui um banco de dados conectado. Um usuário real consegue preencher seus dados, salvar no sistema, utilizar as credenciais para logar na plataforma e ser redirecionado para uma tela "Home", onde já consegue visualizar as primeiras missões sustentáveis carregadas diretamente do banco de dados.

---

## 6️⃣ Retrospectiva da Sprint
*Reflexão da equipe após o fim do ciclo:*
* **O que funcionou bem:** O uso do Kanban no GitHub ajudou muito a equipe a não se perder nas tarefas. A comunicação via grupo foi rápida e eficiente para resolver problemas.
* **O que pode melhorar:** Subestimamos o tempo necessário para configurar a conexão inicial com o banco de dados, o que causou acúmulo de tarefas no segundo dia.
* **Quais ações serão adotadas na próxima Sprint:** 1. Quebrar tarefas mais complexas (como as de 5 pontos) em subtarefas menores no Kanban.
  2. Fazer uma pesquisa prévia técnica (Spike) antes de começar a codificar as funcionalidades de gamificação (XP e Níveis).
