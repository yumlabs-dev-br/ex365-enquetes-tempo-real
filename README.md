# Sistema de Enquetes em Tempo Real

API REST + WebSocket para enquetes ao vivo, com resultados atualizados em tempo real.

> 📦 **Template de trabalho em grupo da WebForge.** Clique em **Use this template** (botão verde acima) para criar o repositório do seu grupo.

## 🚀 Como rodar

```bash
npm install
npm start        # inicia em http://localhost:3000
```

O projeto já sobe com uma rota raiz `GET /`. Todo o resto é com o grupo.

## 📋 Requisitos

- **Auth** — login JWT; apenas autenticados criam enquetes.
- **Enquetes** — `POST /enquetes` (pergunta + 2 a 6 opções + encerramento), listagem com filtro abertas/encerradas, detalhe e encerramento manual (só o criador).
- **Votação** — `POST /enquetes/:id/votar` impedindo voto duplo; `GET /enquetes/:id/resultados` com contagem e percentual.
- **Tempo real** — canal WebSocket por enquete que transmite os resultados a cada voto.

> Persistam os dados (arquivo JSON ou SQLite) — os testes podem reiniciar o servidor entre etapas.

## ✅ O que os testes de correção validam

Os testes automáticos sobem o **seu** servidor e fazem requisições HTTP reais contra a API. Eles verificam **comportamento** (status HTTP e corpo das respostas), não a estrutura interna do código — organizem os arquivos como preferirem. Para ser aprovado, a API precisa:

- [ ] `GET /` responde **200**.
- [ ] `POST /enquetes` exige entre **2 e 6 opções** (fora disso → **400**).
- [ ] `POST /enquetes/:id/votar` registra o voto e atualiza a contagem.
- [ ] Votar **duas vezes** na mesma enquete (mesmo usuário/sessão) é bloqueado (**409**).
- [ ] Votar em enquete **encerrada** responde **409**.
- [ ] `GET /enquetes/:id/resultados` retorna percentuais que somam ~100%.
- [ ] Ao votar, os clientes conectados ao **WebSocket** da enquete recebem os resultados atualizados _(a parte WebSocket é verificada pelo professor na revisão; o validador automático cobre a parte REST)_.

## 👥 Trabalho em equipe (obrigatório)

Este é um ambiente o mais próximo possível do mercado:

- O repositório deve pertencer a **um** dos membros do grupo. Os **demais membros entram como colaboradores** em `Settings → Collaborators → Add people`.
- Cada membro trabalha em sua **própria branch** e abre **Pull Request** para a `main`, pedindo revisão de outro colega.
- A WebForge mede as **contribuições individuais** de cada membro (commits, linhas adicionadas e removidas) direto do histórico do GitHub. Distribuam bem o trabalho.

## 🧱 Stack

- Node.js + Express (CommonJS)
