# ⚙️ Análise de Requisitos Não Funcionais (NFR) - EcoQuest

## 1️⃣ Requisitos Não Funcionais (NFR)
Para garantir a qualidade do EcoQuest, definimos os seguintes NFRs com métricas claras e mensuráveis:

* **NFR01 - Desempenho (Performance):** O tempo de resposta para carregar a lista de missões ativas e o ranking global deve ser inferior a **2 segundos** em conexões 4G. O upload de fotos de comprovação deve iniciar o processamento em menos de **3 segundos**.
* **NFR02 - Escalabilidade (Scalability):** O sistema deve ser capaz de suportar até **1.000 usuários simultâneos** navegando e interagindo com o aplicativo sem que o tempo de resposta se degrade em mais de 10%.
* **NFR03 - Segurança (Security):** 100% das senhas dos usuários devem ser armazenadas com criptografia (hash, ex: bcrypt). As rotas da API (exceto login/cadastro) devem exigir autenticação via token JWT com expiração de **24 horas**.
* **NFR04 - Usabilidade (Usability):** A interface deve ser *Mobile-First*. O usuário deve conseguir acessar a tela de "Concluir Missão" (onde tira a foto) com no máximo **3 toques (cliques)** a partir da tela inicial.
* **NFR05 - Disponibilidade (Availability):** O sistema deve garantir um *uptime* de **99,9%** ao mês (aproximadamente 43 minutos de inatividade máxima tolerada por mês).

---

## 2️⃣ Justificativa Técnica
Cada requisito acima foi pensado para resolver os desafios específicos do nosso domínio (gamificação de sustentabilidade):

* **Por que Desempenho?** O engajamento em sistemas gamificados depende de *feedback* instantâneo. Se o aplicativo demorar para mostrar que o usuário ganhou XP ou subiu de nível, a sensação de recompensa é perdida.
* **Por que Escalabilidade?** Com a funcionalidade de compartilhamento nas redes sociais (US14) e eventos de missões temáticas (US11), o aplicativo pode sofrer picos de acesso repentinos, especialmente no final do mês quando os usuários correm para subir no Ranking.
* **Por que Segurança?** Estamos lidando com dados pessoais (e-mails) e arquivos de mídia (fotos das missões). Vazamentos geram processos sob a LGPD e destroem a confiança da comunidade.
* **Por que Usabilidade?** O público-alvo utilizará o app na rua (ex: no momento em que está separando o lixo ou usando transporte público). Telas complexas em celulares afastarão os usuários.
* **Por que Disponibilidade?** Se o sistema estiver fora do ar exatamente no momento em que o usuário for registrar sua ação sustentável, ele perderá a motivação (e o XP), gerando frustração com a plataforma.

---

## 3️⃣ Impacto Arquitetural
Para atender a esses NFRs, a arquitetura do EcoQuest precisou das seguintes adaptações técnicas:

* **Armazenamento em Nuvem (Cloud Storage):** Para não sobrecarregar nosso banco de dados principal e garantir o **NFR01**, as fotos enviadas pelos usuários não serão salvas no banco, mas sim em um serviço de armazenamento de objetos (ex: Amazon S3 ou Firebase Storage). O banco guardará apenas o link da imagem.
* **Balanceamento de Carga (Load Balancer):** Para garantir o **NFR02** e **NFR05**, o back-end será hospedado em contêineres (ex: Docker) atrás de um *Load Balancer*. Se o tráfego aumentar, novas instâncias da API serão "clonadas" automaticamente (Auto-scaling) para dividir o tráfego.
* **Uso de Cache (Redis):** O *Ranking Global* (Leaderboard) muda a todo momento e é muito acessado. Fazer uma busca no banco de dados toda vez que alguém abre o ranking destruiria o desempenho. Usaremos uma camada de cache na memória (Redis) que atualiza o ranking a cada 5 minutos, poupando o banco de dados.

---

## 4️⃣ Estratégias de Mitigação
Para garantir que essas decisões realmente funcionem na prática, o grupo adotará as seguintes estratégias:

* **Testes de Carga (Stress Testing):** Utilizaremos a ferramenta **K6** ou **Apache JMeter** antes do lançamento oficial para simular 1.000 usuários enviando fotos e pedindo dados da API ao mesmo tempo, validando a escalabilidade.
* **Monitoramento e Alertas:** Implementaremos o **Sentry** para capturar erros no código em tempo real e o **UptimeRobot** para pingar o servidor a cada 5 minutos. Se o sistema cair (quebrando a disponibilidade), os desenvolvedores receberão um alerta no e-mail/Discord.
* **Tratamento de Falhas (Graceful Degradation):** Se o serviço de mapas falhar por algum motivo, o aplicativo não deve travar. A interface deve ocultar o mapa educadamente e permitir que o usuário continue fazendo suas missões de texto normalmente.
