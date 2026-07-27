# Kwai · Nível 🔵 Pleno

> **Foco:** boas práticas de engenharia de software em cima de uma coleta correta.
> **Pré-requisito:** tudo do nível [Júnior](junior.md).
> Leia antes o [problema comum](../README.md#-o-problema-comum-a-todos-os-níveis) e os [schemas](../docs/schemas.md).

---

## O que este nível cobra (além do Júnior)

### Gestão de dependências com Poetry
- Projeto gerenciado por **Poetry** (`pyproject.toml` + `poetry.lock` commitado).
- `requirements.txt` deixa de ser o mecanismo principal. Execução documentada via `poetry install` / `poetry run`.

### Qualidade de código
- **Type hints** em todo o código público, verificados com **mypy** ou **pyright** (sem erros).
- **Lint e formatação** com **ruff** (e/ou black). Sem violações no CI local.
- **Separação de responsabilidades:** cliente de acesso (HTTP/navegador), parsing, modelos e CLI em módulos distintos.
- **Modelos de dados** validando o contrato de saída (ex.: `pydantic` ou `dataclasses`).

### Robustez
- **CLI robusta** (ex.: `typer`/`click`/`argparse`) com `--help`, validação de argumentos e códigos de saída coerentes.
- **Rate limiting configurável** e **retry com backoff** em falhas transitórias.
- **Paginação completa** (não apenas a primeira página) e **deduplicação** de resultados.
- **Logging** com níveis (info/erro), em vez de `print`.
- Configuração via **variáveis de ambiente** tipadas (ex.: `pydantic-settings`).

### Testes
- **Testes automatizados** com `pytest` cobrindo o parsing e a lógica principal (idealmente com respostas mockadas, sem depender da rede).
- Instruções para rodar os testes no README.

---

## Entregáveis

- [ ] Tudo do Júnior.
- [ ] `pyproject.toml` + `poetry.lock`.
- [ ] Suíte de testes executável (`poetry run pytest`).
- [ ] Configuração de lint/type-check (ex.: `ruff`, `mypy`) declarada no `pyproject.toml`.
- [ ] `samples/` com saídas validadas contra os schemas.

---

## Checklist de entrega

Copie para o seu PR (inclui os itens do Júnior).

**Engenharia**
- [ ] Projeto gerenciado com Poetry (`poetry.lock` commitado)
- [ ] Type hints + mypy/pyright sem erros
- [ ] Lint/format com ruff (ou black) sem violações
- [ ] Módulos separados (client / parser / models / cli)
- [ ] Modelos validando o contrato de saída

**Robustez**
- [ ] CLI com `--help` e validação de argumentos
- [ ] Rate limit configurável + retry com backoff
- [ ] Paginação completa + deduplicação
- [ ] Logging estruturado (sem `print`)
- [ ] Configuração via env tipada

**Testes**
- [ ] `pytest` cobrindo parsing e lógica principal
- [ ] Testes não dependem de rede (mocks/fixtures)
- [ ] README explica como rodar os testes

---

## Critérios de avaliação

| Critério | Peso |
|---|---|
| **Corretude** das 3 funcionalidades | 30% |
| **Qualidade de código** (tipagem, lint, modularização) | 25% |
| **Robustez** (rate limit, retry, paginação, dedup) | 20% |
| **Testes** (cobertura útil, independência de rede) | 15% |
| **Documentação e tooling** (Poetry, README, PR) | 10% |
| **Bônus** (cobertura alta, CI local, validação de schema automatizada) | +10% extra |

---

## O que NÃO é exigido neste nível

- Persistência em banco de dados e migrações.
- Dockerização e orquestração.
- Concorrência/async em larga escala, observabilidade com métricas.
- Coleta distribuída, filas, agendamento.

Isso é escopo **Sênior** e **Especialista**.
