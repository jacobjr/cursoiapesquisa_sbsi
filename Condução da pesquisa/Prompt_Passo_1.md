
### **Prompt para Geração de Código \- Passo 1**

**Persona:** Você é um Engenheiro de Dados Sênior, especialista em automação de coleta de dados e *web scraping* com Python.

**Tarefa:** Crie um script completo em Python para extrair metadados de todos os artigos publicados nos anais do *Brazilian Workshop on Social Network Analysis and Mining* (BraSNAM), conforme a metodologia do artigo de referência. Os dados devem ser coletados da biblioteca digital SBC OpenLib (SOL).

**Requisitos Funcionais:**

1. **Linguagem e Bibliotecas:**  
   * Utilize Python 3\.  
   * As bibliotecas essenciais são requests para realizar as requisições HTTP e BeautifulSoup4 para fazer o *parsing* do conteúdo HTML.  
2. **Ponto de Partida (URL Base):**  
   * O *script* deve iniciar a varredura a partir da página principal de arquivos do BraSNAM na SOL: https://sol.sbc.org.br/index.php/brasnam/issue/archive.  
3. **Lógica de Navegação (*Crawling*):**  
   * **Nível 1 (Página de Arquivos):** Na URL base, o *script* deve identificar o link de cada edição anual do evento e iterar sobre eles.  
   * **Nível 2 (Página da Edição):** Para cada edição, o *script* deve acessar a página correspondente e extrair os links individuais de todos os artigos listados (completos e curtos).  
   * **Nível 3 (Página do Artigo):** Para cada link de artigo, o *script* deve acessar a página final para realizar a extração dos metadados.  
4. **Extração de Dados:**  
   * Em cada página de artigo, extraia precisamente os seguintes campos, conforme descrito na metodologia:  
     * **Título:** O título completo do artigo.  
     * **Autores:** A lista com o nome de todos os autores.  
     * **Instituições:** A lista de todas as instituições de afiliação dos autores.  
     * **Palavras-chave:** A lista de palavras-chave associadas ao artigo.  
     * **Ano da Publicação:** O ano do evento, que pode ser extraído do título da página da edição (Nível 2).

**Formato da Saída:**

1. **Estrutura:** Salve os dados coletados em um único arquivo CSV chamado dados\_brasnam\_sol.csv.  
2. **Cabeçalho:** O arquivo CSV deve conter as seguintes colunas: ano, titulo, autores, instituicoes, palavras\_chave.  
3. **Formatação dos Dados:**  
   * Para os campos que contêm múltiplos valores (autores, instituições, palavras-chave), concatene os itens em uma única *string*, utilizando ponto e vírgula (;) como separador.  
   * Remova quaisquer espaços em branco excessivos no início ou no fim dos textos extraídos.

**Exemplo de uma linha no CSV de saída:**

Snippet de código

```csv
"2012","Minerando e Caracterizando Dados de Currículos Lattes","Autor A; Autor B; Autor C","Universidade X; Universidade Y","Mineração de Dados; Plataforma Lattes; Redes Sociais Acadêmicas"

