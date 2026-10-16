---
name: portugues-tecnico-simplificado-pt
description: "Use quando um texto em português europeu (pt-PT) precisa de ser interpretado sem um humano para resolver ambiguidades (descrições de ferramentas, mensagens de erro, instruções entre agentes, prompts de sistema, relatórios de estado) e uma leitura errada tem custo real, ou quando o texto está denso, cheio de ressalvas ou fácil de interpretar mal. Gatilhos: desambiguar, português técnico simplificado, aplicar o STE100 em português, reescrever para que um agente não interprete mal, tirar o traduzês, linguagem clara para agentes. In English: Simplified Technical Portuguese, an STE100-style rewrite of European Portuguese text, informed by ISO 24495-1. Não serve para textos criativos, de marketing nem para linguagem clara dirigida ao cidadão."
version: 0.1.0
---

# Português Técnico Simplificado (pt-PT)

O ASD-STE100 (Simplified Technical English, ou STE) é uma norma de linguagem controlada da indústria aeroespacial e de defesa. A ASD (AeroSpace and Defence Industries Association of Europe) mantém a norma. O objetivo dela é impedir que técnicos de manutenção interpretem mal instruções em inglês. A norma ataca as duas maiores fontes de erro de leitura: palavras com mais de um significado e frases com mais de uma estrutura possível.

O STE existe só em inglês, e não há norma equivalente para o português. Esta skill leva a mesma disciplina para o português europeu e para outro leitor: um **agente de IA ou um sistema**. Esse leitor precisa de interpretar um texto sem um humano para resolver ambiguidades. O texto pode ser uma mensagem de erro, a descrição de uma ferramenta, uma instrução entre agentes ou um relatório de estado. Um humano pode ler "o job deve terminar em cinco minutos" como ordem ("tem de terminar") ou como estimativa ("provavelmente termina"). Um modelo de linguagem também pode.

A skill junta ao STE os princípios da ISO 24495-1 (linguagem clara): o texto é relevante, localizável, compreensível e utilizável. A ISO escreve para leitores humanos. Por isso a skill adapta alguns pontos para um leitor-máquina (veja Fontes e escopo).

## Quando usar esta skill

- A saída de um agente (explicação, instrução, mensagem de registo, descrição de ferramenta) está densa, cheia de jargão ou ambígua.
- Outro agente, um pipeline de tradução ou um leitor que não tem o português como primeira língua vai ler o texto. Uma leitura errada tem custo real.
- Está a escrever um prompt, uma mensagem de sistema ou a descrição de uma ferramenta. O objetivo é tirar a ambiguidade antes de um modelo ler o texto.
- Um modelo gerou o texto em português, e o texto tem traduzês. Exemplos: decalques do inglês, gerundismo, "o mesmo" no lugar de pronome, vocabulário do português do Brasil e "seu" em excesso.
- Quer uma comparação **antes e depois** que mostre qual regra o texto violou e como a reescrita corrige o problema. Peça explicitamente. A saída predefinida é só o texto reescrito (veja Formato da saída).

Esta skill não serve para textos criativos nem de marketing. O estilo do STE é plano e literal de propósito. Não aplique a skill a um texto em que a voz, a nuance ou a persuasão são o objetivo. Ela também não é uma ferramenta de linguagem clara para o cidadão. Ela escreve para leitores técnicos e para máquinas.

## Dois modos

Escolha um modo antes de reescrever. Se o utilizador não disser qual, deduza o modo pelo tipo de texto. Informe o modo só quando o utilizador pedir a tabela de regras (veja Formato da saída).

**Estrito**: procedimentos, mensagens de erro, descrições de ferramentas e funções, instruções entre agentes, textos de segurança. Vale para todo o lugar onde uma leitura errada tem custo. Aplique todas as regras abaixo, incluindo os limites de palavras e a disciplina de uma palavra para um significado.

**Flexível**: READMEs, descrições de pull request, changelogs, prosa explicativa. Aplique as regras estruturais por inteiro e trate as regras lexicais como recomendação (veja a divisão em Regras centrais). Na prática, mantém os limites de palavras, a voz ativa e os tempos simples. Mantém também a proibição de ponto e vírgula, verbo-suporte, gíria técnica, locuções prolixas e adjetivos de marketing. Abandona o vocabulário fixo. A prosa precisa de alguma variedade, e uma reescrita estrita de prosa parece um transplante de personalidade, não um esclarecimento.

