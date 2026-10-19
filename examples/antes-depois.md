# Exemplos de antes e depois

## Parte 1: regras do STE, adaptadas ao português europeu

Estes exemplos ilustram regras reais do ASD-STE100, a partir de fontes secundárias públicas (veja `references/regras-de-redacao.md`). São paráfrases adaptadas ao português, não citações da norma. A norma oficial dá exemplos só em inglês.

| Regra | Antes | Depois | Porquê |
|---|---|---|---|
| Um significado por palavra | "Verifique o sistema." / "Confira os cabos." / "Valide a receção." | "Verifique o sistema." / "Verifique os cabos." / "Verifique a receção." (um só termo, usado de forma consistente) | Três quase sinónimos obrigam o leitor a adivinhar se eles nomeiam a mesma ação. |
| Uma classe gramatical por palavra | "Faça log do evento." | "Escreva o evento no registo (log)." | Se "log" é aprovado só como substantivo, usar a palavra como verbo quebra a garantia de uma palavra para uma função. Além disso, "registo" também quer dizer registo de um dado, por isso o texto define o termo uma vez. |
| Significado preciso do verbo | "Liberte a porta 8080." | Se a firewall bloqueia a porta: "Abra a porta 8080 na firewall." Se a porta está em uso: "Encerre o processo que usa a porta 8080." | "Libertar a porta" pode ser abrir a porta para o tráfego ou desocupar a porta. O STE escolhe a palavra sem ambiguidade. |
| Só tempos simples | "Temos recebido o relatório técnico da matriz." | "Recebemos o relatório técnico da matriz." | Em português, "temos recebido" indica repetição ("recebemos várias vezes"). Com um relatório só, a frase é um decalque do present perfect, e o pretérito perfeito diz o facto. |
| Verbo, não substantivo | "Efetue uma inspeção do filtro." | "Inspecione o filtro." | O substantivo esconde a ação e acrescenta um verbo vazio. |
| Sem locução verbal idiomática (Regra 9.3) | "O job deixou de correr." | Se o job parou: "O job parou de executar." Se o job não executou desta vez: "O job não executou." | "Deixar de" + infinitivo tem duas leituras. O sentido da locução não vem das partes, e esse é o motivo da Regra 9.3. |
| Sem gíria técnica (Regra 9.3) | "Suba o contentor e faça um push da branch." | "Inicie o contentor. Envie a branch para o repositório remoto." | "Subir" tem quatro sentidos: "iniciar", "publicar", "enviar" e "aumentar a versão". "Fazer um push" junta um verbo vazio a um termo em inglês. A reescrita também separa as duas instruções. |
| Condição antes da instrução | "Apague a pasta antiga se a cópia de segurança terminou sem erros." | "Se a cópia de segurança terminou sem erros, apague a pasta antiga." | Quem age antes de ler o fim da frase apaga a pasta e não vê a condição. |

## Parte 2: regras próprias do português europeu

Estas regras não existem no STE. Elas cobrem fontes de ambiguidade do português e o traduzês que os modelos de linguagem produzem. A tabela mostra só os casos que pedem mais do que o exemplo do `SKILL.md`.

