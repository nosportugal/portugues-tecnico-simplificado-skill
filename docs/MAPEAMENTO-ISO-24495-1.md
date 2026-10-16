# Mapeamento da ISO 24495-1 para a skill pt-PT

Estado: rascunho. Fonte de trabalho: ABNT NBR ISO 24495-1:2024 (adoção brasileira da ISO 24495-1:2023). A numeração das cláusulas é a da ISO e deve coincidir com a da NP ISO 24495-1:2024. Confirmar quando a norma portuguesa estiver disponível. Este documento parafraseia e não reproduz o texto da norma.

A norma escreve para leitores humanos e pede uma avaliação com esses leitores. A skill escreve para agentes. Por isso cada diretriz recebe um destino:

- **Já coberta**: uma regra atual da skill (STE) já a cumpre.
- **Nova, linter**: regra nova que o linter consegue verificar.
- **Nova, leitura**: regra nova que exige leitura humana ou de um modelo.
- **Adaptar**: a ideia serve, mas a forma muda para um leitor-máquina.
- **Não aplicar**: serve só para leitores humanos.

## Princípio 1: relevante (cláusula 5.1)

| Cláusula | Ideia | Destino |
|---|---|---|
| 5.1.2 a 5.1.4 | Identificar o leitor, o objetivo e o contexto de leitura. | Adaptar. Antes de reescrever, a skill fixa quem lê (agente, pipeline, pessoa), o que esse leitor vai fazer e se pode pedir esclarecimentos. Hoje isto só aparece no modo Estrito ou Flexível. |
| 5.1.5 | Escolher o tipo de documento. | Adaptar. Tipos da skill: procedimento, mensagem de erro, descrição de ferramenta, relatório de estado, prosa. |
| 5.1.6 | Incluir só o conteúdo de que o leitor precisa. Não incluir falsidades nem esconder informação. | Já coberta em parte (a skill não perde factos). Nova, leitura: cortar conteúdo que o leitor não usa. |

## Princípio 2: localizável (cláusula 5.2)

| Cláusula | Ideia | Destino |
|---|---|---|
| 5.2.2 a) | Mensagem mais importante primeiro. | Nova, leitura. Pode ter um apoio no linter: o primeiro parágrafo não pode ser uma introdução vazia. |
| 5.2.2 b), d) | Partir do que o leitor já sabe. Informação para a maioria antes da informação para poucos. | Nova, leitura. |
| 5.2.2 c) | Instruções em ordem cronológica. | Já coberta (uma instrução por frase, condição antes da instrução). Reforçar: a ordem do texto é a ordem de execução. |
| 5.2.2 e) | Avisar o que não fazer antes de dizer o que fazer. | Já coberta (aviso de segurança antes da ação). |
| 5.2.3 | Hierarquia visual, listas, índice, vários públicos identificados. | Adaptar. Para um agente, interessam listas numeradas para passos, listas com marcadores para itens, tabelas para comparações e uma estrutura Markdown consistente. Nova, linter: passos em prosa corrida com "primeiro... depois..." devem ser lista numerada. |
| 5.2.4 | Títulos que descrevem o que vem a seguir, consistentes e curtos. | Nova, linter: nível de título que salta (de `#` para `###`), títulos repetidos, títulos longos. Nova, leitura: o título descreve o conteúdo. |
| 5.2.5 | Informação complementar separada (anexos, fontes). | Nova, leitura. |

## Princípio 3: compreensível (cláusula 5.3)

