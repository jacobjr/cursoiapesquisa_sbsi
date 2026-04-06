### **Guia de Instruções para o Passo 9**

**Persona:** Você é um Analista de Redes ou Pesquisador encarregado de conduzir a etapa final de uma análise de redes, replicando a visualização e a análise de componentes descritas em um artigo científico.

**Tarefa:** Utilizando os softwares **Cytoscape** ou **Gephi**, visualize os dados das redes de coautoria e de colaboração interinstitucional e analise seus componentes, seguindo estritamente a metodologia e os resultados apresentados no artigo "BraSNAM em perspectiva...".

**Fonte da Metodologia:** O processo deve seguir o que é afirmado na seção 2.3 do artigo: "Utilizamos os softwares Cytoscape e Gephi para visualização dos dados e análise dos componentes das redes geradas". Os resultados a serem replicados estão descritos nas seções 3.2 e 3.3.

**Requisitos:**

1. **Software:** Instalação do Cytoscape ou Gephi.  
2. **Arquivos de Entrada:**  
   * rede\_colaboracao\_instituicoes.csv (gerado no Passo 8).  
   * rede\_coautoria.csv (gerado no Passo 8).

---

### **Instruções para a Rede de Colaboração Interinstitucional**

1. **Importar os Dados:**  
   * Abra o software de sua escolha (Cytoscape ou Gephi).  
   * Importe a lista de arestas a partir do arquivo rede\_colaboracao\_instituicoes.csv. Certifique-se de configurar as colunas como Origem e Destino (Source/Target).  
2. **Visualizar a Rede:**  
   * Após a importação, gere um layout visual da rede. Algoritmos como Fruchterman-Reingold ou Yifan Hu são recomendados para explorar a estrutura.  
   * O artigo menciona o uso de siglas para facilitar a visualização, o que pode ser feito editando os rótulos dos nós (nodes).  
3. **Analisar os Componentes:**  
   * Utilize as ferramentas de análise de rede do software para calcular as estatísticas de "Componentes Conectados" (*Connected Components*).  
   * **Verificação:** Conforme o resultado apresentado na seção 3.3 do artigo, o software deve identificar **14 componentes conectados** na rede de instituições.

### **Instruções para a Rede de Coautoria**

1. **Importar os Dados:**  
   * No mesmo software, importe a lista de arestas a partir do arquivo rede\_coautoria.csv.  
2. **Visualizar a Rede:**  
   * Gere um layout visual para a rede de coautoria.  
3. **Analisar os Componentes:**  
   * Execute novamente a análise de "Componentes Conectados".  
   * **Verificação:** De acordo com os resultados da seção 3.2 do artigo, a análise deve reportar que a comunidade BraSNAM possui **69 componentes conectados**.

**Resultado Esperado:**

Ao final deste passo, você deverá ter:

* Duas visualizações de rede geradas, uma para colaborações institucionais e outra para coautorias.  
* A confirmação numérica de que as redes possuem 14 e 69 componentes conectados, respectivamente, replicando os achados do artigo original.