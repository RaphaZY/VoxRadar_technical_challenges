# Template para novos desafios

> Use este modelo ao criar uma nova branch `challenge/<slug>`. Cada desafio é oferecido em quatro níveis numerados (0 Iniciante, 1, 2, 3 Avançado), com requisitos crescentes.

## Estrutura esperada da branch

```
challenge/<slug>/
├── README.md            # índice: contexto, o que há em cada arquivo, como escolher o nível
├── niveis/
│   ├── nivel-0.md
│   ├── nivel-1.md
│   ├── nivel-2.md
│   └── nivel-3.md
├── docs/
│   ├── schemas.md       # schemas de saída compartilhados
│   └── avaliacao.md     # régua e método de pontuação
├── pyproject.toml       # Poetry (Nível 1+)
├── requirements.txt     # alternativa simples (Nível 0)
└── .env.example
```

## Regra dos níveis

Cada nível **inclui tudo do anterior** e adiciona exigências. O candidato escolhe **um** nível.

| Nível | Foco |
|---|---|
| Nível 0 · Iniciante | Fazer funcionar com código organizado. |
| Nível 1 | Engenharia de software (deps com Poetry, testes, tipagem, CLI). |
| Nível 2 | Arquitetura, resiliência, persistência, observabilidade, Docker. |
| Nível 3 · Avançado | Escala, concorrência, design documentado, infraestrutura. |

## Esqueleto de cada `niveis/nivel-<N>.md`

```markdown
# [Desafio] · Nível N

## Pré-requisito
Inclui tudo do nível anterior.

## O que este nível cobra
<!-- Requisitos específicos, com entrada/saída quando aplicável. -->

## Entregáveis
- [ ] ...

## Checklist de entrega
- [ ] ...

## Critérios de avaliação
| Critério | Peso |
|---|---|
| ... | ... |

## O que NÃO é exigido neste nível
<!-- Deixa claro o limite superior de escopo. -->
```
