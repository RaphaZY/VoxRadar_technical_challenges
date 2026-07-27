# Kwai · Nível 0 🟢 Iniciante

> **Foco:** fazer as três funcionalidades funcionarem, com código organizado e legível.
> **Pré-requisito:** nenhum (este é o nível de entrada).
> Leia antes o [problema comum](../README.md#-o-problema-comum-a-todos-os-níveis) e os [schemas](../docs/schemas.md).

---

## O que este nível cobra

### Funcionalidades (obrigatórias)
1. **Busca por palavra-chave:** dado uma palavra-chave, coletar postagens com **link, texto e engajamento** (`Postagem`).
2. **Postagens de um usuário:** dado a conta do usuário, coletar as postagens daquele usuário (`Postagem`).
3. **Comentários de uma postagem:** dado o link de uma postagem, coletar os comentários (`Comentario`).

### Requisitos técnicos
- **Python** (preferencial). Se usar outra stack, justifique no PR.
- **Interface acionável:** uma CLI simples ou scripts claros, com as três funcionalidades chamáveis por parâmetro. Exemplos:
  ```bash
  python -m kwai_collector busca --keyword "eleicoes" --limit 50 --out out/busca.json
  python -m kwai_collector usuario --user "@perfil" --limit 100 --out out/usuario.json
  python -m kwai_collector comentarios --url "https://www.kwai.com/@perfil/video/XXXX" --out out/comentarios.json
  ```
- **Saída em JSON** aderente aos [schemas](../docs/schemas.md).
- **Dependências** declaradas em `requirements.txt`.
- **Configuração** via `.env` / argumentos. **Nenhuma credencial no código.** Forneça `.env.example`.
- **Tratamento de erros básico:** a ferramenta não pode quebrar sem mensagem em falhas comuns (rede, URL inválida, conteúdo ausente).
- **README de execução:** como instalar e rodar cada modo.

---

## Entregáveis

- [ ] Código-fonte com as 3 funcionalidades.
- [ ] `README.md` com instalação e uso.
- [ ] `requirements.txt`.
- [ ] `.env.example`.
- [ ] Pasta `samples/` com **uma amostra de saída por funcionalidade**.

---

## Checklist de entrega

Copie para o seu PR.

**Funcionalidades**
- [ ] Busca por palavra-chave (link, texto, engajamento)
- [ ] Todas as postagens de um usuário
- [ ] Comentários de uma postagem por link

**Qualidade e execução**
- [ ] Saída em JSON seguindo os schemas
- [ ] `README.md` explica como instalar e rodar cada modo
- [ ] `requirements.txt` presente
- [ ] `.env.example` presente e **nenhum segredo commitado**
- [ ] Amostras em `samples/`
- [ ] Tratamento de erros básico
- [ ] PR descreve abordagem, decisões e limitações

---

## Critérios de avaliação

| Critério | Peso |
|---|---|
| **Corretude** das 3 funcionalidades | 45% |
| **Qualidade de código** (organização, legibilidade, nomes) | 25% |
| **Aderência aos schemas** de saída | 15% |
| **Documentação** (README e PR) | 15% |
| **Bônus** (tratamento de rate limit, paginação, pequenos testes) | +10% extra |

---

## O que NÃO é exigido neste nível

Para não gastar seu tempo além do escopo, **não** cobramos aqui:

- Poetry, tipagem estática, testes automatizados extensos.
- Persistência em banco de dados, Docker, concorrência/async.
- Arquitetura em camadas, observabilidade, resiliência avançada.

Isso é escopo dos níveis **1**, **2** e **3**.
