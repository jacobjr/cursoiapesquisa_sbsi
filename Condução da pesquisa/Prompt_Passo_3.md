### **Prompt para Geração de Código \- Passo 3**

**Persona:** Você é um Cientista de Dados com experiência em enriquecimento de dados via APIs externas e na implementação de metodologias de pesquisa replicáveis.

**Tarefa:** Crie um script em Python que infere o gênero dos autores de uma lista de publicações, utilizando a API "Nomes" do Instituto Brasileiro de Geografia e Estatística (IBGE). O script deve replicar a abordagem descrita no artigo, incluindo o tratamento de nomes não encontrados na base de dados da API.

**Contexto:** O objetivo desta etapa é coletar dados demográficos da comunidade de pesquisadores do BraSNAM para análises posteriores sobre diversidade de gênero. A metodologia original destaca que nomes estrangeiros ou com iniciais não foram reconhecidos pela API e foram tratados como uma categoria separada. O script deve seguir rigorosamente essa lógica.

**Requisitos Funcionais:**

1. **Linguagem e Bibliotecas:**  
   * Utilize Python 3\.  
   * Bibliotecas necessárias: pandas para manipulação de dados e requests para as chamadas à API.  
2. **Arquivo de Entrada:**  
   * O script deve ler o arquivo dados\_brasnam\_com\_citacoes.csv (gerado no Passo 2).  
3. **Lógica de Processamento:**  
   * Leitura e Extração de Nomes Únicos:  
     a. Carregue o arquivo CSV para um DataFrame do pandas.  
     b. Percorra a coluna autores, separe os nomes (que estão delimitados por ;) e crie uma lista única com todos os nomes de autores para evitar chamadas duplicadas à API.  
   * Consulta à API para cada Autor Único:  
     a. Crie um dicionário para armazenar os resultados ({nome\_completo: genero\_inferido}).  
     b. Itere sobre a lista de nomes únicos de autores. Para cada nome completo:  
     c. Extraia o primeiro nome (a primeira palavra da string do nome).  
     d. Construa a URL da API para o primeiro nome extraído: https://servicodados.ibge.gov.br/api/v2/censos/nomes/{primeiro\_nome}.  
     e. Faça uma requisição GET à API em um bloco try-except para tratar possíveis erros de conexão.  
     f. Lógica de Inferência de Gênero:  
     \* Se a resposta da API for bem-sucedida (código 200\) e o JSON retornado não for uma lista vazia, extraia o valor do campo sexo do primeiro elemento da lista. Mapeie 'M' para "Masculino" e 'F' para "Feminino".  
     \* Se a API retornar uma lista vazia (nome não encontrado), a resposta tiver um erro (ex: 404), ou o campo sexo não existir, o gênero deve ser classificado como "Indefinido", conforme a metodologia para nomes estrangeiros ou não registrados3.  
     g. Armazene o par (nome\_completo, genero\_inferido) no dicionário de resultados.  
   * **Controle de Requisições:** Para evitar sobrecarregar a API, inclua um pequeno intervalo (ex: time.sleep(0.1)) entre as chamadas.

**Formato da Saída:**

1. **Arquivo de Saída:** Ao final do processo, crie um **novo arquivo CSV** chamado autores\_com\_genero.csv.  
2. **Estrutura:** O arquivo deve conter duas colunas: autor e genero\_inferido. Cada linha representará um autor único e seu respectivo gênero classificado.

**Exemplo de linhas no CSV de saída:**

**Snippet de código (CSV):**

```csv
"autor","genero_inferido"
"Fábio M. F. Lobato","Masculino"
"Gleyce C. de Sousa","Feminino"
"Min-Yuh Day","Indefinido"
"C. Mateos","Indefinido"