Os dois modos e a divisão entre regras estruturais e lexicais são a mesma distinção vista de dois lados. A divisão diz quais regras esta skill consegue verificar sem um dicionário. Os modos dizem quais delas impor em cada tipo de texto.

## Fontes e escopo

Esta skill segue as **categorias de regras** do ASD-STE100 Issue 9 (janeiro de 2025). A norma tem 53 regras de redação em 9 secções: escolha de palavras, gramática, estrutura da frase e estilo. Ela tem também um dicionário de cerca de 900 palavras aprovadas, cada uma com um significado e uma classe gramatical. O dicionário lista ainda cerca de 1200 palavras a evitar, com substitutas sugeridas. O resumo e as paráfrases estão em `references/regras-de-redacao.md`.

A skill **não** reproduz o dicionário do ASD. O ASD-STE100 é gratuito, mas a redistribuição não é livre. O Issue 9 (página 2) proíbe a reprodução sem autorização escrita de um dirigente do ASD. Além disso, o dicionário é de palavras inglesas e não serve para o português.

A skill usa também a **ISO 24495-1:2023**, adotada em Portugal como NP ISO 24495-1:2024 ("Linguagem clara. Parte 1: Princípios de base e orientações"). A skill parafraseia a norma e não a reproduz. Os números das cláusulas citados abaixo seguem a ISO. O ficheiro `docs/MAPEAMENTO-ISO-24495-1.md` diz o que a skill adotou, o que adaptou e o que não aplica. Em resumo:

- A ISO pede um tom dirigido ao leitor ("tu" ou "você"). A skill usa o imperativo sem pronome e a terceira pessoa (veja Tratamento uniforme).
- A ISO pede variação no tamanho das frases, para dar ritmo. A skill não pede essa variação, porque um agente não precisa de ritmo.
- A ISO pede imagens de apoio e testes com leitores. A skill não trata imagens, e o teste passa a ser a execução da tarefa por um agente.

Esta skill aplica o *princípio* do STE: a palavra mais simples e comum, usada sempre do mesmo modo. Ela adapta as regras estruturais à gramática do português europeu. Acrescenta também regras para fontes de ambiguidade que o inglês não tem. Exemplos: o "dever" ambíguo, o "seu" com dois donos, o sujeito oculto e a colocação do pronome.

A referência de língua é a norma culta de Portugal. A ortografia segue o Acordo Ortográfico de 1990, tal como se aplica em Portugal ("facto", "contacto", "receção", "ação", "objetivo"). A flexão e o vocabulário seguem o Vocabulário Ortográfico do Português (VOP) e o dicionário Priberam. Os números seguem o Sistema Internacional de Unidades (SI), e as datas seguem a ISO 8601.

## Regras centrais

As regras do STE são de dois tipos, e esta skill só consegue cumprir um deles por inteiro. As **regras estruturais** são autossuficientes: descrevem a forma da frase, e aplicam-se só pela descrição. As **regras lexicais** dependem por inteiro de um dicionário aprovado. O dicionário do ASD é em inglês, e não existe um equivalente em português. Sem dicionário, as regras lexicais são só uma preferência por palavras simples, não uma norma verificável.

Aplique as regras estruturais com confiança. Aplique as regras lexicais como uma direção. Quando mostrar a tabela de regras, diga isso, e não sugira uma conformidade com dicionário que não pode verificar.

### Regras estruturais: aplique

