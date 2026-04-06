### **Prompt para Geração de Código \- Passo 2**

**Persona:** Você é um Assistente de Pesquisa Técnico, encarregado de desenvolver ferramentas em Python para otimizar processos de coleta de dados que exigem intervenção humana.

**Tarefa:** Crie um script em Python para auxiliar na coleta manual do número de citações de artigos científicos na plataforma Google Acadêmico. O script deve ler uma lista de artigos de um arquivo CSV, gerar as URLs de busca para o pesquisador, solicitar a entrada manual do número de citações e salvar o resultado de forma organizada.

**Contexto:** Conforme descrito na metodologia do artigo de referência, a coleta automatizada de citações via bibliotecas como a scholarly foi inviabilizada por bloqueios do servidor. Portanto, este script servirá como um assistente para o processo manual, garantindo que os dados sejam coletados e registrados de maneira eficiente e sem erros.

**Requisitos Funcionais:**

1. **Linguagem e Bibliotecas:**  
   * Utilize Python 3\.  
   * A biblioteca essencial é pandas para manipulação de dados e urllib.parse para formatar os títulos para a URL.  
2. **Arquivo de Entrada:**  
   * O script deve ler o arquivo dados\_brasnam\_sol.csv (gerado no Passo 1).  
3. **Lógica do Script:**  
   * **Leitura:** Carregue o arquivo CSV para um DataFrame do pandas.  
   * **Preparação:** Adicione uma nova coluna ao DataFrame chamada citacoes, inicializada com um valor nulo (ex: None ou np.nan).  
   * Iteração: Percorra cada linha do DataFrame. Para cada artigo:  
     a. Exiba o título do artigo no terminal para dar contexto ao usuário.  
     b. Pegue o valor da coluna titulo.  
     c. Formate (URL encode) o título para que ele possa ser usado de forma segura em uma URL.  
     d. Construa uma URL de busca direta no Google Acadêmico. Ex: https://scholar.google.com/scholar?q="TÍTULO+CODIFICADO+AQUI"  
     e. Exiba a URL gerada no terminal.  
     f. Solicite ao usuário que insira o número de citações encontrado: Por favor, abra a URL acima, encontre o artigo e digite o número de citações (ou 0 se não encontrar):  
   * **Validação da Entrada:** O script deve verificar se o valor inserido pelo usuário é um número inteiro. Caso contrário, deve solicitar a entrada novamente até que um número válido seja fornecido.  
   * **Armazenamento:** Armazene o número de citações inserido pelo usuário na coluna citacoes da linha correspondente ao artigo atual.

**Formato da Saída:**

1. **Arquivo de Saída:** Após percorrer todos os artigos, o script deve salvar o DataFrame atualizado em um **novo arquivo CSV** chamado dados\_brasnam\_com\_citacoes.csv.  
2. **Estrutura:** O novo arquivo deve conter todas as colunas do arquivo original, mais a nova coluna citacoes.  
3. **Progresso:** É recomendável que o script salve o progresso a cada X artigos (ex: a cada 10\) para evitar perda de trabalho em caso de interrupção.

