### **Prompt para Geração de Código \- Passo 8**

**Persona:** Você é um Cientista de Dados especializado em Análise de Redes Sociais, encarregado de criar os artefatos de dados necessários para a modelagem de redes a partir de dados tabulares.

**Tarefa:** Crie um script em Python para gerar listas de adjacências que representem três tipos de redes distintas: coautoria, coocorrência de palavras-chave e colaboração interinstitucional. O script deve seguir estritamente a metodologia de "pareamento por artigo" descrita no artigo "BraSNAM em perspectiva...".

**Fonte da Metodologia:** O script deve ser uma implementação direta do processo descrito na seção 2.3 do artigo, que afirma: "Palavras-chave, autores e instituições foram pareados por artigo, gerando uma lista de adjacências, denotando co-ocorrência, coautoria e colaborações interinstitucionais, respectivamente".

**Requisitos Funcionais:**

1. **Linguagem:** O script deve ser escrito em Python, utilizando a biblioteca pandas para a leitura dos dados e a biblioteca itertools (especificamente itertools.combinations) para a geração eficiente de pares.  
2. **Arquivo de Entrada:**  
   * O script deve ler um arquivo CSV finalizado que contenha os dados já limpos e padronizados, com as colunas autores, instituicoes e palavras\_chave.  
3. **Lógica de Geração das Listas de Adjacências:**  
   * Carregue o arquivo CSV em um DataFrame.  
   * Crie três listas vazias em Python para armazenar as arestas de cada rede: arestas\_coautoria, arestas\_palavras\_chave e arestas\_instituicoes.  
   * Itere sobre cada linha (que representa um artigo) do DataFrame:  
     a. Para Coautoria:  
     i. Leia a célula da coluna autores e separe os nomes em uma lista.  
     ii. Se houver dois ou mais autores, gere todas as combinações únicas de pares de autores e adicione cada par à lista arestas\_coautoria.  
     b. Para Coocorrência de Palavras-chave:  
     i. Leia a célula da coluna palavras\_chave e separe os termos em uma lista.  
     ii. Se houver duas ou mais palavras-chave, gere todas as combinações únicas de pares e adicione cada par à lista arestas\_palavras\_chave.  
     c. Para Colaboração Interinstitucional:  
     i. Leia a célula da coluna instituicoes, separe os nomes e obtenha uma lista de instituições únicas para aquele artigo.  
     ii. Se houver duas ou mais instituições únicas, gere todas as combinações de pares e adicione cada par à lista arestas\_instituicoes.

**Formato da Saída:**

1. **Arquivos de Saída:** O script deve gerar **três arquivos CSV separados**, cada um representando uma lista de arestas (ou lista de adjacências) para uma rede.  
   * **Arquivo 1:** rede\_coautoria.csv, com as colunas autor\_origem e autor\_destino.  
   * **Arquivo 2:** rede\_palavras\_chave.csv, com as colunas palavra\_origem e palavra\_destino.  
   * **Arquivo 3:** rede\_instituicoes.csv, com as colunas instituicao\_origem e instituicao\_destino.  
2. **Estrutura:** Cada linha em cada arquivo de saída representará uma aresta (uma conexão) na respectiva rede.