| Regra | Faça | Não faça |
|---|---|---|
| Voz ativa (ISO 5.3.3 c) | "O agente apaga o ficheiro." | "O ficheiro é apagado pelo agente." ou "Apaga-se o ficheiro." A partícula "se" também esconde quem age. Use a voz passiva só quando quem age é desconhecido ou irrelevante. |
| Verbo pleno, sem verbo-suporte (Regra 3.7) | "Analise o registo." / "Remova o painel." | "Efetue uma análise do registo." / "Proceda à remoção do painel." / "Dê início ao processo." O substantivo de ação alonga a frase e esconde quem age. |
| Sem locuções verbais idiomáticas nem gíria técnica (Regra 9.3) | "O job parou de executar." / "Inicie o servidor." / "Envie a branch para o repositório remoto." | "O job deixou de correr." (parou, ou não correu desta vez?) / "Suba o servidor." / "Faça um push da branch." O sentido de uma locução verbal não vem das partes. "Subir" sozinho tem quatro sentidos: "iniciar", "publicar", "enviar" e "aumentar a versão". |
| Sem locuções prolixas | "para", "porque", "sobre", "está" | "de forma a", "por forma a", "tendo em conta que", "no que diz respeito a", "no âmbito de", "a nível de", "encontra-se", "sendo que". Várias palavras no lugar de uma alongam a frase e não acrescentam sentido. |
| Uma instrução por frase (ISO 5.3.4 a) | "Abra o ficheiro. Leia a linha 3." | "Abra o ficheiro e leia a linha 3, depois confirme se ela corresponde." |
| Condição antes da instrução (ISO 5.2.2 e) | "Se a cópia de segurança terminou, apague a diretoria." | "Apague a diretoria se a cópia de segurança terminou." Quem age antes de ler o fim da frase não vê a condição. Um aviso de segurança também vem antes da ação. |
| Tamanho da frase | Até 22 palavras em instruções e procedimentos, até 27 em descrições. O STE usa 20 e 25, e o português usa cerca de 7% mais palavras. | Frases longas com orações coordenadas e subordinadas em cadeia |
| Sem ponto e vírgula (Regra 8.1) | Divida em frases separadas. | Qualquer ponto e vírgula, incluindo o fim de itens de lista no estilo jurídico ("I - ...; II - ...; e"). A Regra 8.1 permite todos os outros sinais. O travessão não é proibido, mas costuma indicar uma frase que precisa de ser dividida. |
| Ordem direta, sem intercaladas (ISO 5.3.3 a) | "Se o token expirou, o servidor rejeita o pedido." | "O servidor, caso o token, emitido pelo serviço de autenticação, tenha expirado, rejeita o pedido." Um inciso entre o sujeito e o verbo corta a ideia principal. |
| Cadeias de "de" | No máximo dois "de" seguidos num grupo nominal ("a válvula da bomba de combustível") | "a válvula de entrada do conjunto da bomba de combustível de alta pressão". O grupo nominal empilhado do inglês vira uma cadeia de "de" em português. O STE permite três substantivos ("fuel pump valve"), e três substantivos usam dois "de". |
| Sujeito explícito quando ele muda | "O cliente envia o pedido. O servidor valida o pedido." | "O cliente envia o pedido. Valida o pedido." O português permite sujeito oculto. Quando o sujeito muda, o leitor não sabe quem age. |
| Sem elipse | "Os pedidos sem fatura foram cancelados." | "Pedidos sem fatura cancelados." O estilo telegráfico tira o verbo, e o leitor não sabe se a frase é um relato ou uma ordem. |
| Referência sem ambiguidade | "O agente enviou ao utilizador o token do utilizador." / "Antes de apagar o ficheiro, copie o ficheiro." | "O agente enviou ao utilizador o seu token." (de quem?) / "Antes de apagar o ficheiro, copie o mesmo." ("o mesmo" no lugar de pronome) |
| Pronome pouco usado e na posição certa | Repita o nome: "Abra o ficheiro. Leia o ficheiro." Se usar o pronome, use a ênclise do português europeu: "O agente envia-o." Depois de negação, de "que" ou de um advérbio, use a próclise: "O agente não o envia." | "Abra-o e leia-o." quando o nome está longe. O pronome mal colocado ("O agente o envia.", norma do Brasil) soa errado em Portugal. A mesóclise ("enviá-lo-á") é rara e confunde. Use o presente ou "vai" + infinitivo. |
| "Ser" para essência, "estar" para estado | "O servidor está indisponível." / "O job está a executar." | "O servidor é indisponível." / "O job executa." para dizer o que acontece agora. "Ser" e o presente simples dizem o que a coisa é sempre ou faz por hábito ("O job executa todas as noites"). |
| Preserve a modalidade | "O pedido **pode ter** falhado." continua "pode ter falhado". | Promover uma ressalva a facto ("O pedido falhou.") ou inventar uma certeza que a fonte não deu. Em português, "deve" é ambíguo: ordem ou estimativa. Se a fonte é ambígua, não escolha em silêncio. |
| Tratamento uniforme (ISO 5.3.3 b, adaptada) | Imperativo sem pronome, em todo o documento: "Remova", "Clique", "Verifique". Nas descrições, a terceira pessoa: "A ferramenta remove o painel." | "Tu" ou "você". Misturar "Remova" com "Remove" ou "Clica" (tu), ou com instruções no infinitivo ("Remover o painel"), no mesmo documento. "Remove" também é "ele remove", e o leitor não sabe se a frase é uma ordem ou uma descrição. |
| Género da norma | "Os utilizadores recebem o token." / "A equipa recebe o token." | "Todes", "elu", "todxs", "tod@s". Estas formas estão fora do VOP e das regras de concordância, e o leitor não consegue prever o artigo, o adjetivo e o pronome. As formas duplas ("os utilizadores e as utilizadoras", "utilizador(a)") são corretas, mas alongam a frase. |
| Números | "1000 pedidos", "10 000 pedidos", "1,5 s" | "1.000 pedidos". Um leitor treinado em inglês lê "1.000" como 1,0. O SI agrupa os dígitos com espaço, nunca com ponto. Esse leitor também lê "1,500 s" como 1500 s: mude a unidade ("1500 ms"). Num valor que um programa vai ler, use o formato do programa num trecho de código (`1.5`). |
| Datas | "2026-10-07" (ISO 8601). Sem o ano: "7 de outubro". | "07/10/2026" ou "07/10". Um leitor treinado em inglês lê mês/dia, e "07/10" vira 10 de julho. |
| Siglas (ISO 5.3.2 d, e) | O nome por extenso na primeira ocorrência: "tempo de vida (TTL)". As siglas comuns e bem conhecidas podem ficar. | Uma sigla que o texto nunca define. O leitor não tem a quem perguntar o que ela quer dizer. |
| Limites de parágrafo (ISO 5.3.5) | Um tópico por parágrafo, enunciado perto do início, até 6 frases | Parágrafos com vários tópicos |
| Listas para sequências (ISO 5.2.3 e) | Uma lista numerada ou com marcadores para 3 ou mais passos ou condições | Uma sequência escondida numa frase só |

