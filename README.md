# Planejamento Inteligente de Manutenção de Escadas Rolantes

**Challenge FIAP | Engenharia de Software | Motiva | 2026**

## 1. Sobre o Projeto

Este projeto foi desenvolvido como parte do Challenge FIAP em parceria com a Motiva, com o objetivo de propor uma solução para apoiar o planejamento de manutenção das escadas rolantes da Linha 4-Amarela do metrô de São Paulo.

A aplicação utiliza dados de sensores para identificar equipamentos com sinais de degradação, estabelecer prioridades de atendimento e calcular rotas de deslocamento entre as estações.

A proposta é integrar o monitoramento dos equipamentos ao planejamento operacional das equipes de manutenção, considerando a criticidade das escadas, sua localização e o tempo disponível para os serviços.

O projeto foi desenvolvido em Python, utilizando Jupyter Notebook para implementar os algoritmos, realizar experimentos e apresentar os resultados.

## 2. Integrantes

| Nome | RM |
|---|---|
| Artur Henrique Siqueira | RM566986 |
| Davi de Souza Malta | RM560327 |
| Guilherme de Oliveira Scremin | RM564788 |
| Guilherme Cruz Alves | RM566861 |
| Pedro Sales Ferreira | RM566990 |

**Instituição:** FIAP  
**Curso:** Engenharia de Software

## 3. Tecnologias Utilizadas

- **Python:** desenvolvimento da solução e implementação dos algoritmos.
- **Pandas:** processamento dos dados e organização dos resultados.
- **Matplotlib:** visualização dos experimentos.
- **Jupyter Notebook / Google Colab:** ambiente de desenvolvimento e execução.
- **CSV e JSON:** armazenamento e exportação dos dados.
- **GitHub:** versionamento e documentação do projeto.

## 4. Desenvolvimento da Aplicação

O projeto foi dividido em cinco etapas, integrando análise de sensores, cálculo de rotas e planejamento de manutenção.

### Parte 1 — Monitoramento e Priorização das Escadas

Inicialmente, foram processadas as leituras dos sensores para avaliar a condição dos equipamentos.

A aplicação considera informações como vibração, temperatura, corrente elétrica, tensão, nível de óleo e velocidade.

Para calcular a degradação acumulada, foram implementadas três abordagens: recursão simples, recursão com memoização e tabulação.

Essas implementações foram comparadas em termos de desempenho. A partir dos índices calculados, foi elaborado um **ranking de criticidade**, identificando as escadas que devem receber maior prioridade no planejamento de manutenção.

### Parte 2 — Modelagem das Estações e Cálculo de Rotas

As estações da Linha 4-Amarela foram representadas por um grafo ponderado, incluindo uma base de manutenção simulada.

As conexões entre as estações receberam tempos estimados de deslocamento.

Foram aplicados dois algoritmos:

- **BFS:** utilizado para identificar trajetos com a menor quantidade de trechos.
- **Dijkstra:** utilizado para calcular os trajetos de menor tempo entre a base e as estações.

Os resultados permitem consultar os caminhos até os equipamentos monitorados, considerando a localização de cada escada.

### Parte 3 — Planejamento dos Atendimentos

Nesta etapa, as informações de criticidade foram integradas aos tempos de deslocamento.

Foi desenvolvida a função `planejar_turno(base, horas)`, responsável por sugerir os atendimentos que podem ser realizados dentro de um turno.

O planejamento considera:

- Prioridade dos equipamentos conforme o ranking de criticidade.
- Estação em que cada escada está localizada.
- Deslocamento entre os locais de atendimento.
- Tempo estimado para execução de cada manutenção.
- Tempo necessário para retornar à base.

Como resultado, a aplicação apresenta uma relação de escadas selecionadas para manutenção e seus respectivos tempos estimados.

### Parte 4 — Otimização e Comparação de Rotas com A*

O algoritmo A* foi implementado como uma alternativa ao Dijkstra para calcular rotas entre a base de manutenção e as estações.

Na aplicação, foi utilizada uma heurística baseada na quantidade mínima de trechos restantes e no menor peso das conexões.

O objetivo dessa etapa foi comparar os caminhos calculados pelos dois algoritmos, verificar se apresentam o mesmo custo mínimo e avaliar seus tempos de execução.

A comparação permite discutir qual abordagem é mais adequada para o cenário de deslocamento das equipes de manutenção.

### Parte 5 — Consolidação e Análise dos Resultados

A etapa final reúne os resultados gerados durante o projeto.

Foram organizadas tabelas e análises referentes ao desempenho dos algoritmos, às rotas calculadas e aos atendimentos selecionados.

Também foram implementadas verificações para conferir a consistência dos resultados, como a equivalência dos custos encontrados pelo A* e Dijkstra e o respeito à duração do turno.

Os resultados são apresentados no notebook e exportados nos formatos CSV e JSON.

## 5. Dados Utilizados

O projeto considera um cenário com **197 escadas rolantes distribuídas entre 12 estações da Linha 4-Amarela**.

O conjunto de dados utilizado na aplicação contém informações de identificação dos equipamentos, suas respectivas estações e leituras simuladas de sensores.

