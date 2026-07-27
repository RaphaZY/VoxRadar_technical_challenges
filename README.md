# VoxRadar · Desafios Técnicos

> Repositório oficial de **desafios técnicos** da VoxRadar para avaliação de pessoas desenvolvedoras.

Os desafios aqui **não são exercícios artificiais**: são recortes de **problemas reais** que enfrentamos no dia a dia (coleta de dados, monitoramento de redes sociais, engenharia de dados e automação). O objetivo é avaliar como você pensa, estrutura e entrega uma solução de engenharia — não apenas se o código "roda".

---

## 📌 Como funciona

1. **Escolha o desafio** na tabela de [Desafios disponíveis](#-desafios-disponíveis).
2. **Faça um _fork_** deste repositório.
3. No seu fork, faça o **checkout da branch do desafio** (ex.: `challenge/kwai`).
4. **Resolva o desafio** seguindo os requisitos e o _checklist_ descritos na branch.
5. **Abra um Pull Request** do seu fork para a branch original do desafio (ver [Como entregar](#-como-entregar)).

Cada desafio é **autocontido na sua branch**: lá você encontra o contexto, os requisitos funcionais e técnicos, o _checklist_ de entrega e os critérios de avaliação.

---

## 🗂️ Estrutura do repositório

| Branch | Conteúdo |
|---|---|
| `main` | Este README, o processo, e os _templates_ (PR e novos desafios). |
| `challenge/<slug>` | Um desafio completo e autocontido (contexto + requisitos + checklist + critérios). |

**Convenção de branches de desafio:** `challenge/<slug>` — ex.: `challenge/kwai`.

**Convenção da branch de entrega (candidato):** a partir da branch do desafio, crie `solution/<seu-usuario>` no seu fork.

---

## 🎯 Desafios disponíveis

| Desafio | Branch | Área | Nível | Status |
|---|---|---|---|---|
| **Kwai — Coleta de postagens, engajamento e comentários** | [`challenge/kwai`](../../tree/challenge/kwai) | Web Scraping / Coleta de dados | Júnior/Pleno | ✅ Aberto |

> Novos desafios serão adicionados como novas branches `challenge/*` e listados aqui.

---

## 📤 Como entregar

Adotamos o fluxo **Fork + Pull Request**:

1. **Fork** deste repositório para a sua conta.
2. No seu fork:
   ```bash
   git checkout challenge/<slug>          # ex.: challenge/kwai
   git checkout -b solution/<seu-usuario> # sua branch de solução
   ```
3. Desenvolva, commitando com mensagens claras e um histórico legível.
4. Faça _push_ da sua branch `solution/*` para o **seu fork**.
5. Abra um **Pull Request** apontando:
   - **base:** `challenge/<slug>` (deste repositório)
   - **compare:** `solution/<seu-usuario>` (do seu fork)
6. Preencha o **template do PR** (marque o _checklist_ de entrega e descreva suas decisões).

> Prefira um PR bem documentado a um README gigante no seu código. Queremos entender **suas decisões**.

---

## ✅ O que avaliamos

Os pesos exatos são detalhados em cada desafio, mas em geral olhamos para:

- **Corretude** — a solução resolve o que foi pedido?
- **Qualidade de código** — legibilidade, organização, nomes, coesão.
- **Decisões de engenharia** — trade-offs conscientes e bem justificados.
- **Robustez** — tratamento de erros, casos de borda, resiliência.
- **Documentação** — como rodar, o que foi feito e o que ficou de fora.
- **Testes** — quando aplicável ao nível do desafio.
- **Comunicação** — clareza no PR e nos commits.

Não valorizamos "over-engineering". Uma solução **simples, correta e bem explicada** vale mais do que uma complexa e confusa.

---

## 🧭 Diretrizes gerais

- **Stack:** Python é a linguagem **preferencial** da VoxRadar. Você pode usar outra stack, mas **justifique a escolha** no PR.
- **Dependências:** liste todas (ex.: `requirements.txt`, `pyproject.toml`) e explique como rodar.
- **Segredos:** **nunca** commite credenciais, tokens ou cookies. Use `.env` e forneça um `.env.example`.
- **Ética e legalidade:** respeite os _Termos de Uso_ das plataformas, _rate limits_ e a legislação aplicável (ex.: LGPD). Trate os dados coletados apenas para os fins do desafio.
- **Prazo:** combinado com o time de recrutamento no momento do convite.
- **Dúvidas:** abra uma _issue_ ou fale com o contato do processo seletivo.

---

## 📄 Licença

Uso restrito ao processo seletivo da VoxRadar. As soluções enviadas permanecem de autoria do candidato; a VoxRadar as utiliza exclusivamente para fins de avaliação.