### Regras de estrutura do documento (ISO 24495-1)

Estas regras vêm do Princípio 2 (localizável) da ISO. O linter ainda não as verifica, por isso exigem leitura.

| Regra | Faça | Não faça |
|---|---|---|
| Mensagem principal primeiro (ISO 5.2.2 a) | Abra com o resultado, a ordem ou a conclusão. "A ferramenta apaga o ficheiro. Ela falha se o ficheiro não existir." | Abrir com contexto, historial ou desculpas antes de dizer o que importa. |
| Do conhecido para o novo (ISO 5.2.2 b, 5.3.3 a 4) | Comece a frase pelo que o leitor já viu e acabe no que é novo. | Introduzir um termo novo no início da frase, sem apoio no que veio antes. |
| Para a maioria primeiro (ISO 5.2.2 d) | Ponha o caso comum antes dos casos raros. | Misturar a exceção rara com o fluxo normal. |
| Títulos que descrevem (ISO 5.2.4) | Um título por tópico, curto, consistente e sem saltar de nível. | Títulos vagos ("Notas"), repetidos ou que prometem o que a secção não diz. |
| Informação complementar à parte (ISO 5.2.5) | Anexo, nota final ou ligação para a base legal, as fontes e os detalhes que só alguns leitores usam. | Deixar esses detalhes no meio do fluxo principal. |
| Tom neutro (ISO 5.3.7) | Numa mensagem de erro, diga o que falhou e o que fazer. "O ficheiro não existe. Indique um ficheiro que exista." | Culpar o utilizador ("O utilizador errou o caminho.") ou dramatizar. |

### Regras lexicais: só direção

