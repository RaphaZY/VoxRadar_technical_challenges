# VoxRadar · Desafios Técnicos

> Repositório oficial de **desafios técnicos** da VoxRadar, usados para **avaliar e alinhar** pessoas desenvolvedoras: em contratação, em avaliações de times internos, em promoções e no nivelamento técnico entre devs e squads.

Os desafios aqui **não são exercícios artificiais**. São recortes de **problemas reais** que enfrentamos no dia a dia: coleta de dados, monitoramento de redes sociais, engenharia de dados e automação. O objetivo é avaliar como você pensa, estrutura e entrega uma solução de engenharia, não apenas se o código "roda".

---

## 🚀 Comece por aqui (o fluxo em 6 passos)

1. **Faça um _fork_** deste repositório para a sua conta.
2. No seu fork, **selecione a branch do desafio** (ex.: `challenge/kwai`). Cada desafio vive na sua própria branch `challenge/<slug>`.
3. **Escolha o seu nível** dentro do desafio: `0`, `1`, `2` ou `3`. Cada nível cobra requisitos diferentes (ver a pasta `niveis/` na branch do desafio).
4. **Crie a sua branch de solução** a partir da branch do desafio, seguindo a convenção de nome abaixo (o nome carrega o desafio e o nível, para sabermos o que você está resolvendo).
5. **Desenvolva** cumprindo os requisitos e o _checklist_ do nível escolhido.
6. **Abra um Pull Request** do seu fork para a branch do desafio neste repositório e preencha o template.

### Convenção da branch de solução

```
solution/<slug-do-desafio>-nivel<N>-<seu-usuario>
```

Exemplos:

```
solution/kwai-nivel0-imnascimento
solution/kwai-nivel1-maria-silva
solution/kwai-nivel2-joao99
```

Assim, à medida que novos desafios e participantes entram, conseguimos identificar **de imediato** qual desafio, qual nível e quem está resolvendo.

---

## 🗂️ Como o repositório é organizado

| Onde | Conteúdo |
|---|---|
| Branch `main` | Este README (o processo), os _templates_ (PR e novos desafios) e as diretrizes gerais. |
| Branch `challenge/<slug>` | Um desafio completo e autocontido. |

Cada branch de desafio segue esta estrutura:

```
challenge/<slug>/
├── README.md            # índice do desafio: contexto, o que há em cada arquivo, como escolher o nível
├── niveis/
│   ├── nivel-0.md       # requisitos e avaliação do Nível 0 (Iniciante)
│   ├── nivel-1.md       # requisitos e avaliação do Nível 1
│   ├── nivel-2.md       # requisitos e avaliação do Nível 2
│   └── nivel-3.md       # requisitos e avaliação do Nível 3 (Avançado)
├── docs/
│   ├── schemas.md       # schemas de saída compartilhados por todos os níveis
│   └── avaliacao.md     # como pontuamos e a régua geral de avaliação
├── pyproject.toml       # gestão de dependências com Poetry (Nível 1+)
├── requirements.txt     # alternativa simples (Nível 0)
└── .env.example
```

**Convenção de branch de desafio:** `challenge/<slug>` (ex.: `challenge/kwai`).

---

## 🎯 Desafios disponíveis

| Desafio | Branch | Área | Níveis | Status |
|---|---|---|---|---|
| **Kwai: coleta de postagens, engajamento e comentários** | [`challenge/kwai`](../../tree/challenge/kwai) | Web Scraping / Coleta de dados | 0 · 1 · 2 · 3 | ✅ Aberto |

> Novos desafios serão adicionados como novas branches `challenge/*` e listados aqui.

---

## 📈 Os quatro níveis

Todo desafio é oferecido em quatro níveis numerados. Cada nível **inclui tudo do anterior** e adiciona novas exigências. Você escolhe **um** nível para resolver (o combinado com o time responsável).