| Regra | Antes | Depois | Porquê |
|---|---|---|---|
| "Seu" com dois donos | "O agente enviou ao utilizador o seu token." | "O agente enviou ao utilizador o token do utilizador." | "Seu" pode ser do agente ou do utilizador. "Dele" também não resolve, porque os dois nomes são masculinos. |
| "Dever" ambíguo | "O job deve terminar em cinco minutos." | Se é ordem: "O job tem de terminar em cinco minutos." Se é estimativa: "O job provavelmente termina em cinco minutos." | Uma frase, duas leituras. Se o contexto não decide, a reescrita também não decide. Ela mantém a frase e sinaliza na linha `Mantido como está:`. |
| Sujeito oculto com troca de sujeito | "O cliente envia o pedido ao servidor, que valida o token. Se o token expirou, rejeita o pedido." | "O cliente envia o pedido ao servidor. O servidor valida o token. Se o token expirou, o servidor rejeita o pedido." | O sujeito oculto de "rejeita" pode ser o cliente (sujeito da frase anterior) ou o servidor. A reescrita nomeia o servidor, porque a fonte atribui ao servidor a frase "valida o token". |
| Tratamento uniforme | "Abre o painel. Remova o filtro. Limpar o ecrã." | "Abra o painel. Remova o filtro. Limpe o ecrã." | "Abre" (segunda pessoa) é também a forma de "ele abre". O leitor não sabe se a frase é uma ordem ou uma descrição. O infinitivo "Limpar" muda de registo a meio do procedimento. |
| "Excluir" com dois sentidos | "Exclua os ficheiros temporários do pacote." | Se é apagar: "Apague os ficheiros temporários do pacote." Se é deixar de fora: "Não inclua os ficheiros temporários no pacote." | "Excluir" quer dizer apagar e também deixar de fora. Com "do pacote", as duas leituras fazem sentido. |
| "Carregar" com vários sentidos | "Carregue o ficheiro." | Se é enviar: "Envie o ficheiro para o servidor." Se é obter: "Descarregue o ficheiro do servidor." Se é ler: "Leia o ficheiro." | "Carregar" quer dizer enviar, ler para a memória ou premir. O leitor não sabe a direção da transferência. |
| Estar a + infinitivo | "O job está executando." | "O job está a executar." | O gerúndio de ação em curso é a forma do Brasil. Em Portugal, "estar a" + infinitivo diz o mesmo e soa natural. |
| Vocabulário de Portugal | "Salve o arquivo e baixe o pacote." | "Guarde o ficheiro e descarregue o pacote." | As formas do Brasil denunciam um texto gerado sem cuidado. "Salvar" é resgatar, e "baixar" é diminuir. |
| Colocação do pronome | "O agente o envia ao servidor." | "O agente envia o ficheiro ao servidor." Se o pronome ficar: "O agente envia-o ao servidor." | A ênclise é a colocação normal em Portugal. Repetir o nome evita a dúvida e a colocação errada. |
| Decalque: "eventualmente" | "O cache é eventualmente invalidado." | Se o sentido é "eventually": "O cache é invalidado em algum momento." Se o sentido é "por vezes": "O cache é invalidado por vezes." | Em português, "eventualmente" quer dizer "por vezes" ou "por acaso". Quem escreve a pensar em "eventually" quer dizer "mais cedo ou mais tarde". A voz passiva fica, porque a fonte não diz quem invalida o cache. |
| Decalque: "uma vez que" | "Uma vez que o deploy terminou, o agente liberta o tráfego." | Se é tempo: "Depois de o deploy terminar, o agente liberta o tráfego." Se é causa: "Como o deploy terminou, o agente liberta o tráfego." | Com o indicativo, "uma vez que" indica causa ("já que"). Como decalque de "once", indica tempo. |
| Locução prolixa e verbo-suporte | "O servidor encontra-se indisponível. Favor efetuar uma nova tentativa." | "O servidor está indisponível. Tente de novo." | "Encontra-se" é "está" com mais palavras. "Favor efetuar" junta o infinitivo de cortesia ao verbo-suporte. |

## Parte 3: aplicado à saída de agentes

Estes são exemplos originais, criados para o uso real desta skill. O objetivo é reescrever a saída de agentes de IA. Outro agente, uma camada de tradução ou um leitor estrangeiro precisa de interpretar o texto sem ambiguidade. São ilustrações, não citações de um sistema real.

Cada bloco "Antes" fica entre duas diretivas `deve-falhar` do linter, com as regras que ele precisa de quebrar. O `--autoteste` verifica se cada bloco ainda falha com essas regras. Os blocos "Depois" passam pelo linter como o resto do ficheiro.

### Exemplo A: descrição de ferramenta

**Antes:**

<!-- pts-lint: deve-falhar frase-longa verbo-suporte -->
> Esta ferramenta irá tentar realizar a sincronização do estado entre os diversos backends que foram configurados, e caso um conflito seja detetado ela poderá resolvê-lo automaticamente dependendo da estratégia que tiver sido definida, ou caso contrário irá apresentar o conflito para revisão manual.
<!-- pts-lint: fim -->

**Violações marcadas:**
- Duas instruções numa frase (sincronizar, e depois resolver ou mostrar o conflito).
- Verbo-suporte ("realizar a sincronização").
- Voz passiva nas orações subordinadas ("foram configurados", "seja detetado", "tiver sido definida").
- Futuro ("irá") para descrever o comportamento da ferramenta. A skill descreve o comportamento de um sistema no presente.
- 43 palavras, muito acima do limite de 27 para descrições.