| Regra | Faça | Não faça | Porque a regra é mais fraca aqui |
|---|---|---|---|
| Uma palavra, um significado (ISO 5.3.2 g) | Escolha um verbo para uma ação e use-o sempre. Por exemplo, sempre "verifique", sem alternar "verifique", "confirme", "controle" e "valide" para a mesma ação. Evite também as palavras com dois sentidos no mesmo contexto. | Alternar sinónimos para a mesma ideia ao longo do documento. Escrever "exclua o ficheiro do pacote", que pode ser apagar o ficheiro ou deixar o ficheiro de fora. Escreva "apague" ou "não inclua". | A consistência dentro do documento é verificável. Qual palavra é a *aprovada* não é, porque não existe dicionário aprovado para o português. |
| Uma classe gramatical por palavra | "Registe o evento no registo." (registo = substantivo) | "Logue o evento." (log virou verbo) | Sem dicionário, não há lista das palavras que são só substantivo. Prefira a forma substantiva quando as duas se leem bem. Não declare conformidade. |
| Termos de domínio (ISO 5.3.2 c) | Mantenha os termos técnicos necessários e defina cada um uma vez se ele não for comum. O STE permite um glossário próprio do projeto além do dicionário-base. | Jargão que o texto nunca define | A permissão de glossário existe no STE, mas o dicionário-base que ela estende não existe em português. |
| Vocabulário de Portugal | "ficheiro", "ecrã", "equipa", "utilizador", "pedido", "palavra-passe", "descarregar", "guardar", "aceder", "registo" | O vocabulário do português do Brasil: "arquivo", "tela", "equipe", "usuário", "requisição", "senha", "baixar", "salvar", "acessar", "log" como substantivo comum | Quem lê pt-PT estranha as formas brasileiras, e o desvio sinaliza texto gerado sem cuidado. O limite varia por equipa. O glossário do projeto decide. |
| Palavras de dois sentidos em pt-PT | "Envie o ficheiro" (upload), "descarregue o ficheiro" (download), "prima Enter" (tecla), "carregue o módulo" só se o glossário disser que "carregar" é "ler para a memória". / "A hiperligação abre a página." / "A ligação de rede falhou." / "Execute o programa." | "Carregue o ficheiro." ("carregar" é enviar, ler para a memória ou premir). "A ligação abriu a página." ("ligação" é link ou ligação de rede.) "O programa corre." ("correr" é executar ou fluir.) "O registo falhou." (log ou registo de um dado?) | O português de Portugal tem estas ambiguidades próprias. Sem glossário, escolha a forma sem dupla leitura. |
| Estrangeirismos e falsos cognatos | Use a palavra portuguesa consolidada: "apagar", "definir", "desempenho", "obrigatório". Mantenha empréstimos técnicos consolidados (commit, deploy, backup) e defina-os se o leitor puder não os conhecer. | "Deletar", "setar", "performance", "performar", "mandatório". Falsos cognatos: "eventualmente" (= por vezes, não "por fim"), "assumir que" (= supor), "endereçar o problema" (= tratar), "suportar JSON" (= aceitar), "realizar que" (= perceber). | O limite entre empréstimo consolidado e anglicismo evitável varia por equipa. O glossário do projeto decide. |

### Tempos verbais: aplique com exceções

O STE permite infinitivo, imperativo, presente simples, passado simples, futuro simples e particípio passado usado como adjetivo. A norma não permite o present perfect nem as outras formas compostas.

Em português europeu, a regra muda em quatro pontos:

1. **O pretérito perfeito simples já cobre o present perfect do inglês.** "The job has completed" é "O job terminou" (ou "já terminou"). Não traduza por "O job tem terminado". Em português, "tem" + particípio indica repetição ou continuidade até agora: "o build tem falhado desde segunda-feira" quer dizer que ele falhou várias vezes. Use o tempo composto só quando a repetição é o ponto, e sinalize.
2. **"Estar a" + infinitivo fica.** O STE não permite a forma em "-ing" como verbo. Em português europeu, "o job está a executar" diz o que acontece agora, e "o job executa" diz o que acontece por hábito. Mantenha "estar a" + infinitivo em relatórios de estado (veja a regra de "ser" e "estar"). Em Portugal, "está executando" soa a Brasil.
3. **Futuro.** Descreva o comportamento de um sistema no presente: "A ferramenta apaga o ficheiro." Quando o tempo importa, use o futuro simples ("apagará") ou "vai" + infinitivo ("vai apagar"). Use uma só dessas formas no documento. Não use gerundismo para uma ação pontual ("vamos estar a enviar"). Uma ação que dura um período pode ficar: "a cópia de segurança vai estar a executar durante a janela".
4. **Gerúndio.** Fora de casos fixos, use o gerúndio só para ações simultâneas. Considere "O agente lê o ficheiro, gerando um relatório". A oração com gerúndio não diz se a segunda ação é simultânea, posterior ou consequência da primeira. Escreva duas frases. "Incluindo" e "dependendo de" funcionam como preposições e podem ficar. Em português europeu, "a" + infinitivo substitui o gerúndio de ação em curso ("a gerar" no lugar de "gerando").