| Cláusula | Ideia | Destino |
|---|---|---|
| 5.3.2 a), g) | Palavras precisas, sem ambiguidade, e as mesmas palavras para o mesmo sentido. | Já coberta (rotação de sinónimos, "excluir", gíria técnica). Alargar as listas de sinónimos para pt-PT. |
| 5.3.2 c) | Termos especializados só se o leitor os conhece ou precisa deles, e explicados na primeira ocorrência. | Já coberta em parte (termos de domínio). Nova, linter: termo definido uma vez. |
| 5.3.2 d) a f) | Abreviaturas e siglas: por extenso na primeira vez, salvo as comuns. | Nova, linter: sigla em maiúsculas sem expansão na primeira ocorrência, com uma lista de siglas comuns configurável (API, URL, HTTP, etc.). |
| 5.3.2 h) | Linguagem culturalmente adequada. | Adaptar. Em pt-PT: vocabulário de Portugal e não de outras variantes (ver o plano, ponto 2). |
| 5.3.3 a) 1, 2 | Estruturas de frase familiares, sem dupla leitura. | Já coberta (ordem direta, sujeito oculto, "seu" ambíguo). |
| 5.3.3 a) 3 | Não interromper a ideia principal com incisos. | Já coberta em parte (travessão consultivo). Nova, linter: parêntesis ou travessões a meio da frase, entre o sujeito e o verbo. |
| 5.3.3 a) 4 | Começar a frase pelo que é conhecido e acabar no que é novo. | Nova, leitura. |
| 5.3.3 b) | Dirigir-se diretamente ao leitor ("tu", "você"). | Não aplicar. A decisão do projeto é o tratamento impessoal, e a própria norma usa o impessoal. Manter o imperativo sem sujeito ("Abra o ficheiro"). Documentar a diferença. |
| 5.3.3 c) | Voz ativa. | Já coberta. |
| 5.3.3 d), e) | Gramática, ortografia e pontuação que o leitor aceita. Seguir as normas linguísticas oficiais. | Já coberta. Passa a referir o Acordo Ortográfico de 1990 em Portugal e o Priberam. |
| 5.3.4 a), b) | Uma ideia por frase. Sem palavras redundantes, modificadores vagos nem clichés. | Já coberta (uma instrução por frase, locuções prolixas, adjetivos de marketing). |
| 5.3.4 c) | Frases curtas, com o tamanho a variar para dar ritmo. | Adaptar. O ritmo não interessa a um agente. Manter os limites de palavras da skill e não pedir variação. |
| 5.3.5 | Um tópico por parágrafo, enunciado perto do início, com ligações claras. | Nova, leitura. Nova, linter: parágrafo acima de um número máximo de frases (configurável). |
| 5.3.6 | Imagens e multimédia de apoio. | Não aplicar a texto lido por agentes. Quando há imagens, o texto alternativo descreve o conteúdo. |
| 5.3.7 | Tom respeitoso e linguagem inclusiva. | Já coberta em parte (formas de género fora da norma). Nova, leitura: tom neutro nas mensagens de erro, sem culpar quem usa. |
| 5.3.8 | Coesão: relações claras, desenho e tom consistentes. | Nova, leitura. |

## Princípio 4: utilizável (cláusula 5.4)

| Cláusula | Ideia | Destino |
|---|---|---|
| 5.4.2 | Avaliar durante a redação, com a lista de verificação do Anexo B. | Já coberta (lista de varredura e linter). Atualizar a lista de varredura com os itens novos. |
| 5.4.3 | Avaliar com leitores reais. | Adaptar. Para agentes, a avaliação é um teste: o agente destino executa a tarefa a partir do texto reescrito. Propor um pequeno conjunto de casos de teste por tipo de documento. |
| 5.4.4 | Reavaliar ao longo do tempo. | Adaptar. Voltar a verificar o texto quando o comportamento da ferramenta mudar. |

## Resumo do trabalho novo

Estado do linter: as seis regras abaixo estão implementadas como consultivas (`sigla`, `titulo`, `passos-em-prosa`, `paragrafo-longo`, `inciso`), juntamente com `marca-do-brasil`, `tratamento-pessoal` e o gerundismo "estar a" + infinitivo. Os limites são configuráveis (`--max-frases`).

**Regras novas para o linter** (todas consultivas no início, para não reprovar execuções):
1. Sigla sem expansão na primeira ocorrência.
2. Nível de título que salta.
3. Títulos repetidos ou demasiado longos.
4. Passos sequenciais em prosa que deviam ser lista numerada.
5. Parágrafo com mais frases do que o máximo.
6. Inciso entre parêntesis ou travessões a separar sujeito e verbo.

**Regras novas só de leitura** (entram no `SKILL.md` e na lista de varredura): mensagem principal primeiro, informação conhecida antes da nova, uma ideia por parágrafo, informação complementar separada, tom neutro.

**Diferenças a documentar**: tratamento impessoal em vez de "você" (5.3.3 b), sem variação de ritmo (5.3.4 c), sem imagens (5.3.6), avaliação por teste com agente em vez de leitores (5.4.3).

## Ordem sugerida

1. Reescrever `SKILL.md` em pt-PT com o léxico e a gramática do plano, mais os itens de leitura acima.
2. Adaptar o linter (listas pt-PT, regras 1 a 6).
3. Reescrever `README.md`, `references/` e `examples/`.
4. Quando a NP ISO 24495-1:2024 estiver disponível, confirmar a numeração e a terminologia ("linguagem clara").