Note o que *não* foi marcado: "tentar" e "poderá resolvê-lo". São ressalvas, não violações. A ferramenta não promete sucesso, e a reescrita também não pode prometer. O "irá" de "irá tentar" é só o tempo futuro. A reescrita troca o futuro pelo presente ("tenta"), e a ressalva continua em "tentar".

**Depois:**
> A ferramenta tenta sincronizar o estado entre os backends configurados. Se encontrar um conflito, a ferramenta lê a estratégia configurada. Se a estratégia permitir resolução automática, a ferramenta pode resolver o conflito automaticamente. Se a ferramenta não resolver o conflito, ela encaminha o conflito para revisão manual.

A última frase depende de a ferramenta resolver ou não o conflito, e não do que a estratégia permite. Esse é o sentido de "ou caso contrário" no original: o caminho alternativo cobre também uma resolução permitida que não aconteceu.

### Exemplo B: mensagem de erro

**Antes:**

<!-- pts-lint: deve-falhar frase-longa -->
> Um erro pode ter ocorrido durante o processamento do seu pedido devido a uma possível incompatibilidade no formato de dados esperado, o que poderia ser causado por uma versão desatualizada do cliente.
<!-- pts-lint: fim -->

**Violações marcadas:**
- Uma frase com três afirmações separadas (um erro, uma incompatibilidade de formato, uma versão de cliente).
- Ação congelada em substantivo ("o processamento do seu pedido").
- 32 palavras, acima do limite de 27 para descrições.

Não marcado: "pode ter ocorrido" e "poderia ser causado por". Quem escreveu a mensagem é um sistema que não sabe o que falhou. As duas ressalvas relatam essa incerteza com exatidão.

**Depois:**
> O seu pedido pode ter falhado. A causa pode ser um formato de dados diferente do formato que o servidor espera. Uma versão desatualizada do cliente pode causar essa diferença.

**A regra da modalidade existe por causa deste exemplo.** Uma reescrita tentadora troca a primeira frase por "O seu pedido falhou". Troca também a terceira por "uma versão desatualizada do cliente **é a causa mais comum**". As duas trocas melhoram a leitura, e as duas estão erradas. A primeira afirma uma falha de que o sistema só suspeita. A segunda inventa uma frequência que não aparece em lado nenhum da entrada. Uma reescrita que fornece uma causa, uma frequência ou um mecanismo é outro texto, não uma reescrita.

Em inglês, "may have failed" mantém uma forma composta que a regra dos tempos não permitiria. Em português, o conflito não aparece nesta frase. "Pode ter falhado" usa o infinitivo composto depois do verbo modal, e a regra dos tempos trata de outra forma ("tem falhado"). Nas duas línguas vale o mesmo princípio. **Quando a regra dos tempos e a regra da modalidade entram em conflito, a modalidade vence.** Sem o auxiliar, a incerteza some junto com o tempo verbal.

### Exemplo C: instrução entre agentes

**Antes:**

<!-- pts-lint: deve-falhar frase-longa verbo-suporte locucao-prolixa -->
> Uma vez que o job upstream tenha sido concluído e assumindo que nenhum erro tenha sido gerado, o agente downstream deverá proceder ao consumo do artefacto de saída, sendo que importa salientar que artefactos parciais eventualmente são produzidos em condições de timeout.
<!-- pts-lint: fim -->

**Violações marcadas:**
- Voz passiva e orações subordinadas empilhadas ("tenha sido concluído", "assumindo que...", "sendo que importa salientar que...").
- Decalques do inglês: "assumindo que" (assuming) e "eventualmente".
- Verbo-suporte ("proceder ao consumo") e expressão de preenchimento ("importa salientar que").
- Uma frase, três factos separados (condição de término, próxima ação, aviso sobre um caso-limite).
- 40 palavras, acima do limite de 22 para instruções.

**Depois:**
> Espere que o job upstream termine sem erros. Depois, leia o artefacto de saída. Atenção: um timeout pode produzir um artefacto parcial. Verifique se o artefacto está completo antes de usar o artefacto.