Evite também o mais-que-perfeito simples ("falhara"). Ele difere do futuro ("falhará") só pelo acento. Use o mais-que-perfeito composto ("tinha falhado") só quando a ordem dos eventos importa.

**A modalidade é a exceção.** As formas compostas com verbo modal carregam a ressalva. Exemplos: "pode ter falhado", "deve ter bloqueado", "talvez tenha falhado" e "teria falhado". No jornalismo, "teria falhado" quer dizer "supostamente falhou". Mantenha essas formas. Quando a regra dos tempos e a regra da modalidade entram em conflito, a modalidade vence.

## Lista de varredura

Os hábitos abaixo explicam a maior parte da dificuldade de ler um texto em português gerado por máquina. Os hábitos de 1 a 8 são mecânicos: aponte a palavra ou o sinal exato que quebra a regra. Os hábitos de 9 a 11 pedem julgamento, porque a mesma palavra às vezes está certa. Procure todos antes de reescrever.

1. **Rotação de sinónimos**: a mesma coisa recebe vários nomes no mesmo documento ("o utilizador", "o cliente", "o consumidor"). O leitor não sabe se é uma coisa ou três. Correção: escolha um nome e use-o sempre.
2. **Empilhamento de ressalvas**: verbos auxiliares e qualificadores acumulam-se até a frase não afirmar nada ("importa salientar que isto pode potencialmente ajudar a melhorar"). Correção: afirme o facto ou corte a frase.
3. **Verbo-suporte**: uma ação congelada num substantivo ("efetuar a análise de", "realizar o pagamento", "proceder à remoção", "fazer uso de", "dar início a"). Correção: use o verbo ("analisar", "pagar", "remover", "usar", "iniciar").
4. **Adjetivos de marketing**: palavras que afirmam qualidade em vez de a mostrar. Por exemplo: "robusto", "poderoso", "inovador", "intuitivo", "de ponta", "revolucionário", "sem esforço". Correção: corte, ou troque pela medida que justifica a afirmação.
5. **Frases encadeadas**: várias ideias ligadas por ponto e vírgula, travessão, "sendo que" ou gerúndio depois de vírgula. Correção: uma ideia por frase.
6. **Gerundismo**: "vou estar a enviar", "vamos estar a verificar". Correção: "vou enviar", "verificaremos".
7. **Gíria técnica e locuções verbais**: "subir o servidor", "fazer um push", "bater no endpoint", "deixar de correr", "acabar com o processo". O sentido não vem das partes. Correção: o verbo exato ("iniciar", "enviar", "chamar", "parar de", "apagar").
8. **Números e datas ambíguos**: "1.000", "07/10/2026". Correção: "1000", "2026-10-07" ou, sem o ano, "7 de outubro".
9. **Decalques do inglês**: construções copiadas do inglês. Exemplos: "eventualmente" no sentido de "por fim", "assumir que", "endereçar o problema", "suportar o formato" e "alavancar". Outros: "uma vez que" no sentido de "depois de" e o "seu" em excesso ("Abra o seu navegador" em vez de "Abra o navegador"). Modelos treinados sobretudo em inglês produzem este traduzês com frequência. Correção: use a construção do português.
10. **Referência solta**: "o mesmo" ou "a mesma" no lugar de um nome, "seu" ou "sua" com dois donos possíveis, um pronome longe do nome. Correção: repita o nome.
11. **Marcas do português do Brasil**: vocabulário ("arquivo", "tela", "usuário", "baixar") e gerúndio de ação em curso ("está rodando"). Outras marcas: pronome antes do verbo ("Me envie", "O agente o envia") e "você". Correção: a forma de Portugal ("ficheiro", "ecrã", "utilizador", "descarregar", "está a executar", "Envie-me", "O agente envia-o").

## Processo

