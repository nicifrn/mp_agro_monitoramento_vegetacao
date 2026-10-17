# Plano de trabalho - Monitoramento da vegetação do Agreste potiguar por imagens de satélite (NDVI)

**Estudante:** Victor (@Genneton-Aguiar) - Tecnologia em Sistemas para Internet

**Orientadores:** Prof. Bruno Gomes (@brunogomesifrn) e Entony (@franciscoentony) - NIC/IFRN

**Repositório:** https://github.com/nicifrn/mp_agro_monitoramento_vegetacao

**Período:** 16/10/2026 a 10/12/2026: 8 sprints de 1 semana (de sexta a quinta-feira).

**Projeto pai:** AgroAgreste, observatório territorial da agricultura familiar no Agreste do Rio Grande do Norte (resumo em [`docs/projeto_agroagreste.md`](projeto_agroagreste.md)).

**Trabalho escrito:** um **artigo**, no **formato de TCC do NIC**, seguindo as normas de [`docs/orientacoes_escrita_tcc.md`](orientacoes_escrita_tcc.md).

> **Leia este documento inteiro antes de começar a Sprint 1.** Ele é a referência completa do seu trabalho: tudo o que você vai programar, pesquisar e escrever está aqui, sprint por sprint. As *issues* do GitHub são o resumo de cada semana e sempre apontam para a seção correspondente deste documento. Se uma *issue* e este documento parecerem dizer coisas diferentes, **vale este documento**.

---

## Sumário

