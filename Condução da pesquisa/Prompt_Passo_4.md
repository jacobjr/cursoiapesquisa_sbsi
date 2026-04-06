### **Prompt para Geração de Código \- Passo 4**

**Persona:** Você é um Engenheiro de Dados focado em garantir a qualidade e a consistência dos dados, especializado na criação de *pipelines* de limpeza e pré-processamento em Python.

**Tarefa:** Crie um script em Python para realizar o pré-processamento e a padronização básica de campos textuais em um arquivo CSV, seguindo rigorosamente a metodologia descrita no artigo de referência.

**Contexto:** Esta etapa é fundamental para normalizar os dados antes das análises e das etapas de padronização mais complexas (como a consolidação de sinônimos). O objetivo é garantir que variações simples, como o uso de maiúsculas/minúsculas ou espaçamento extra, não afetem a qualidade dos resultados. O artigo especifica as operações como: "remoção de espaços em branco duplicados ou à direita/esquerda da string, remoção de caracteres especiais e padronização para caixa-baixa".

**Requisitos Funcionais:**

1. **Linguagem e Bibliotecas:**  
   * Utilize Python 3\.  
   * A biblioteca principal é pandas para a manipulação dos dados.  
2. **Arquivo de Entrada:**  
   * O script deve ler o arquivo dados\_brasnam\_com\_citacoes.csv (gerado nos passos anteriores).  
3. **Colunas-Alvo:**  
   * O processo de limpeza deve ser aplicado às seguintes colunas: autores, instituicoes e palavras\_chave.  
4. **Lógica de Pré-processamento:**  
   * Crie uma função de limpeza de texto que receba uma *string* como entrada e execute, na ordem, as seguintes operações:  
     1. **Converter para Caixa-Baixa:** Transforme toda a *string* para letras minúsculas (lowercase).  
     2. **Remover Espaços das Extremidades:** Elimine quaisquer espaços em branco no início ou no final da *string* (strip).  
     3. **Remover Espaços Duplicados:** Substitua uma ou mais ocorrências de espaços em branco no meio da *string* por um único espaço.  
     4. **Remover Caracteres Especiais:** Remova todos os caracteres que não sejam letras, números, espaços ou o ponto e vírgula (;), usado como delimitador. Mantenha a acentuação por enquanto, pois ela será tratada em etapas posteriores se necessário.  
   * Aplique esta função a cada valor contido nas colunas-alvo especificadas.

**Formato da Saída:**

1. **Arquivo de Saída:** Salve o DataFrame modificado em um **novo arquivo CSV** chamado dados\_brasnam\_preprocessados.csv.  
2. **Estrutura:** O arquivo de saída deve manter a mesma estrutura (mesmas colunas e ordem) do arquivo de entrada, mas com os dados das colunas-alvo devidamente limpos e padronizados conforme a função descrita.

**Exemplo de transformação:**

* **Entrada na coluna instituicoes:** " Universidade Federal do Rio de Janeiro ; CEFET/RJ "  
* **Saída após a limpeza:** "universidade federal do rio de janeiro;cefet/rj"