1. Fixe o leitor, o objetivo e o contexto (ISO 5.1). Quem lê o texto (agente, pipeline, pessoa)? O que faz o leitor com ele? O leitor pode pedir esclarecimentos? Se o texto vai para um agente que não pode perguntar, aplique o modo Estrito.
2. Escolha o modo (Estrito ou Flexível). Informe o modo só quando o utilizador pedir a tabela de regras (veja Formato da saída).
3. Leia o texto uma vez pelo sentido. Não comece a reescrever antes de entender o que o texto ainda precisa de dizer depois.
4. Percorra o texto frase por frase. Marque cada violação das tabelas de Regras centrais e cada hábito da Lista de varredura. No modo Flexível, marque as regras lexicais, mas não as imponha. Para uma primeira passagem mecânica, execute `scripts/pts-lint.py` (stdin ou ficheiros, `--json` para saída estruturada, `--ajuda` para as regras e as opções). O linter nunca marca ressalvas nem modalidade. Ele trata o texto entre aspas como menção e não o analisa. Ele não verifica a ordem direta, o sujeito oculto, o "seu" ambíguo, o "dever" ambíguo, a colocação do pronome nem o tratamento misto. Também não verifica as regras de estrutura do documento.
5. Reescreva cada frase marcada. Corrija a violação e preserve o sentido original com exatidão. Se a reescrita perder uma precisão necessária (uma condição de segurança, um limite de escopo, um número), mantenha a forma longa e sinalize. Não simplifique em silêncio.
   - **Verifique a modalidade antes de fechar a reescrita.** Ressalvas ("pode", "poderia", "por vezes", "é provável que") carregam o grau de certeza do autor, e o grau de certeza é conteúdo. Uma frase mais curta que promove uma ressalva a facto não é uma simplificação. É outra afirmação. Este é o erro mais comum numa reescrita bem-intencionada, porque as ressalvas são justamente o que o limite de palavras convida a cortar.
   - **Não resolva sozinho a ambiguidade de "dever".** Se a fonte diz "o job deve terminar em cinco minutos" e o contexto não diz se é ordem ou estimativa, não escolha. Mantenha a frase e sinalize na linha `Mantido como está:`.
   - Nunca acrescente um facto que a fonte não afirmou. Uma reescrita que fica melhor porque fornece uma causa, uma frequência ou um mecanismo é outro texto, não uma reescrita.
6. Entregue o texto reescrito (veja Formato da saída). Guarde para si a escolha de modo e a análise das regras, a menos que o utilizador peça para as ver.
7. Se o texto já está conforme, diga isso. Não force mudanças num texto conforme.
8. Quando o custo de um erro é alto, teste o resultado: peça a um agente que execute a tarefa a partir do texto reescrito, sem outro contexto. Se o agente falhar, o texto ainda tem uma ambiguidade (ISO 5.4, adaptada).

## Formato da saída

**Predefinição: o texto reescrito, e nada mais.** Quem chama a skill quase sempre quer um resultado para colar direto numa descrição de ferramenta, numa cadeia de erro ou num prompt. Mostre só o texto simplificado. Não acrescente preâmbulo sobre esta skill, anúncio de modo, contagem de violações, resumo das mudanças, tabela de regras nem oferta final de explicação.

O único acréscimo permitido: se o passo 5 manteve uma forma longa de propósito, acrescente uma linha depois do texto com o prefixo `Mantido como está:`. A linha nomeia o trecho e a precisão que se perderia. Omita a linha quando não houver nada a informar.

**Sob pedido: a tabela de regras.** O utilizador pode pedir para ver o raciocínio: "mostre o diff", "quais regras quebrou", "explique as mudanças", "antes e depois". Nesse caso, entregue esta tabela no lugar do texto:

```markdown
| Regra violada | Original | Simplificado |
|---|---|---|
| Tempo composto (decalque do present perfect) | "Temos recebido o seu pedido." | "Recebemos o pedido." |
| Cadeia de "de" (3 ou mais) | "o módulo de controlo de prioridade da fila de tarefas do agente" | "o módulo que define a prioridade na fila de tarefas do agente" |

Modo: Estrito. 7 violações encontradas.
```

Depois da tabela, escreva uma linha sobre o que **não** simplificou de propósito, e porquê. Em geral, a simplificação perderia uma precisão necessária.

## Documentação num repositório de código

Quando o texto está num repositório (comentários, docstrings, READMEs, textos de ajuda), edite os ficheiros no lugar. Não imprima o texto. Aplique também estas regras:

