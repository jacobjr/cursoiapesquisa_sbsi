### **Prompt para Geração de Código \- Passo 7**

**Persona:** Você é um Engenheiro de Dados encarregado de implementar um script de limpeza de dados que utiliza um conjunto de regras de mapeamento definidas manualmente, replicando um processo de pesquisa científica.

**Tarefa:** Crie um script em Python para padronizar os nomes das instituições em um conjunto de dados. O script deve aplicar um conjunto de regras de mapeamento a partir de um arquivo externo, seguindo estritamente a metodologia de "inspeção manual" e mapeamento descrita no artigo "BraSNAM em perspectiva...".

**Fonte da Metodologia:** O script deve ser uma implementação direta do processo descrito nas seções 2.3 e 3.3. O artigo afirma: "As instituições também foram mapeadas dessa forma \[...\] realizando uma inspeção manual". O texto fornece exemplos claros de mapeamento, como transformar "universidade de brazilia", "university of brasilia" e "unb" em "Universidade de Brasília", e diferentes variações de "CEFET/RJ" para "cefet-rj".

**Requisitos Funcionais:**

1. **Linguagem:** O script deve ser escrito em Python.  
2. **Arquivos de Entrada:**  
   * **Arquivo de Dados:** dados\_brasnam\_preprocessados.csv (gerado no Passo 4).  
   * **Arquivo de Mapeamento:** O script deve ler as regras de um arquivo externo que será criado pelo usuário, chamado mapeamento\_instituicoes.csv. Este arquivo deve conter duas colunas: nome\_original e nome\_padronizado.  
3. **Coluna-Alvo:**  
   * O processo de padronização deve ser aplicado à coluna instituicoes.  
4. **Lógica de Padronização:**  
   * **Carregar Regras:** Carregue as regras do mapeamento\_instituicoes.csv para uma estrutura de dados eficiente para busca (ex: um dicionário Python).  
   * **Processar Coluna:** Itere sobre cada célula da coluna instituicoes no DataFrame principal.  
   * Aplicar Mapeamento: Para cada nome de instituição encontrado na célula (lembrando que podem ser múltiplos, separados por ;):  
     a. Busque o nome no dicionário de mapeamento.  
     b. Se uma correspondência for encontrada, substitua o nome pelo nome\_padronizado.  
     c. Se nenhuma correspondência for encontrada, mantenha o nome como está.  
   * **Atualizar o DataFrame:** Junte os nomes das instituições (agora padronizados) de volta em uma única string delimitada por ; e atualize a célula no DataFrame.

**Formato da Saída:**

1. **Arquivo de Saída:** Salve o DataFrame com os nomes das instituições padronizados em um **novo arquivo CSV** chamado dados\_brasnam\_instituicoes\_padronizadas.csv.  
2. **Estrutura:** O arquivo de saída deve manter a mesma estrutura do arquivo de entrada, mas com os valores da coluna instituicoes atualizados conforme as regras de mapeamento.

**Exemplo de conteúdo para o arquivo mapeamento\_instituicoes.csv (a ser criado pelo usuário):**

Snippet de código

1. nome\_original,nome\_padronizado  
2. "centro federal de educacao tecnologica celso suckow da fonseca","cefet-rj"  
3. "celso suckow da fonseca federal center for technological education","cefet-rj"  
4. "cefet/rj","cefet-rj"  
5. "universidade de brazilia","universidade de brasília"  
6. "university of brasilia","universidade de brasília"  
7. "unb","universidade de brasília"