Decisões que vale a pena declarar em vez de esconder:
- "Deverá proceder ao consumo" virou o imperativo "leia". Aqui o contexto decide o sentido de "dever". A frase é uma instrução para o agente que executa a tarefa, então "deverá" é uma ordem, não uma estimativa. O STE permite a troca por um imperativo em instruções. Não faça a mesma troca em texto descritivo.
- "Uma vez que" tem duas leituras. Com o conjuntivo ("tenha sido concluído"), indica tempo ou condição. Com o indicativo, indica causa. A reescrita usa "Espere que... termine" e "Depois", que só têm a leitura de tempo.
- Aqui, "eventualmente" está certo em português ("por vezes"). Mas um leitor que pensa em inglês lê "eventually". A reescrita usa "pode", que tem uma leitura só.
- A última frase é **nova**. O original avisava sobre artefactos parciais, mas não dizia o que fazer. A verificação torna o aviso útil, mas é conteúdo acrescentado. Por isso, este exemplo declara a frase e não a esconde na reescrita. Se o silêncio da fonte era intencional, corte a frase.
- A última frase repete "o artefacto" em vez de usar o pronome ("antes de o usar"). Assim não há dúvida sobre a referência nem sobre a colocação do pronome.

### Exemplo D: prosa de README (modo Flexível)

**Antes:**

<!-- pts-lint: deve-falhar frase-longa ponto-e-virgula adjetivo-de-marketing -->
> A nossa camada de cache foi projetada para se encaixar perfeitamente na sua stack existente com o mínimo de atrito e sem vendor lock-in; ela alavanca a similaridade semântica para reduzir drasticamente os cache misses que tradicionalmente atormentam as cargas de trabalho de LLMs.
<!-- pts-lint: fim -->

**Violações marcadas:**
- Adjetivos e afirmações de marketing sem medida ("perfeitamente", "com o mínimo de atrito", "drasticamente").
- Ponto e vírgula entre duas ideias separadas.
- Decalque e jargão ("alavanca", "vendor lock-in").
- Voz passiva ("foi projetada").
- 43 palavras, acima do limite de 27 para descrições.

**Depois:**
> Este cache usa a similaridade semântica entre prompts para reduzir os cache misses, um problema comum em aplicações de grandes modelos de linguagem (LLM). Ele funciona com a stack existente e não prende o utilizador a um fornecedor.

O modo Flexível não impôs um termo fixo por conceito. Ainda assim, cortou os adjetivos de marketing, o ponto e vírgula, o decalque e a frase longa. A reescrita não explica como um cache comum funciona, porque a fonte não explica.

### Exemplo E: documento com estrutura (ISO 24495-1)

Este exemplo mostra as regras de estrutura do `SKILL.md`: mensagem principal primeiro, passos numerados e uma ideia por parágrafo. O linter só verifica as formas mecânicas (siglas, títulos, tamanho do parágrafo, passos em prosa).

**Antes** (o linter só dá um achado consultivo, `passos-em-prosa`):

> Este procedimento aplica-se quando a cópia de segurança falha. Primeiro verifique o espaço livre no disco, depois apague as cópias antigas e por fim execute a cópia de segurança de novo. Nos últimos meses a cópia falhou algumas vezes por falta de espaço.

Ficam por assinalar duas decisões de leitura. A mensagem principal (o que fazer) vem depois do contexto, e o contexto histórico ("nos últimos meses") não ajuda quem executa os passos.

**Depois:**

> **Se a cópia de segurança falhar, liberte espaço e execute-a de novo.**
>
> 1. Verifique o espaço livre no disco.
> 2. Apague as cópias antigas.
> 3. Execute a cópia de segurança.
>
> Nos últimos meses, a cópia de segurança falhou algumas vezes por falta de espaço.

A última frase mantém o dado histórico da fonte, no fim, e não acrescenta nenhuma frequência. Quem não precisa do historial lê só a primeira linha e a lista.

## Como ler estes exemplos

A Parte 1 ilustra as regras do STE em que esta skill se baseia. A Parte 2 ilustra as regras que o português europeu acrescenta. A Parte 3 aplica as regras à saída de agentes. A mesma disciplina torna mais seguro interpretar o texto entre máquinas e entre línguas, não só os manuais de aeronaves. Essa disciplina é: um significado por palavra, voz ativa, tempos simples, uma instrução por frase e condições explícitas em vez de orações subordinadas escondidas.