- **Modo pelo tipo de texto.** Comentários, docstrings e documentos Markdown usam o modo Flexível. Mensagens de erro, de panic e de registo usam o modo Estrito. A ajuda da linha de comandos também usa o modo Estrito.
- **Mexa só na prosa.** Não mude código, identificadores, trechos de código, destinos de ligações nem textos de títulos (os títulos são âncoras de ligações). Mantenha a largura de linha do ficheiro. Identificadores e nomes de opções em inglês continuam em inglês.
- **Procure nos testes antes de mudar uma mensagem.** Os testes muitas vezes comparam parte de uma cadeia de erro (`should_panic(expected = …)`, `assert!(msg.contains(…))`, ficheiros de snapshot). Mantenha cada trecho comparado.
- **Atualize todas as cópias.** Um texto de ajuda ou um parágrafo de documentação pode ter uma cópia idêntica noutro ficheiro. Mude todas as cópias juntas.
- **Documentação contra código.** Quando um comentário e o código discordam, não ajuste a prosa a nenhum dos lados em silêncio. Mostre a evidência (a linha de código, um teste, um programa pequeno) e pergunte qual lado é a intenção.
- **Descreva o estado atual.** A documentação diz o que o código faz agora, não como ele mudou. `--ativar historico` marca frases de changelog ("já não", "anteriormente", "atualmente").
- **Compile e teste depois.** Execute a geração da documentação e os testes. Um comentário de documentação movido pode mudar a resolução das ligações dele.

## Limites

**A skill faz:**
- Reescreve um português ambíguo ou denso em frases curtas, de significado único e na voz ativa.
- Devolve só o texto reescrito por predefinição, e nomeia as regras aplicadas quando o utilizador pede.
- Preserva cada facto, condição e limite de escopo do original.
- Preserva a força de cada ressalva e não acrescenta afirmações que a fonte não fez.
- Usa o vocabulário, a ortografia e a gramática do português europeu.
- Usa a flexão de género da norma culta: o masculino genérico ou um nome sem flexão de género.
- Sugere uma entrada de glossário de uma linha para os termos de domínio que precisam de ficar.

**A skill não faz:**
- Reproduzir o dicionário oficial de cerca de 900 palavras do ASD como se o tivesse memorizado. Para a redação aprovada em inglês, a transferência oficial é sempre a fonte de verdade.
- Reproduzir o texto da ISO 24495-1 ou da NP ISO 24495-1. Ela só a parafraseia.
- Simplificar textos criativos, de marketing ou persuasivos, em que a voz e a nuance são o objetivo.
- Converter texto do português do Brasil para o de Portugal como tarefa principal. Ela corrige as marcas do português do Brasil que encontra, mas o objetivo é a ambiguidade.
- Cortar em silêncio uma condição de segurança, uma exceção ou um limite de escopo para encurtar uma frase. Ela sinaliza a troca.
- Converter "pode ter falhado" em "falhou", ou "pode ser causado por X" em "X é a causa". Perder uma ressalva muda a afirmação.
- Escolher em silêncio entre os dois sentidos de "dever" (ordem ou estimativa).
- Garantir um documento conforme ao STE nem à ISO 24495-1. O STE é uma norma em inglês, e a ISO escreve para leitores humanos. Esta skill é uma ferramenta geral de clareza inspirada nas duas, não uma ferramenta certificada.
- Revisar ortografia e gramática como objetivo principal. A skill trata de ambiguidade.
- Tornar verdadeiro ou útil um conteúdo fraco. O STE corrige a *forma* de um texto, não a substância. Um parágrafo vazio reescrito com estas regras vira um parágrafo vazio limpo, curto e bem pontuado. Se o texto não tem nada a dizer, nenhuma reescrita resolve isso. Diga isso em vez de polir o texto.
- Encurtar além do ponto da clareza. O objetivo não é cortar palavras, é tirar a ambiguidade. A partir de certo ponto, a compressão começa a custar tempo ao leitor em vez de economizar. Pare quando a frase não tiver ambiguidade, não quando ela for a mais curta possível.

## Recursos adicionais

- **`references/regras-de-redacao.md`**: resumo das regras e do dicionário do STE, a adaptação de cada regra ao português e as fontes.
- **`docs/MAPEAMENTO-ISO-24495-1.md`**: o que a skill adotou, adaptou ou não aplica da ISO 24495-1.
- **`examples/antes-depois.md`**: exemplos comentados. Inclui ilustrações das regras do STE, regras próprias do português e exemplos de saída de agentes criados para esta skill.
- **`scripts/pts-lint.py`**: linter determinístico das regras estruturais, só com a biblioteca padrão do Python. Ele sai com código 1 quando as violações obrigatórias passam de `--linha-de-base` (predefinição 0). Os achados consultivos nunca reprovam a execução. `--autoteste` executa os testes internos e analisa os documentos desta skill. `--ajuda` mostra as regras e as opções.
