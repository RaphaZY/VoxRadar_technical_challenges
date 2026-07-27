# Desafio Técnico · Kwai — Coleta de Postagens, Engajamento e Comentários

> **Área:** Web Scraping / Coleta de dados · **Nível:** Júnior/Pleno · **Branch:** `challenge/kwai`
>
> ℹ️ O processo geral (fork, entrega, avaliação) está no [README da `main`](../../tree/main). Esta branch descreve **apenas este desafio**.

---

## 🎯 Contexto

A VoxRadar monitora redes sociais para entender **o que está sendo dito** sobre marcas, temas e pessoas. Para isso, precisamos de coletores confiáveis que transformem o conteúdo público de uma plataforma em **dados estruturados** — prontos para análise de engajamento, sentimento e alcance.

O [Kwai](https://www.kwai.com/) é uma dessas plataformas. Neste desafio você vai construir um **coletor de dados do Kwai** que resolve três necessidades reais do nosso time de dados.

---

## 🧩 Objetivo

Construir uma ferramenta que colete conteúdo **público** do Kwai em três modos, exportando o resultado em um formato **estruturado e consistente** (JSON).

---

## 📋 Requisitos funcionais

Sua solução deve implementar as **três funcionalidades** abaixo. Cada uma recebe uma entrada e produz uma saída estruturada.

### 1. Busca por palavra-chave
> **Dado** uma palavra-chave, **coletar postagens** relacionadas, contendo **link, texto e engajamento**.

- **Entrada:** uma palavra-chave (ex.: `"eleições"`) e, opcionalmente, um limite de resultados.
- **Saída:** lista de postagens no schema [`Postagem`](#postagem).

### 2. Postagens de um usuário
> **Dado** a conta de um usuário, **coletar todas as postagens** daquele usuário.

- **Entrada:** identificador do usuário (username, ID ou URL do perfil) e, opcionalmente, um limite.
- **Saída:** lista de postagens no schema [`Postagem`](#postagem).

### 3. Comentários de uma postagem
> **Dado** o link de uma postagem, **coletar os comentários** dessa postagem.

- **Entrada:** URL de uma postagem e, opcionalmente, um limite.
- **Saída:** lista de comentários no schema [`Comentario`](#comentario).

---

## 🧾 Schemas de saída

A saída deve ser **JSON** (arquivo `.json` ou `.jsonl`). Use os campos abaixo como referência; se algum não estiver disponível, use `null` e **documente** o motivo. Campos extras são bem-vindos.

<a name="postagem"></a>
### `Postagem`
```json
{
  "id": "string | null",
  "url": "https://www.kwai.com/...",
  "autor": {
    "usuario": "string | null",
    "id": "string | null",
    "url_perfil": "string | null"
  },
  "texto": "string | null",
  "data_publicacao": "ISO-8601 | null",
  "engajamento": {
    "curtidas": 0,
    "comentarios": 0,
    "compartilhamentos": 0,
    "visualizacoes": 0
  },
  "coletado_em": "ISO-8601"
}
```

<a name="comentario"></a>
### `Comentario`
```json
{
  "id": "string | null",
  "postagem_url": "https://www.kwai.com/...",
  "autor": {
    "usuario": "string | null",
    "id": "string | null"
  },
  "texto": "string",
  "curtidas": 0,
  "data": "ISO-8601 | null",
  "coletado_em": "ISO-8601"
}
```

---

## 🛠️ Requisitos técnicos

- **Linguagem:** Python é **preferencial**. Outra stack é aceita, mas justifique no PR.
- **Interface de uso:** uma **CLI** ou scripts claros, com as três funcionalidades acionáveis por parâmetro. Exemplos:
  ```bash
  python -m kwai_collector busca --keyword "eleicoes" --limit 50 --out out/busca.json
  python -m kwai_collector usuario --user "@perfil" --limit 100 --out out/usuario.json
  python -m kwai_collector comentarios --url "https://www.kwai.com/@perfil/video/XXXX" --out out/comentarios.json
  ```
- **Saída estruturada:** JSON conforme os [schemas](#-schemas-de-saída).
- **Configuração:** parâmetros e segredos via `.env`/argumentos. **Nada de credenciais no código.** Forneça um `.env.example`.
- **Robustez:** tratamento de erros (rede, HTTP, conteúdo ausente), _timeout_ e **respeito a _rate limits_** (delays/backoff).
- **Logs:** mensagens de progresso e de erro compreensíveis.
- **Documentação:** README de execução (instalação, como rodar cada modo, exemplos).

> 💡 **Sobre a abordagem:** o Kwai carrega conteúdo dinamicamente. Você pode optar por consumir os _endpoints_ que a página usa (requests) ou por automação de navegador (Playwright/Selenium). **Ambas são válidas** — descreva sua escolha e os _trade-offs_ no PR.

---

## 📦 Entregáveis

- [ ] Código-fonte da ferramenta com as 3 funcionalidades.
- [ ] `README.md` com instruções de instalação e execução.
- [ ] `requirements.txt` (ou equivalente) com as dependências.
- [ ] `.env.example` (se houver configuração/segredos).
- [ ] **Amostras de saída** em `samples/` — um arquivo por funcionalidade.

---

## 🧱 Estrutura sugerida

> Sugestão, **não obrigatória**. Organize como fizer sentido para você.

```
kwai_collector/
├── __init__.py
├── __main__.py          # CLI
├── busca.py             # func. 1 — busca por palavra-chave
├── usuario.py           # func. 2 — postagens de um usuário
├── comentarios.py       # func. 3 — comentários de uma postagem
├── models.py            # schemas (dataclasses/pydantic)
├── client.py            # http/navegador, rate limit, retry
└── utils.py
samples/
├── busca.json
├── usuario.json
└── comentarios.json
tests/                   # opcional (bônus)
.env.example
requirements.txt
README.md
```

---

## ✅ Checklist de entrega

Copie para o seu Pull Request e marque conforme concluir:

**Funcionalidades**
- [ ] 1 — Busca por palavra-chave (link, texto, engajamento)
- [ ] 2 — Todas as postagens de um usuário
- [ ] 3 — Comentários de uma postagem por link

**Qualidade e execução**
- [ ] Saída em JSON seguindo os schemas (`Postagem` / `Comentario`)
- [ ] `README.md` explica como instalar e rodar cada modo
- [ ] `requirements.txt` (ou equivalente) presente
- [ ] `.env.example` fornecido e **nenhum segredo commitado**
- [ ] Amostras de saída em `samples/`
- [ ] Tratamento de erros e respeito a _rate limit_
- [ ] PR descreve a abordagem, decisões e limitações

**Bônus (não obrigatório)**
- [ ] Testes automatizados
- [ ] Paginação completa / deduplicação de resultados
- [ ] Persistência em banco de dados
- [ ] Dockerfile / execução conteinerizada
- [ ] Retry com _backoff_ exponencial

---

## 📊 Critérios de avaliação

| Critério | Peso |
|---|---|
| **Corretude** — as 3 funcionalidades coletam os dados pedidos | 40% |
| **Qualidade de código** — organização, legibilidade, nomes | 20% |
| **Robustez** — erros, casos de borda, rate limit | 15% |
| **Documentação** — README, execução e decisões no PR | 15% |
| **Consistência da saída** — aderência aos schemas | 10% |
| **Bônus** — testes, persistência, Docker, etc. | +10% (extra) |

> Buscamos uma solução **simples, correta e bem explicada**. Não é necessário resolver escala industrial nem evasão avançada de bloqueios — isso é escopo de níveis mais sêniores.

---

## 📤 Como entregar

Fluxo **Fork + Pull Request** (detalhado no [README da `main`](../../tree/main)):

```bash
# no seu fork
git checkout challenge/kwai
git checkout -b solution/<seu-usuario>
# ... desenvolva ...
git push origin solution/<seu-usuario>
```
Abra o PR com **base:** `challenge/kwai` e **compare:** `solution/<seu-usuario>`, preenchendo o template.

---

## ⚠️ Regras e observações

- Colete **apenas conteúdo público**. Não tente acessar áreas privadas ou burlar autenticação.
- Respeite os **Termos de Uso** do Kwai, os _rate limits_ e a **LGPD**. Use os dados exclusivamente para os fins deste desafio.
- Prefira **contas de teste** e palavras-chave neutras nas suas amostras.
- Se a coleta completa não for viável no tempo disponível, **entregue o que funcionar** e explique no PR o que faria a seguir. **Valorizamos honestidade técnica.**

Boa sorte! 🚀
