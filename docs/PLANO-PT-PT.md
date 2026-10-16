# Plano: versão para português europeu (pt-PT)

Estado: rascunho inicial. Base: fork de `swfsql/portugues-tecnico-simplificado-skill` (pt-BR, versão 0.3.0).

## Objetivo

Uma skill equivalente para o português europeu, com regras de redação para textos lidos por agentes de IA. Usa a NP ISO 24495-1:2024 como uma das bases, ao lado do ASD-STE100.

## Papel da NP ISO 24495-1:2024

A norma (adoção portuguesa da ISO 24495-1:2023, linguagem simples) define quatro princípios: o texto é relevante, fácil de encontrar, fácil de compreender e fácil de usar. Escreve para pessoas. Esta skill escreve para agentes. Por isso:

- Os princípios entram como critérios de revisão (relevância, estrutura e ordem, clareza, utilização).
- As regras mecânicas continuam a vir do STE (voz ativa, uma instrução por frase, sem ponto e vírgula, etc.).
- É preciso ler o texto da norma (pago, via IPQ/ISO) antes de citar cláusulas. Não citar de memória.

## Trabalho a fazer

1. **Texto da skill** (`SKILL.md`, `README.md`, `references/`, `examples/`): reescrever em pt-PT, com o Acordo Ortográfico de 1990 aplicado como em Portugal, e Priberam/Ciberdúvidas como referência. Trocar "você" por tratamento por "tu"/forma impessoal conforme o registo definido (decidir).
2. **Léxico**: "arquivo" para "ficheiro", "tela" para "ecrã", "equipe" para "equipa", "apagar/excluir", "rodar/executar", "baixar" para "descarregar", "mouse" para "rato", "celular" para "telemóvel", "time" para "equipa". Rever os verbos-suporte, as locuções e os decalques do inglês próprios de Portugal.
3. **Gramática**: gerúndio ("estar a" + infinitivo em vez de "estar" + gerúndio), colocação do pronome (ênclise/próclise), mesóclise, "a gente" vs. "nós", "dar para" e "deixar de" a rever. O gerundismo muda de forma: "vamos estar a enviar".
4. **Números e datas**: pt-PT usa vírgula decimal e espaço como separador de milhares ("1 000"), tal como o SI. Rever a regra do ponto de milhar.
5. **Linter** (`scripts/pts-lint.py`): extrair as listas e as expressões regulares específicas de pt-BR para dados de configuração por variante (`--variante pt-pt`), ou manter um ficheiro por variante. Adaptar os testes automáticos do próprio linter.
6. **Novas regras vindas da ISO 24495-1**: título e resumo informativos, informação mais importante primeiro, termos consistentes, listas e tabelas quando ajudam. Decidir quais são verificáveis pelo linter e quais ficam como leitura.
7. **Nome e distribuição**: nome da skill (por exemplo `portugues-tecnico-simplificado-pt`), e como convive com a versão pt-BR (branch, diretório ou repositório separado).

## Decisões em aberto

- Branch `pt-pt` neste fork, ou diretório/skill separada que mantém as duas variantes no mesmo repositório?
- Registo: "tu", "você" ou impessoal nas instruções?
- O fork deve contribuir de volta para o upstream (a licença é MIT)?
- Quem tem acesso ao texto da NP ISO 24495-1:2024?