As variáveis monitoradas incluem:

| Variável | Aplicação no projeto |
|---|---|
| Vibração | Identificação de alterações no funcionamento mecânico |
| Temperatura | Monitoramento de possíveis condições de aquecimento |
| Corrente e tensão | Acompanhamento de alterações elétricas |
| Nível de óleo | Identificação de possíveis necessidades de lubrificação |
| Velocidade | Monitoramento de variações na movimentação da escada |

**Observação:** as leituras dos sensores, os tempos de deslocamento e as durações previstas das manutenções são utilizados para fins de simulação acadêmica. A localização da base de manutenção também é hipotética.

## 6. Resultados e Interpretação

### 6.1. Priorização dos Equipamentos

O processamento das leituras permitiu calcular índices de degradação e organizar as escadas conforme sua criticidade.

O ranking resultante foi utilizado diretamente no planejamento dos atendimentos, conectando a análise dos sensores à definição das prioridades de manutenção.

A comparação entre as implementações de degradação também permitiu avaliar o custo computacional de cada abordagem.

### 6.2. Planejamento de Rotas

A aplicação dos algoritmos BFS e Dijkstra permitiu representar os deslocamentos necessários entre a base de manutenção e as estações.

Enquanto a BFS considera a quantidade de trechos, o Dijkstra utiliza o tempo estimado de deslocamento.

O A* foi utilizado para comparar os custos mínimos encontrados e avaliar outra estratégia de busca de rotas.

Como a rede modelada possui uma estrutura simplificada, os experimentos também demonstram as limitações de desempenho dos algoritmos nesse cenário.

### 6.3. Organização do Turno de Manutenção

A integração entre o ranking de criticidade e os tempos de deslocamento possibilitou gerar um planejamento simulado para um turno de oito horas.

A aplicação seleciona os equipamentos prioritários que podem ser atendidos dentro do período disponível, considerando o deslocamento, o tempo de serviço e o retorno à base.

A solução utiliza uma estratégia de seleção por prioridade, não garantindo necessariamente a combinação globalmente ótima de atendimentos.

### 6.4. Considerações Gerais

Os resultados demonstram como informações obtidas por sensores podem ser utilizadas para apoiar decisões relacionadas à manutenção.

A solução desenvolvida integra três atividades principais: **identificação de equipamentos críticos, cálculo de rotas e organização dos atendimentos**.

Embora utilize dados simulados, o projeto apresenta uma estrutura que pode ser expandida futuramente com informações operacionais reais e técnicas adicionais de otimização.

## 7. Como Executar

### Requisitos

- Python 3.10 ou superior.
- Jupyter Notebook ou Google Colab.
- Bibliotecas Pandas, NumPy e Matplotlib.

### Instalação

Execute:

`pip install pandas numpy matplotlib jupyter`

### Passo a Passo

1. Clone ou baixe o repositório.
2. Abra o arquivo `notebook.ipynb` no Jupyter Notebook ou Google Colab.
3. Verifique se os arquivos CSV necessários estão disponíveis nos caminhos utilizados pelo código.
4. Execute as células na ordem apresentada.
5. Consulte os resultados, tabelas e gráficos gerados.

O notebook disponibilizado no repositório deverá conter todas as células previamente executadas, permitindo visualizar os experimentos sem necessidade de executá-los novamente.

## 8. Arquivos do Projeto

| Arquivo | Descrição |
|---|---|
| `notebook.ipynb` | Implementação e resultados dos experimentos |
| `README.md` | Documentação da aplicação |
| `escadas.csv` | Cadastro das escadas e suas estações |
| `leituras_sensores.csv` | Dados simulados dos sensores |
| `rede_vertices.csv` | Representação dos vértices do grafo |
| `rede_arestas.csv` | Conexões e tempos estimados |
| `plano_manutencao.csv` | Planejamento dos atendimentos |
| `comparacao_rotas.csv` | Comparação das rotas obtidas |
| `comparacao_algoritmos.csv` | Comparação entre A* e Dijkstra |
| `resumo_turno.csv` | Resumo do turno planejado |

Os arquivos de resultados são gerados na pasta `resultados/`, nos formatos CSV e JSON.

## 9. Conclusão

O projeto permitiu desenvolver uma solução integrada para apoiar o planejamento de manutenção de escadas rolantes, combinando o processamento de leituras de sensores com algoritmos de busca e organização de atendimentos.

A aplicação utiliza os índices de degradação para definir prioridades, calcula rotas entre as estações e propõe atendimentos considerando o tempo disponível de uma equipe.

Além de demonstrar a utilização prática dos algoritmos estudados, o projeto evidencia como a integração de dados e métodos computacionais pode contribuir para uma gestão de manutenção mais organizada e orientada por informações.

## 10. Entrega

O repositório GitHub contém o código-fonte, a documentação e o notebook com os experimentos executados, além dos arquivos necessários para reproduzir a aplicação.

O link do repositório será disponibilizado por meio do **Microsoft Teams**, conforme os requisitos de entrega da disciplina.

---

**FIAP | Engenharia de Software | Challenge Motiva — 2026**