# 🔄 Gestão de Mudança - EcoQuest

## 1️⃣ Descrição da Mudança
**Tipo de Mudança:** Alteração de Regra de Negócio e Inclusão de Nova Funcionalidade.
**Descrição:** Durante a validação do protótipo da Sprint 1, a equipe (e os stakeholders) percebeu uma falha grave na regra de negócio da gamificação: os usuários poderiam simplesmente clicar em "Concluir Missão" repetidas vezes sem realizar a ação sustentável, apenas para ganhar pontos de experiência (XP) e subir no ranking.
**A Mudança:** Para garantir a integridade da plataforma, tornou-se obrigatório que o usuário faça o upload de uma foto comprovando a ação (ex: foto da lixeira com o lixo separado) no momento de concluir a missão.

---

## 2️⃣ Impacto no Backlog
A introdução do envio de fotos causou uma reação em cadeia no nosso *Product Backlog*:

* **Histórias Modificadas:**
  * `US04 - [Gamificação] Concluir missão e ganhar XP`: Foi alterada para incluir o requisito de upload de imagem antes da liberação do XP.
* **Histórias Adicionadas:**
  * `US16 - [Admin] Painel de moderação de fotos de missões concluídas`: Adicionada para que os administradores possam rejeitar fotos falsas e remover os pontos do infrator.
* **Impacto em tarefas já planejadas:**
  * O desenvolvimento do *Ranking Global* (US06) e do sistema de *Medalhas* (US07) precisará ser adiado, pois a equipe terá que focar primeiro em implementar o armazenamento de imagens (novo banco de dados/AWS S3).

---

## 3️⃣ Decisão de Priorização
O grupo decidiu elevar a alteração da **US04** e a criação da **US16** para **Prioridade Alta (P0)**. 
Como consequência, reorganizamos o backlog da seguinte forma:
1. As funcionalidades de upload e validação de fotos entrarão imediatamente na **Sprint 2**.
2. Funcionalidades menos críticas que estavam na fila, como a seção de "Dicas e Artigos" (US09) e o "Compartilhamento nas Redes Sociais" (US14), foram rebaixadas para **Prioridade Baixa (P2)** e movidas para o final do Backlog. 
Não faz sentido investir tempo em redes sociais se o núcleo do jogo (ganhar XP de forma justa) estiver quebrado.

---

## 4️⃣ Justificativa Técnica
A decisão do grupo baseia-se nos seguintes pilares técnicos e de produto:

* **Valor para o usuário:** Um jogo gamificado perde todo o sentido e engajamento se os usuários perceberem que os líderes do ranking estão trapaceando. A mudança garante um ambiente justo e competitivo.
* **Complexidade de implementação:** A mudança possui complexidade **Alta**. Exigirá a reestruturação do banco de dados para salvar URLs de imagens, configuração de um serviço de Storage em nuvem (ex: AWS S3 ou Firebase Storage) e tratamento de erros de upload no front-end.
* **Dependências técnicas:** A evolução de Nível (US05) agora é totalmente dependente do sucesso do fluxo de upload de fotos (US04 revisada).
* **Impacto no cronograma do projeto:** A equipe estima que essa mudança adicionará cerca de 8 *Story Points* de esforço não planejado. Isso empurrará a entrega do mapa interativo (US08) para uma Sprint extra no final do semestre.
