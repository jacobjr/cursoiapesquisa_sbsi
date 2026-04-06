### **Prompt para Geração de Código \- Passo 5**

**Persona:** Você é um assistente de pesquisa encarregado de desenvolver um script em Python para replicar uma metodologia de padronização de dados que combina análise computacional e validação manual.

**Tarefa:** Crie um script em Python para padronizar as palavras-chave de um conjunto de dados, seguindo estritamente o processo semi-automático descrito no artigo "BraSNAM em perspectiva...". O script deve usar a similaridade de strings Levenshtein para sugerir padronizações, que serão então confirmadas ou rejeitadas pelo usuário.

**Fonte da Metodologia:** O script deve implementar o método descrito na seção 2.3 do artigo. A fonte afirma: "Para as palavras-chave, utilizamos a medida de similaridade de strings Levenshtein, na qual identificamos termos com similaridade maior que 85% e os padronizamos de forma semi-automática". O processo não é totalmente automatizado para evitar a fusão incorreta de termos distintos, como "análise de popularidade" e "análise de polaridade".

**Requisitos Funcionais:**

1. **Linguagem:** O script deve ser escrito em Python. Pode-se utilizar uma biblioteca como python-Levenshtein ou fuzzywuzzy para o cálculo da similaridade.  
2. **Arquivo de Entrada:**  
   * O script deve ler o arquivo dados\_brasnam\_preprocessados.csv (gerado no Passo 4).  
3. **Lógica de Sugestão e Interação:**  
   * **Extração:** Crie uma lista com todas as palavras-chave únicas presentes na coluna palavras\_chave.  
   * **Comparação:** Compare cada par de palavras-chave únicas da lista.  
   * **Cálculo de Similaridade:** Para cada par, calcule a razão de similaridade Levenshtein.  
   * Interação com o Usuário: Se a similaridade entre duas palavras-chave for maior que 85%, o script deve:  
     a. Pausar a execução.  
     b. Apresentar os dois termos ao usuário. Ex: Similaridade \> 85% encontrada: \[1\] 'rede de coautorias' e \[2\] 'redes de coautoria'.  
     c. Solicitar uma ação do usuário. Ex: Para qual termo devem ser padronizados? Digite 1, 2, ou um novo termo. Pressione Enter para ignorar..  
   * **Mapeamento:** O script deve construir um dicionário de mapeamento (ex: {'rede de coautorias': 'redes de coautoria'}) com base nas decisões do usuário.  
4. **Aplicação da Padronização:**  
   * Após o usuário revisar todos os pares sugeridos, o script deve aplicar as regras de mapeamento definidas na coluna palavras\_chave do DataFrame original.

**Formato da Saída:**

1. **Arquivo de Dados:** Salve o DataFrame com as palavras-chave padronizadas em um **novo arquivo CSV** chamado dados\_brasnam\_final.csv.  
2. **Arquivo de Mapeamento (Opcional, mas recomendado para replicabilidade):** Salve o dicionário de mapeamento gerado a partir das decisões do usuário em um arquivo (ex: mapeamento\_palavras\_chave.json) para que o processo possa ser auditado ou reutilizado.

