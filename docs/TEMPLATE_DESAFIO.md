# Template para novos desafios

> Use este modelo ao criar uma nova branch `challenge/<slug>`. Cada desafio é oferecido em quatro níveis (Júnior, Pleno, Sênior, Especialista), com requisitos crescentes.

## Estrutura esperada da branch

```
challenge/<slug>/
├── README.md            # índice: contexto, o que há em cada arquivo, como escolher o nível
├── niveis/
│   ├── junior.md
│   ├── pleno.md
│   ├── senior.md
│   └── especialista.md
├── docs/
│   ├── schemas.md       # schemas de saída compartilhados
│   └── avaliacao.md     # régua e método de pontuação
├── pyproject.toml       # Poetry (níveis Pleno+)
├── requirements.txt     # alternativa simples (nível Júnior)
└── .env.example
```

## Regra dos níveis

Cada nível **inclui tudo do anterior** e adiciona exigências. O candidato escolhe **um** nível.

| Nível | Foco |
|---|---|
| Júnior | Fazer funcionar com código organizado. |
| Pleno | Engenharia de software (deps com Poetry, testes, tipagem, CLI). |
| Sênior | Arquitetura, resiliência, persistência, observabilidade, Docker. |
| Especialista | Escala, concorrência, design documentado, infraestrutura. |

## Esqueleto de cada `niveis/<nivel>.md`

```markdown
# [Desafio] · Nível [X]

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