| Nível | O que se espera, em resumo |
|---|---|
| **Nível 0 · Iniciante** | Fazer as funcionalidades funcionarem com código organizado e legível. |
| **Nível 1** | Engenharia de software: Poetry, testes, tipagem, tratamento de erros, CLI robusta. |
| **Nível 2** | Arquitetura, resiliência, persistência, observabilidade e conteinerização. |
| **Nível 3 · Avançado** | Escala, concorrência, design documentado e decisões de infraestrutura. |

Os requisitos exatos e a régua de avaliação de cada nível estão nos arquivos `niveis/*.md` da branch do desafio.

---

## 📤 Como entregar

Fluxo **Fork + Pull Request**:

```bash
# no seu fork, a partir da branch do desafio
git checkout challenge/<slug>                                # ex.: challenge/kwai
git checkout -b solution/<slug>-nivel<N>-<seu-usuario>       # ex.: solution/kwai-nivel1-imnascimento
# ... desenvolva ...
git push origin solution/<slug>-nivel<N>-<seu-usuario>
```

Depois, abra um **Pull Request** apontando:

- **base:** `challenge/<slug>` (deste repositório)
- **compare:** `solution/<slug>-nivel<N>-<seu-usuario>` (do seu fork)

Preencha o **template do PR**: marque o _checklist_ do seu nível e descreva suas decisões.

> Prefira um PR bem documentado a um README gigante no seu código. Queremos entender **as suas decisões**.

---

## ✅ O que avaliamos

Os pesos exatos variam por nível (ver `niveis/*.md` e `docs/avaliacao.md`), mas em geral olhamos para:

- **Corretude:** a solução resolve o que foi pedido?
- **Qualidade de código:** legibilidade, organização, nomes, coesão.
- **Decisões de engenharia:** trade-offs conscientes e bem justificados.
- **Robustez:** tratamento de erros, casos de borda, resiliência.
- **Documentação:** como rodar, o que foi feito e o que ficou de fora.
- **Testes:** conforme o nível do desafio.
- **Comunicação:** clareza no PR e nos commits.

Não valorizamos "over-engineering". Uma solução **simples, correta e bem explicada** no nível escolhido vale mais do que uma complexa e confusa.

---

## 🧭 Diretrizes gerais

- **Stack:** Python é a linguagem **preferencial** da VoxRadar. Você pode usar outra stack, mas **justifique a escolha** no PR.
- **Dependências:** a partir do Nível 1 usamos **Poetry** (`pyproject.toml`). O `requirements.txt` é aceito no Nível 0.
- **Segredos:** **nunca** commite credenciais, tokens ou cookies. Use `.env` e forneça um `.env.example`.
- **Ética e legalidade:** respeite os _Termos de Uso_ das plataformas, os _rate limits_ e a legislação aplicável (ex.: LGPD). Trate os dados coletados apenas para os fins do desafio.
- **Prazo:** combinado com o time responsável no momento do convite.
- **Dúvidas:** abra uma _issue_ ou fale com o time responsável pela avaliação.

---

## 🎯 Propósito e uso

Estes desafios são uma ferramenta de **avaliação e alinhamento técnico** da VoxRadar. Não servem apenas para contratação ou promoção. Usamos em vários contextos:

- **Contratação:** avaliar candidatos de forma prática e justa.
- **Times internos:** calibrar e acompanhar o nível técnico de quem já está na casa.
- **Promoção:** evidenciar prontidão para o próximo nível.
- **Alinhamento:** nivelar expectativas técnicas entre devs e squads, com uma régua comum.

### Uso do código

Ao enviar uma solução, você concede à VoxRadar o direito de **usar, adaptar e manter** o código entregue para fins internos: avaliação, referência técnica, evolução dos próprios desafios e apoio ao trabalho dos times. A **autoria continua sua** e o crédito é preservado, mas a VoxRadar pode aproveitar o código produzido, ainda que tenha sido escrito por você durante o desafio.
