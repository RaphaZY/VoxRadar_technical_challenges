# Kwai · Nível 2 🟣

> **Foco:** arquitetura, resiliência, persistência e operação. Um coletor que você colocaria em produção.
> **Pré-requisito:** tudo do [Nível 1](nivel-1.md).
> Leia antes o [problema comum](../README.md#-o-problema-comum-a-todos-os-níveis) e os [schemas](../docs/schemas.md).

---

## O que este nível cobra (além do Nível 1)

### Arquitetura
- **Camadas bem definidas:** coleta (acesso à plataforma), transformação/normalização, domínio (modelos) e persistência, com dependências apontando para dentro.
- **Extensibilidade:** ficar claro como adicionar uma nova fonte ou um novo tipo de coleta sem reescrever o núcleo.
- **Documento de arquitetura:** um `ARCHITECTURE.md` (ou ADRs) com diagrama e as principais decisões e trade-offs.

### Persistência
- **Banco de dados** (SQLite/Postgres) com **modelo de dados** para postagens, autores e comentários.
- **Migrações** versionadas (ex.: Alembic).
- **Idempotência:** reexecutar a coleta não duplica registros (upsert por chave natural).

### Resiliência
- **Retry com backoff exponencial + jitter**, **timeouts** e tratamento explícito de erros por tipo.
- **Circuit breaker** ou equivalente para degradar com elegância sob falha contínua.
- **Tratamento de bloqueios/anti-bot dentro da ética:** detecção de resposta bloqueada, recuo, e mensagem clara (sem burlar autenticação).

### Concorrência
- Coleta **concorrente controlada** (async ou threads) com limite de concorrência e respeito ao rate limit global.

### Observabilidade
- **Logging estruturado** (JSON) e **métricas de coleta**: itens coletados, falhas, itens por segundo, páginas percorridas.
- Modo de execução que reporta um **resumo da coleta** ao final.

### Empacotamento
- **Dockerfile** e **docker-compose** para subir a aplicação (e o banco).
- Configuração **12-factor** (tudo por ambiente).

### Testes
- Testes **unitários e de integração** (ex.: coleta contra respostas gravadas/fixtures e persistência contra um banco de teste).

---

## Entregáveis

- [ ] Tudo do Nível 1.
- [ ] Camada de persistência com migrações.
- [ ] `ARCHITECTURE.md` (ou ADRs) com diagrama e decisões.
- [ ] `Dockerfile` + `docker-compose.yml`.
- [ ] Testes de integração além dos unitários.

---

## Checklist de entrega

Copie para o seu PR (inclui os itens do Nível 1).

**Arquitetura e persistência**
- [ ] Camadas separadas e dependências apontando para dentro
- [ ] Banco de dados com modelo de dados e migrações
- [ ] Idempotência (upsert por chave natural)
- [ ] `ARCHITECTURE.md`/ADRs com diagrama e trade-offs

**Resiliência e concorrência**
- [ ] Retry com backoff exponencial + jitter e timeouts
- [ ] Circuit breaker (ou equivalente)
- [ ] Detecção e tratamento ético de bloqueio/anti-bot
- [ ] Concorrência controlada respeitando rate limit global

**Operação**
- [ ] Logging estruturado + métricas de coleta
- [ ] Resumo da coleta ao final da execução
- [ ] `Dockerfile` + `docker-compose` funcionando
- [ ] Configuração 12-factor

**Testes**
- [ ] Testes de integração (coleta e persistência)

---

## Critérios de avaliação

| Critério | Peso |
|---|---|
| **Arquitetura** (camadas, extensibilidade, clareza) | 25% |
| **Resiliência** (retry, circuit breaker, anti-bot ético) | 20% |
| **Persistência** (modelo, migrações, idempotência) | 15% |
| **Observabilidade e operação** (logs, métricas, Docker) | 15% |
| **Corretude** das 3 funcionalidades | 15% |
| **Testes** (unitários + integração) | 10% |
| **Bônus** (benchmark, health check, cobertura alta) | +10% extra |

---

## O que NÃO é exigido neste nível

- Coleta **distribuída** com filas e workers separados.
- Agendamento/orquestração de execuções recorrentes em produção.
- Engenharia reversa documentada de endpoints em profundidade.
- Infraestrutura como código completa, monitoramento com alertas.

Isso é escopo do **Nível 3**.
