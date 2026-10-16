# Plano: versão para português europeu (pt-PT)

Estado: rascunho inicial. Base: fork de `swfsql/portugues-tecnico-simplificado-skill` (pt-BR, versão 0.3.0).

## Objetivo

Uma skill só para o português europeu, com regras de redação para textos lidos por agentes de IA. Este repositório contém só a versão pt-PT. A versão pt-BR fica no upstream e não é mantida aqui. Não há contribuições de volta ao upstream.

## Papel da NP ISO 24495-1:2024

A ISO 24495-1:2023 (linguagem simples) define quatro princípios: o texto é relevante, fácil de encontrar, fácil de compreender e fácil de usar. Escreve para pessoas. Esta skill escreve para agentes. Por isso:

- Os princípios entram como critérios de revisão (relevância, estrutura e ordem, clareza, utilização).
- As regras mecânicas continuam a vir do STE (voz ativa, uma instrução por frase, sem ponto e vírgula, etc.).
- A NP ISO 24495-1:2024 existe: "Linguagem clara - Parte 1: Princípios de base e orientações", em português (Portugal), CT 221 do IPQ, publicada em 2024-06-14, 21 páginas, 21,00 EUR sem IVA (https://www.ipq.pt/loja/normas/norma/1335f156-072b-ef11-840a-6045bddfaf5e/). A página não diz que é uma adoção da ISO 24495-1, mas o número coincide.
- Até comprarmos a NP, o texto de trabalho é a ABNT NBR ISO 24495-1:2024 (adoção brasileira da mesma norma ISO). Não citar cláusulas de memória. As duas normas têm direitos reservados: parafrasear, nunca copiar.
- A ISO 24495-1 é uma norma internacional sobre princípios, não sobre uma variante da língua. As adoções nacionais (ABNT, UNE) traduzem o mesmo conteúdo. Não existe norma de linguagem só para o português europeu que eu tenha confirmado.

## Estado

Feito: `SKILL.md`, linter (vocabulário, gerundismo "estar a", `marca-do-brasil`, `tratamento-pessoal`, `sigla`, `titulo`, `paragrafo-longo`, `inciso`, `passos-em-prosa`), `README.md`, `references/` e `examples/`.

Por fazer: ler a NP ISO 24495-1:2024 e confirmar a numeração e a terminologia, medir o tamanho do português europeu para os limites de palavras, detetar a colocação do pronome no linter, rever o ficheiro `LICENSE` e decidir o nome final da skill.

## Trabalho a fazer (plano original)

1. **Texto da skill** (`SKILL.md`, `README.md`, `references/`, `examples/`): reescrever em pt-PT, com o Acordo Ortográfico de 1990 aplicado como em Portugal, e Priberam/Ciberdúvidas como referência. Trocar "você" por tratamento por "tu"/forma impessoal conforme o registo definido (decidir).
2. **Léxico**: "arquivo" para "ficheiro", "tela" para "ecrã", "equipe" para "equipa", "apagar/excluir", "rodar/executar", "baixar" para "descarregar", "mouse" para "rato", "celular" para "telemóvel", "time" para "equipa". Rever os verbos-suporte, as locuções e os decalques do inglês próprios de Portugal.
3. **Gramática**: gerúndio ("estar a" + infinitivo em vez de "estar" + gerúndio), colocação do pronome (ênclise/próclise), mesóclise, "a gente" vs. "nós", "dar para" e "deixar de" a rever. O gerundismo muda de forma: "vamos estar a enviar".
4. **Números e datas**: pt-PT usa vírgula decimal e espaço como separador de milhares ("1 000"), tal como o SI. Rever a regra do ponto de milhar.
5. **Linter** (`scripts/pts-lint.py`): extrair as listas e as expressões regulares específicas de pt-BR para dados de configuração por variante (`--variante pt-pt`), ou manter um ficheiro por variante. Adaptar os testes automáticos do próprio linter.
6. **Novas regras vindas da ISO 24495-1**: título e resumo informativos, informação mais importante primeiro, termos consistentes, listas e tabelas quando ajudam. Decidir quais são verificáveis pelo linter e quais ficam como leitura.
7. **Nome e distribuição**: nome da skill (por exemplo `portugues-tecnico-simplificado-pt`), e como convive com a versão pt-BR (branch, diretório ou repositório separado).

## Decisões tomadas

- Este repositório contém só a versão pt-PT. A pt-BR fica no upstream.
- Tratamento impessoal nas instruções.
- Sem contribuição de volta ao upstream. Edição separada, focada em pt-PT.

## Em aberto

- Comprar a NP ISO 24495-1:2024 (alguém da NOS) e comparar a terminologia com a ABNT.
- Nome da skill (por exemplo `portugues-tecnico-simplificado-pt`).
