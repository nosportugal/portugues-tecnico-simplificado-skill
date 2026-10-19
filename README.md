# Português Técnico Simplificado (pt-PT): o STE para agentes

Esta é uma skill do Claude Code que reescreve um português denso e ambíguo. Ela usa as regras do [ASD-STE100 Simplified Technical English](https://www.asd-ste100.org/) (STE), adaptadas ao português europeu, e os princípios da ISO 24495-1 (linguagem clara). O STE é uma norma de linguagem controlada da indústria aeroespacial e de defesa. Ela existe para que ninguém leia mal as instruções de manutenção de aeronaves.

Esta skill usa a mesma disciplina para outro leitor: um **agente de IA**. Esse agente interpreta a saída de outro agente, a descrição de uma ferramenta, uma mensagem de erro ou uma instrução entre agentes. Não há um humano para resolver ambiguidades.

Esta é uma edição só para o português europeu. Parte da skill [portugues-tecnico-simplificado-skill](https://github.com/swfsql/portugues-tecnico-simplificado-skill), que faz o mesmo trabalho para o português do Brasil. Essa, por sua vez, adapta a skill [asd-ste100](https://github.com/danyuchn/asd-ste100-skill), que serve o inglês. Esta edição não mantém a versão do Brasil.

## Porque o STE, e porque para agentes

O STE existe porque uma instrução mal lida numa aeronave pode matar pessoas. Os leitores da norma muitas vezes não falavam inglês como língua materna e não tinham um autor a quem pedir esclarecimentos. A solução da norma: um significado por palavra, voz ativa, tempos simples, uma instrução por frase, frases curtas e nenhuma palavra omitida.

Um agente que interpreta a saída de outro agente está numa posição muito parecida. Ele não tem canal de volta nem forma de perguntar "quis dizer X ou Y?". As regras que impedem um mecânico de ler mal uma especificação de torque protegem também um agente. Com elas, o agente não lê mal a descrição de uma ferramenta nem uma mensagem entre agentes.

## Porque uma versão em português europeu

Não existe norma de linguagem controlada para o português. O STE é só para o inglês, e uma tradução direta das regras não funciona. O português não tem a partícula dos phrasal verbs ("take off"). Mas tem locuções verbais cujo sentido não vem das partes ("deixar de", "acabar com") e uma gíria técnica com o mesmo problema ("subir o servidor", "fazer um push"). O pretérito perfeito composto ("tem falhado") tem outro sentido do que o present perfect do inglês. O português separa também a essência ("ser") do estado ("estar"), e o inglês não separa.

O português tem ainda fontes de ambiguidade que o inglês não tem. Exemplos: o "dever" (ordem ou estimativa?), o "seu" com dois donos possíveis, o sujeito oculto e o "excluir" (apagar ou deixar de fora?). Os números e as datas também mudam de leitura entre as duas línguas: "1.000" e "07/10".

O português europeu tem ainda os seus problemas próprios:

- **Vocabulário.** "Ficheiro", "ecrã", "equipa", "utilizador", "pedido", "descarregar". Os modelos de linguagem escrevem muitas vezes com o vocabulário do Brasil, e o leitor em Portugal nota.
- **Palavras com vários sentidos técnicos.** "Carregar" (enviar, ler para a memória ou premir), "ligação" (hiperligação ou ligação de rede) e "correr" (executar ou fluir).
- **Gerúndio e pronomes.** Em Portugal, "está a executar" substitui "está executando", e o pronome vai depois do verbo ("envia-o"). O gerundismo toma a forma "vamos estar a enviar".
- **Tratamento.** O português europeu tem "tu", "você" e formas impessoais. A skill usa o imperativo sem pronome ("Abra o ficheiro") e a terceira pessoa nas descrições.

Há também o traduzês. Os modelos de linguagem aprendem sobretudo com texto em inglês. O português que escrevem traz decalques: "eventualmente" no sentido de "por fim", "endereçar o problema", "suportar o formato". Outros sinais do traduzês são o gerundismo e "o mesmo" no lugar de pronome. Esta skill trata estes casos como regras próprias.

## A ISO 24495-1

A ISO 24495-1:2023 fixa quatro princípios de linguagem clara: o texto é relevante, localizável, compreensível e utilizável. Portugal adotou a norma como NP ISO 24495-1:2024 ("Linguagem clara. Parte 1: Princípios de base e orientações"). A norma escreve para pessoas e a skill escreve para agentes. Por isso a skill adota algumas diretrizes, adapta outras e deixa de fora as que servem só a leitores humanos.

- **Adota:** a mensagem principal primeiro, os títulos descritivos, as listas numeradas para passos, um tópico por parágrafo, as siglas por extenso e a informação complementar à parte.
- **Adapta:** o "conhecer o leitor" (a skill fixa quem lê, o objetivo e o contexto) e a avaliação (um agente executa a tarefa a partir do texto).
- **Não aplica:** o tratamento direto ao leitor, a variação do ritmo das frases e as imagens.

O ficheiro [`docs/MAPEAMENTO-ISO-24495-1.md`](docs/MAPEAMENTO-ISO-24495-1.md) lista o destino de cada diretriz. A skill não reproduz o texto da norma. Os números das cláusulas seguem a ISO e foram verificados na adoção brasileira da norma. Falta verificá-los na NP.

## Antes e depois

| Antes | Depois |
|---|---|
| "Esta ferramenta irá tentar realizar a sincronização do estado entre os diversos backends que foram configurados, e caso um conflito seja detetado ela poderá resolvê-lo automaticamente dependendo da estratégia que tiver sido definida, ou caso contrário irá apresentar o conflito para revisão manual." | "A ferramenta tenta sincronizar o estado entre os backends configurados. Se encontrar um conflito, a ferramenta lê a estratégia configurada. Se a estratégia permitir resolução automática, a ferramenta pode resolver o conflito automaticamente. Se a ferramenta não resolver o conflito, ela encaminha o conflito para revisão manual." |
| "Um erro pode ter ocorrido durante o processamento do seu pedido devido a uma possível incompatibilidade no formato de dados esperado, o que poderia ser causado por uma versão desatualizada do cliente." | "O seu pedido pode ter falhado. A causa pode ser um formato de dados diferente do formato que o servidor espera. Uma versão desatualizada do cliente pode causar essa diferença." |

Há mais exemplos em [`examples/antes-depois.md`](examples/antes-depois.md), incluindo ilustrações das regras do STE, das regras que só o português tem e das regras de estrutura da ISO.

## O que esta skill faz

1. Fixa o leitor, o objetivo e o contexto do texto.
2. Escolhe um modo. O modo **Estrito** cobre procedimentos, mensagens de erro e descrições de ferramentas. O modo **Flexível** cobre READMEs, descrições de pull request e prosa explicativa. O modo Flexível mantém a disciplina da frase, mas não o vocabulário fixo.
3. Lê o texto de entrada pelo sentido.
4. Marca cada violação, frase a frase. Exemplos: escolha ambígua de palavras, tempo composto, voz passiva com quem age indefinido, várias instruções numa frase, cadeias de "de", palavras omitidas e frases longas. Outros: verbo-suporte, gíria técnica, locuções verbais e prolixas, ponto e vírgula, ressalvas empilhadas, adjetivos de marketing, gerundismo, decalques do inglês e marcas do português do Brasil. Por fim: "ser" no lugar de "estar", números e datas ambíguos, colocação do pronome e formas de género fora da norma.
5. Reescreve cada frase marcada, sem perder nenhum facto, condição ou limite de escopo do original. Se uma forma mais curta perdesse uma precisão necessária, a skill mantém a forma longa e sinaliza a troca. Ela não simplifica em silêncio.
6. Entrega só o texto reescrito: sem preâmbulo, sem anúncio de modo, sem resumo das mudanças. Quando deixa algo sem simplificar de propósito, acrescenta uma linha `Mantido como está:`.

Peça o raciocínio ("mostre o diff", "quais regras quebrou") e a skill entrega uma tabela de antes e depois que nomeia cada regra.

As regras estruturais que a skill verifica são mecânicas: aponta-se a palavra ou o sinal que quebra cada uma. As regras que dependeriam de um dicionário aprovado são só recomendações, porque não existe esse dicionário para o português. As regras que pedem bom gosto ficam com quem lê.

## O linter

`scripts/pts-lint.py` é um linter determinístico que usa só a biblioteca padrão do Python. Ele verifica só padrões estruturais. Ele não compara um texto original com uma reescrita. Ele não verifica se a força de uma exigência continua a mesma e não prova que a reescrita preservou o sentido. Um resultado com zero violações quer dizer que as verificações estruturais configuradas não encontraram problemas.

O linter verifica:

- **Achados obrigatórios** reprovam a execução. São eles: ponto e vírgula, frase longa, locução prolixa, verbo-suporte, gíria técnica e adjetivo de marketing. Também: gerundismo com verbo de ação pontual (inclui "vou estar a enviar"), data no formato dia/mês/ano, número com ponto de milhar e forma de género fora da norma. Por fim: a rotação de sinónimos (com as conjugações dos verbos) e a conjunção pendente no fim de item de lista.
- **Achados consultivos** nunca reprovam a execução. São eles: voz passiva, partícula "se", tempo composto, cadeia de "de", "o mesmo" como pronome, gerúndio depois de vírgula, decalque do inglês e travessão. Também: locução verbal idiomática, "excluir", "ser" no lugar de "estar", outros casos de gerundismo e data sem o ano. Por fim: número com três casas depois da vírgula.
- **Achados consultivos do português europeu e da ISO 24495-1**:
  - `marca-do-brasil`: vocabulário do Brasil ("arquivo", "tela", "usuário", "baixar") e gerúndio de ação em curso ("está rodando").
  - `tratamento-pessoal`: "você" e "tu".
  - `sigla`: sigla sem o nome por extenso na primeira ocorrência (há uma lista de siglas comuns).
  - `titulo`: título que salta de nível, repetido ou com mais de 12 palavras.
  - `paragrafo-longo`: parágrafo com mais de 6 frases.
  - `inciso`: inciso entre o sujeito e o verbo, ou parêntesis longo a meio da frase.
  - `passos-em-prosa`: "primeiro... depois... por fim..." em prosa corrida.

O linter nunca marca ressalvas nem modalidade. "Pode ter falhado", "talvez tenha falhado" e "teria falhado" passam limpos, e o autoteste comprova isso. O linter também não verifica a ordem direta, o sujeito oculto, o "seu" ambíguo, o "dever" ambíguo, a colocação do pronome nem a mistura de tratamentos. Essas regras precisam de leitura humana ou de um modelo.

O linter lê Markdown por parágrafo. Uma frase quebrada em várias linhas conta como uma frase, e o achado aponta para a primeira palavra dela. O linter ignora blocos de código, blocos de fórmula `$$`, comentários HTML, definições de ligação e front matter YAML. Código e fórmulas inline contam como uma palavra cada, e os destinos de ligação não contam. As colunas ficam exatas.

Um trecho entre aspas ("...", “...” ou «...») é uma menção: um exemplo, um rótulo ou uma citação. O linter conta o trecho como uma palavra e não analisa o conteúdo dele. `--ler-citacoes` desliga esse comportamento, por exemplo para analisar as mensagens de erro citadas num README.

Um exemplo que precisa de falhar fica entre duas diretivas:

```markdown
<!-- pts-lint: deve-falhar frase-longa ponto-e-virgula -->
> Um texto mau de propósito; com várias violações.
<!-- pts-lint: fim -->
```

Os achados dentro da região são esperados e saem do relatório. A região falha (`exemplo-sem-falha`) se não tiver um achado obrigatório ou se faltar uma das regras listadas. A lista de regras é opcional. Os blocos "Antes" de `examples/antes-depois.md` usam estas diretivas.

Em ficheiros Rust (`*.rs`, ou `--linguagem rust`), o linter lê só a prosa, nunca o código. `--partes` escolhe a prosa (predefinição `docs,comentarios`):

- `docs`: `///`, `//!`, `/** */` e `/*! */`, lidos como Markdown.
- `comentarios`: `//` e `/* */`.
- `mensagens`: literais de string dentro de `panic!`, `assert!`, `expect`, `println!` e chamadas parecidas. Mensagens são texto de erro, por isso usam o limite estrito de 22 palavras (`--max-palavras-estrito`).
- `literais`: todo o literal de string com três palavras ou mais.

Outras opções:

- `--max-palavras N` define o limite de palavras por frase (predefinição 27).
- `--max-frases N` define o limite de frases por parágrafo (predefinição 6).
- `--resumo` imprime uma linha por ficheiro, com o pior ficheiro primeiro.
- `--ativar historico` acrescenta uma regra opcional que marca frases de changelog ("já não", "anteriormente", "atualmente") em documentação do estado atual.
- `--linha-de-base N` tolera N violações obrigatórias.
- `--ajuda` mostra o uso completo.
- `--autoteste` executa os testes internos e analisa os documentos desta skill. Os documentos precisam de passar, e o ficheiro de casos-limite precisa de falhar.

Uma opção desconhecida ou um nome de regra desconhecido em `--desativar` ou `--ativar` é erro (código 2). Um nome de opção do ste-lint, como `--baseline`, recebe a indicação do nome em português.

A saída em JSON usa a chave `ficheiro` (nas versões em português do Brasil, a chave era `arquivo`).

A regra de conjunção pendente lê os marcadores de lista comuns (`-`, `*`, `+`, `1.` e `1)`) com até três espaços antes. Ela não interpreta listas dentro de citações, continuação preguiçosa (lazy continuation) nem a semântica completa de listas aninhadas.

O ficheiro `examples/casos-limite-do-linter.md` é inválido de propósito e mostra itens de lista incompletos. Execute `python3 scripts/pts-lint.py examples/casos-limite-do-linter.md` e veja que o linter informa os dois achados esperados. O ficheiro é um caso de teste e não serve de exemplo de prosa conforme.

A skill **não** reproduz o dicionário oficial de cerca de 900 palavras do ASD. A norma é gratuita, mas a redistribuição não é livre. O Issue 9 permite a reprodução só com autorização escrita do ASD ou por oito categorias de organizações. Este projeto não pertence a nenhuma delas. Além disso, o dicionário é de palavras inglesas. Esta skill aplica o *princípio* do dicionário (a palavra mais simples, usada sempre do mesmo modo), e não uma lista fixa de palavras.

O resumo completo das regras, a adaptação ao português europeu e as fontes estão em [`references/regras-de-redacao.md`](references/regras-de-redacao.md).

## Instalação

Clone o repositório para a pasta de skills do Claude Code:

```bash
git clone git@github.com:nosportugal/portugues-tecnico-simplificado-skill.git ~/.claude/skills/portugues-tecnico-simplificado-pt
```

O clone deixa a skill disponível em todos os projetos. Para um projeto só, clone para `.claude/skills/portugues-tecnico-simplificado-pt` dentro do projeto. Atualize a skill com `git pull`.

## Utilização

Peça para simplificar ou esclarecer um texto em português:

```
Desambigue esta descrição de ferramenta
Reescreva esta mensagem de erro para que um agente não a interprete mal
Aplique o português técnico simplificado a esta instrução
Tire o traduzês deste texto
```

Ou cole o texto e peça ao Claude para "desambiguar", "simplificar com o STE" ou "reduzir a ambiguidade desta saída".

A resposta é só o texto reescrito. Para ver quais regras a skill aplicou, acrescente "mostre o diff" ou "explique as mudanças" ao pedido.

## Âmbito

Feita para: mensagens entre agentes, descrições de ferramentas e funções, mensagens de erro, prompts de sistema e instruções entre agentes. Vale para todo o texto em português europeu que uma máquina ou um leitor estrangeiro precisa de interpretar sem um humano a quem perguntar.

Não serve para: escrita criativa, textos de marketing ou qualquer texto em que a voz e a nuance são o objetivo. O STE é plano e literal de propósito. Também não serve de ferramenta de linguagem clara para o cidadão.

Um limite que vale dizer logo: a skill corrige a forma de um texto, não a substância. Um parágrafo sem nada a dizer sai curto, limpo e ainda vazio.

## Fontes

- [Site oficial do ASD-STE100](https://www.asd-ste100.org/)
- [ASD-STE100: About STE](https://www.asd-ste100.org/about_STE.html)
- [ASD Europe: Simplified Technical English](https://www.asd-europe.org/standards-specifications/simplified-technical-english/)
- [NP ISO 24495-1:2024 na loja do IPQ](https://www.ipq.pt/loja/normas/norma/1335f156-072b-ef11-840a-6045bddfaf5e/)
- [ISO 24495-1:2023, Plain language, Part 1](https://www.iso.org/standard/78907.html)

As fontes de língua, números e datas (Acordo Ortográfico, VOP, Priberam, SI, ISO 8601) estão em [`references/regras-de-redacao.md`](references/regras-de-redacao.md).

## Licença

MIT. Veja [LICENSE](LICENSE). O texto da licença fica em inglês, porque a licença MIT exige manter o aviso original sem alterações. Os avisos de copyright dos projetos originais ficam.
