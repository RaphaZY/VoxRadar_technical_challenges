# Desafio Técnico · Kwai

> **Área:** Web Scraping / Coleta de dados · **Branch:** `challenge/kwai` · **Níveis:** Júnior · Pleno · Sênior · Especialista
>
> ℹ️ O processo geral (fork, entrega e avaliação) está no [README da `main`](../../tree/main). Esta branch descreve **apenas este desafio** e **este README é o índice**: ele explica o problema, o que há em cada arquivo e como escolher o seu nível.

---

## 🎯 Contexto

A VoxRadar monitora redes sociais para entender **o que está sendo dito** sobre marcas, temas e pessoas. Para isso precisamos de coletores confiáveis que transformem o conteúdo público de uma plataforma em **dados estruturados**, prontos para análise de engajamento, sentimento e alcance.

O [Kwai](https://www.kwai.com/) é uma dessas plataformas. Neste desafio você vai construir um **coletor de dados do Kwai**.

---

## 🧩 O problema (comum a todos os níveis)

Independentemente do nível, a sua solução precisa resolver **três necessidades reais** do time de dados. Cada funcionalidade recebe uma entrada e produz uma saída estruturada em JSON (schemas em [`docs/schemas.md`](docs/schemas.md)).

| # | Funcionalidade | Entrada | Saída |
|---|---|---|---|
| 1 | **Busca por palavra-chave** | uma palavra-chave | postagens relacionadas com **link, texto e engajamento** (`Postagem`) |
| 2 | **Postagens de um usuário** | a conta/perfil do usuário | **todas as postagens** daquele usuário (`Postagem`) |
| 3 | **Comentários de uma postagem** | o link de uma postagem | os **comentários** daquela postagem (`Comentario`) |

O **que** coletar é igual para todos. O **como** (engenharia, robustez, escala) é o que muda conforme o nível.

---

## 📈 Escolha o seu nível

Cada nível **inclui tudo do anterior** e adiciona novas exigências. Resolva **apenas o nível** combinado com o time de recrutamento.

| Nível | Foco | Requisitos e avaliação |
|---|---|---|
| 🟢 **Júnior** | Fazer as 3 funcionalidades funcionarem com código limpo. | [`niveis/junior.md`](niveis/junior.md) |
| 🔵 **Pleno** | Engenharia de software: Poetry, testes, tipagem, CLI robusta. | [`niveis/pleno.md`](niveis/pleno.md) |
| 🟣 **Sênior** | Arquitetura, resiliência, persistência, observabilidade, Docker. | [`niveis/senior.md`](niveis/senior.md) |
| 🔴 **Especialista** | Escala, concorrência, design documentado, infraestrutura. | [`niveis/especialista.md`](niveis/especialista.md) |

Leia também [`docs/avaliacao.md`](docs/avaliacao.md) para entender **como pontuamos**.

---

## 🗺️ O que há nesta branch

```
challenge/kwai/
├── README.md              # você está aqui: índice do desafio
├── niveis/
│   ├── junior.md          # requisitos + checklist + critérios do nível Júnior
│   ├── pleno.md           # idem, nível Pleno
│   ├── senior.md          # idem, nível Sênior
│   └── especialista.md    # idem, nível Especialista
├── docs/
│   ├── schemas.md         # schemas de saída (Postagem, Comentario)
│   └── avaliacao.md       # método de pontuação e régua geral
├── pyproject.toml         # gestão de dependências com Poetry (Pleno+)
├── requirements.txt       # alternativa simples (Júnior)
├── .env.example           # variáveis de configuração de exemplo
└── .github/
    └── PULL_REQUEST_TEMPLATE.md
```

---

## 💡 Sobre a abordagem técnica

O Kwai carrega conteúdo **dinamicamente**. Você pode:

- consumir os _endpoints_ HTTP que a própria página usa (com `requests`/`httpx`), ou
- automatizar um navegador (`Playwright`/`Selenium`).

**Ambas são válidas.** O que avaliamos é a qualidade da decisão e da execução no seu nível. **Descreva a escolha e os trade-offs no PR.**

---

## 📤 Como entregar (resumo)

Fluxo completo no [README da `main`](../../tree/main). Em resumo:

```bash
git checkout challenge/kwai
git checkout -b solution/kwai-<nivel>-<seu-usuario>   # ex.: solution/kwai-pleno-imnascimento
# ... desenvolva ...
git push origin solution/kwai-<nivel>-<seu-usuario>
```

Abra o PR com **base:** `challenge/kwai` e **compare:** a sua branch de solução, preenchendo o template. O nome da branch **deve conter o desafio e o nível**.

---

## ⚠️ Regras e ética

- Colete **apenas conteúdo público**. Não tente acessar áreas privadas nem burlar autenticação.
- Respeite os **Termos de Uso** do Kwai, os _rate limits_ e a **LGPD**. Use os dados exclusivamente para os fins deste desafio.
- Prefira **contas de teste** e palavras-chave neutras nas amostras.
- Se a coleta completa não for viável no tempo disponível, **entregue o que funcionar** e explique no PR o que faria a seguir. **Valorizamos honestidade técnica.**

Boa sorte. 🚀
