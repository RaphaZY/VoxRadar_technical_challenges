# Como avaliamos

Este documento explica o **método** de pontuação. Os **pesos específicos** de cada nível estão em `niveis/nivel-<N>.md`.

## Princípios

1. **Nível escolhido é o contrato.** Avaliamos a sua entrega contra os requisitos do **nível que você escolheu**, não contra um nível acima. Entregar além do escopo não compensa falhas no escopo.
2. **Corretude vem primeiro.** Uma solução que não resolve as 3 funcionalidades não passa, por mais elegante que seja.
3. **Sem over-engineering.** Complexidade sem propósito conta contra. Simplicidade adequada ao nível conta a favor.
4. **Decisões documentadas valem pontos.** Um trade-off consciente e explicado no PR é melhor do que uma escolha "certa" sem justificativa.
5. **Honestidade técnica.** Dizer "não consegui X por causa de Y, faria Z com mais tempo" é positivo, não negativo.

## Escala por critério

Cada critério é pontuado de 0 a 4 e depois ponderado:

| Nota | Significado |
|---|---|
| 0 | Ausente ou não funciona. |
| 1 | Tentativa incipiente, com falhas graves. |
| 2 | Funciona no caminho feliz, com limitações. |
| 3 | Sólido, atende ao esperado para o nível. |
| 4 | Excelente, acima do esperado para o nível. |

A nota final é a soma ponderada (peso × nota) normalizada. Itens de **bônus** somam por cima, sem prejudicar quem não os fez.

## O que sempre observamos, em qualquer nível

- O código roda seguindo o seu próprio README?
- A saída adere aos [`schemas`](schemas.md)?
- Há segredos commitados? (isso é eliminatório)
- O histórico de commits e o PR comunicam bem o raciocínio?