- [1. Como usar este documento e o quadro de tarefas](#como-usar)
- [2. A ideia do trabalho](#ideia)
- [3. Decisões já tomadas](#decisoes)
- [4. Cronograma](#cronograma)
- [5. Como trabalhar no repositório (fluxo do NIC)](#fluxo-git)
- [6. A estrutura de pastas que você vai construir](#estrutura)
- [7. Combinados que valem para todas as sprints](#combinados)
- [8. Como escrever o artigo](#escrita-geral)
- [Sprint 1 - Ambiente, repositório e o catálogo de imagens](#sprint-1-dev)
- [Sprint 2 - O primeiro mapa de NDVI de um município](#sprint-2-dev)
- [Sprint 3 - A máscara de nuvem e o NDVI médio de uma data](#sprint-3-dev)
- [Sprint 4 - A série temporal de um município](#sprint-4-dev)
- [Sprint 5 - Os outros municípios e a chuva](#sprint-5-dev)
- [Sprint 6 - O NDVI responde à chuva? E quanto custa?](#sprint-6-dev)
- [Sprint 7 - Anos secos, anos chuvosos e os mapas](#sprint-7-dev)
- [Sprint 8 - README, recomendação e fechamento](#sprint-8-dev)
- [9. Quadro-resumo](#quadro-resumo)
- [10. Riscos e planos B](#riscos)
- [11. Se sobrar tempo](#extras)
- [12. Referências mínimas do artigo](#referencias-minimas)

---

<a id="como-usar"></a>
## 1. Como usar este documento e o quadro de tarefas

### As *issues* e o quadro (kanban)

Eu cadastrei as suas tarefas como *issues* no repositório. Toda semana tem:

- **uma *issue* com a etiqueta `Desenvolvimento`**: o que você vai programar, testar e medir;
- **uma *issue* com a etiqueta `Escrita`**: o que você vai pesquisar e escrever no artigo. Em seis semanas ela é a entrega de uma parte do texto. Em duas semanas (Sprints 1 e 6) não há entrega de seção nova, e a *issue* é uma tarefa menor: na Sprint 1, preparar o documento e fichar leituras; na Sprint 6, colocar no documento as tabelas e os gráficos com os dados das Sprints 3 a 5. Essas tarefas pequenas existem para o texto não ficar parado, porque **quem deixa os Resultados para o fim não entrega**.

As *issues* de uma semana estão agrupadas em um **marco** (*milestone*) com o nome e a data da sprint, por exemplo `Sprint 04 - Série temporal (06/11 a 12/11)`. A página **Milestones** do repositório mostra quanto de cada sprint já foi concluído.

O **quadro do projeto** (aba *Projects* do repositório) tem quatro colunas:

| Coluna | Quando o card fica aqui |
|---|---|
| **A fazer** | a tarefa ainda não começou |
| **Em andamento** | você está trabalhando nela. **Mova o card assim que começar** |
| **Em revisão** | você terminou e avisou os orientadores |
| **Concluído** | os orientadores aprovaram e fecharam a *issue* |

### Como cada sprint está organizada neste documento

Cada sprint tem duas partes, **Desenvolvimento** e **Escrita**, e cada uma tem um endereço próprio (`#sprint-4-dev`, `#sprint-4-escrita`), que é para onde as *issues* apontam.

A parte de desenvolvimento tem sempre os mesmos blocos:

- **O que você vai entregar**: em uma frase, o que precisa estar funcionando no fim da semana;
- **Divida a semana assim**: uma sugestão de distribuição dos passos pelos dias;
- **Passo a passo**: a lista numerada do que fazer, na ordem. Siga na ordem, sem pular;
- **Como saber que deu certo**: o que você deve ver na tela ou no arquivo. Se não vir isso, ainda não terminou;
- **Entrega da sprint**: a lista de conferência que também está na *issue*;
- **Erros comuns**: os problemas mais prováveis da semana e como resolver.

**Neste documento eu não dou os programas prontos.** Eu digo o que cada programa precisa fazer, em que ordem, quais funções usar e o que pesquisar. Quem escreve o código é você, e é isso que faz o trabalho ser seu. As fórmulas aparecem completas, porque são o objeto de estudo e vão para o artigo. Os trechos de Python são **peças**: uma chamada de função que não dá para adivinhar, um esqueleto com comentários. Quando uma peça aparece inteira, é porque ela esconde uma armadilha técnica que eu já conferi e que não vale a pena você descobrir sozinho.

### Como entregar

**Desenvolvimento:**

1. abra um *pull request* (PR) da *branch* da sprint para a `develop`, seguindo a [seção 5](#fluxo-git), com `Closes #N` na descrição (o número N de cada sprint está indicado na própria sprint);
2. comente na *issue*: `@brunogomesifrn @franciscoentony entrega da Sprint N pronta para revisão - PR #X`;
3. mova o card para **Em revisão**.

Quando um de nós aprovar e fizer o *merge* do PR, a *issue* fecha sozinha e o card vai para **Concluído**. Se pedirmos ajustes, faça os ajustes na mesma *branch* (o PR se atualiza sozinho) e comente de novo.

**Escrita:**

1. escreva no documento do Google Drive (veja a [seção 8](#escrita-geral));
2. nomeie a versão no histórico do Drive (*Arquivo → Histórico de versões → Nomear versão atual*), por exemplo `Entrega 1 - Introdução - 29/10`;
3. comente na *issue*: `@brunogomesifrn @franciscoentony Introdução pronta para revisão - versão "Entrega 1 - Introdução - 29/10"`;
4. mova o card para **Em revisão**.

Nós comentamos no próprio documento do Drive. Quando a seção estiver aprovada, fechamos a *issue*.

### Regras de ouro

- **Entregue no prazo, mesmo incompleto.** Trabalho pela metade dá para revisar; trabalho que não chega, não. Na *issue*, diga o que ficou faltando.
- **Terminou antes? Não comece a próxima sprint.** Use o tempo para entender melhor o que fez, para olhar os mapas com calma e para adiantar a escrita.
- **Travou mais de 40 minutos no mesmo erro? Pare e peça ajuda.** Comente na *issue* da semana, marcando nós dois, com: o que estava tentando fazer, o comando que rodou e **a mensagem de erro inteira, copiada e colada** (não um resumo, nem um print cortado). Nesta temática isso é ainda mais importante: erro de banda trocada, de máscara de nuvem ou de sistema de coordenadas **não gera mensagem de erro**, só um número errado. Pedir ajuda depois de 40 minutos não é desistir, é administrar o tempo.

---

<a id="ideia"></a>
## 2. A ideia do trabalho

### O problema

O observatório AgroAgreste quer acompanhar as condições da vegetação e das lavouras no Agreste potiguar. Hoje não existe esse acompanhamento: sabe-se que um ano foi de seca ou que choveu bem, mas não há um **número** que descreva, mês a mês e município a município, como a vegetação respondeu.

Satélites fotografam a Terra inteira, de graça, a cada poucos dias. A partir dessas imagens é possível calcular o **NDVI** (*Normalized Difference Vegetation Index*, índice de vegetação por diferença normalizada), que mede o **vigor da vegetação**: quanto mais verde e viçosa a planta, maior o valor. Acompanhar o NDVI ao longo dos meses mostra o ciclo da vegetação; comparar anos mostra o efeito das secas.

A pergunta que o seu trabalho responde é:

> **É possível construir, com imagens de satélite gratuitas, um indicador mensal de vigor da vegetação para os municípios do Agreste potiguar? E esse indicador se comporta como a literatura prevê, respondendo à chuva?**

### O que você vai construir

Um processo em Python que, para cada município e cada mês de 2021 a 2025:

1. procura no catálogo de satélites as imagens daquele mês que **cobrem o município inteiro**;
2. escolhe a menos nublada;
3. baixa **apenas o pedaço da imagem que cobre o município** (e não a cena inteira);
4. descarta os pixels cobertos por nuvem e por sombra de nuvem;
5. calcula o NDVI de cada pixel restante;
6. grava **uma linha em uma planilha** com o NDVI médio daquele município naquele mês, o percentual de pixels aproveitados, o tempo gasto e o volume baixado;
7. descarta a imagem.

No fim, você tem a série temporal do NDVI. Aí começa a análise: comparar com a chuva, comparar anos secos com anos chuvosos, comparar municípios e medir quanto custa rodar tudo isso.

### O que vai ser medido (é isso que faz o trabalho ser um artigo, e não um relatório)

| O que | Como |
|---|---|
| **Cobertura** | Quantos meses tiveram imagem aproveitável, e em que época do ano estão os meses perdidos por nuvem |
| **Ciclo anual** | Se o NDVI sobe e desce todo ano, como a literatura descreve para a vegetação do semiárido |
| **Resposta à chuva** | Correlação entre o NDVI do mês e a chuva do mesmo mês, do mês anterior, de dois e de três meses antes. A literatura diz que a vegetação responde com atraso: você vai verificar se isso acontece no Agreste |
| **Anos secos e anos chuvosos** | Comparação do NDVI entre o ano de menor e o de maior chuva da série, conferida com o Monitor de Secas, da Agência Nacional de Águas e Saneamento Básico (ANA) |
| **Diferença entre municípios** | Se o nível e o ciclo do NDVI são iguais nos quatro municípios |
| **Custo computacional** | Tempo de processamento e **volume de dados baixados** por município e por mês, e a projeção para o Agreste inteiro |

A última linha não é detalhe: se o observatório for adotar esse indicador, alguém vai perguntar quanto custa rodar isso todo mês. Você vai ter a resposta medida.

### O que este trabalho **não** é

**Não é "fazer o mapa do observatório".** A plataforma AgroAgreste é o **contexto** que justifica a pergunta. O objeto do artigo é o **indicador construído e validado por medição**. Você não mexe no código da plataforma. Escreva isso na Introdução: é o que separa um artigo de um manual de programa.

**Não é medir produtividade agrícola.** O NDVI mede vigor da vegetação. A média do município mistura lavoura, pastagem, caatinga, cidade e açude. Separar a lavoura do resto é um passo seguinte (está nos [extras](#extras)), e no artigo ele aparece como trabalho futuro.

---

<a id="decisoes"></a>
## 3. Decisões já tomadas

Para você não perder tempo escolhendo:

| Item | Decisão |
|---|---|
| Linguagem | **Python 3** (3.10 ou mais novo) |
| Onde você trabalha | **computadores do laboratório (Windows)**. Não é possível instalar programas, mas o `pip install` e o Git funcionam |
| Editor | **VS Code** |
| Fonte das imagens | **Microsoft Planetary Computer**, catálogo gratuito, sem cadastro, coleção `sentinel-2-l2a` |
| Satélite | **Sentinel-2**, nível **L2A** (já corrigido dos efeitos da atmosfera) |
| Bandas | **B04** (vermelho), **B8A** (infravermelho próximo) e **SCL** (classificação da cena), todas em **20 m** |
| Imagem do mês | **uma por mês**: a de menor nuvem, entre as que cobrem o município inteiro, com até 3 tentativas |
| Critério de aceitação | o mês só vale se **pelo menos 60% dos pixels** do município estiverem livres de nuvem. Na Sprint 3 você testa 40%, 60% e 80% e confirma (ou troca, com justificativa) |
| Municípios | **Nova Cruz, São Paulo do Potengi, Tangará e Japi** (tabela abaixo) |
| Período | **janeiro de 2021 a dezembro de 2025** (60 meses). A chuva vai de janeiro de **2020** a dezembro de 2025 (o motivo está na Sprint 5) |
| Fonte da chuva | **NASA POWER**, API gratuita, chuva mensal no centro de cada município |
| Limites dos municípios | **API de malhas do IBGE** |
| Armazenamento | **arquivos CSV**. São 4 municípios × 60 meses = 240 linhas: cabe folgadamente em CSV, abre no Excel para conferência e não precisa de banco de dados. Essa escolha vai justificada no artigo |
| Bibliotecas | `pystac-client`, `planetary-computer`, `rioxarray`, `shapely`, `requests`, `pandas`, `matplotlib`, `psutil` e `pytest`. Todas pelo `pip` |
| Repositório | `nicifrn/mp_agro_monitoramento_vegetacao`, só seu, seguindo a política de desenvolvimento do NIC ([seção 5](#fluxo-git)) |
| Texto | **artigo**, no **formato de TCC do NIC**, em um documento do Google Drive que eu compartilho com você |
| O que **não** entra | banco de dados, Django, Docker, aprendizado de máquina, Google Earth Engine, QGIS e dados de pessoas. O MapBiomas fica como extra |

### Os quatro municípios

Os quatro ficam na mesorregião **Agreste Potiguar** do IBGE e foram escolhidos por contraste: dois mais a leste, mais perto do litoral, e dois mais a oeste, no planalto da Borborema.

| Município | Código IBGE | Microrregião (IBGE) | Por que entra |
|---|---|---|---|
| Nova Cruz | 2408300 | Agreste Potiguar | o mais a leste; é também o município estudado em outro trabalho do projeto (necessidade de água das culturas), e os resultados podem ser cruzados |
| São Paulo do Potengi | 2412609 | Agreste Potiguar | no vale do rio Potengi, polo da sua região imediata |
| Tangará | 2414001 | Borborema Potiguar | mais a oeste, no planalto da Borborema |
| Japi | 2405405 | Borborema Potiguar | também na Borborema, menor, vizinho de Santa Cruz |

Eu conferi, antes de escrever este plano, que **cada um desses municípios cabe inteiro em pelo menos uma das "cenas" do Sentinel-2**. Isso não acontece com qualquer município: Santa Cruz, por exemplo, é grande e fica dividida entre duas cenas, o que obrigaria a montar um mosaico. Na Sprint 2 você vai entender o que isso quer dizer.

### Uso de inteligência artificial

- **Pode:** usar uma ferramenta de IA para entender uma mensagem de erro ou um conceito, como faria com um colega.
- **Não pode:** pedir para a IA escrever os programas ou o texto do artigo. O código e o texto têm de ser seus, e você precisa saber explicar cada linha na apresentação.
- **Nunca:** colocar no artigo uma referência que você não abriu e leu. Ferramentas de IA inventam referências com naturalidade e, nesta área, inventam também valores de correlação e nomes de satélite.

---

<a id="cronograma"></a>
## 4. Cronograma

Cada sprint vai de **sexta a quinta-feira**. O prazo de tudo é a **quinta-feira** que fecha a sprint.

| Sprint | Período | Desenvolvimento | Escrita |
|---|---|---|---|
| 1 | 16/10 a 22/10 | Ambiente, repositório e o catálogo de imagens | Preparar o documento e fichar as leituras da Introdução |
| 2 | 23/10 a 29/10 | O primeiro mapa de NDVI de um município | **Entrega 1:** Introdução e Objetivo geral |
| 3 | 30/10 a 05/11 | A máscara de nuvem e o NDVI médio de uma data, com testes | **Entrega 2:** Referencial 2.1, 2.2 e 2.3 |
| 4 | 06/11 a 12/11 | A série temporal de um município e o mapa de localização | **Entrega 3:** Referencial 2.4 e 2.5 |
| 5 | 13/11 a 19/11 | Os outros municípios e a chuva da NASA POWER | **Entrega 4:** Metodologia e Materiais e Métodos |
| 6 | 20/11 a 26/11 | O NDVI responde à chuva? E o custo computacional | Tarefa curta: tabelas e gráficos das Sprints 3 a 5 no documento |
| 7 | 27/11 a 03/12 | Anos secos, anos chuvosos e os mapas | **Entrega 5:** Resultados e Discussão |
| 8 | 04/12 a 10/12 | README, recomendação e fechamento | **Entrega 6:** Conclusão, Objetivos específicos, Resumo e Título |

**Tudo termina em 10/12.**

**Feriados:** 02/11 (segunda, Sprint 3) e 20/11 (sexta, primeiro dia da Sprint 6). Nenhum prazo cai em feriado, mas nessas duas semanas o laboratório fica fechado um dia: **a semana tem um dia útil a menos**, então comece cedo.

**Três avisos sobre o cronograma:**

1. **As Sprints 4 e 5 têm programas que rodam por horas.** Processar 60 meses de um município leva de uma a duas horas, por causa do download. Deixe rodando e, enquanto isso, faça os outros passos da semana e a escrita. O programa que você vai escrever na Sprint 4 continua de onde parou se for interrompido, então nada se perde.
2. **Os Resultados vencem em 03/12, na mesma semana dos mapas.** Por isso a Sprint 6 já manda colocar no documento as tabelas e os gráficos que existirem, e a Sprint 7 manda terminar os mapas **até segunda-feira, 30/11**: a terça, a quarta e a quinta ficam para escrever.
3. **A última semana é cheia.** A Conclusão precisa estar escrita até **segunda-feira, 07/12**, para sobrar a terça, a quarta e a quinta para o Resumo, o *Abstract*, o Título e a revisão final.

---

<a id="fluxo-git"></a>
## 5. Como trabalhar no repositório (fluxo do NIC)

O NIC tem uma política de desenvolvimento que vale para todos os projetos. Abaixo está o que ela significa no seu trabalho.

### 5.1 As *branches*

| *Branch* | Para que serve | Quem mexe |
|---|---|---|
| `main` | versão estável e aprovada | só os orientadores, no fim do trabalho |
| `develop` | onde as sprints aprovadas vão se juntando. É a *branch* padrão do repositório | ninguém envia direto: só entra por PR aprovado |
| `feature/...` | **uma por sprint**, onde você trabalha | você |

Os nomes das *branches* das sprints já estão definidos em cada sprint (por exemplo, `feature/serie-temporal`). Se precisar corrigir algo de uma sprint que já foi aprovada, use `fix/` (por exemplo, `fix/deslocamento-reflectancia`).

### 5.2 O ciclo de cada sprint

**No começo da sprint** (sexta-feira), crie a *branch* da semana a partir da `develop` atualizada e envie para o GitHub:

```
git checkout develop
git pull
git checkout -b feature/nome-da-sprint
git push -u origin feature/nome-da-sprint
```

**Ao fim de cada dia**, envie o trabalho. Código que só existe na máquina do laboratório não foi entregue, e a máquina pode ser formatada:

```
git status
git add (os arquivos que você mexeu)
git commit -m "feat: adiciona cálculo do NDVI"
git push
```

**Antes de todo `git add`, olhe o `git status`.** Se aparecer `.venv/`, `__pycache__/` ou algum arquivo `.tif`, o `.gitignore` está errado: corrija antes de continuar. **Nunca use `git add .` sem olhar o `git status` antes.**

Se você trabalhar em mais de uma máquina do laboratório, comece sempre com `git pull` na *branch* da sprint, para trazer o que enviou da outra máquina.

**No fim da sprint**, abra o PR (seção 5.4).

### 5.3 Mensagens de *commit*

Os *commits* devem ser **pequenos, objetivos e frequentes**: pelo menos 3 por semana. Use o padrão abaixo, com a mensagem em português e o verbo no presente:

```
feat: adiciona busca de imagens que cobrem o município
fix: corrige deslocamento da reflectância a partir da versão 04.00
docs: registra configuração da máquina e velocidade da internet
test: adiciona testes do cálculo do NDVI
refactor: move as funções de cálculo para vegetacao.py
```

| Prefixo | Quando usar |
|---|---|
| `feat:` | algo novo funcionando (um script, uma função, uma coluna nova no CSV) |
| `fix:` | correção de algo que estava errado |
| `docs:` | documentação, diário, `README.md`, prints, tabelas e gráficos de resultado |
| `test:` | testes |
| `refactor:` | reorganizar código sem mudar o que ele faz |

**Mensagens proibidas pela política do NIC:** `ajustes`, `mudanças`, `update`, `correções`. Se você não consegue dizer em uma frase o que o *commit* faz, ele está grande demais.

### 5.4 O *pull request* do fim da sprint

1. Confira se tudo foi enviado (`git status` deve dizer `nothing to commit`).
2. Rode os testes (a partir da Sprint 3): `python -m pytest`. Todos precisam passar.
3. No GitHub, abra o repositório. Vai aparecer uma faixa amarela com o botão **Compare & pull request**. Se não aparecer: aba **Pull requests → New pull request**, com **base: `develop`** e **compare: a *branch* da sprint**.
4. Preencha a descrição. O repositório já traz um modelo com os campos que a política do NIC exige:
   - **Objetivo:** o que esta sprint entrega, em uma ou duas frases;
   - **O que foi feito:** a lista do que foi implementado;
   - **Possíveis impactos:** o que muda para quem roda o projeto (um script novo, uma pasta nova, uma biblioteca nova);
   - **Evidências de teste:** a saída do `pytest` e dos scripts (copiadas do terminal), as tabelas, os gráficos e os mapas;
   - **Issue:** `Closes #N`, com o número indicado na sprint.
5. Em **Reviewers**, marque `brunogomesifrn` e `franciscoentony`.
6. Comente na *issue* e mova o card para **Em revisão** (veja a [seção 1](#como-usar)).

**Você não faz o *merge* do próprio PR**: a política do NIC exige que um revisor aprove antes da integração, e os revisores somos nós. **Um PR por sprint**: não acumule duas sprints no mesmo PR.

### 5.5 Testes

A política do NIC pede que toda funcionalidade tenha testes compatíveis com a sua complexidade. No seu trabalho, as funções de cálculo ficam em `vegetacao.py` e os testes ficam na pasta `tests/`, usando a biblioteca **`pytest`**. Um teste é uma função cujo nome começa com `test_` e que usa o comando `assert`:

```python
def test_ndvi_de_vegetacao():
    assert calcular_ndvi(0.1, 0.5) == pytest.approx(0.6667, abs=0.0001)
```

Se a condição do `assert` for **verdadeira**, o teste passa. Se for **falsa**, o `pytest` mostra qual teste falhou, o valor esperado e o valor obtido. O `pytest.approx` serve para comparar números decimais com uma tolerância, porque contas com decimais no computador não são exatas.

Rode sempre **a partir da raiz do repositório**, com o `.venv` ativo, assim:

```
python -m pytest
```

(Com `python -m` na frente, o Python enxerga os arquivos da raiz, e o `from vegetacao import ...` dos testes funciona.)

**Os testes não usam a internet.** Eles testam as contas com números pequenos que você inventa (uma "imagem" de 2 × 2 pixels, uma tabela de 6 linhas). É isso que deixa o teste rápido e confiável: se ele dependesse do catálogo de imagens, falharia toda vez que a rede caísse.

### 5.6 Segurança

Nunca envie para o repositório senhas, *tokens*, chaves ou arquivos `.env`. Neste trabalho você não precisa de nenhum deles: o Planetary Computer, a NASA POWER e o IBGE não pedem cadastro. A biblioteca `planetary-computer` gera sozinha, a cada execução, uma autorização temporária para ler as imagens; ela **não** é uma senha sua e não vai para nenhum arquivo.

---

<a id="estrutura"></a>
## 6. A estrutura de pastas que você vai construir

Você não precisa criar tudo de uma vez: cada sprint cria a sua parte. Esta é a figura final, para você saber aonde está indo. Tudo fica **na raiz do repositório** `mp_agro_monitoramento_vegetacao/`:

```
mp_agro_monitoramento_vegetacao/
├── .github/
│   └── pull_request_template.md   ← já existe (modelo do PR)
├── dados/
│   ├── municipios.csv             ← Sprint 1
│   ├── limites/                   ← contornos do IBGE: municípios, RN, Brasil e Agreste (Sprints 2 e 6)
│   ├── chuva_brutos/              ← o que veio da NASA POWER, sem mexer (Sprint 5)
│   ├── ndvi_mensal.csv            ← Sprints 4 e 5
│   ├── chuva_mensal.csv           ← Sprint 5
│   └── ndvi_chuva.csv             ← Sprint 5
├── resultados/                    ← tabelas de análise (Sprints 3 a 8)
├── graficos/                      ← gráficos e mapas do artigo (Sprints 2 a 7)
├── tests/
│   ├── test_vegetacao.py          ← Sprints 3 e 4
│   └── test_analise.py            ← Sprints 5 e 6
├── docs/
│   ├── 01_descricao_geral.md      ← este documento (já existe)
│   ├── projeto_agroagreste.md     ← já existe
│   ├── orientacoes_escrita_tcc.md ← já existe
│   ├── ambiente.md                ← Sprint 1
│   ├── diario.md                  ← Sprint 1 em diante
│   ├── leituras.md                ← Sprint 1 em diante
│   ├── recomendacao.md            ← Sprint 8
│   └── evidencias/                ← prints de tela
├── vegetacao.py                   ← as funções de cálculo (Sprints 2 a 6)
├── verificar_ambiente.py          ← Sprint 1
├── testar_catalogo.py             ← Sprint 1
├── conferir_municipios.py         ← Sprint 1
├── baixar_limites.py              ← Sprint 2
├── ndvi_uma_data.py               ← Sprint 2
├── comparar_limiares.py           ← Sprint 3
├── gerar_serie.py                 ← Sprint 4
├── grafico_serie.py               ← Sprint 4
├── mapa_localizacao.py            ← Sprint 4
├── baixar_chuva.py                ← Sprint 5
├── juntar_ndvi_chuva.py           ← Sprint 5
├── correlacao.py                  ← Sprint 6
├── custo.py                       ← Sprint 6
├── anos_secos_chuvosos.py         ← Sprint 7
├── mapas_comparacao.py            ← Sprint 7
├── .gitignore
├── requirements.txt
└── README.md
```

A ideia da organização: **as funções de cálculo** (deslocamento da reflectância, NDVI, máscara de nuvem, defasagens) ficam todas em `vegetacao.py`, que é o arquivo testado pelo `pytest`. **Os scripts** (`gerar_serie.py`, `correlacao.py`...) buscam as imagens, leem e gravam os arquivos e chamam as funções. Separar "fazer a conta" de "baixar, ler e gravar arquivo" é o que permite testar as contas sem internet.

**As imagens de satélite nunca vão para o repositório.** Elas são baixadas, usadas e descartadas pelo próprio programa. O que vai para o repositório são os CSV de resultado e os gráficos, que são pequenos.

---

<a id="combinados"></a>
## 7. Combinados que valem para todas as sprints

- **Rode tudo a partir da raiz do repositório:** `python gerar_serie.py`, e não de dentro de outra pasta. Todos os caminhos dos programas (`dados/`, `resultados/`, `graficos/`) partem da raiz.
- **Diário (`docs/diario.md`):** no fim de cada sprint, escreva 3 linhas: o que funcionou, o que deu errado e o que aprendeu. Leva cinco minutos e vai escrever a Conclusão por você no fim do trabalho. Use este formato:

  ```
  ## Sprint 4 - 06/11 a 12/11
  - Funcionou: ...
  - Deu errado: ...
  - Aprendi: ...
  ```

  Além das três linhas, o diário guarda as **anotações técnicas** que cada sprint pede (tempos, contagens, observações sobre os mapas). Elas viram texto do artigo.

- **Nunca apague uma linha das planilhas de `dados/`.** Mês sem dado também é linha, com o motivo. Ele vira observação no artigo, não lixo: é ele que mostra a limitação real do satélite em região com nuvem.
- **Olhe as imagens.** Este é um trabalho visual. Não confie só nos números: abra o mapa de NDVI e veja se faz sentido. Vegetação é verde, solo exposto e cidade ficam claros ou alaranjados, açude fica vermelho-escuro. Se estiver estranho, tem erro no código, mesmo sem mensagem de erro.
- **Anote todo erro e toda surpresa.** Neste trabalho, **surpresa é resultado**. Se um mês saiu com NDVI muito diferente dos vizinhos, se um município perdeu muito mais meses por nuvem, isso vai para o artigo.
- **Prints (`docs/evidencias/`):** sempre que algo funcionar (ou falhar de um jeito interessante), tire um print (`Win + Shift + S`). Dê nomes que digam o que é: `s02_primeiro_ndvi_tangara.png`.
- **Acompanhamento semanal:** no começo de cada sprint, você mostra aos orientadores o que fez na anterior, **rodando na tela**. A partir da Sprint 3, "está funcionando" não basta: tem que ter número.

---

<a id="escrita-geral"></a>
## 8. Como escrever o artigo

### 8.1 Onde escrever: o documento compartilhado no Google Drive

Na Sprint 1 eu compartilho com você um documento do Google Drive que **já está no formato de TCC do NIC** (capa, folha de rosto, resumo, sumário e as seções). O seu trabalho é um **artigo**: o formato é o do TCC, mas o texto é mais curto e mais direto (veja o tamanho na seção 8.3). Você não cria arquivo novo nem trabalha em cópia local.

- **Escreva sempre no documento compartilhado.** Nada de escrever no Word e colar depois: o histórico do Drive é o que nos permite ver o que mudou de uma semana para outra.
- **Não crie cópias** ("Artigo v2", "Artigo final"). O Drive já guarda tudo em **Arquivo → Histórico de versões**.
- **Marque cada entrega no histórico:** *Arquivo → Histórico de versões → Nomear versão atual*, com um rótulo como `Entrega 1 - Introdução - 29/10`.
- **Avise na *issue* quando entregar**, como explicado na [seção 1](#como-usar).
- **Comentário se responde, não se apaga.** Responda a cada comentário dizendo o que fez e só então marque como resolvido.
- **Resolva todos os comentários da entrega anterior antes de avisar sobre a próxima.**
- **Figuras, mapas e tabelas** vão dentro do documento, no lugar certo, com a identificação em cima e a fonte embaixo.
- **Não dê acesso ao documento a outras pessoas.**

### 8.2 As normas

Todas as regras de escrita e de ABNT estão em [`docs/orientacoes_escrita_tcc.md`](orientacoes_escrita_tcc.md): estrutura, citações, referências, figuras, tabelas, formatação e linguagem. **Leia esse arquivo inteiro na Sprint 1.** Ele foi escrito para o TCC e vale para o artigo do mesmo jeito; a única diferença é o tamanho de cada seção. Este plano não repete as regras da ABNT; ele diz **o que pesquisar e o que escrever** em cada seção.

> **Importante:** o que está neste plano são **orientações**, não o texto pronto. Não copie estas frases para o artigo. Elas dizem sobre o que é cada parágrafo; o texto tem de ser escrito por você, com as suas palavras e com as referências que leu.

### 8.3 A estrutura do artigo

```
1 INTRODUÇÃO
1.1 Objetivo geral
1.2 Objetivos específicos
2 REFERENCIAL TEÓRICO
2.1 Agricultura familiar e o Agreste potiguar
2.2 Sensoriamento remoto e o satélite Sentinel-2
2.3 Índices de vegetação e o NDVI
2.4 Vegetação do semiárido, chuva e séries temporais de NDVI
2.5 Trabalhos relacionados
3 METODOLOGIA
3.1 Classificação da pesquisa
3.2 Área de estudo e período
3.3 Etapas do trabalho
4 MATERIAIS E MÉTODOS
4.1 Materiais
4.2 Seleção e recorte das imagens
4.3 Máscara de nuvem e cálculo do NDVI
4.4 Dados de chuva e análise
4.5 Medição do custo computacional
5 RESULTADOS E DISCUSSÃO
5.1 Cobertura de dados obtida
5.2 O ciclo anual da vegetação
5.3 A relação entre NDVI e chuva
5.4 Anos secos e anos chuvosos
5.5 Custo computacional
5.6 Limitações
6 CONCLUSÃO
REFERÊNCIAS
```

Tamanho de referência da parte textual (da Introdução à Conclusão): **de 12 a 18 páginas**, mais ou menos assim: Introdução, 2; Referencial, 4 a 5; Metodologia e Materiais e Métodos, 3 a 4; Resultados, 4 a 6; Conclusão, 1.

### 8.4 As três perguntas de pesquisa

O trabalho gira em torno de três perguntas, que saem da pergunta principal da [seção 2](#ideia). Elas aparecem na Introdução, organizam os Resultados e são respondidas na Conclusão:

1. o NDVI mensal reproduz o **ciclo anual** esperado da vegetação do semiárido nos quatro municípios?
2. o NDVI **responde à chuva**, e com quantos meses de atraso?
3. o NDVI distingue **anos secos de anos chuvosos**, reconhecidos por uma fonte independente (o Monitor de Secas)?

Além delas, o artigo apresenta a **cobertura de dados** obtida (quantos meses se perderam por nuvem) e o **custo computacional**, que são as informações práticas de que o observatório precisa para decidir se adota o indicador.

### 8.5 Regras que valem para o texto inteiro

- **Toda afirmação técnica precisa de referência.**
- **Não empilhe citações.** Explique com as suas palavras e amarre ao seu trabalho.
- **Documentação oficial** (Agência Espacial Europeia, Planetary Computer, NASA POWER, IBGE) serve para descrever a fonte de dados, não para fundamentar conceito. Para conceito, use livro ou artigo.
- **Nada de blog, Stack Overflow ou site sem autoria** nas Referências. Você vai usar muito esse material para resolver problema técnico, e isso é normal, mas ele não entra na lista.
- **Nunca cite uma referência que você não leu.**
- **Crie a seção "Referências" no primeiro dia** e acrescente cada obra assim que ler.
- **Meta:** de 15 a 22 referências, equilibradas entre o lado técnico e o lado ambiental e agrícola (lista mínima na [seção 12](#referencias-minimas)).
- **Fichamento:** tudo o que você ler vai para `docs/leituras.md`, no formato abaixo. É ele que transforma leitura em texto:

  ```
  ## TUCKER (1979)
  - Referência completa (ABNT): ...
  - Onde achei: (endereço)
  - Ideia principal, com as minhas palavras: ...
  - Trecho que posso citar (com página): "..." (p. X)
  - Vou usar na seção: 2.3
  ```

---

# Sprint 1: 16/10 a 22/10/2026

<a id="sprint-1-dev"></a>
## Sprint 1 · Desenvolvimento: ambiente, repositório e o catálogo de imagens

**Branch:** `feature/ambiente-catalogo` · **No PR:** `Closes #1`

**O que você vai entregar:** o Git configurado, o repositório clonado, o ambiente virtual com as bibliotecas, o programa que confere o ambiente, um programa que **encontra** imagens de satélite de Nova Cruz no catálogo (ainda sem baixar nada) e a lista dos quatro municípios conferida na API do IBGE.

Esta sprint é um **teste de viabilidade**. Se a rede do laboratório bloquear o acesso ao catálogo de imagens, é melhor descobrir agora do que na Sprint 4.

**Divida a semana assim:**

| Dia | O que fazer |
|---|---|
| sexta, 16/10 | passos 1 a 4 (leitura do plano, Git, convite, clone e *branch*) |
| segunda, 19/10 | passos 5 a 7 (ambiente, pastas, `verificar_ambiente.py` e `docs/ambiente.md`) |
| terça, 20/10 | passo 8 (o catálogo de imagens) |
| quarta, 21/10 | passo 9 (os municípios na API do IBGE) |
| quinta, 22/10 | passo 10 (diário, *commits* e PR); a escrita da semana |

### Passo a passo

**1. Leia as seções 1 a 8 deste documento inteiras.** Se você nunca trabalhou com *branches* e *pull requests*, assista também às aulas iniciais do Curso de Git e GitHub do Curso em Vídeo (https://www.cursoemvideo.com/curso/curso-de-git-e-github/), até a parte em que o repositório é enviado para o GitHub.

**2. Configure o Git** na máquina do laboratório (uma vez só por máquina), com o mesmo e-mail da sua conta do GitHub. Abra o Prompt de Comando (tecla `Win`, digite `cmd`, Enter):

```
git config --global user.name "Seu Nome Completo"
git config --global user.email "seu-email-do-github@exemplo.com"
```

**3. Aceite o convite do repositório.** Você recebeu por e-mail um convite para o `nicifrn/mp_agro_monitoramento_vegetacao`. Aceite (ou abra https://github.com/nicifrn/mp_agro_monitoramento_vegetacao/invitations). Aceite também o convite do quadro do projeto, que chega no mesmo e-mail.

**4. Clone o repositório e crie a *branch* da sprint:**

```
cd %USERPROFILE%
git clone https://github.com/nicifrn/mp_agro_monitoramento_vegetacao.git
cd mp_agro_monitoramento_vegetacao
git checkout -b feature/ambiente-catalogo
git push -u origin feature/ambiente-catalogo
```

Na primeira vez que o Git falar com o GitHub, abre uma janela do navegador pedindo login. Entre com a sua conta e autorize. Abra a pasta `mp_agro_monitoramento_vegetacao` no VS Code (*File → Open Folder*). A partir de agora, **é sempre essa pasta que você abre**.

**5. Crie o ambiente virtual e instale as bibliotecas.** Na raiz do repositório, **no Prompt de Comando** (e não no PowerShell):

```
python -m venv .venv
.venv\Scripts\activate
pip install pystac-client planetary-computer rioxarray shapely requests pandas matplotlib psutil pytest
pip freeze > requirements.txt
```

Depois de ativar, o começo da linha passa a mostrar `(.venv)`. **Se não mostrar, o ambiente não está ativo**, e o que você instalar vai para o lugar errado. Toda vez que abrir um terminal novo, ative de novo.

A instalação do `rioxarray` baixa bastante coisa (ele traz junto o `rasterio`, o `xarray` e o `pyproj`) e pode levar alguns minutos. É normal. O `rasterio` já vem com tudo o que precisa para ler imagens de satélite, sem instalar nenhum programa à parte.

Para que serve cada biblioteca:

| Biblioteca | Para quê |
|---|---|
| `pystac-client` | procurar imagens no catálogo de satélites |
| `planetary-computer` | liberar o acesso aos arquivos das imagens encontradas |
| `rioxarray` | abrir e recortar as imagens (traz o `rasterio` e o `xarray`) |
| `shapely` | trabalhar com o contorno dos municípios |
| `requests` | conversar com as APIs do IBGE e da NASA POWER |
| `pandas` | organizar as planilhas e calcular as correlações |
| `matplotlib` | fazer os gráficos e os mapas |
| `psutil` | medir quantos megabytes a máquina recebeu pela rede |
| `pytest` | rodar os testes automatizados |

> No terminal do VS Code (`` Ctrl + ` ``), abra o seletor de terminal (setinha ao lado do `+`) e escolha **Command Prompt**. No PowerShell, o `activate` costuma dar erro de "execução de scripts desabilitada".
>
> Se o comando `python` não for reconhecido, tente `py`. Se o `py` funcionar, use `py` no lugar de `python` em todos os comandos deste documento, e anote isso no diário.

**6. Crie as pastas e o `.gitignore`.**

1. Crie as pastas `dados\limites`, `resultados`, `graficos`, `tests` e `docs\evidencias` (veja a [seção 6](#estrutura)). *Pesquise:* o comando `mkdir` no Windows. O Git não guarda pastas vazias; por isso, coloque dentro de cada pasta vazia um arquivo vazio chamado `.gitkeep`.
2. Crie o arquivo `.gitignore` na raiz, com este conteúdo:

   ```
   .venv/
   __pycache__/
   *.pyc
   .pytest_cache/
   temp/
   *.tif
   ```

   As duas últimas linhas garantem que nenhuma imagem de satélite vá parar no repositório, mesmo que você salve uma para testar.

**7. Escreva `verificar_ambiente.py` e preencha `docs/ambiente.md`.**

O programa mostra, um por linha, a versão do Python e a versão de cada uma das nove bibliotecas. Ele precisa:

1. importar o módulo `sys` e mostrar `sys.version`;
2. importar a função `version` do módulo `importlib.metadata`;
3. para cada nome da lista `["pystac-client", "planetary-computer", "rioxarray", "rasterio", "shapely", "requests", "pandas", "matplotlib", "psutil", "pytest"]`, mostrar o nome e `version(nome)`.

*Pesquise:* `importlib.metadata.version`. Ela devolve a versão instalada a partir do nome que você usou no `pip install`, o que funciona para todas as bibliotecas do mesmo jeito.

Crie `docs/ambiente.md` com:

- a configuração da máquina (tecla `Win`, digite "Sobre o seu PC": anote "Processador", "RAM instalada", "Edição" e "Versão" do Windows);
- a saída do `verificar_ambiente.py`;
- **a velocidade da internet do laboratório**: abra https://fast.com no navegador, espere o número parar e clique em **Mostrar mais informações** para ver também a latência. Anote a velocidade de download, a latência, o dia e a hora. Repita em outro dia da semana.

**A velocidade da internet importa de verdade neste trabalho:** boa parte do tempo que você vai medir é tempo de download. Sem essa anotação, os tempos do artigo não significam nada para quem lê.

**8. Encontre imagens no catálogo.** Crie `testar_catalogo.py`. A primeira parte, que abre o catálogo, é esta (copie, porque o `modifier` não dá para adivinhar):

```python
import pystac_client
import planetary_computer

catalogo = pystac_client.Client.open(
    "https://planetarycomputer.microsoft.com/api/stac/v1",
    modifier=planetary_computer.sign_inplace,
)
```

Depois, o programa precisa:

1. guardar a longitude e a latitude da sede de Nova Cruz: `LONGITUDE = -35.4339` e `LATITUDE = -6.4778`;
2. fazer uma busca com `catalogo.search(...)` usando:
   - `collections=["sentinel-2-l2a"]`;
   - `intersects={"type": "Point", "coordinates": [LONGITUDE, LATITUDE]}` (no padrão do catálogo, **a longitude vem primeiro**);
   - `datetime="2024-01-01/2024-03-31"`;
   - `query={"eo:cloud_cover": {"lt": 60}}` (só imagens com menos de 60% de nuvem na cena);
3. transformar o resultado em lista com `list(busca.items())` e mostrar quantas imagens vieram;
4. para cada imagem, mostrar em uma linha: a data (`item.datetime.date()`), a nuvem (`item.properties["eo:cloud_cover"]`), o código da cena (`item.properties["s2:mgrs_tile"]`) e a versão de processamento (`item.properties["s2:processing_baseline"]`).

Rode. Se aparecer uma lista de datas, **o acesso funciona** e a maior incerteza do trabalho está resolvida. Tire um print.

**Se der erro de conexão**, pode ser bloqueio da rede do laboratório. Comente na *issue* **nesta semana**, com o erro inteiro.

Agora **olhe a lista com atenção** e anote no diário:

- quantas imagens vieram e quantas **datas diferentes** existem (*pesquise:* transformar uma lista em `set` para contar valores distintos);
- quais códigos de cena (`s2:mgrs_tile`) aparecem;
- **por que a mesma data aparece mais de uma vez?** Escreva o seu palpite. A resposta vem na Sprint 2, e ela é importante.

Entenda os conceitos novos, porque eles vão para o artigo:

- **catálogo STAC** (*SpatioTemporal Asset Catalog*): um padrão aberto de catálogo de imagens de satélite. Você diz "quero imagens deste lugar, neste período, com pouca nuvem" e ele devolve a lista. *Pesquise:* "STAC specification";
- **`eo:cloud_cover`**: a porcentagem de nuvem da **cena inteira**, que tem cerca de 110 km × 110 km. Ela não diz se havia nuvem exatamente sobre o município, só ajuda a descartar as cenas muito nubladas antes de baixar qualquer coisa;
- **Sentinel-2 L2A**: L2A quer dizer que a imagem já vem corrigida dos efeitos da atmosfera (reflectância de superfície). É a versão que se usa para calcular índices de vegetação. Existe também a L1C, sem essa correção: **não use**, e no artigo explique por quê.

**9. Confira os municípios na API do IBGE.** Crie `dados/municipios.csv` com as colunas `codigo_ibge,nome,microrregiao,justificativa`, uma linha para cada um dos quatro municípios da [seção 3](#decisoes). A coluna `justificativa` é uma frase **sua** dizendo por que o município entra (ela vai direto para a Metodologia do artigo).

Depois escreva `conferir_municipios.py`, que lê o CSV com o `pandas` e, para cada código, consulta:

```
https://servicodados.ibge.gov.br/api/v1/localidades/municipios/{codigo}
```

e mostra o nome, a microrregião (`["microrregiao"]["nome"]`) e a mesorregião (`["microrregiao"]["mesorregiao"]["nome"]`) que o IBGE devolve. **Os quatro precisam aparecer na mesorregião Agreste Potiguar**, e o nome e a microrregião precisam bater com o que você escreveu no CSV.

*Pesquise:* `requests.get(...).json()` e como acessar um dicionário dentro de outro. Abra o endereço de um dos municípios no navegador antes de programar: ver o JSON ajuda a entender o caminho até a informação.

**10. Diário, *commits* e PR.** Crie `docs/diario.md` com as três linhas da semana e as anotações do passo 8. Faça os *commits* e abra o PR para a `develop` com `Closes #1`, colando em **Evidências de teste** a saída do `verificar_ambiente.py`, do `testar_catalogo.py` e do `conferir_municipios.py`.

### Como saber que deu certo

- O terminal mostra `(.venv)` no começo da linha.
- `python verificar_ambiente.py` mostra a versão do Python e das dez bibliotecas da lista.
- `python testar_catalogo.py` lista imagens de Nova Cruz do primeiro trimestre de 2024, com data, nuvem, cena e versão.
- `python conferir_municipios.py` mostra os quatro municípios na mesorregião Agreste Potiguar.
- O `git status` **não** mostra `.venv/` nem `__pycache__/`.

### Entrega da sprint

- [ ] Git configurado e repositório clonado, na *branch* `feature/ambiente-catalogo`.
- [ ] Ambiente virtual com as bibliotecas e `requirements.txt` enviado.
- [ ] Estrutura de pastas e `.gitignore`.
- [ ] `verificar_ambiente.py` funcionando e `docs/ambiente.md` com a máquina e a velocidade da internet.
- [ ] `testar_catalogo.py` listando imagens, com as anotações no diário.
- [ ] `dados/municipios.csv` e `conferir_municipios.py`, com os quatro no Agreste Potiguar.
- [ ] `docs/diario.md` com as três linhas da semana.
- [ ] PR aberto para a `develop`, com `Closes #1`.

### Erros comuns

- **`'python' não é reconhecido`:** use `py` (veja o passo 5).
- **O `activate` não funciona:** você está no PowerShell. Troque para o Command Prompt.
- **`ConnectionError` ou tempo esgotado no catálogo:** pode ser a rede do laboratório. Tente de novo em outro horário e, se continuar, comente na *issue* com o erro inteiro.
- **Nenhuma imagem encontrada:** confira as coordenadas. Longitude no Brasil é **negativa** e vem **primeiro** no formato do catálogo (`[longitude, latitude]`). Trocar a ordem é o erro mais comum aqui, e ele não dá erro: só devolve uma lista vazia (o ponto vai parar no oceano).
- **`KeyError` no `conferir_municipios.py`:** o caminho no dicionário está errado. Abra o endereço no navegador e siga as chaves com os olhos.

<a id="sprint-1-escrita"></a>
## Sprint 1 · Escrita: preparar o documento e fichar as leituras da Introdução

**O que você vai entregar:** o documento do artigo aberto e preparado, as normas lidas e as leituras da Introdução fichadas. Nesta semana não há entrega de seção.

### Passo a passo

**1. Abra o documento do artigo** que eu compartilhei com você no Google Drive (o convite chega no e-mail). Preencha a capa e a folha de rosto com o seu nome, o curso, o nome dos orientadores e o título provisório: *Monitoramento do vigor da vegetação no Agreste potiguar com imagens Sentinel-2: um indicador mensal baseado no NDVI*.

**2. Crie a seção "REFERÊNCIAS"** no fim do documento, ainda vazia. A partir de hoje, toda obra que você ler entra nela no mesmo dia.

**3. Leia as normas.** Leia [`docs/orientacoes_escrita_tcc.md`](orientacoes_escrita_tcc.md) inteiro, com atenção especial a: estrutura do trabalho, Introdução, objetivo geral, como citar e como referenciar.

**4. Leia o resumo do projeto pai** em [`docs/projeto_agroagreste.md`](projeto_agroagreste.md). Ele é o ponto de partida da Introdução.

**5. Pesquise, leia e fiche em `docs/leituras.md`** (no formato da [seção 8.5](#escrita-geral); este arquivo entra no PR de desenvolvimento da semana):

- **a Lei nº 11.326, de 24 de julho de 2006**, que define agricultor familiar: procure no portal da legislação federal (`planalto.gov.br`) e leia o artigo 3º;
- **o Censo Agropecuário 2017 do IBGE:** no **SIDRA** (`sidra.ibge.gov.br`), abra a **tabela 6778** (número de estabelecimentos agropecuários, por tipologia). Em "Tipologia", escolha as opções de **agricultura familiar** e **não familiar**; em "Unidade Territorial", escolha **Município** e marque os quatro municípios do trabalho. Anote quantos estabelecimentos são da agricultura familiar em cada um e que porcentagem isso representa do total. Anote também a data da consulta. Número concreto vale mais que adjetivo;
- **o Semiárido brasileiro:** procure no site da **SUDENE** (`gov.br/sudene`) a delimitação oficial do Semiárido mais recente e verifique se os quatro municípios estão na lista. Anote o resultado e o documento oficial (número da resolução e ano);
- **o Monitor de Secas**, da ANA (`monitordesecas.ana.gov.br`): leia a página que explica o que é o Monitor, quem o produz, com que frequência e como as categorias de seca são definidas. Você vai usá-lo na Introdução (como exemplo de monitoramento que existe em escala regional) e na Sprint 7 (para conferir os anos secos);
- **o guia do Sentinel-2:** procure o "Sentinel-2 User Handbook" ou as páginas do Sentinel-2 no portal da Agência Espacial Europeia (ESA, `sentiwiki.copernicus.eu` ou `sentinels.copernicus.eu`). Anote: quando o satélite foi lançado, de quantos em quantos dias ele passa no mesmo lugar, quais são as bandas e a resolução de cada uma (procure a tabela das bandas e anote B04, B08 e B8A);
- **o trabalho que propôs o NDVI:** ROUSE, J. W. *et al.* *Monitoring vegetation systems in the Great Plains with ERTS*, apresentado em 1974 no *Third Earth Resources Technology Satellite-1 Symposium*, da NASA. Ele está disponível gratuitamente no NASA Technical Reports Server (`ntrs.nasa.gov`): procure pelo título. Está em inglês; leia o resumo e a parte em que a razão entre as bandas é apresentada.

### Como saber que deu certo

- O documento do Drive tem capa, folha de rosto e a seção de Referências criadas.
- O `docs/leituras.md` tem pelo menos **6 obras fichadas**, cada uma com a referência completa no formato ABNT.
- Você tem anotados: o número de estabelecimentos da agricultura familiar dos quatro municípios, a situação deles no Semiárido e a revisita e as bandas do Sentinel-2, cada um com a fonte e a data da consulta.

### Entrega

- [ ] Documento do Drive com capa, folha de rosto, título provisório e seção de Referências.
- [ ] `docs/orientacoes_escrita_tcc.md` e `docs/projeto_agroagreste.md` lidos.
- [ ] Pelo menos 6 obras fichadas em `docs/leituras.md`, com referência ABNT.
- [ ] Os números do IBGE e da SUDENE e os dados do Sentinel-2 anotados com a fonte e a data.
- [ ] As obras lidas lançadas na seção de Referências do documento.

Para entregar, comente na *issue* dizendo quantas obras fichou e mova o card para **Em revisão**.

---

# Sprint 2: 23/10 a 29/10/2026

<a id="sprint-2-dev"></a>
## Sprint 2 · Desenvolvimento: o primeiro mapa de NDVI de um município

**Branch:** `feature/primeiro-ndvi` · **No PR:** `Closes #3`

**O que você vai entregar:** o contorno dos quatro municípios baixado do IBGE, o NDVI de **uma data** de **Tangará** calculado e desenhado em um mapa, e a medição de quanto isso custou em tempo e em megabytes.

Esta é a sprint em que você aprende como uma imagem de satélite é guardada. Há duas armadilhas técnicas nela (a cena que não cobre o município e o deslocamento dos valores a partir de 2022). Eu as explico nos passos 4 e 6: **leia com calma**, porque elas não dão mensagem de erro, só resultado errado.

**Divida a semana assim:**

| Dia | O que fazer |
|---|---|
| sexta, 23/10 | passos 1 a 3 (bandas, contornos e `vegetacao.py`) |
| segunda, 26/10 | passo 4 (escolher a imagem que cobre o município) |
| terça, 27/10 | passos 5 e 6 (recorte e deslocamento) |
| quarta, 28/10 | passos 7 a 9 (NDVI, mapa e medição) |
| quinta, 29/10 | passo 10 (diário, *commits* e PR); a Entrega 1 da escrita |

### Passo a passo

**1. Entenda as bandas antes de programar.** Um satélite óptico mede quanta luz a superfície reflete em várias faixas do espectro, chamadas **bandas**. Cada banda é uma imagem em tons de cinza. Você vai usar três bandas do Sentinel-2:

| Banda | O que é | Resolução |
|---|---|---|
| **B04** | luz **vermelha**. A planta saudável **absorve** essa luz para fazer fotossíntese, então reflete pouco | 10 m |
| **B8A** | **infravermelho próximo**, que o olho humano não vê. A folha saudável **reflete muito** essa luz | 20 m |
| **SCL** | não é luz: é uma **classificação** que a ESA já fez de cada pixel (vegetação, solo, água, nuvem, sombra...) | 20 m |

O NDVI combina o vermelho e o infravermelho próximo:

```
NDVI = (infravermelho - vermelho) / (infravermelho + vermelho)
```

O resultado vai de -1 a +1. Valores típicos:

| Faixa | O que costuma ser |
|---|---|
| abaixo de 0 | água, nuvem |
| 0 a 0,2 | solo exposto, rocha, área construída |
| 0,2 a 0,4 | vegetação rala ou seca |
| 0,4 a 0,7 | vegetação em bom vigor |
| acima de 0,7 | vegetação densa e muito viçosa |

Na caatinga, o NDVI varia **muito** entre a seca e a chuva, porque boa parte das plantas perde as folhas no período seco. Essa variação forte é exatamente o que torna a região interessante para este estudo.

*Pesquise* e anote no diário: o que é **resolução espacial**; por que a B8A é chamada de "infravermelho próximo estreito"; e a diferença entre a **B08** (infravermelho próximo, 10 m) e a **B8A** (20 m). Você vai usar a B8A porque ela tem a mesma resolução da SCL, e assim as três bandas casam pixel a pixel sem precisar reamostrar nada. Essa decisão vai para Materiais e Métodos.

**2. Baixe o contorno dos municípios.** Crie `baixar_limites.py`. O IBGE tem uma API que devolve o desenho do limite de qualquer município, em GeoJSON:

```
https://servicodados.ibge.gov.br/api/v3/malhas/municipios/{codigo}?formato=application/vnd.geo+json
```

O programa precisa:

1. ler `dados/municipios.csv`;
2. para cada código, **se o arquivo `dados/limites/{codigo}.geojson` ainda não existir** (*pesquise:* `os.path.exists`), baixar o GeoJSON e salvar nesse arquivo (*pesquise:* `json.dump`);
3. baixar também, do mesmo jeito, mais dois arquivos que você vai usar no mapa de localização da Sprint 4:
   - o contorno do Rio Grande do Norte, de `https://servicodados.ibge.gov.br/api/v3/malhas/estados/RN?formato=application/vnd.geo+json`, salvando em `dados/limites/rn.geojson`;
   - o Brasil dividido por estados, de `https://servicodados.ibge.gov.br/api/v3/malhas/paises/BR?formato=application/vnd.geo+json&intrarregiao=UF`, salvando em `dados/limites/brasil_uf.geojson` (cerca de 1 MB; cada estado é um item da lista `features`, com o código do estado em `properties["codarea"]`, e o do RN é `24`).

Abra um dos arquivos no VS Code e veja a estrutura: um `FeatureCollection` com uma lista `features`, e a geometria em `features[0]["geometry"]`.

**3. Crie `vegetacao.py`, o módulo das funções**, com a primeira função:

- `carregar_limite(codigo)`: abre `dados/limites/{codigo}.geojson`, lê com `json.load` e devolve a geometria do município como objeto do `shapely`, com `shape(dados["features"][0]["geometry"])` (*pesquise:* `from shapely.geometry import shape`).

Teste no terminal do Python (`python`, depois `from vegetacao import carregar_limite`): carregue Tangará (`2414001`) e mostre `geometria.bounds` e `geometria.centroid`. O `bounds` é o retângulo que envolve o município, no formato `(oeste, sul, leste, norte)`, em graus. O `centroid` é o ponto central, que você vai usar para a chuva na Sprint 5.

**4. Escolha a imagem certa: a que cobre o município inteiro.** Este é o primeiro cuidado técnico. Crie `ndvi_uma_data.py` e, nele, faça a busca de **agosto de 2024** para Tangará, como na Sprint 1, mas agora com o retângulo do município (`bbox=geometria.bounds` no lugar do `intersects`) e o período `"2024-08-01/2024-08-31"`, mantendo o filtro de nuvem abaixo de 60%.

Para cada imagem encontrada, mostre a data, o código da cena, a nuvem e mais duas coisas:

```python
from shapely.geometry import shape

area_com_dados = shape(item.geometry)
cobre_tudo = area_com_dados.contains(geometria)
percentual = 100 * area_com_dados.intersection(geometria).area / geometria.area
```

O `item.geometry` é o contorno da **área que tem dados** naquela imagem. **Agora você vai descobrir a resposta da pergunta da Sprint 1:** o Sentinel-2 divide o planeta em quadrados de cerca de 110 km × 110 km (as **cenas**, identificadas pelo código `s2:mgrs_tile`), que se sobrepõem nas bordas. Além disso, a faixa que o satélite fotografa em cada passagem (a **órbita**) não cobre a cena inteira. Por isso a mesma data aparece várias vezes, uma por cena, e **algumas dessas imagens cobrem só um pedaço do município, ou nenhum**.

Rode e veja: a imagem com **menos nuvem** do mês nem sempre é uma que cobre o município. Se você escolhesse só pela nuvem, poderia recortar um município que não está na imagem.

A regra do trabalho fica assim: **só valem as imagens que cobrem o município inteiro, e entre elas escolhe-se a de menor nuvem.** Crie em `vegetacao.py` a função `cobre_municipio(item, geometria)`, que devolve `True` ou `False`, e use-a para filtrar a lista antes de ordenar pela nuvem (*pesquise:* `sorted` com `key=lambda`).

Anote no diário a data, a cena, a nuvem e a versão de processamento (`s2:processing_baseline`) da imagem escolhida.

**5. Baixe só o recorte das três bandas.** Coloque **no topo** de `ndvi_uma_data.py`, antes de todos os outros `import`, estas linhas:

```python
import os
os.environ["GDAL_DISABLE_READDIR_ON_OPEN"] = "EMPTY_DIR"
os.environ["GDAL_HTTP_MERGE_CONSECUTIVE_RANGES"] = "YES"
```

Elas configuram a biblioteca que lê as imagens (o GDAL, que vem dentro do `rasterio`) para não fazer pedidos desnecessários ao servidor: a primeira impede que ele peça a lista de arquivos da pasta onde a imagem está, e a segunda junta pedidos de pedaços vizinhos do arquivo em um pedido só. Nos testes que fiz para preparar este plano, a leitura de uma data ficou mais rápida e baixou menos dados com elas.

Depois, crie em `vegetacao.py` a função que abre uma banda já recortada no município:

```python
import rioxarray

def abrir_recorte(item, banda, geometria):
    if banda == "B04":
        imagem = rioxarray.open_rasterio(item.assets[banda].href, masked=True, overview_level=0)
    else:
        imagem = rioxarray.open_rasterio(item.assets[banda].href, masked=True)
    recorte = imagem.rio.clip([geometria], crs="EPSG:4326", from_disk=True)
    return recorte.squeeze()
```

**O que está acontecendo aqui**, porque você vai precisar explicar isso no artigo:

- o `open_rasterio` **não** baixa a imagem. As imagens do Sentinel-2 ficam guardadas no formato **COG** (*Cloud Optimized GeoTIFF*), que permite ler só um pedaço do arquivo pela internet;
- o `clip` pede só os pixels de dentro do contorno do município, e só esses trafegam pela rede. O `crs="EPSG:4326"` avisa que o contorno do IBGE está em latitude e longitude, já que a imagem está em outro sistema de coordenadas (UTM); o `from_disk=True` faz o recorte na leitura, sem carregar a cena inteira;
- o `masked=True` transforma os pixels "sem dado" do arquivo em vazio (`nan`);
- a **B04** existe só em 10 m. O `overview_level=0` lê a **versão reduzida** que o próprio arquivo COG guarda, com o dobro do tamanho de pixel: **20 m**, a mesma grade da B8A e da SCL. Assim as três bandas saem com o mesmo número de linhas e colunas.

Abra as três bandas da imagem escolhida e mostre, para cada uma, o `.shape` e o `.rio.resolution()`. **As três precisam ter exatamente o mesmo `shape` e resolução de 20 m.**

*Pesquise:* "Cloud Optimized GeoTIFF" e "overviews" (o site `cogeo.org` explica bem). Escreva no diário, com as suas palavras, por que esse formato tornou o trabalho viável na rede do laboratório.

**6. O deslocamento de 1000 nos valores a partir da versão 04.00.** Este é o segundo cuidado técnico, e o mais traiçoeiro. Os pixels da imagem não vêm em reflectância (de 0 a 1), e sim em números inteiros. Para obter a reflectância:

- nas imagens com versão de processamento (`s2:processing_baseline`) **menor que 04.00**: `reflectância = valor / 10000`;
- nas imagens com versão **04.00 ou maior**: `reflectância = (valor - 1000) / 10000`.

A ESA passou a somar 1000 a todos os valores a partir da versão 04.00 (em uso desde 25 de janeiro de 2022), para poder representar reflectâncias muito baixas sem que virassem zero. **Se você não descontar esse 1000, o NDVI das imagens de 2022 em diante sai mais baixo que o de 2021, e a sua série temporal ganha um "degrau" falso** no começo de 2022, que parece um efeito da seca, mas é só a mudança de versão.

Faça o experimento, porque ele vai para o artigo: rode o passo 4 também para **agosto de 2021** e, para a imagem escolhida em cada ano, mostre a versão de processamento e o **menor valor** da banda B04 (`float(vermelho.min())`). Compare os dois e anote no diário. *Pesquise:* "Sentinel-2 processing baseline 04.00 BOA_ADD_OFFSET" e leia a nota da ESA sobre a mudança; ela entra nas suas Referências como documentação da fonte de dados.

Crie em `vegetacao.py` duas funções:

- `deslocamento(versao)`: recebe o texto da versão (por exemplo, `"05.11"`) e devolve `1000` se ela for 04.00 ou maior, e `0` se for menor (*pesquise:* converter o texto com `float`);
- `reflectancia(valores, desloc)`: devolve `(valores - desloc) / 10000`, transformando em vazio os resultados menores ou iguais a zero (*pesquise:* o método `.where(condição)` do `xarray`, que mantém o que satisfaz a condição e troca o resto por `nan`). Reflectância zero ou negativa não existe na natureza: é ruído, e se sobrar pode gerar divisão por zero no NDVI.

**7. Calcule o NDVI.** Crie em `vegetacao.py` a função `calcular_ndvi(vermelho, infravermelho)`, que recebe as **reflectâncias** e aplica a fórmula do passo 1. Ela funciona com números soltos e com imagens inteiras, sem mudar nada, porque o `xarray` faz a conta pixel a pixel.

**8. Desenhe o mapa e olhe para ele.** No `ndvi_uma_data.py`, desenhe o NDVI com:

```python
ndvi.plot(cmap="RdYlGn", vmin=-0.2, vmax=0.9)
```

O mapa de cores `RdYlGn` vai do vermelho (pouco vigor) ao verde (muito vigor). **Não coloque título dentro da imagem** (o título vai na identificação da figura, no artigo, em cima dela). Salve em `graficos/ndvi_exemplo_tangara.png` com `plt.savefig(..., dpi=150, bbox_inches="tight")`.

**Abra a imagem e olhe com calma.** O contorno do município tem de aparecer (fora dele, tudo em branco). Açudes devem aparecer em vermelho-escuro (água tem NDVI negativo); a área urbana, em tons de laranja; a vegetação, em amarelo e verde. **Se a água estiver verde e a vegetação vermelha, você trocou as bandas na fórmula.** É o erro mais comum, e ele não gera mensagem de erro nenhuma.

**9. Meça o custo.** Este é um dos resultados do artigo. Envolva a leitura das três bandas e o cálculo com duas medições:

- **tempo:** `time.perf_counter()` antes e depois (*pesquise:* `time.perf_counter`);
- **volume baixado:** `psutil.net_io_counters().bytes_recv` antes e depois. A diferença é quantos bytes a máquina recebeu pela rede no intervalo. Divida por 1.000.000 para ter megabytes.

O `psutil` mede **tudo** o que a máquina recebeu, inclusive o que outros programas baixaram ao mesmo tempo. Por isso, **feche o navegador e outros programas** enquanto mede. Rode três vezes, anote os três valores no diário e calcule a média. Essa limitação da medida vai para o artigo, na seção de Materiais e Métodos.

Faça a conta no diário: 4 municípios × 60 meses = 240 datas. Multiplique pela média de segundos e de megabytes por data e anote quanto tempo e quantos gigabytes o trabalho inteiro vai custar. **Leve esses números para o acompanhamento da próxima sexta.** Se o tempo por data passar de 5 minutos, comente na *issue* na mesma hora (é o plano B da [seção 10](#riscos)).

**10. Diário, *commits* e PR.** Atualize o diário com as anotações dos passos 1, 4, 5, 6 e 9. Faça os *commits* e abra o PR com `Closes #3`, colando em **Evidências de teste** a saída do `ndvi_uma_data.py` e o mapa `graficos/ndvi_exemplo_tangara.png`.

### Como saber que deu certo

- `dados/limites/` tem os quatro contornos, o do RN e o do Brasil, e rodar `baixar_limites.py` de novo não baixa outra vez.
- `ndvi_uma_data.py` lista as imagens do mês com `cobre_tudo` e o percentual de cobertura, e escolhe uma que cobre o município inteiro.
- As três bandas saem com o mesmo `shape` e resolução de 20 m.
- O diário mostra o menor valor da B04 em 2021 e em 2024, e a explicação da diferença.
- O mapa de NDVI faz sentido visualmente (água em vermelho-escuro, vegetação em verde).
- Tempo e megabytes por data, com a projeção para as 240 datas, anotados no diário.

### Entrega da sprint

- [ ] `baixar_limites.py` e os seis arquivos em `dados/limites/`.
- [ ] `vegetacao.py` com `carregar_limite`, `cobre_municipio`, `abrir_recorte`, `deslocamento`, `reflectancia` e `calcular_ndvi`.
- [ ] `ndvi_uma_data.py` escolhendo a imagem que cobre o município, com o deslocamento aplicado.
- [ ] Experimento do deslocamento (2021 × 2024) anotado no diário.
- [ ] `graficos/ndvi_exemplo_tangara.png`, conferido visualmente.
- [ ] Tempo, megabytes e projeção para as 240 datas no diário.
- [ ] PR aberto para a `develop`, com `Closes #3`.

### Erros comuns

- **`clip` dá erro de "No data found in bounds":** a imagem escolhida não cobre o município. Você esqueceu o filtro do passo 4.
- **As bandas saem com tamanhos diferentes:** a B04 foi lida sem o `overview_level=0` (ficou em 10 m).
- **Tudo com NDVI negativo:** bandas trocadas na fórmula.
- **NDVI das imagens de 2024 bem mais baixo que o de 2021, sem motivo aparente:** o deslocamento não foi descontado.
- **Muito lento (vários minutos por banda):** confira se o `from_disk=True` está no `clip` e se as linhas do `os.environ` estão **antes** de todos os `import`.
- **`ModuleNotFoundError: No module named 'vegetacao'`:** você rodou o programa de dentro de outra pasta. Rode da raiz do repositório.

<a id="sprint-2-escrita"></a>
## Sprint 2 · Escrita: Introdução e Objetivo geral (Entrega 1)

**Prazo:** 29/10/2026

**O que você vai entregar:** a Introdução completa, nos cinco blocos de parágrafos da sequência fixa do [`docs/orientacoes_escrita_tcc.md`](orientacoes_escrita_tcc.md), e o Objetivo geral. Cerca de 2 páginas.

Como os resultados ainda não existem, escreva o bloco 4 (apresentação da solução) **no futuro** ("será desenvolvido", "serão analisados"). Na Sprint 8 você passa para o passado.

### Bloco 1: Contextualização (1 a 2 parágrafos)

**Pesquise:** a agricultura familiar no Agreste potiguar (os números do Censo Agropecuário que você fichou na Sprint 1); o Semiárido, com a chuva concentrada em poucos meses e a irregularidade entre anos (procure por "semiárido brasileiro", "regime pluviométrico do Rio Grande do Norte"); o papel da informação organizada no planejamento territorial.

**Escreva sobre:** a importância da agricultura familiar no Agreste e a dependência direta que ela tem da chuva. Traga **pelo menos um número** (estabelecimentos da agricultura familiar dos municípios do trabalho, com a fonte). Depois apresente o AgroAgreste como o observatório que está sendo construído para reunir e organizar essas informações, e diga qual parte dele o seu trabalho atende: um **indicador ambiental de vigor da vegetação**.

### Bloco 2: Problemática (1 a 2 parágrafos)

**Pesquise:** a falta de monitoramento contínuo da vegetação em escala municipal (levantamentos de campo são caros e raros; os dados agrícolas do IBGE são anuais e saem com atraso); os impactos da seca na agricultura familiar do semiárido; o Monitor de Secas como exemplo de acompanhamento que existe, mas em escala regional e baseado em vários indicadores.

**Escreva sobre:** o problema em duas camadas. Primeiro, **o que falta hoje**: não há um número que descreva, mês a mês e município a município, como a vegetação respondeu à chuva. Segundo, **por que a solução óbvia não é óbvia**: as imagens de satélite que permitiriam calcular esse número são públicas e gratuitas há anos; o obstáculo é o caminho até elas (encontrar a imagem certa, tirar a nuvem, recortar por município, cuidar das mudanças de versão dos dados, transformar tudo em série temporal) e o custo de fazer isso todo mês.

**Feche com a pergunta de pesquisa** da [seção 2](#ideia), com as suas palavras, e com as três perguntas menores da [seção 8.4](#escrita-geral).

**Não escreva** que "o AgroAgreste não tem indicadores". Ele está em construção, e esse é o argumento: é o momento certo de validar a técnica antes de a equipe implementá-la.

### Bloco 3: Caminho para a solução (1 parágrafo)

**Pesquise:** as formas de acompanhar a vegetação (levantamento de campo, dados agregados do IBGE, sensoriamento remoto); os satélites gratuitos e suas diferenças, comparando resolução espacial, frequência de passagem e volume de dados: **Sentinel-2** (10 a 20 m, a cada 5 dias), **Landsat** (30 m, série histórica longa) e **MODIS** (250 m, diário).

**Escreva sobre:** as alternativas, dizendo o que cada uma resolve e o que custa. Mostre que o sensoriamento remoto se destaca por cobrir **todo** o território, por ser **retroativo** (dá para reconstruir anos passados) e por ser **gratuito**. Justifique o Sentinel-2 (resolução compatível com o tamanho das propriedades da agricultura familiar) e o NDVI (o índice de vegetação mais consolidado e mais comparável com a literatura). Diga o recorte: quatro municípios, de 2021 a 2025.

### Bloco 4: Apresentação da solução (1 a 2 parágrafos)

**Escreva sobre:** o que será construído, de forma concreta: um processo em Python que, para cada município e cada mês, busca no catálogo aberto a imagem Sentinel-2 menos nublada que cobre o município, recorta apenas a área dele, descarta os pixels de nuvem, calcula o NDVI e registra o valor médio em uma série temporal. Destaque a decisão de projeto de **não armazenar imagens**: o processo baixa só o recorte, calcula o número e descarta o dado bruto.

Diga **como o indicador será avaliado**: a cobertura de dados, o ciclo anual, a correlação com a chuva com defasagens, a comparação entre anos secos e chuvosos conferida com o Monitor de Secas e a medição do custo computacional.

Registre que **todos os dados são públicos e secundários**, de órgãos oficiais, e que **o trabalho não envolve pessoas**: por isso não há necessidade de submissão ao Comitê de Ética em Pesquisa (CEP).

### Bloco 5: Vínculo com o projeto e escopo (1 parágrafo)

**Escreva sobre:** o vínculo com o projeto AgroAgreste, do IFRN, e o fato de o trabalho ser um **protótipo independente**, para validar a técnica antes de incorporá-la à plataforma. Deixe claro que a **integração ao observatório é trabalho futuro**, fora do escopo, e que o que se entrega é um indicador avaliado e uma recomendação baseada em medição.

Feche a Introdução com um parágrafo curto dizendo como o texto está organizado (o que vem na seção 2, na 3, e assim por diante).

### 1.1 Objetivo geral

Uma **única frase**, com **uma única ação principal**. Modelo do [`docs/orientacoes_escrita_tcc.md`](orientacoes_escrita_tcc.md):

> "O objetivo principal do presente trabalho consiste [na ação] de [o quê] para [finalidade]."

**Direcionamentos:**

- o verbo que melhor descreve o trabalho é **avaliar** (a ênfase é na validação do indicador), e o objeto é um indicador mensal de vigor da vegetação, obtido do NDVI de imagens Sentinel-2;
- diga **sobre qual território**: municípios do Agreste potiguar;
- diga **para quê**: apoiar o monitoramento ambiental do observatório AgroAgreste;
- **não** empilhe ações: "desenvolver, avaliar e integrar" são três objetivos, não um;
- **não** prometa o que não vai medir: escreva "vegetação", e não "áreas agrícolas" ou "produtividade".

**Confira antes de entregar:** leia o objetivo geral e a pergunta de pesquisa do bloco 2. Os dois precisam estar falando da mesma coisa.

### 1.2 Objetivos específicos

Deixe o título da seção e escreva embaixo "(a ser escrito na Sprint 8)". Eles ficam para o fim de propósito: descrevem o que foi **realmente** alcançado.

### Entrega

- [ ] Os cinco blocos, na ordem, com citações, em cerca de 2 páginas.
- [ ] Pelo menos um número do IBGE no bloco 1, com a fonte.
- [ ] A pergunta de pesquisa e as três perguntas menores no fim do bloco 2.
- [ ] Bloco 4 no futuro, com a dispensa do Comitê de Ética.
- [ ] Objetivo geral em uma frase, com uma ação principal.
- [ ] Seção 1.2 com "(a ser escrito na Sprint 8)".
- [ ] Obras citadas lançadas nas Referências.
- [ ] Versão nomeada no histórico: `Entrega 1 - Introdução - 29/10`.

Para entregar, comente na *issue* com o nome da versão e mova o card para **Em revisão**.

---

# Sprint 3: 30/10 a 05/11/2026

<a id="sprint-3-dev"></a>
## Sprint 3 · Desenvolvimento: a máscara de nuvem e o NDVI médio de uma data

**Branch:** `feature/mascara-nuvem` · **No PR:** `Closes #5`

**O que você vai entregar:** a função que transforma um mapa de NDVI em **um número só** (o NDVI médio do município naquela data), descartando os pixels de nuvem e de sombra de nuvem; os primeiros testes automatizados; e a comparação entre três limiares de aceitação de uma data.

**Por que isso importa:** nuvem é branca e reflete muito tanto no vermelho quanto no infravermelho. O NDVI de uma nuvem dá um valor baixo, parecido com o de solo exposto. Se você calcular a média sem tirar as nuvens, um mês nublado vai parecer um mês de vegetação seca, e a série temporal inteira fica errada. **Esta é a parte do trabalho que mais influencia a qualidade do resultado**, e vale escrever bastante sobre ela no artigo.

**Atenção ao calendário:** segunda, 02/11, é feriado. A semana tem quatro dias úteis.

**Divida a semana assim:**

| Dia | O que fazer |
|---|---|
| sexta, 30/10 | passos 1 a 3 (a SCL, a máscara e o `processar_data`) |
| terça, 03/11 | passo 4 (os testes) e início do passo 5 (deixe o `comparar_limiares.py` rodando) |
| quarta, 04/11 | passos 5 e 6 (análise dos limiares e figura com e sem máscara) |
| quinta, 05/11 | passo 7 (diário, *commits* e PR); a Entrega 2 da escrita |

### Passo a passo

**1. Entenda a SCL.** A banda **SCL** (*Scene Classification Layer*, camada de classificação da cena) vem pronta no Sentinel-2 L2A, em 20 m. Cada pixel traz um número que diz o que a ESA achou que ele é:

| Valor | Significado | Você usa? |
|---|---|---|
| 0 | sem dado | não |
| 1 | pixel saturado ou com defeito | não |
| 2 | área escura ou sombra do relevo | não |
| 3 | sombra de nuvem | não |
| 4 | vegetação | **sim** |
| 5 | solo sem vegetação | **sim** |
| 6 | água | **sim** |
| 7 | não classificado | **sim** |
| 8 | nuvem, probabilidade média | não |
| 9 | nuvem, probabilidade alta | não |
| 10 | cirro (nuvem fina e alta) | não |
| 11 | neve ou gelo | não |

**Confirme essa tabela na documentação oficial do Sentinel-2** (procure "Sentinel-2 L2A Scene Classification" no portal da ESA) e cite a fonte no artigo.

Duas escolhas desta tabela precisam ser justificadas no artigo, e por isso vou explicá-las:

- **a água (6) fica.** Açude é parte do município, e tirá-lo seria uma escolha que muda o indicador. Mas a água tem NDVI negativo e puxa a média para baixo: é por isso que você vai guardar também a **mediana**, que sofre menos com esses valores extremos;
- **o "não classificado" (7) fica.** São pixels que o algoritmo da ESA não conseguiu pôr em nenhuma classe, quase sempre bordas e misturas, e não nuvem. Tirá-los descartaria área boa.

**2. Escreva a máscara e o percentual, em `vegetacao.py`:**

- uma constante no topo do arquivo: `CLASSES_VALIDAS = [4, 5, 6, 7]`;
- `mascara_validos(scl)`: devolve `True` nos pixels cuja classe está em `CLASSES_VALIDAS` (*pesquise:* o método `.isin` do `xarray`);
- `percentual_valido(scl, ndvi)`: devolve a porcentagem de pixels do município que são válidos **e** têm NDVI calculado, sobre o total de pixels do município. O total de pixels do município é a contagem dos pixels da SCL que não estão vazios (*pesquise:* `.notnull()` e `.sum()`). Lembre que fora do contorno o `clip` deixou tudo vazio: esses pixels não contam.

**3. Junte tudo em `processar_data(item, geometria)`, em `vegetacao.py`.** É a função que faz, para **uma** imagem, tudo o que você fez na Sprint 2, mais a máscara. Ela:

1. marca o tempo e os bytes recebidos no início (Sprint 2, passo 9);
2. abre o recorte da B04, da B8A e da SCL;
3. calcula o deslocamento pela versão da imagem, as reflectâncias e o NDVI;
4. aplica a máscara: `ndvi_limpo = ndvi.where(mascara_validos(scl))`. O `where` mantém os pixels bons e transforma os ruins em vazio, e eles somem da média automaticamente;
5. calcula o percentual válido, o número de pixels válidos, a **média** e a **mediana** do `ndvi_limpo` (*pesquise:* `.mean()` e `.median()` do `xarray`, e converta o resultado com `float(...)`);
6. marca o tempo e os bytes no fim;
7. devolve um dicionário com as chaves `data_imagem`, `cena`, `versao`, `nuvem_cena`, `percentual_valido`, `pixels_validos`, `ndvi_medio`, `ndvi_mediana`, `segundos` e `mb_baixados`.

Se **todos** os pixels forem mascarados, a média sai `nan`. Isso não é erro do programa: é uma data toda nublada. A função deve devolver o dicionário normalmente, com percentual 0 e NDVI vazio, e quem chama decide o que fazer.

**Guarde a mediana junto com a média.** Elas quase sempre ficam próximas; quando ficarem muito diferentes, é sinal de que sobrou alguma coisa estranha na imagem (nuvem não detectada, muita água), e você quer saber disso.

Teste a função no `ndvi_uma_data.py` com a mesma imagem da Sprint 2 e confira se o NDVI médio é coerente com o mapa que você viu.

**4. Escreva os primeiros testes**, em `tests/test_vegetacao.py`. Os testes **não usam a internet**: eles montam "imagens" pequeninas com o `xarray`:

```python
import numpy as np
import xarray as xr

vermelho = xr.DataArray(np.array([[0.1, 0.3], [0.05, np.nan]]))
```

Escreva **pelo menos dez testes**, cobrindo:

| Função | O que testar |
|---|---|
| `deslocamento` | `"02.12"` e `"03.00"` dão 0; `"04.00"` e `"05.11"` dão 1000 |
| `reflectancia` | com deslocamento 1000, os valores `[[1000, 1500], [2000, 900]]` dão `[[vazio, 0.05], [0.1, vazio]]` (*pesquise:* `np.isnan` para testar o vazio) |
| `calcular_ndvi` | vermelho 0,1 e infravermelho 0,5 dão 0,6667; os dois iguais dão 0; vermelho maior que o infravermelho (água) dá negativo |
| `mascara_validos` | uma SCL `[[4, 9], [5, 3]]` dá `[[True, False], [True, False]]` |
| `percentual_valido` | essa mesma SCL, com um NDVI sem vazios, dá 50% |
| `cobre_municipio` | um "item" falso cujo contorno é um quadrado grande cobre um "município" que é um quadrado pequeno dentro dele, e não cobre um que está metade para fora |

Para o "item" falso do último teste, você não precisa do catálogo: o seu `cobre_municipio` só usa `item.geometry`. *Pesquise:* `types.SimpleNamespace` (cria um objeto com os atributos que você quiser) e `shapely.geometry.box` (cria um retângulo a partir de `oeste, sul, leste, norte`). O `item.geometry` real é um dicionário GeoJSON; para criar um a partir de um retângulo, *pesquise* `shapely.geometry.mapping`.

Rode `python -m pytest` da raiz. **Faça um teste falhar de propósito** (troque um valor esperado), veja como o `pytest` mostra a falha, e desfaça. Tire um print dos testes passando.

**5. Compare três limiares de aceitação.** A pergunta é: **com que porcentagem mínima de pixels válidos uma data representa o município?** Se 90% do município estava debaixo de nuvem, a média dos 10% restantes não representa nada. O padrão do trabalho é 60%, mas você vai **medir** o efeito de 40%, 60% e 80% antes de fechar a escolha. Isso se chama **análise de sensibilidade**, e eleva bastante o nível do artigo.

Crie `comparar_limiares.py`, para **Tangará em 2024** (12 meses). Para cada mês:

1. busque as imagens do mês, filtre as que cobrem o município e ordene pela nuvem;
2. **pule as datas repetidas** (a mesma data pode aparecer em duas cenas que cobrem o município; guarde as datas já vistas em um `set`);
3. processe **as três primeiras datas** com `processar_data`, **todas as três**, sem parar na primeira boa;
4. grave cada data processada como uma linha de `resultados/limiares_tangara_2024.csv`, com o mês, a ordem da tentativa (1, 2 ou 3) e o dicionário devolvido.

Isso processa até 36 datas e leva cerca de meia hora: deixe rodando e vá para a escrita.

Depois, **sem baixar mais nada**, simule cada limiar lendo esse CSV com o `pandas`: para cada mês, a data aceita é a **primeira tentativa** (na ordem 1, 2, 3) com percentual válido maior ou igual ao limiar; se nenhuma atingir, o mês fica **sem dado**. Monte a tabela:

| Limiar | Meses aceitos | Meses sem dado | Quais meses ficaram sem dado |
|---|---|---|---|
| 40% | | | |
| 60% | | | |
| 80% | | | |

e grave em `resultados/sensibilidade_limiar.csv`. Anote também, para os meses em que o limiar mudou a data aceita, quanto o NDVI médio mudou.

**Escolha o limiar e justifique por escrito no diário**, com os números da tabela. O raciocínio esperado é um equilíbrio: limiar baixo aceita mais meses, mas com médias menos confiáveis; limiar alto dá médias confiáveis, mas perde meses, justamente os da estação chuvosa, que são os mais interessantes. Se você escolher outro valor que não 60%, troque o valor da constante `LIMIAR_VALIDO` que você vai criar na Sprint 4 e explique na *issue*.

**6. Faça a figura com e sem máscara.** No CSV dos limiares, procure uma data com percentual válido **entre 30% e 70%** (uma data parcialmente nublada). Gere uma figura com **dois mapas lado a lado** da mesma data: à esquerda, o NDVI sem máscara; à direita, o NDVI com máscara. *Pesquise:* `plt.subplots(1, 2)` e o parâmetro `ax=` do `.plot()` do `xarray`. Use o mesmo `cmap`, `vmin` e `vmax` nos dois. Salve em `graficos/mascara_nuvem.png`.

É uma das melhores figuras que o seu artigo pode ter, porque mostra o problema e a solução na mesma imagem. Olhe bem: as nuvens aparecem como manchas de NDVI baixo à esquerda e como buracos em branco à direita? Sobrou alguma borda de nuvem sem máscara? Anote no diário o que você viu.

**7. Diário, *commits* e PR.** Faça os *commits* e abra o PR com `Closes #5`, colando em **Evidências de teste** a saída do `pytest`, a tabela de sensibilidade e a figura com e sem máscara.

### Como saber que deu certo

- `python -m pytest` mostra pelo menos dez testes passando.
- `processar_data` devolve o dicionário completo para a imagem da Sprint 2, com percentual válido e NDVI coerentes com o mapa.
- `resultados/limiares_tangara_2024.csv` tem até três linhas por mês, e `resultados/sensibilidade_limiar.csv` tem as três linhas da tabela.
- `graficos/mascara_nuvem.png` mostra a mesma data com e sem máscara, na mesma escala.
- O limiar escolhido está justificado no diário, com números.

### Entrega da sprint

- [ ] `CLASSES_VALIDAS`, `mascara_validos`, `percentual_valido` e `processar_data` em `vegetacao.py`.
- [ ] `tests/test_vegetacao.py` com pelo menos dez testes passando.
- [ ] `comparar_limiares.py`, com `resultados/limiares_tangara_2024.csv` e `resultados/sensibilidade_limiar.csv`.
- [ ] `graficos/mascara_nuvem.png`.
- [ ] Limiar escolhido e justificado no diário.
- [ ] PR aberto para a `develop`, com `Closes #5`.

### Erros comuns

- **Percentual válido sempre 100%:** a máscara não está sendo aplicada. Confira o `.isin(CLASSES_VALIDAS)` e se o `where` usa a máscara.
- **Percentual válido muito baixo em todas as datas, até nas sem nuvem:** você está dividindo pelo total de pixels do retângulo, e não pelo total de pixels do município (os de fora do contorno são vazios e não contam).
- **NDVI médio dá `nan`:** todos os pixels foram mascarados. Trate esse caso, como explicado no passo 3.
- **Os testes dão `ModuleNotFoundError`:** rode com `python -m pytest`, da raiz, e não só `pytest`.

<a id="sprint-3-escrita"></a>
## Sprint 3 · Escrita: Referencial Teórico, seções 2.1, 2.2 e 2.3 (Entrega 2)

**Prazo:** 05/11/2026

**O que você vai entregar:** as três primeiras seções do Referencial, cerca de 2,5 páginas.

**Vídeo com a explicação do Referencial Teórico (assista antes de começar):** https://youtu.be/8Qztq1Q5vb0

O tema é **interdisciplinar**: você vai ler material de computação, de sensoriamento remoto e de agronomia. Uma regra prática resolve metade dos problemas: **tudo o que vai aparecer nos Resultados precisa estar explicado antes**. Se a tabela vai mostrar "percentual de pixels válidos" ou "correlação com defasagem de dois meses", esses conceitos têm de estar definidos aqui.

Para achar artigos: Google Acadêmico, SciELO, o **Portal de Periódicos da CAPES** (acessado pela rede do IFRN, ele libera artigos pagos de revistas como a *Remote Sensing of Environment*) e os anais do **Simpósio Brasileiro de Sensoriamento Remoto (SBSR)**, que é o principal evento da área no Brasil e tem os anais abertos no site do INPE.

### 2.1 Agricultura familiar e o Agreste potiguar (cerca de 0,5 página)

**Pesquise:** a Lei nº 11.326/2006 e o Censo Agropecuário 2017 (já fichados na Sprint 1); o Agreste potiguar e o Semiárido (delimitação da SUDENE); a dependência da produção em relação à chuva.

**Escreva:** o que caracteriza a agricultura familiar e o seu peso nos municípios do trabalho; as características do território (clima semiárido, chuva concentrada em poucos meses, irregularidade entre anos). Feche dizendo **por que** faz diferença monitorar a vegetação justamente aqui: em uma região de chuva regular, o NDVI varia pouco; no semiárido, ele varia muito, e essa variação carrega informação.

### 2.2 Sensoriamento remoto e o satélite Sentinel-2 (cerca de 1 página)

**Pesquise:** "sensoriamento remoto", "reflectância", "resolução espacial, temporal, espectral e radiométrica", "correção atmosférica". Para os fundamentos, use livros brasileiros consagrados, como *Sensoriamento remoto da vegetação*, de Ponzoni, Shimabukuro e Kuplich, e *Sensoriamento remoto: princípios e aplicações*, de Evlyn Novo (procure na biblioteca do campus e na Biblioteca Virtual do IFRN). Para o Sentinel-2, use a documentação da ESA que você fichou na Sprint 1.

**Escreva:**

- o que é sensoriamento remoto e como um satélite "enxerga": ele mede a **energia refletida** pela superfície em várias faixas do espectro, inclusive faixas invisíveis ao olho humano;
- os **quatro tipos de resolução**, com o que cada um significa na prática: **espacial** (o tamanho do pixel no chão, que importa para a agricultura familiar, cujas áreas são pequenas), **temporal** (de quantos em quantos dias o satélite passa no mesmo lugar), **espectral** (quais faixas ele mede) e **radiométrica** (quantos níveis de intensidade ele distingue);
- o Sentinel-2: os satélites, a revisita, as bandas usadas e a resolução de cada uma, a divisão em cenas de cerca de 110 km × 110 km;
- a diferença entre os níveis **L1C** e **L2A**, e por que o L2A (corrigido dos efeitos da atmosfera) é o indicado para índices de vegetação;
- **o problema da nuvem**: sensores ópticos não enxergam através de nuvem, e em região com estação chuvosa isso significa perder justamente os meses mais interessantes. Apresente a **camada de classificação da cena (SCL)** como a ferramenta que o próprio produto oferece para identificar nuvem e sombra. Isso prepara o leitor para os meses sem dado dos Resultados.

### 2.3 Índices de vegetação e o NDVI (cerca de 1 página)

**Pesquise:** "índice de vegetação", "NDVI". As referências fundamentais são **Rouse e colaboradores (1974)**, que propuseram o índice (fichado na Sprint 1), e **Tucker (1979)**, publicado na revista *Remote Sensing of Environment* (pelo Portal de Periódicos da CAPES). Procure também o **SAVI**, proposto por **Huete (1988)** na mesma revista, para áreas de vegetação rala.

**Escreva:**

- por que o NDVI funciona, explicando o mecanismo físico: a vegetação saudável **absorve** a luz vermelha para a fotossíntese e **reflete fortemente** o infravermelho próximo, por causa da estrutura interna das folhas. Quanto maior a diferença entre as duas, maior o vigor;
- a fórmula, como equação numerada, e a faixa de valores com a interpretação típica (água, solo exposto, vegetação rala, vegetação densa);
- **por que o índice é "normalizado"**: dividir pela soma faz o resultado ficar entre -1 e 1 e reduz o efeito de diferenças de iluminação entre imagens. É isso que permite comparar datas diferentes e, portanto, montar uma série temporal. Vale um parágrafo;
- as **limitações do NDVI**, porque elas voltam na discussão: a **saturação** em vegetação muito densa (o índice para de crescer) e a **influência do solo** quando a vegetação é rala e o solo aparece entre as plantas, que é exatamente o caso da caatinga. Foi para corrigir isso que o SAVI foi proposto. Mencione isso aqui: é a principal ressalva técnica do trabalho e um bom candidato a trabalho futuro.

### Entrega

- [ ] Seções 2.1, 2.2 e 2.3, com cerca de 2,5 páginas e toda afirmação técnica referenciada.
- [ ] A fórmula do NDVI como equação numerada.
- [ ] A SCL apresentada na 2.2.
- [ ] As limitações do NDVI (saturação e solo) na 2.3.
- [ ] Comentários da Entrega 1 respondidos e resolvidos.
- [ ] Versão nomeada no histórico: `Entrega 2 - Referencial 2.1 a 2.3 - 05/11`.

Para entregar, comente na *issue* com o nome da versão e mova o card para **Em revisão**.

---

# Sprint 4: 06/11 a 12/11/2026

<a id="sprint-4-dev"></a>
## Sprint 4 · Desenvolvimento: a série temporal de um município e o mapa de localização

**Branch:** `feature/serie-temporal` · **No PR:** `Closes #7`

**O que você vai entregar:** o programa que processa **todos os meses de 2021 a 2025** de um município e continua de onde parou se for interrompido; a série completa de **Tangará**; o primeiro gráfico da série temporal; e o mapa de localização da área de estudo, que vai para a Metodologia.

**Divida a semana assim:**

| Dia | O que fazer |
|---|---|
| sexta, 06/11 | passos 1 a 3 (funções auxiliares e testes) |
| segunda, 09/11 | passo 4 (`gerar_serie.py`) e passo 5 (deixe Tangará rodando) |
| terça, 10/11 | passo 6 (`mapa_localizacao.py`), enquanto a série roda |
| quarta, 11/11 | passos 7 e 8 (gráfico da série e leitura do gráfico) |
| quinta, 12/11 | passo 9 (diário, *commits* e PR); a Entrega 3 da escrita |

### Passo a passo

**1. Escreva três funções auxiliares, em `vegetacao.py`:**

- `intervalo_do_mes(ano, mes)`: devolve o texto do período no formato do catálogo, do primeiro ao último dia do mês. Por exemplo, `intervalo_do_mes(2024, 2)` devolve `"2024-02-01/2024-02-29"`. *Pesquise:* `calendar.monthrange`, que devolve quantos dias o mês tem (e já sabe dos anos bissextos), e a formatação `f"{mes:02d}"`, que escreve o mês com dois dígitos;
- `escolher_candidatos(itens, geometria, maximo=3)`: recebe a lista de imagens da busca e devolve no máximo três, **sem datas repetidas**, só as que cobrem o município, da menos nublada para a mais nublada. É o que você fez à mão no `comparar_limiares.py`, agora em uma função;
- `ja_processado(caminho_csv, codigo, ano, mes)`: devolve `True` se o CSV já existe e já tem uma linha daquele município, ano e mês. Se o arquivo ainda não existe, devolve `False` (*pesquise:* `os.path.exists` e filtros com várias condições no `pandas`, unidas com `&`).

Crie no topo de `vegetacao.py` a constante `LIMIAR_VALIDO = 60` (ou o valor que você escolheu na Sprint 3).

**2. Teste as três**, em `tests/test_vegetacao.py`:

- `intervalo_do_mes`: fevereiro de 2024 termina no dia 29; fevereiro de 2023, no dia 28; dezembro de 2025 termina no dia 31; janeiro de 2021 começa em `2021-01-01`;
- `escolher_candidatos`: com cinco "itens" falsos (`SimpleNamespace` com `geometry`, `datetime` e `properties`), em que um não cobre o município e dois têm a mesma data, a função devolve três itens, na ordem certa da nuvem, sem a data repetida e sem o que não cobre;
- `ja_processado`: com um CSV pequeno que o próprio teste grava em uma pasta temporária (*pesquise:* o recurso `tmp_path` do `pytest`), devolve `True` para um mês que está no arquivo e `False` para um que não está, e `False` quando o arquivo não existe.

**3. Rode `python -m pytest`.** Todos os testes, os da Sprint 3 e os novos, precisam passar antes de você seguir.

**4. Escreva `gerar_serie.py`.** Ele recebe o código do município na linha de comando:

```
python gerar_serie.py 2414001
```

(*pesquise:* `sys.argv`). A lógica, que você deve escrever primeiro como comentários e depois transformar em código:

```python
# lê o nome do município em dados/municipios.csv e carrega o contorno
# abre o catálogo
# para cada ano de 2021 a 2025:
#     para cada mês de 1 a 12:
#         se já foi processado, pula
#         busca as imagens do mês (filtro de nuvem da cena abaixo de 60%)
#         escolhe até 3 candidatos
#         para cada candidato:
#             processa a data
#             soma o tempo e os megabytes desta tentativa ao total do mês
#             se o percentual válido for maior ou igual ao LIMIAR_VALIDO: aceita e para
#         grava UMA linha no CSV: a da data aceita, ou uma linha "sem_dado" com o motivo
#         mostra o progresso na tela
```

O arquivo de saída é `dados/ndvi_mensal.csv`, com estas colunas, nesta ordem:

```
codigo_ibge,municipio,ano,mes,situacao,motivo,data_imagem,cena,versao,nuvem_cena,percentual_valido,pixels_validos,ndvi_medio,ndvi_mediana,tentativas,segundos,mb_baixados
```

- `situacao` é `ok` ou `sem_dado`;
- `motivo` fica vazio quando é `ok`. Quando é `sem_dado`, explica: `nenhuma imagem cobre o município` (a lista de candidatos veio vazia) ou `nuvem: melhor tentativa com X% válido`;
- `tentativas` é quantas datas foram processadas naquele mês, e `segundos` e `mb_baixados` são a **soma de todas as tentativas**, inclusive as reprovadas. O custo de uma tentativa reprovada é custo de verdade, e vai para o artigo.

Três cuidados que fazem a diferença na rede do laboratório:

1. **Grave o CSV a cada mês**, e não só no final. *Pesquise:* `DataFrame.to_csv` com `mode="a"` (acrescenta ao arquivo em vez de sobrescrever) e `header=not os.path.exists(caminho)` (escreve o cabeçalho só na primeira vez). Assim, se o programa cair, tudo o que já foi feito está salvo;
2. **Se der erro de rede no meio de um mês, não grave nada daquele mês** e siga para o próximo. *Pesquise:* `try` e `except Exception as erro`, e mostre o erro na tela. Como o mês não foi gravado, ele será tentado de novo na próxima execução;
3. **Mostre o progresso.** Um programa que roda por uma hora em silêncio parece travado. Uma linha por mês basta, por exemplo: `[2024-08] Tangará: ok, NDVI=0.xxx (xx% válido, 1 tentativa, xx s, xx MB)`.

**5. Rode a série completa de Tangará.** São 60 meses. Pelos tempos da Sprint 2, deve levar de uma a duas horas. **Interrompa de propósito** uma vez no meio (`Ctrl + C`) e rode de novo: ele tem de continuar de onde parou, sem repetir meses. Tire um print disso: é a prova de que a retomada funciona. Enquanto roda, faça o passo 6 e a escrita.

**6. Faça o mapa de localização**, em `mapa_localizacao.py`. Ele vai para a seção 3.2 do artigo (Área de estudo). Uma figura com **dois painéis** lado a lado (`plt.subplots(1, 2)`):

- à esquerda, o **Brasil** com os estados em cinza claro e o **Rio Grande do Norte** destacado em outra cor (`dados/limites/brasil_uf.geojson`, o RN é o de `codarea` igual a `"24"`);
- à direita, o **Rio Grande do Norte** em cinza claro (`dados/limites/rn.geojson`) com os **quatro municípios** preenchidos em cor e o nome de cada um escrito perto do seu centro (*pesquise:* `ax.text` e `geometria.centroid`).

Para desenhar um contorno, use as coordenadas da borda: `x, y = poligono.exterior.xy` e `ax.fill(x, y, ...)`. Alguns estados são formados por **vários pedaços** (ilhas): nesse caso, o `shapely` devolve um `MultiPolygon`, e você precisa desenhar cada pedaço, que fica em `geometria.geoms`. Escreva uma função `desenhar(ax, geometria, cor)` que trate os dois casos (*pesquise:* `geometria.geom_type`).

Coloque nome nos eixos ("Longitude" e "Latitude"), use `ax.set_aspect("equal")` para o mapa não sair esticado, **não coloque título dentro da imagem** e salve em `graficos/mapa_localizacao.png` com `dpi=200`.

**7. Faça o gráfico da série**, em `grafico_serie.py`, que também recebe o código do município na linha de comando:

1. leia `dados/ndvi_mensal.csv` e filtre o município;
2. crie uma coluna de data com o primeiro dia de cada mês (*pesquise:* `pd.to_datetime` com um dicionário de `year`, `month` e `day`);
3. desenhe o NDVI médio em linha, com marcador em cada mês, e a mediana em outra linha, mais clara;
4. **os meses sem dado devem aparecer como buracos na linha**, e não ser ligados por cima. Isso acontece sozinho se o NDVI desses meses estiver vazio (`nan`) e a tabela estiver ordenada por data;
5. eixo horizontal "Mês", eixo vertical "NDVI", grade leve (`plt.grid(alpha=0.3)`), legenda, sem título;
6. salve em `graficos/serie_<codigo>.png`.

**8. Olhe o gráfico e converse com ele.** Responda no diário, porque estes parágrafos vão para os Resultados:

- dá para ver um padrão que **sobe e desce todo ano**? Em que meses o NDVI fica mais alto e em quais mais baixo?
- **existe um "degrau" na virada de 2021 para 2022?** Se a série inteira de 2022 em diante estiver mais baixa que a de 2021, desconfie do deslocamento da Sprint 2 antes de desconfiar do clima: confira se o `deslocamento` está sendo aplicado com a versão de **cada** imagem;
- quantos meses ficaram **sem dado**, e em que época do ano eles se concentram?
- há algum mês isolado muito diferente dos vizinhos? Se houver, abra a imagem daquela data (com o `ndvi_uma_data.py`) e veja o que aconteceu.

**Se você vê o ciclo anual, o seu indicador está funcionando**, e esse é o primeiro resultado de verdade do trabalho.

**9. Diário, *commits* e PR.** Faça os *commits* (o `dados/ndvi_mensal.csv` também vai para o repositório) e abra o PR com `Closes #7`, colando em **Evidências de teste** a saída do `pytest`, o print da retomada, o gráfico da série e o mapa de localização.

### Como saber que deu certo

- `python -m pytest` passa, com os testes novos.
- `dados/ndvi_mensal.csv` tem **exatamente 60 linhas** de Tangará, contando os meses sem dado.
- Interromper e rodar de novo continua de onde parou, sem linhas repetidas.
- `graficos/serie_2414001.png` mostra a série, com buracos nos meses sem dado.
- `graficos/mapa_localizacao.png` mostra o Brasil com o RN destacado e o RN com os quatro municípios.

### Entrega da sprint

- [ ] `intervalo_do_mes`, `escolher_candidatos`, `ja_processado` e `LIMIAR_VALIDO` em `vegetacao.py`, com testes.
- [ ] `gerar_serie.py` com gravação a cada mês, retomada e tratamento de erro de rede.
- [ ] `dados/ndvi_mensal.csv` com os 60 meses de Tangará.
- [ ] Print da retomada depois de uma interrupção.
- [ ] `grafico_serie.py` e `graficos/serie_2414001.png`.
- [ ] `mapa_localizacao.py` e `graficos/mapa_localizacao.png`.
- [ ] Leitura do gráfico (ciclo anual, degrau, meses sem dado) no diário.
- [ ] PR aberto para a `develop`, com `Closes #7`.

### Erros comuns

- **O programa refaz tudo do zero:** o `ja_processado` não está funcionando. Os testes do passo 2 existem para pegar isso antes.
- **Linhas repetidas no CSV:** quase sempre o `ja_processado` está comparando texto com número (o código IBGE, o ano ou o mês lidos como texto). Confira os tipos das colunas com `tabela.dtypes` e, se precisar, converta com `astype(int)`.
- **Memória estourando:** você está guardando as imagens em uma lista. Processe uma data, guarde só o dicionário e deixe a imagem ir embora.
- **O mapa de localização sai esticado:** falta o `set_aspect("equal")`.
- **Muitos meses sem dado:** na estação chuvosa é esperado. Conte quantos e em que meses: é resultado, não erro.

<a id="sprint-4-escrita"></a>
## Sprint 4 · Escrita: Referencial Teórico, seções 2.4 e 2.5 (Entrega 3)

**Prazo:** 12/11/2026

**O que você vai entregar:** as duas últimas seções do Referencial, com o quadro comparativo dos trabalhos relacionados, cerca de 2 páginas.

### 2.4 Vegetação do semiárido, chuva e séries temporais de NDVI (cerca de 1 página)

Esta é a subseção que fundamenta a sua validação. Dedique atenção a ela.

**Pesquise:** "fenologia da caatinga", "vegetação decídua", "NDVI e precipitação", "série temporal de NDVI", "*NDVI rainfall lag*", "resposta da vegetação à precipitação no semiárido", "monitoramento de secas por satélite". Busque na SciELO, no Google Acadêmico, na *Revista Brasileira de Engenharia Agrícola e Ambiental*, na *Revista Brasileira de Meteorologia*, na revista *Remote Sensing* (acesso aberto) e nos anais do SBSR.

**Escreva:**

- o comportamento da caatinga, uma vegetação **decídua**: perde as folhas na estiagem e rebrota rapidamente com as primeiras chuvas. Isso produz uma variação sazonal de NDVI muito mais forte do que em outros biomas, e é o que torna o índice um bom indicador nessa região;
- o conceito de **defasagem** (*lag*): a vegetação não responde à chuva no mesmo instante. Há um intervalo entre a chuva e o pico de verde. **Diga o que a literatura encontrou**, com a referência: com quantos meses de atraso o NDVI do semiárido responde à chuva, e com que correlação. Na sua análise (Sprint 6), você vai comparar o seu resultado com esse valor, e é essa comparação que valida o seu indicador. Anote o número com cuidado, com a página;
- o uso de séries de NDVI para **monitoramento de secas**, citando o Monitor de Secas da ANA como exemplo de aplicação operacional no Brasil.

### 2.5 Trabalhos relacionados (cerca de 1 página)

**Pesquise:** trabalhos que usaram NDVI para monitorar vegetação ou lavouras no Nordeste, na caatinga ou no semiárido; trabalhos que relacionaram NDVI e chuva. Busque nos anais do SBSR, na Biblioteca Digital Brasileira de Teses e Dissertações (BDTD), em repositórios de institutos federais e universidades, na SciELO e no Google Acadêmico. Termos úteis: "NDVI caatinga", "NDVI semiárido precipitação", "Sentinel-2 caatinga", "série temporal NDVI município".

**Escreva:** de 3 a 4 trabalhos, um parágrafo cada, dizendo qual área estudaram, qual satélite e qual período usaram, **como avaliaram** o resultado e quais as limitações. Dê preferência a trabalhos dos últimos dez anos.

Feche com um **quadro comparativo** entre esses trabalhos e o seu, com as colunas: área de estudo, satélite e resolução, período, escala de agregação (pixel, município, bacia), forma de avaliação, e se o processo é automatizado e reprodutível (código disponível). A última linha do quadro é o seu trabalho.

**Esse quadro é a justificativa do seu trabalho.** O seu diferencial provavelmente vai aparecer em duas colunas: o **recorte municipal do Agreste potiguar**, que é o território do observatório, e o fato de entregar um **processo automatizado e reprodutível, com o custo computacional medido**. Muitos trabalhos da área apresentam o resultado, mas não o caminho nem o custo para repeti-lo. Se você encontrar um trabalho que já faça exatamente isso nos mesmos municípios, comente na *issue* com a referência: ainda dá tempo de ajustar o recorte.

### Regras que valem para o referencial inteiro

- Ao fim desta entrega, a seção de Referências precisa ter **pelo menos 12 obras**.
- Releia as seções 2.1 a 2.3 e confira se todo conceito que vai aparecer nos Resultados (percentual de pixels válidos, média e mediana, correlação, defasagem) tem onde se apoiar no Referencial. A **correlação** de Pearson você explica na Metodologia (Sprint 5); aqui basta a ideia de que NDVI e chuva variam juntos.

### Entrega

- [ ] Seções 2.4 e 2.5, com cerca de 2 páginas e toda afirmação técnica referenciada.
- [ ] O valor de defasagem encontrado pela literatura, com a referência e a página.
- [ ] Quadro comparativo com 3 a 4 trabalhos e a linha do seu.
- [ ] Pelo menos 12 obras nas Referências.
- [ ] Comentários da Entrega 2 respondidos e resolvidos.
- [ ] Versão nomeada no histórico: `Entrega 3 - Referencial 2.4 e 2.5 - 12/11`.

Para entregar, comente na *issue* com o nome da versão e mova o card para **Em revisão**.

---

# Sprint 5: 13/11 a 19/11/2026

<a id="sprint-5-dev"></a>
## Sprint 5 · Desenvolvimento: os outros municípios e a chuva da NASA POWER

**Branch:** `feature/municipios-chuva` · **No PR:** `Closes #9`

**O que você vai entregar:** a série de NDVI dos quatro municípios completa, a chuva mensal de cada um baixada da NASA POWER e conferida, a tabela que junta NDVI e chuva, e o gráfico com as duas séries juntas, que provavelmente vai ser o gráfico principal do artigo.

**Divida a semana assim:**

| Dia | O que fazer |
|---|---|
| sexta, 13/11 | passo 1 (deixe Nova Cruz rodando) e passo 2 (`baixar_chuva.py`) |
| segunda, 16/11 | passo 1 (São Paulo do Potengi) e passos 3 e 4 (conferir a chuva) |
| terça, 17/11 | passo 1 (Japi) e passo 5 (juntar as tabelas) |
| quarta, 18/11 | passo 6 (gráfico NDVI e chuva) |
| quinta, 19/11 | passo 7 (diário, *commits* e PR); a Entrega 4 da escrita |

### Passo a passo

**1. Rode a série dos outros três municípios**, **um por vez**, com o mesmo `gerar_serie.py` da Sprint 4:

```
python gerar_serie.py 2408300
python gerar_serie.py 2412609
python gerar_serie.py 2405405
```

Cada um leva de uma a duas horas. **Depois de cada um, faça o gráfico** com o `grafico_serie.py` e olhe antes de passar ao próximo. No fim, `dados/ndvi_mensal.csv` tem de ter **240 linhas** (4 × 60). Enquanto cada série roda, faça os outros passos.

**2. Baixe a chuva da NASA POWER**, em `baixar_chuva.py`. A NASA POWER é uma API gratuita, sem cadastro, que devolve dados climáticos para qualquer coordenada do planeta. O endereço da chuva **mensal** é:

```
https://power.larc.nasa.gov/api/temporal/monthly/point
```

com estes parâmetros (*pesquise:* o argumento `params=` do `requests.get`, que monta o endereço por você):

| Parâmetro | Valor |
|---|---|
| `parameters` | `PRECTOTCORR,PRECTOTCORR_SUM` |
| `community` | `AG` (comunidade de agricultura) |
| `longitude` e `latitude` | as do **centro do município** (`carregar_limite(codigo).centroid`, Sprint 2), arredondadas para 4 casas |
| `start` e `end` | `2020` e `2025` (na API mensal, só o ano) |
| `format` | `JSON` |

**Por que começar em 2020, se as imagens começam em 2021?** Porque na Sprint 6 você vai comparar o NDVI de janeiro de 2021 com a chuva de **dezembro, novembro e outubro de 2020**. Sem 2020, os primeiros meses da série ficariam sem comparação.

O programa precisa, para cada município de `dados/municipios.csv`, **se o arquivo `dados/chuva_brutos/{codigo}.json` ainda não existir**, baixar e salvar a resposta inteira nesse arquivo. **Nunca mexa no arquivo bruto**: os próximos passos leem dele e gravam em outro lugar. Use `timeout=120` no `requests.get` e `resposta.raise_for_status()` logo depois, para que um erro da API apareça como erro, e não como um JSON estranho.

Abra um dos JSON no VS Code antes de seguir. Os valores ficam em `["properties"]["parameter"]["PRECTOTCORR_SUM"]`, um dicionário em que a chave é `"AAAAMM"` (por exemplo, `"202104"`) e o valor é a chuva.

**3. Confira o que cada parâmetro significa, antes de usar.** Este é o tipo de detalhe que invalida uma correlação inteira se estiver errado. Responda no diário, olhando os números do JSON:

- **qual é a unidade de cada um?** O JSON tem, no fim, a seção `parameters` com a unidade declarada. Pegue um mês de 31 dias e multiplique o `PRECTOTCORR` desse mês por 31: o resultado bate com o `PRECTOTCORR_SUM`? O que isso diz sobre o que cada parâmetro é, e sobre a unidade escrita no próprio JSON? (Confira com a documentação da NASA POWER, procurando por "POWER monthly PRECTOTCORR_SUM".)
- **o que é o mês "13"?** Cada ano tem uma chave terminada em `13` (`"202113"`). Some os 12 meses de um ano e compare com o valor do "13";
- **existe algum valor `-999`?** É o código da NASA POWER para "sem dado".

Você vai usar o `PRECTOTCORR_SUM`: a chuva **total do mês**, em milímetros.

**4. Transforme o JSON em tabela.** Crie em `vegetacao.py` a função `chuva_mensal_do_json(dados)`, que recebe o dicionário lido do JSON e devolve uma lista de dicionários `{"ano": ..., "mes": ..., "chuva_mm": ...}`, **ignorando o mês 13** e trocando `-999` por vazio (`float("nan")`). Teste em `tests/test_analise.py` com um JSON **inventado e pequeno**, montado dentro do próprio teste, que tenha três meses, um "13" e um `-999`: a função tem de devolver três linhas, sem o "13", com o vazio no lugar certo.

Depois, em `baixar_chuva.py`, use a função para gravar `dados/chuva_mensal.csv`, com as colunas `codigo_ibge,municipio,ano,mes,chuva_mm` (4 municípios × 72 meses = 288 linhas).

Agora **compare as quatro séries de chuva** (por exemplo, os totais anuais de cada município). Você vai notar algo estranho: alguns municípios têm **exatamente** os mesmos valores. *Pesquise:* qual é a **resolução espacial** da precipitação da NASA POWER, e veja a distância entre os centros dos seus municípios. Explique no diário o que aconteceu. **Isso é uma limitação importante do trabalho e vai para o artigo**: a chuva usada não distingue municípios vizinhos, e a diferença de NDVI entre eles não pode ser atribuída à chuva medida.

**5. Confira se a chuva faz sentido e junte as tabelas.**

1. Faça um gráfico de barras com a **chuva média de cada mês do ano** (média de 2020 a 2025), uma cor por município, e salve em `graficos/chuva_mensal.png`. O Agreste potiguar tem a estação chuvosa concentrada no primeiro semestre e uma estiagem marcada no segundo. **Pesquise o regime de chuvas do Agreste potiguar na literatura** e confira se o gráfico mostra o mesmo padrão. Se a chuva estiver espalhada igualmente pelo ano, tem algo errado (coordenada trocada ou parâmetro errado);
2. crie `juntar_ndvi_chuva.py`, que junta `dados/ndvi_mensal.csv` com `dados/chuva_mensal.csv` pelas colunas `codigo_ibge`, `ano` e `mes`, mantendo todas as linhas do NDVI (*pesquise:* `merge` com `how="left"`), e grava `dados/ndvi_chuva.csv`.

**Confira quantas linhas saíram: tem de ser 240.** Se o `merge` reduziu ou multiplicou as linhas, as tabelas estão desalinhadas, quase sempre por diferença de tipo (o código IBGE lido como texto em uma e como número na outra).

**6. O gráfico das duas séries juntas.** Para cada município, um gráfico com o NDVI em **linha** e a chuva em **barras**, no mesmo eixo de tempo, com dois eixos verticais: o NDVI à esquerda e a chuva (mm) à direita. *Pesquise:* `ax.twinx()` no `matplotlib`. Use barras com largura de uns 20 dias (`width=20`) para não se encostarem. Coloque nome nos dois eixos verticais, com unidade, e uma legenda. Salve em `graficos/ndvi_chuva_<codigo>.png`.

Olhe os quatro gráficos: dá para ver, a olho nu, o NDVI subindo **depois** das chuvas? Quantos meses depois, mais ou menos? Anote o seu palpite no diário. Na Sprint 6, você mede.

**7. Diário, *commits* e PR.** Faça os *commits* (os JSON brutos e os CSV vão para o repositório; são pequenos) e abra o PR com `Closes #9`, colando em **Evidências de teste** a saída do `pytest`, a contagem de linhas do `ndvi_mensal.csv` e do `ndvi_chuva.csv`, o gráfico da chuva mensal e um dos gráficos de NDVI e chuva.

### Como saber que deu certo

- `dados/ndvi_mensal.csv` tem 240 linhas (60 por município, contando os meses sem dado).
- `dados/chuva_brutos/` tem os quatro JSON, e rodar de novo não baixa outra vez.
- `dados/chuva_mensal.csv` tem 288 linhas, sem o mês 13.
- O diário responde às perguntas do passo 3 e explica por que há municípios com a mesma chuva.
- `graficos/chuva_mensal.png` mostra a estação chuvosa no primeiro semestre.
- `dados/ndvi_chuva.csv` tem 240 linhas.
- Os quatro gráficos `ndvi_chuva_<codigo>.png` têm os dois eixos com nome e unidade.

### Entrega da sprint

- [ ] Séries de NDVI dos quatro municípios em `dados/ndvi_mensal.csv` (240 linhas), com o gráfico de cada um.
- [ ] `baixar_chuva.py`, com os JSON brutos em `dados/chuva_brutos/`.
- [ ] `chuva_mensal_do_json` em `vegetacao.py`, com teste em `tests/test_analise.py`.
- [ ] `dados/chuva_mensal.csv` (288 linhas) e `graficos/chuva_mensal.png`.
- [ ] Unidades, mês 13 e resolução da NASA POWER explicados no diário.
- [ ] `juntar_ndvi_chuva.py` e `dados/ndvi_chuva.csv` (240 linhas).
- [ ] Os quatro gráficos de NDVI e chuva.
- [ ] PR aberto para a `develop`, com `Closes #9`.

### Erros comuns

- **NASA POWER devolve erro 422:** algum parâmetro está escrito errado, ou você mandou a data completa (a API mensal aceita só o ano).
- **A chuva não tem estação chuvosa:** longitude e latitude trocadas (o ponto foi parar em outro lugar).
- **O `merge` perdeu ou multiplicou linhas:** tipos diferentes na coluna de junção. Force com `astype(int)` nas duas tabelas.
- **O gráfico de dois eixos mostra só uma legenda:** cada eixo tem a sua. *Pesquise* como juntar as legendas dos dois eixos em uma só.

<a id="sprint-5-escrita"></a>
## Sprint 5 · Escrita: Metodologia e Materiais e Métodos (Entrega 4)

**Prazo:** 19/11/2026

**O que você vai entregar:** as seções 3 (Metodologia) e 4 (Materiais e Métodos), de 3 a 4 páginas. Verbos no passado e linguagem impessoal ("foi realizado", "realizou-se") no que já foi feito; para o que ainda não foi (a análise da Sprint 6 e da Sprint 7), escreva "como planejado" e passe para o passado na Sprint 6.

**Pasta com metodologias prontas para consulta:** https://drive.google.com/drive/folders/1OwAjk47aQWuRKLf-ktesizSax9csEtXO?usp=sharing

### 3.1 Classificação da pesquisa

**Pesquise:** Gil (2017) e Prodanov e Freitas (2013), com as referências completas em [`docs/orientacoes_escrita_tcc.md`](orientacoes_escrita_tcc.md). Leia os capítulos de classificação antes de escrever.

**Escreva** a classificação pelos quatro critérios, **justificando cada uma com uma frase ligada ao seu trabalho** (o erro mais comum é só listar os rótulos):

- **natureza:** aplicada, porque responde a uma necessidade concreta do observatório AgroAgreste;
- **objetivos:** exploratória e descritiva, porque investiga a viabilidade de uma técnica ainda não aplicada a esses municípios e descreve o comportamento medido do indicador;
- **abordagem:** quantitativa, porque todos os resultados são numéricos (NDVI, percentuais, correlações, tempos);
- **procedimentos:** bibliográfica e documental, porque os dados são secundários, de bases públicas oficiais (imagens, chuva e limites municipais).

### 3.2 Área de estudo e período

**Escreva:** onde fica o Agreste potiguar; quais municípios foram estudados e **por que esses** (a coluna `justificativa` do `dados/municipios.csv`); a área de cada um (procure a área territorial oficial no IBGE Cidades, `cidades.ibge.gov.br`); as características relevantes (clima, chuva, cobertura vegetal). Coloque aqui o **mapa de localização** da Sprint 4, com identificação em cima e fonte embaixo ("Fonte: elaborado pelo autor com dados do IBGE").

Informe o **período** (janeiro de 2021 a dezembro de 2025) e justifique: cinco anos é o mínimo para ter anos secos e chuvosos na mesma série, e o Sentinel-2 tem cobertura regular nesse intervalo.

### 3.3 Etapas do trabalho

**Escreva** as etapas em ordem, com uma **figura com o fluxo do processamento**, feita no draw.io (gratuito, `app.diagrams.net`): busca no catálogo → seleção da imagem que cobre o município → recorte → correção do deslocamento → máscara de nuvem → cálculo do NDVI → agregação municipal → série temporal → análise com a chuva.

As etapas:

1. levantamento bibliográfico;
2. definição da área de estudo e do período;
3. implementação da busca, da seleção e do recorte das imagens;
4. implementação da máscara de nuvem e definição do limiar de aceitação, com a análise de sensibilidade;
5. geração das séries temporais mensais de NDVI;
6. obtenção dos dados de chuva;
7. análise da relação entre NDVI e chuva, com defasagens;
8. comparação entre anos secos e chuvosos e entre municípios;
9. medição do custo computacional e elaboração da recomendação.

**Justifique as decisões que um revisor vai questionar:**

- **por que uma imagem por mês**, e não todas: para manter o volume de dados compatível com a infraestrutura, e porque o interesse é a variação sazonal, não a diária;
- **por que só imagens que cobrem o município inteiro**: para que a média de cada mês represente sempre a mesma área, sem montar mosaicos de cenas diferentes;
- **por que o limiar de X% de pixels válidos**: com a tabela de sensibilidade da Sprint 3;
- **por que a média do município**: é a escala em que o observatório trabalha. Diga também que ela mistura usos da terra diferentes, e que por isso a mediana foi guardada junto;
- **por que a água foi mantida**: como explicado na Sprint 3, passo 1.

### 4.1 Materiais

Uma **tabela das fontes de dados**, com endereço e **data de acesso**:

| Fonte | O que forneceu | Detalhes a informar |
|---|---|---|
| Sentinel-2 L2A, via Microsoft Planetary Computer | imagens de satélite | coleção `sentinel-2-l2a`, bandas B04, B8A e SCL, resolução de 20 m |
| NASA POWER | chuva mensal | parâmetro `PRECTOTCORR_SUM`, unidade, ponto de consulta (centro do município) e resolução da grade |
| IBGE, API de malhas | limites municipais e estaduais | endereço da API |
| ANA, Monitor de Secas | conferência dos anos secos | meses consultados |

Uma **tabela das ferramentas**, com a versão de cada uma (do `requirements.txt`) e para que foi usada. A **máquina** e a **internet** do laboratório (do `docs/ambiente.md`): elas importam de verdade aqui, porque parte do tempo medido é tempo de download. O **endereço do repositório** (https://github.com/nicifrn/mp_agro_monitoramento_vegetacao).

**Declare o que não foi usado e por quê:** banco de dados (240 linhas cabem em CSV), Google Earth Engine e serviços pagos (o objetivo incluía verificar a viabilidade em infraestrutura comum, com ferramentas abertas).

### 4.2 Seleção e recorte das imagens

Como o catálogo foi consultado (filtro de nuvem da cena abaixo de 60%), a regra de cobertura do município, a escolha pela menor nuvem, as até três tentativas sem datas repetidas, e o recorte pelo contorno municipal lendo apenas a janela de interesse dos arquivos COG. **Essa é a decisão que tornou o trabalho viável na infraestrutura disponível, e merece um parágrafo.** Inclua a leitura da B04 em 20 m pela versão reduzida do arquivo.

### 4.3 Máscara de nuvem e cálculo do NDVI

A correção do deslocamento de 1000 a partir da versão 04.00 (com a equação e a referência da ESA), a fórmula da reflectância, a fórmula do NDVI (cite a equação da seção 2.3), as classes da SCL usadas como válidas e as descartadas (uma tabela), o cálculo do percentual de pixels válidos, o limiar, e a agregação municipal (média e mediana dos pixels válidos).

### 4.4 Dados de chuva e análise

O parâmetro, a unidade (com a conferência que você fez), o ponto de consulta, o período e a resolução da NASA POWER. Depois, **como planejado**: a correlação de Pearson e a de Spearman entre o NDVI e a chuva, com defasagens de 0 a 3 meses construídas dentro de cada município; o tratamento dos meses sem dado (excluídos da correlação, com o número de meses usados informado); e a classificação dos anos em secos e chuvosos pelo total anual, conferida com o Monitor de Secas.

**Pesquise** a correlação de Pearson e a de Spearman em um livro de estatística básica (por exemplo, o de Bussab e Morettin, *Estatística básica*) e apresente as duas com as suas palavras: a de Pearson mede o quanto duas variáveis variam juntas **em linha reta**; a de Spearman, o quanto variam juntas **na mesma ordem**, mesmo que não em linha reta. Coloque a fórmula de Pearson como equação numerada.

### 4.5 Medição do custo computacional

Como o tempo (`time.perf_counter`) e o volume baixado (`psutil`, bytes recebidos pela rede) foram medidos, por data processada, somando as tentativas reprovadas, e em que condições (máquina, internet, outros programas fechados). Diga a limitação da medida do volume (ela conta tudo o que a máquina recebeu no intervalo).

### Entrega

- [ ] 3.1 com os quatro critérios justificados.
- [ ] 3.2 com o mapa de localização e as áreas do IBGE.
- [ ] 3.3 com o fluxograma e as justificativas das decisões.
- [ ] 4.1 com as tabelas de fontes (com data de acesso) e de ferramentas (com versão), a máquina e o repositório.
- [ ] 4.2 a 4.5 escritas, com as equações numeradas.
- [ ] Comentários da Entrega 3 respondidos e resolvidos.
- [ ] Versão nomeada no histórico: `Entrega 4 - Metodologia e Materiais e Métodos - 19/11`.

Para entregar, comente na *issue* com o nome da versão e mova o card para **Em revisão**.

---

# Sprint 6: 20/11 a 26/11/2026

<a id="sprint-6-dev"></a>
## Sprint 6 · Desenvolvimento: o NDVI responde à chuva? E quanto custa?

**Branch:** `feature/correlacao-custo` · **No PR:** `Closes #11`

**O que você vai entregar:** a tabela de correlações entre o NDVI e a chuva, com defasagens de 0 a 3 meses, por município e no conjunto; a defasagem de maior correlação; o gráfico de dispersão; e a tabela do custo computacional com a projeção para o Agreste inteiro.

**Atenção ao calendário:** sexta, 20/11, é feriado. A semana começa na segunda.

**A ideia, explicada.** Quando chove, a vegetação não fica verde no mesmo dia: ela leva algumas semanas para responder. Então o NDVI de maio provavelmente tem mais a ver com a chuva de **abril** ou de **março** do que com a de maio. Esse atraso se chama **defasagem**. Descobrir qual é a defasagem no Agreste potiguar é o resultado mais interessante do seu trabalho, e é uma informação que o observatório pode usar de verdade.

**Divida a semana assim:**

| Dia | O que fazer |
|---|---|
| segunda, 23/11 | passos 1 e 2 (defasagens e testes) |
| terça, 24/11 | passos 3 e 4 (correlações e gráfico de dispersão) |
| quarta, 25/11 | passos 5 e 6 (custo e projeção) |
| quinta, 26/11 | passo 7 (diário, *commits* e PR); a tarefa curta da escrita |

### Passo a passo

**1. Crie as colunas de chuva com atraso**, com a função `adicionar_defasagens(chuva, atrasos)` em `vegetacao.py`. Ela recebe a tabela `dados/chuva_mensal.csv` (a que vai de 2020 a 2025) e a lista `[1, 2, 3]`, e devolve a tabela com as colunas novas `chuva_lag1`, `chuva_lag2` e `chuva_lag3`: a chuva de 1, 2 e 3 meses antes. Acrescente também a coluna `chuva_acum3`, com a **soma da chuva do mês e dos dois meses anteriores**, que é a forma de "chuva acumulada" usada em vários trabalhos da área.

**Cuidado:** a tabela precisa estar **ordenada por município, ano e mês**, e o atraso tem de ser feito **dentro de cada município**, separadamente. Senão, a chuva de dezembro de 2025 de um município vira a "chuva do mês anterior" de janeiro de 2020 do município seguinte. *Pesquise:* `sort_values`; `groupby("codigo_ibge")["chuva_mm"].shift(atraso)` para o atraso; e, para a acumulada, `groupby("codigo_ibge")["chuva_mm"].transform(lambda serie: serie.rolling(3).sum())`. O `transform` devolve uma coluna do mesmo tamanho da tabela, na mesma ordem, pronta para ser gravada como coluna nova.

**É por isso que as defasagens são calculadas na tabela da chuva, antes de juntar com o NDVI:** a tabela da chuva tem 2020 inteiro, e a do NDVI não.

**2. Teste a função**, em `tests/test_analise.py`, com uma tabela inventada de **dois municípios com três meses cada**:

- a `chuva_lag1` do primeiro mês de cada município é vazia;
- a `chuva_lag1` do segundo mês do segundo município é a chuva do primeiro mês **dele**, e não do primeiro município;
- a `chuva_acum3` do terceiro mês é a soma dos três meses do mesmo município.

**3. Calcule as correlações**, em `correlacao.py`:

1. leia a chuva, adicione as defasagens e junte com `dados/ndvi_mensal.csv` por `codigo_ibge`, `ano` e `mes` (mantendo as linhas do NDVI);
2. fique só com os meses de `situacao` igual a `ok`;
3. para cada município e para **os quatro juntos**, e para cada coluna de chuva (`chuva_mm`, `chuva_lag1`, `chuva_lag2`, `chuva_lag3` e `chuva_acum3`), calcule a correlação com o `ndvi_medio` pelos dois métodos (*pesquise:* `Series.corr` com `method="pearson"` e `method="spearman"`), e conte **quantos meses** entraram na conta;
4. grave `resultados/correlacoes.csv`, com as colunas `municipio`, `chuva`, `meses`, `pearson` e `spearman`.

Crie em `vegetacao.py` uma função `correlacao(tabela, coluna_x, coluna_y, metodo)` que descarta as linhas com vazio em qualquer uma das duas colunas e devolve a correlação e o número de linhas usadas. Teste com dados inventados: duas colunas que crescem juntas em linha reta dão 1; uma que cresce enquanto a outra cai dá -1; uma linha com vazio é descartada e o número de linhas diminui.

A correlação é um número entre -1 e +1:

| Valor | Leitura |
|---|---|
| perto de +1 | quando uma sobe, a outra sobe |
| perto de 0 | não variam juntas |
| perto de -1 | quando uma sobe, a outra desce |

Monte, a partir do CSV, a tabela que vai para o artigo:

| Município | Mesmo mês | 1 mês antes | 2 meses antes | 3 meses antes | Acumulada de 3 meses |
|---|---|---|---|---|---|

**A pergunta a responder no diário:** em qual coluna a correlação é mais alta? Ela é a mesma nos quatro municípios? O resultado bate com o que a literatura diz (o valor que você anotou na seção 2.4 do Referencial)? Compare também com o palpite que você fez olhando os gráficos na Sprint 5.

**4. O gráfico de dispersão.** Para a coluna de chuva de **maior correlação** no conjunto dos quatro municípios: chuva no eixo horizontal, NDVI no vertical, um ponto por mês, uma cor por município, com legenda e nome dos eixos com unidade. Se houver relação, os pontos formam uma nuvem inclinada. Salve em `graficos/dispersao_ndvi_chuva.png`.

**5. Dois cuidados que precisam estar no diário, e depois no artigo:**

- **correlação não é causa.** Você mostrou que as duas coisas variam juntas, o que é coerente com o que se sabe da vegetação do semiárido. Não escreva que "provou" que a chuva causa o aumento do NDVI;
- **as duas séries têm estação**, e isso infla a correlação: as duas sobem e descem todo ano, então parte da correlação vem só de seguirem o calendário. Esta limitação vai para a seção de Limitações. Remover esse efeito é um dos [extras](#extras).

**6. O custo computacional e a projeção**, em `custo.py`.

1. A partir de `dados/ndvi_mensal.csv`, monte, por município e no total: meses `ok`, meses `sem_dado`, total de tentativas, tempo total (em minutos), megabytes totais, tempo médio por mês (em segundos) e megabytes médios por mês. Grave em `resultados/custo.csv`.
2. **Calcule a área de cada município em km²**, a partir do contorno. Como o contorno está em graus, ele precisa antes ser convertido para metros, em uma projeção que **preserva as áreas**. Esta peça você pode usar como está:

   ```python
   import numpy as np
   import shapely
   from pyproj import Transformer

   transformador = Transformer.from_crs("EPSG:4326", "ESRI:102033", always_xy=True)

   def para_metros(coordenadas):
       x, y = transformador.transform(coordenadas[:, 0], coordenadas[:, 1])
       return np.column_stack([x, y])

   area_km2 = shapely.transform(geometria, para_metros).area / 1_000_000
   ```

   O `ESRI:102033` é a projeção cônica equivalente de Albers para a América do Sul: "equivalente" quer dizer que ela preserva as áreas (*pesquise:* "projeção equivalente" e por que uma projeção qualquer, como a UTM ou a policônica, distorce a área). O `pyproj` já veio instalado junto com o `rioxarray`. Compare a área calculada com a área territorial oficial do IBGE Cidades que você usou na seção 3.2 e anote no diário. A diferença deve ser pequena; se passar de 5%, registre e explique que a malha da API e a área oficial podem ter sido calculadas com versões diferentes dos limites.
3. **Projete o custo para o Agreste inteiro.** O Agreste Potiguar tem 43 municípios. Baixe o contorno de todos eles de uma vez, em um arquivo só:

   ```
   https://servicodados.ibge.gov.br/api/v3/malhas/mesorregioes/2403?formato=application/vnd.geo+json&intrarregiao=municipio
   ```

   (salve em `dados/limites/agreste.geojson`; cada município é um item de `features`), some as áreas e calcule: **megabytes por km² por mês** e **segundos por km² por mês**, a partir dos seus quatro municípios, multiplicados pela área total do Agreste. O resultado é quanto custaria, em tempo e em dados, atualizar o indicador **uma vez por mês para os 43 municípios**. Grave a projeção em `resultados/custo_projecao.csv`, com a explicação do cálculo no diário.

   A projeção pela área é uma aproximação: municípios que não cabem em uma cena só (como Santa Cruz) custariam mais, porque precisariam de mosaico. Escreva isso no diário.

**7. Diário, *commits* e PR.** Faça os *commits* e abra o PR com `Closes #11`, colando em **Evidências de teste** a saída do `pytest`, a tabela de correlações, o gráfico de dispersão e a tabela de custo com a projeção.

### Como saber que deu certo

- `python -m pytest` passa, com os testes das defasagens e da correlação.
- `resultados/correlacoes.csv` tem 25 linhas (5 grupos × 5 colunas de chuva), com o número de meses de cada uma.
- A coluna de maior correlação está identificada no diário e comparada com a literatura.
- `graficos/dispersao_ndvi_chuva.png` mostra os quatro municípios em cores diferentes.
- `resultados/custo.csv` e `resultados/custo_projecao.csv` existem, e a área calculada dos quatro municípios bate com a do IBGE.

### Entrega da sprint

- [ ] `adicionar_defasagens` e `correlacao` em `vegetacao.py`, com testes.
- [ ] `correlacao.py` e `resultados/correlacoes.csv`.
- [ ] Coluna de maior correlação identificada e comparada com a literatura no diário.
- [ ] `graficos/dispersao_ndvi_chuva.png`.
- [ ] Os dois cuidados (causa e estação) anotados no diário.
- [ ] `custo.py`, `resultados/custo.csv` e `resultados/custo_projecao.csv`.
- [ ] PR aberto para a `develop`, com `Closes #11`.

### Erros comuns

- **Correlação estranhamente baixa:** confira se a defasagem foi feita dentro de cada município e com a tabela ordenada. Olhe algumas linhas da tabela antes de calcular.
- **Correlação exatamente 1:** você correlacionou uma coluna com ela mesma.
- **Os primeiros meses de 2021 ficaram sem defasagem:** você calculou as defasagens depois de juntar com o NDVI. Calcule na tabela da chuva, que começa em 2020.
- **A área sai minúscula (menor que 1):** você calculou a área em graus. Faltou converter para metros com a função `para_metros`.

<a id="sprint-6-escrita"></a>
## Sprint 6 · Escrita: colocar no documento as tabelas e os gráficos das Sprints 3 a 5

**Prazo:** 26/11/2026

**O que você vai entregar:** as tabelas e os gráficos que já existem colocados no lugar certo da seção 5, e a seção 4 sem nada "como planejado". Nesta semana não há entrega de seção nova. Esta tarefa existe para a próxima semana ser só de escrever: **quem deixa os Resultados para o fim não entrega**.

### Passo a passo

**1. Crie os títulos** 5.1 a 5.6 da seção 5 no documento (veja a [seção 8.3](#escrita-geral)).

**2. Monte a tabela de cobertura de dados** na 5.1: por município, quantos meses `ok`, quantos `sem_dado`, a porcentagem da série perdida e em que meses do ano estão os meses perdidos. Os números saem do `dados/ndvi_mensal.csv` (faça a contagem com o `pandas` e copie). Coloque também, na 5.1, a tabela de sensibilidade do limiar (Sprint 3) e a figura com e sem máscara.

**3. Coloque os gráficos** na 5.2 (as quatro séries de NDVI, que podem virar uma figura só com quatro painéis, ou as duas mais contrastantes) e na 5.3 (os gráficos de NDVI e chuva e a tabela de correlações desta semana).

**4. Coloque na 5.5 a tabela de custo** desta semana.

**5. Para cada tabela e figura**, escreva **uma frase antes** anunciando o que ela mostra ("A Tabela 3 apresenta..."). A discussão vem na Sprint 7. Toda tabela e figura com identificação em cima, centralizada, e fonte embaixo ("Fonte: elaborado pelo autor"). Números decimais com **vírgula**.

**6. Complete a seção 4.4**, tirando o "como planejado" do que já foi feito (as correlações), e passe a seção 4 inteira para o passado.

### Entrega

- [ ] Títulos 5.1 a 5.6 criados.
- [ ] Tabela de cobertura, tabela de sensibilidade e figura com e sem máscara na 5.1.
- [ ] Séries de NDVI na 5.2; gráficos de NDVI e chuva e tabela de correlações na 5.3; tabela de custo na 5.5.
- [ ] Uma frase anunciando cada tabela e figura, com identificação e fonte.
- [ ] Seção 4 no passado, sem "como planejado" no que já foi feito.
- [ ] Comentários da Entrega 4 respondidos e resolvidos.
- [ ] Versão nomeada no histórico: `Sprint 6 - tabelas e gráficos - 26/11`.

Para entregar, comente na *issue* com o nome da versão e mova o card para **Em revisão**.

---

# Sprint 7: 27/11 a 03/12/2026

<a id="sprint-7-dev"></a>
## Sprint 7 · Desenvolvimento: anos secos, anos chuvosos e os mapas

**Branch:** `feature/anos-secos-mapas` · **No PR:** `Closes #13`

**O que você vai entregar:** a comparação do NDVI entre o ano mais seco e o mais chuvoso da série, conferida com o Monitor de Secas; os mapas de NDVI do mesmo mês em um ano seco e em um chuvoso, lado a lado; a comparação entre os quatro municípios; e todas as figuras revisadas para o artigo.

**Atenção ao calendário:** os Resultados vencem na quinta, 03/12. **Os mapas e as tabelas precisam estar prontos até segunda, 30/11.**

**Divida a semana assim:**

| Dia | O que fazer |
|---|---|
| sexta, 27/11 | passos 1 a 3 (anos, Monitor de Secas e curvas) |
| segunda, 30/11 | passos 4 e 5 (mapas e comparação entre municípios) |
| terça, 01/12 | passo 6 (revisão das figuras) |
| quarta e quinta, 02 e 03/12 | escrita dos Resultados; passo 7 (diário e PR) |

### Passo a passo

**1. Classifique os anos**, em `anos_secos_chuvosos.py`. A partir de `dados/ndvi_mensal.csv` e `dados/chuva_mensal.csv`, só de **2021 a 2025**, monte por município e por ano:

- a chuva total do ano;
- o NDVI médio dos meses `ok` do ano, **e quantos meses `ok` o ano teve** (uma média de 6 meses não vale o mesmo que uma de 12, e o leitor precisa saber);
- o NDVI máximo do ano (o pico de verde).

*Pesquise:* `groupby` com `agg`, que calcula várias coisas de uma vez. Grave em `resultados/anos.csv` e identifique, por município, o **ano mais seco** e o **ano mais chuvoso** (menor e maior chuva total). Grave os dois em `resultados/extremos.csv`, com a chuva, o NDVI médio, o NDVI máximo e a diferença entre os dois anos.

**2. Confira com a realidade, no Monitor de Secas.** Isto é importante e é fácil de esquecer: os anos que apareceram como secos na sua análise foram, de fato, anos de seca reconhecida no Rio Grande do Norte? Abra o Monitor de Secas (`monitordesecas.ana.gov.br`), vá ao mapa e, para **cada ano de 2021 a 2025**, consulte dois meses: **julho** (fim da estação chuvosa) e **dezembro** (fim da estiagem). Em cada um, anote a **categoria de seca** que o mapa mostra na região dos seus municípios: sem seca relativa, S0 (fraca), S1 (moderada), S2 (grave), S3 (extrema) ou S4 (excepcional). Grave as 10 consultas em `resultados/monitor_secas.csv`, com as colunas `ano`, `mes`, `categoria` e `data_da_consulta`, e tire um print de pelo menos um dos mapas.

Compare no diário: o ano mais seco pela chuva da NASA POWER é um ano de seca mais forte no Monitor? E o mais chuvoso, de seca mais fraca ou sem seca? **Se bater, você tem uma validação externa do indicador**, ou seja, a sua medição concorda com uma fonte independente: é um argumento forte no artigo. Se não bater, investigue e relate: também é resultado.

**3. Compare as curvas do ano seco e do ano chuvoso.** Uma figura com **quatro painéis** (um por município; *pesquise:* `plt.subplots(2, 2)`), cada um com duas linhas: o NDVI mês a mês do ano mais seco e do ano mais chuvoso daquele município, com o mês (1 a 12) no eixo horizontal. Use a **mesma escala vertical** nos quatro painéis (*pesquise:* `sharey=True`). Salve em `graficos/ano_seco_chuvoso.png`. Dá para ver a diferença de altura do pico e, às vezes, de duração do período verde.

**4. Os mapas lado a lado**, em `mapas_comparacao.py`. Escolha **um município** (o que teve a maior diferença de NDVI entre os anos extremos) e **um mês** que esteja `ok` no ano seco e no ano chuvoso, de preferência no fim da estação chuvosa (de julho a setembro), quando a diferença costuma ser maior. A data e a cena de cada imagem estão em `dados/ndvi_mensal.csv`.

Como as imagens não foram guardadas, você vai baixar de novo só essas duas datas:

1. separe, dentro de `processar_data`, a parte que calcula o NDVI com a máscara em uma função própria, `ndvi_da_data(item, geometria)`, que devolve o mapa (o `ndvi_limpo`). O `processar_data` passa a chamá-la. Rode o `pytest` depois da mudança: é o tipo de reorganização (`refactor`) que os testes protegem;
2. busque a imagem de cada data no catálogo (período de um dia só, por exemplo `"2023-08-12/2023-08-12"`) e fique com a da cena anotada no CSV (`item.properties["s2:mgrs_tile"]`);
3. desenhe os dois mapas lado a lado (`plt.subplots(1, 2)`), **com o mesmo `cmap`, o mesmo `vmin` e o mesmo `vmax`** e uma barra de cores só. Escreva embaixo de cada mapa o ano e a data (*pesquise:* `ax.set_xlabel`). Salve em `graficos/mapas_seco_chuvoso.png`, com `dpi=200`.

> **Usar a mesma escala nos dois mapas é obrigatório.** Se cada mapa usar a sua própria escala, os dois vão parecer igualmente verdes, e a comparação vira ilusão de ótica. É um erro comum e sério em trabalhos com mapas.

Esses dois mapas lado a lado são, provavelmente, **a figura mais forte do seu artigo**: qualquer pessoa entende o resultado em dois segundos.

**5. Compare os municípios.** Monte `resultados/resumo_municipios.csv` com, por município: meses `ok`, NDVI médio, mínimo, máximo, **amplitude** (máximo menos mínimo) e a média da diferença entre a média e a mediana. E uma figura com as **quatro séries sobrepostas** no mesmo gráfico, uma cor por município: `graficos/series_municipios.png`.

Responda no diário: o ciclo anual é parecido nos quatro? Algum mantém o NDVI mais alto na estiagem (o que pode indicar mais vegetação que não perde as folhas, ou irrigação)? Algum varia muito mais? Lembre que os municípios com a mesma chuva (Sprint 5) **não** podem ter as diferenças de NDVI explicadas pela chuva medida: procure outra explicação (relevo, uso da terra, distância do litoral) e diga que é uma hipótese.

**6. Revise todas as figuras do artigo.** Para cada gráfico e mapa de `graficos/`: eixos com nome e **unidade**, legenda quando houver mais de uma série, **nenhum título dentro da imagem** (na ABNT o título vai acima da figura, no texto), letras legíveis quando a figura for reduzida no documento, salvo com `dpi=150` ou mais. Refaça o que não estiver assim.

**7. Diário, *commits* e PR.** Faça os *commits* e abra o PR com `Closes #13`, colando em **Evidências de teste** a saída do `pytest`, as tabelas `extremos.csv` e `monitor_secas.csv`, os mapas lado a lado e a figura dos quatro municípios.

### Como saber que deu certo

- `resultados/anos.csv` tem 20 linhas (4 municípios × 5 anos), com o número de meses `ok` de cada ano.
- `resultados/monitor_secas.csv` tem as 10 consultas, e o diário diz se os anos extremos batem com o Monitor.
- `graficos/ano_seco_chuvoso.png` tem quatro painéis com a mesma escala vertical.
- `graficos/mapas_seco_chuvoso.png` mostra os dois mapas com a mesma escala de cores e uma barra só.
- `python -m pytest` passa depois da separação da `ndvi_da_data`.

### Entrega da sprint

- [ ] `anos_secos_chuvosos.py`, com `resultados/anos.csv` e `resultados/extremos.csv`.
- [ ] `resultados/monitor_secas.csv` com as 10 consultas e a comparação no diário.
- [ ] `graficos/ano_seco_chuvoso.png`, com a mesma escala vertical.
- [ ] `ndvi_da_data` separada, `mapas_comparacao.py` e `graficos/mapas_seco_chuvoso.png`, com a mesma escala de cores.
- [ ] `resultados/resumo_municipios.csv` e `graficos/series_municipios.png`.
- [ ] Todas as figuras revisadas.
- [ ] PR aberto para a `develop`, com `Closes #13`.

### Erros comuns

- **Os dois mapas parecem iguais:** escalas de cor diferentes. Confira se os dois usam o mesmo `vmin` e `vmax`.
- **A imagem da data não aparece na busca:** o período de um dia precisa ter a data de início igual à de fim, e a cena tem de ser a do CSV.
- **Os dois anos extremos têm números de meses `ok` muito diferentes:** é esperado, porque o ano chuvoso tende a ter mais nuvem e, portanto, mais meses sem dado. Olhe a coluna de meses `ok` antes de comparar as médias e escreva isso no diário: é uma ressalva que vai para a seção 5.4.

<a id="sprint-7-escrita"></a>
## Sprint 7 · Escrita: Resultados e Discussão (Entrega 5)

**Prazo:** 03/12/2026

**O que você vai entregar:** a seção 5 completa, de 4 a 6 páginas. É a seção mais importante do artigo. As tabelas e os gráficos já estão no documento desde a Sprint 6: agora é escrever a discussão.

> **Regra sem exceção:** toda figura ou tabela é **anunciada no texto antes** de aparecer e **explicada depois**. Nada de duas figuras seguidas sem texto entre elas. Organize a seção respondendo às **três perguntas de pesquisa**, na ordem.

### 5.1 Cobertura de dados obtida

Comece por aqui, porque é o que sustenta todo o resto: a tabela de cobertura, a análise de sensibilidade do limiar e a figura com e sem máscara. **Discuta:** quantos por cento da série se perdeu por nuvem, em que época do ano, e o que isso significa para um observatório que pretenda usar o indicador todo mês. **Esse achado é um resultado, não uma falha**, e é uma informação de que a equipe do projeto precisa.

### 5.2 O ciclo anual da vegetação (pergunta 1)

As séries de NDVI e a tabela-resumo dos municípios. **Discuta:** em que meses o NDVI sobe e desce, se o padrão se repete nos cinco anos, e compare com o que a literatura descreve sobre a caatinga (seção 2.4): essa comparação é a primeira validação. Discuta a **amplitude** (a assinatura da vegetação que perde as folhas) e as diferenças entre municípios. Inclua um mapa de NDVI de um mês de pico verde, para o leitor ver como o vigor varia dentro do município: a média esconde essa variação.

### 5.3 A relação entre NDVI e chuva (pergunta 2)

O resultado central. Comece pelo gráfico de NDVI e chuva, depois a tabela de correlações e o gráfico de dispersão. **Discuta:**

- qual defasagem (ou a chuva acumulada) deu a maior correlação, e se ela é igual nos quatro municípios;
- **compare com a literatura**: o valor que você encontrou está na faixa que os trabalhos relatam para o semiárido? Se estiver, o indicador foi validado contra o conhecimento consolidado. Se não, discuta por quê;
- a diferença entre Pearson e Spearman, se houver;
- **as ressalvas**: correlação não é causa, e a estação comum às duas séries infla a correlação;
- a chuva igual para municípios vizinhos (resolução da NASA POWER) e o que isso limita na comparação entre eles.

### 5.4 Anos secos e anos chuvosos (pergunta 3)

A tabela dos extremos, as curvas e os **mapas lado a lado** (diga na legenda que a escala de cores é a mesma nos dois). **Discuta:** a diferença de NDVI entre os anos extremos, em número; **a conferência com o Monitor de Secas** (se bateu, diga com todas as letras que é uma validação externa e independente); e algum ano em que NDVI e chuva não conversaram como esperado.

### 5.5 Custo computacional

A tabela de custo e a projeção para os 43 municípios do Agreste. **Discuta** a viabilidade de atualizar o indicador todo mês, o peso das tentativas reprovadas por nuvem no custo e a decisão de **não armazenar imagens**, que mantém a necessidade de disco praticamente nula. Um observatório de projeto de extensão não tem servidor de imagens: mostrar que o indicador cabe em uma máquina comum é um resultado prático relevante.

### 5.6 Limitações

Curta e honesta:

- **nuvem:** meses perdidos, concentrados justamente na estação chuvosa;
- **resolução espacial:** um pixel de 20 m pode misturar culturas diferentes em propriedades pequenas;
- **a média municipal mistura usos da terra** (lavoura, pastagem, caatinga, cidade, açude);
- **o próprio NDVI:** a influência do solo em vegetação rala, para a qual existem índices como o SAVI;
- **a chuva da NASA POWER** é uma estimativa em grade grossa, de um ponto por município, e não distingue municípios vizinhos;
- **cinco anos** é pouco para falar em tendência: o trabalho descreve variação sazonal e entre anos, **não** tendência de longo prazo.

Feche notando que várias dessas limitações valem igualmente para todos os municípios e anos, o que preserva a validade das **comparações**, ainda que os valores absolutos devam ser lidos com cautela.

### Entrega

- [ ] Seções 5.1 a 5.6, com os números dos arquivos de `resultados/`.
- [ ] Todas as figuras e tabelas anunciadas antes e explicadas depois, com identificação e fonte.
- [ ] As três perguntas de pesquisa respondidas, na ordem.
- [ ] Comparação com a literatura na 5.2 e na 5.3, e com o Monitor de Secas na 5.4.
- [ ] Comentários da Sprint 6 respondidos e resolvidos.
- [ ] Versão nomeada no histórico: `Entrega 5 - Resultados - 03/12`.

Para entregar, comente na *issue* com o nome da versão e mova o card para **Em revisão**.

---

# Sprint 8: 04/12 a 10/12/2026

<a id="sprint-8-dev"></a>
## Sprint 8 · Desenvolvimento: README, recomendação e fechamento

**Branch:** `feature/fechamento` · **No PR:** `Closes #15`

**O que você vai entregar:** a conferência de que o processo é reproduzível, o `README.md` completo, a recomendação para o AgroAgreste, o código revisado e a apresentação.

**Divida a semana assim:**

| Dia | O que fazer |
|---|---|
| sexta, 04/12 | passos 1 e 2 (conferência da reprodução e revisão do código) |
| segunda, 07/12 | passo 3 (`README.md`); a Conclusão do artigo tem de estar pronta hoje |
| terça, 08/12 | passo 4 (recomendação) |
| quarta e quinta, 09 e 10/12 | passos 5 e 6 (apresentação e PR) e o fechamento do texto |

### Passo a passo

**1. Confira se o resultado se repete.** Refazer o trabalho inteiro levaria horas de download, mas dá para conferir uma amostra. Escreva `conferir_reproducao.py`, que sorteia **um mês `ok` de cada município** em `dados/ndvi_mensal.csv` (*pesquise:* `DataFrame.sample` com `random_state`, para o sorteio sair sempre igual), busca de novo a imagem daquela data e cena, roda o `processar_data` e compara o NDVI médio e o percentual válido com os do CSV. Mostre as duas colunas lado a lado e a diferença. **A diferença tem de ser praticamente zero** (menor que 0,001). Se não for, alguma coisa mudou no código depois que a série foi gerada: investigue antes de seguir. Anote o resultado no diário: ele vai para o artigo como evidência de reprodutibilidade.

**2. Revise o código.** Para cada arquivo `.py`:

- um comentário no topo dizendo o que ele faz, o que lê e o que grava;
- cada função de `vegetacao.py` com uma *docstring* (o texto entre `"""` logo abaixo do `def`) dizendo o que recebe e o que devolve;
- nada de código comentado "para usar depois", nem de `print` de teste esquecido;
- **nenhum caminho fixo da sua máquina** (`C:\Users\...`) dentro do código: tudo relativo à raiz do repositório.

Rode `python -m pytest` no fim.

**3. Escreva o `README.md`.** Ele precisa permitir que outra pessoa repita tudo. Escreva na ordem em que a pessoa faria:

1. o que é o projeto, a que projeto pai pertence e o que ele calcula;
2. o que precisa ter: Python 3.10 ou mais novo, Git e internet;
3. como criar o ambiente virtual e instalar (`pip install -r requirements.txt`);
4. **a ordem dos scripts**, numerada, com uma linha explicando o que cada um faz, o que grava e **quanto tempo demora** (os tempos estão no diário e em `resultados/custo.csv`);
5. como rodar os testes (`python -m pytest`);
6. o que tem em cada pasta e em cada arquivo de `dados/` e de `resultados/`, com as colunas dos dois CSV principais (`ndvi_mensal.csv` e `ndvi_chuva.csv`);
7. quanto de rede e de disco é preciso;
8. as fontes de dados, com o endereço e a data de acesso;
9. a configuração da máquina onde as medições foram feitas;
10. os responsáveis.

**4. Escreva a recomendação para o AgroAgreste**, em `docs/recomendacao.md`, em **uma página**, escrita para a equipe do projeto (pessoas que não leram o artigo):

- o indicador funciona? Ele responde à chuva como esperado? (com os números principais);
- com que frequência ele pode ser atualizado no observatório, e o que fazer com os meses sem dado;
- quanto custa, em tempo e em rede, para os 43 municípios do Agreste (a projeção da Sprint 6);
- as limitações que a equipe precisa conhecer antes de publicar o indicador;
- o que seria preciso para levar isso ao observatório de verdade (por exemplo: rodar uma vez por mês, guardar o CSV, tratar os municípios que precisam de mosaico).

**5. Monte a apresentação.** Dez minutos, de 8 a 10 slides no Google Apresentações, salvos na mesma pasta do Drive do artigo: o problema (com um número da região), como o NDVI funciona, como as imagens foram obtidas (com os dois cuidados técnicos: a cena que cobre o município e o deslocamento de 1000), a máscara de nuvem (a figura com e sem máscara), o gráfico de NDVI e chuva, a tabela de correlações, os mapas lado a lado, o custo e a recomendação.

**6. Feche.** Confira o `git status` (nada de `.venv/`, `__pycache__/`, `.pytest_cache/` ou `.tif`), apague arquivos de teste soltos e abra o PR com `Closes #15`, com a saída do `pytest` e do `conferir_reproducao.py`. Depois do *merge*, os orientadores levam a `develop` para a `main` e publicam a versão `v1.0`.

### Como saber que deu certo

- `python conferir_reproducao.py` mostra diferenças menores que 0,001 nos quatro meses sorteados.
- `python -m pytest` passa, e o `git status` está limpo.
- O `README.md` tem as dez partes, e a ordem dos scripts tem o tempo de cada um.
- `docs/recomendacao.md` cabe em uma página e tem números.
- A apresentação está na pasta do Drive.

### Entrega da sprint

- [ ] `conferir_reproducao.py`, com o resultado anotado no diário.
- [ ] Código revisado (comentário no topo, *docstrings*, nenhum caminho fixo).
- [ ] `README.md` completo.
- [ ] `docs/recomendacao.md`.
- [ ] Apresentação de 10 minutos na pasta do Drive.
- [ ] Repositório limpo.
- [ ] PR aberto para a `develop`, com `Closes #15`.

<a id="sprint-8-escrita"></a>
## Sprint 8 · Escrita: Conclusão, Objetivos específicos, Resumo e Título (Entrega 6)

**Prazo:** 10/12/2026 · **A Conclusão precisa estar pronta na segunda, 07/12.**

**O que você vai entregar:** a Conclusão, os Objetivos específicos, o Resumo, o *Abstract*, as palavras-chave, o Título definitivo e o texto inteiro revisado.

### 6 Conclusão (cerca de 1 página, até 07/12)

Curta e direta. Nada de resultado, conceito ou citação que não tenha aparecido antes. **Escreva, nesta ordem:**

1. **o problema e o objetivo geral**, dizendo que foi alcançado, **com número**: "[...] uma vez que o processo desenvolvido gerou séries mensais de NDVI para quatro municípios ao longo de cinco anos, com X% dos meses aproveitados e correlação de Y com a chuva de Z meses antes";
2. **a resposta direta às três perguntas de pesquisa**, uma ou duas frases cada;
3. **as contribuições:** um processo automatizado, testado e reprodutível de geração de um indicador de vegetação em escala municipal, com código aberto; as séries de NDVI dos quatro municípios, que outros trabalhos do projeto podem reaproveitar; a medição do custo computacional; e a recomendação técnica para o AgroAgreste;
4. **as dificuldades reais**, do `docs/diario.md`: a cena que não cobria o município, o deslocamento de 1000, a escolha do limiar de nuvem, o tempo de download;
5. **trabalhos futuros**, concretos: separar o NDVI por uso da terra com o MapBiomas, para distinguir lavoura de caatinga (o principal); estender a todos os municípios do Agreste, com mosaico de cenas, e integrar ao observatório; testar o SAVI; usar uma fonte de chuva de resolução mais fina; comparar com os dados de produção agrícola do IBGE, para ver se o NDVI antecipa variações de safra.

**Não escreva** que "o NDVI mede a produtividade agrícola": ele mede vigor da vegetação. E não generalize para o semiárido inteiro o que você mediu em quatro municípios do Agreste potiguar.

### 1.2 Objetivos específicos

De 4 a 5 itens, verbo no infinitivo, minúscula no início, ponto e vírgula no fim de cada um e ponto no último, **na mesma ordem** das etapas da Metodologia e das subseções dos Resultados. Cada um tem de ser **verificável**: na Conclusão, você mostrou com número que foi atingido. "Instalar as bibliotecas" é tarefa, não objetivo.

O que os itens devem cobrir (escreva com as suas palavras): a implementação do processo de obtenção, recorte, máscara de nuvem e cálculo do NDVI; a construção das séries mensais dos quatro municípios; a análise da relação com a chuva e da diferença entre anos secos e chuvosos; e a medição do custo computacional com a recomendação ao observatório.

### Resumo, *Abstract* e palavras-chave

Escrito **por último**, depois do texto aprovado. Parágrafo único, de 150 a 250 palavras (é um artigo), impessoal, sem citações, sem siglas pouco conhecidas e sem menção a figuras ou tabelas (NBR 6028:2021). Uma ou duas frases para cada item:

1. **contexto e problema:** a dependência da agricultura familiar do Agreste em relação à chuva e a falta de acompanhamento contínuo da vegetação;
2. **objetivo:** o que o trabalho avaliou;
3. **método:** imagens Sentinel-2, quatro municípios, 2021 a 2025, máscara de nuvem, NDVI mensal, comparação com a chuva;
4. **resultados:** os números principais (meses aproveitados, correlação e defasagem, diferença entre anos secos e chuvosos, custo);
5. **conclusão:** a viabilidade do indicador e o encaminhamento para o observatório.

**Coloque números no resumo.** Resumo sem número é resumo fraco.

O ***Abstract*** é a versão em inglês. Os termos da área têm forma consagrada (*remote sensing*, *vegetation index*, *time series*, *cloud masking*, *smallholder farming*): use-as, e não a tradução literal. Não entregue tradução automática sem revisar.

**Palavras-chave:** de 3 a 5, separadas por ponto e vírgula, no campo de: sensoriamento remoto; NDVI; Sentinel-2; série temporal; semiárido; agricultura familiar. Escolha os termos pelos quais alguém **procuraria** o seu trabalho, equilibrando o lado técnico e o territorial.

### Título

Deve indicar **o que foi feito** e **onde**, coerente com o objetivo geral: a ação (monitoramento, avaliação), o objeto (vigor da vegetação por NDVI, com imagens Sentinel-2) e o recorte (municípios do Agreste potiguar). Subtítulo separado por dois-pontos, se precisar. Em trabalho com recorte territorial, **incluir o território no título** é o que faz o trabalho ser encontrado por quem pesquisa a região. Evite títulos genéricos ("Uso de satélites na agricultura") e não prometa mais do que o artigo mede ("áreas agrícolas", "produtividade"). Proponha **três opções** na *issue*; nós escolhemos uma com você na revisão.

### Revisão final

- [ ] A Introdução (bloco 4) e a Metodologia estão no **passado**?
- [ ] O objetivo geral, as perguntas de pesquisa, os objetivos específicos, as subseções dos Resultados e a Conclusão falam das mesmas coisas, na mesma ordem?
- [ ] Todos os números do Resumo, dos Resultados e da Conclusão são **exatamente** os dos arquivos de `resultados/` e `dados/`?
- [ ] Toda métrica dos Resultados foi explicada no Referencial ou na Metodologia?
- [ ] O mapa de localização está na seção 3.2?
- [ ] Os mapas comparativos usam a **mesma escala de cores**, e isso está dito na legenda?
- [ ] As fontes de dados têm endereço e **data de acesso**?
- [ ] As bandas, a resolução, o nível de processamento (L2A) e a correção do deslocamento estão informados?
- [ ] O limiar de pixels válidos está justificado com a análise de sensibilidade?
- [ ] Os meses sem dado estão informados, e não escondidos?
- [ ] As equações estão numeradas e citadas no texto?
- [ ] Toda tabela e figura é citada antes de aparecer, tem identificação em cima e fonte embaixo, e os gráficos têm unidade nos eixos?
- [ ] A seção de limitações está presente?
- [ ] As siglas (NDVI, SAVI, SCL, STAC, COG, ESA, NASA, IBGE, ANA, SUDENE, CEP) estão por extenso na primeira vez?
- [ ] O texto está impessoal e no passado?
- [ ] Está declarado que os dados são públicos e secundários e que não houve participantes humanos?
- [ ] O endereço do repositório está em Materiais e Métodos?
- [ ] Todos os comentários foram respondidos e resolvidos?
- [ ] A versão final foi nomeada no histórico: `Entrega 6 - versão final - 10/12`?

Para entregar, comente na *issue* com o nome da versão e as três opções de título, e mova o card para **Em revisão**.

---

<a id="quadro-resumo"></a>
## 9. Quadro-resumo

| Sprint | Período | Desenvolvimento | Escrita | Conceitos novos |
|---|---|---|---|---|
| 1 | 16/10 a 22/10 | Ambiente e catálogo de imagens | Preparar o documento e fichar | STAC, Sentinel-2 L2A, API do IBGE |
| 2 | 23/10 a 29/10 | Primeiro mapa de NDVI | Introdução e Objetivo geral | bandas, COG, recorte, cena que cobre o município, deslocamento de 1000 |
| 3 | 30/10 a 05/11 | Máscara de nuvem e NDVI médio | Referencial 2.1 a 2.3 | SCL, percentual válido, análise de sensibilidade, `pytest` |
| 4 | 06/11 a 12/11 | Série temporal de Tangará | Referencial 2.4 e 2.5 | gravação incremental, retomada, mapa de localização |
| 5 | 13/11 a 19/11 | Demais municípios e chuva | Metodologia e Materiais e Métodos | NASA POWER, unidade, resolução da grade, `merge` |
| 6 | 20/11 a 26/11 | Correlação e custo | Tabelas e gráficos no documento | defasagem, Pearson, Spearman, projeção equivalente |
| 7 | 27/11 a 03/12 | Anos secos e chuvosos e mapas | Resultados e Discussão | validação externa, mesma escala de cores |
| 8 | 04/12 a 10/12 | README, recomendação e fechamento | Conclusão, Resumo e Título | reprodutibilidade, síntese |

---

<a id="riscos"></a>
## 10. Riscos e planos B

| Risco | Sinal de alerta | O que fazer |
|---|---|---|
| A rede do laboratório bloqueia o catálogo | Sprint 1, erro de conexão repetido | Comente na *issue* **na mesma semana**, com o erro inteiro. É o risco mais sério do trabalho |
| Cada data custa tempo demais | Sprint 2, mais de 5 minutos por data | Comente na *issue* com os números. **Plano B:** trocar o Sentinel-2 pelo produto de NDVI do **MODIS**, que já vem calculado, em 250 m, em arquivos muito menores (coleção `modis-13Q1-061` do mesmo catálogo). O método do artigo continua o mesmo; muda a fonte e a resolução, o que vira limitação declarada. Nós decidimos com você no acompanhamento da Sprint 3 |
| A série de um município demora muitas horas | Sprints 4 e 5 | Deixe rodando em outro horário. A retomada da Sprint 4 garante que nada se perde |
| Muitos meses sem dado | Sprint 4, mais da metade dos meses `sem_dado` | Use o limiar de 40% da análise de sensibilidade e **declare a mudança** no artigo, com a tabela da Sprint 3 |
| A API da NASA POWER fora do ar | Sprint 5, erro repetido | Tente em outro horário. Se continuar por mais de um dia, comente na *issue* com o erro inteiro, e eu envio os JSON para você colocar em `dados/chuva_brutos/` (o programa não baixa de novo o que já existe) |
| O tempo aperta na Sprint 7 | segunda, 30/11, sem os mapas | Faça os mapas de um município só e as curvas dos quatro. A comparação entre municípios entra só com a tabela |
| Atraso geral | qualquer sprint | Reduza de 4 para 3 municípios (tire Japi), ou de 5 para 4 anos (tire 2025). **Não reduza** a máscara de nuvem, a correção do deslocamento nem a medição de custo |

**Se algo tiver de ser cortado, corte quantidade, não qualidade.** Três municípios bem processados valem mais que quatro processados de qualquer jeito.

---

<a id="extras"></a>
## 11. Se sobrar tempo (opcional)

Só depois de a sprint da semana estar entregue. Cada extra que você fizer vira um parágrafo a mais nos Resultados.

- **E1. Separar as áreas agrícolas com o MapBiomas.** O NDVI médio do município mistura tudo. O MapBiomas publica mapas anuais de uso da terra, em 30 m, que dizem o que é lavoura, pastagem, caatinga ou cidade. Com ele, dá para calcular o NDVI **por classe** e responder se a agricultura responde à chuva de forma diferente da caatinga. Baixe o mapa do Rio Grande do Norte de um ano, registre a fonte e o **número da coleção** (o MapBiomas numera suas versões), recorte para o município e coloque na mesma grade do NDVI (*pesquise:* `rio.reproject_match` do `rioxarray`, com reamostragem pelo vizinho mais próximo, porque são classes e não números contínuos).
- **E2. Remover o efeito do calendário na correlação.** Calcule, para cada mês do ano, a média dos cinco anos; subtraia essa média de cada valor (o resultado se chama **anomalia**); e correlacione as anomalias de NDVI com as anomalias de chuva. É um número mais conservador e mais convincente que o da Sprint 6.
- **E3. Calcular o SAVI**, índice criado para vegetação rala sobre solo exposto, que é o caso da caatinga: `SAVI = 1,5 × (infravermelho - vermelho) / (infravermelho + vermelho + 0,5)`, e comparar a série com a do NDVI.
- **E4. Testar a água fora da máscara**, tirando a classe 6 de `CLASSES_VALIDAS`, e ver quanto o NDVI médio muda em cada município.
- **E5. Animação** com um quadro por mês de um ano, mostrando o verde chegando e indo embora (*pesquise:* `matplotlib.animation`).

---

<a id="referencias-minimas"></a>
## 12. Referências mínimas do artigo

**Lado ambiental e territorial:**

- **2 a 3 fontes sobre agricultura familiar e o Agreste potiguar** (seção 2.1), incluindo a Lei nº 11.326/2006 e o Censo Agropecuário 2017 do IBGE;
- **2 a 3 fontes sobre caatinga, semiárido e chuva** (seção 2.4), incluindo a delimitação do Semiárido da SUDENE e o Monitor de Secas da ANA.

**Lado técnico:**

- **2 a 3 obras sobre sensoriamento remoto** (seção 2.2), incluindo pelo menos um livro de referência da área;
- **os trabalhos fundadores dos índices de vegetação** (seção 2.3): Rouse *et al.* (1974) e Tucker (1979), e Huete (1988) se o SAVI for citado;
- **3 a 4 trabalhos relacionados** (seção 2.5), de preferência sobre o Nordeste ou o semiárido.

**Obrigatórias:**

- **2 obras de metodologia científica:** Gil (2017) e Prodanov e Freitas (2013), em [`docs/orientacoes_escrita_tcc.md`](orientacoes_escrita_tcc.md);
- **1 livro de estatística básica**, para as correlações;
- **a documentação oficial das fontes de dados:** Sentinel-2 (ESA, incluindo a nota sobre a versão de processamento 04.00), Microsoft Planetary Computer, NASA POWER e IBGE.

Registre a referência completa de **tudo** o que ler, na seção de Referências do documento do Drive, desde o primeiro dia. Zotero e Mendeley ajudam a montar, mas confira cada entrada contra a NBR 6023:2018 antes de entregar: esses gerenciadores erram com frequência.
