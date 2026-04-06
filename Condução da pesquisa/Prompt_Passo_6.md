### **Prompt para Geração de Código \- Passo 6**

**Persona:** Você é um assistente de pesquisa focado na replicação de metodologias científicas, responsável por criar um script em Python para a etapa de padronização de nomes de autores.

**Tarefa:** Crie um script em Python para padronizar os nomes dos autores de um conjunto de dados, implementando estritamente as regras de transformação descritas no artigo "BraSNAM em perspectiva...".

**Fonte da Metodologia:** O script deve ser uma implementação direta dos procedimentos descritos na seção 2.3 do artigo. A fonte especifica duas operações: "Por exemplo, Jr. foi padronizado para Júnior" e "Além disso, consideramos apenas o primeiro e o último nome".

**Requisitos Funcionais:**

1. **Linguagem:** O script deve ser escrito em Python.  
2. **Arquivo de Entrada:**  
   * O script deve ler o arquivo dados\_brasnam\_preprocessados.csv (gerado no Passo 4), que já contém os nomes em caixa-baixa e com limpeza básica.  
3. **Coluna-Alvo:**  
   * O processo de padronização deve ser aplicado à coluna autores.  
4. **Lógica de Padronização:**  
   * O script deve processar a coluna autores, que contém um ou mais nomes separados por ponto e vírgula (;).  
   * Para cada célula da coluna autores:  
     a. Separe a string em uma lista de nomes individuais.  
     b. Para cada nome individual na lista, aplique as seguintes regras na ordem:  
     i. Substituição de Termos: Encontre e substitua a sub-string " jr." (em caixa-baixa) por " júnior".  
     ii. Redução do Nome: Divida o nome em componentes (palavras) e construa uma nova string contendo apenas o primeiro e o último componente, separados por um espaço. Por exemplo, "fábio m. f. lobato" deve se tornar "fábio lobato".  
     c. Junte a lista de nomes processados de volta em uma única string, usando o ponto e vírgula (;) como separador.  
   * Substitua o valor original da célula pelo novo valor padronizado.

**Formato da Saída:**

1. **Arquivo de Saída:** Salve o DataFrame com os nomes dos autores padronizados em um **novo arquivo CSV**. Um nome apropriado seria dados\_brasnam\_autores\_padronizados.csv.  
2. **Estrutura:** O arquivo de saída deve manter a mesma estrutura do arquivo de entrada, mas com os valores da coluna autores atualizados conforme a metodologia.

