
# Agrupamento de Clientes Bancários

## Objetivo do Projeto

O objetivo deste projeto foi realizar a segmentação de clientes bancários utilizando algoritmos de clustering. Com base nos resultados, buscamos oferecer um novo produto de investimento para cada segmento de cliente identificado.

## Abordagem e Resultados

### Notebook 1 – Agrupamento com todas as variáveis

- Utilização de todas as 35 features disponíveis.
- Testes com diferentes valores de k, variando de 20 a 1500 (step = 100) e de 2 a 20 (step = 2).
- Comparação entre os algoritmos KMeans, GMM, Hierárquico e DBSCAN.
- O melhor resultado com KMeans foi um silhouette score de 0.05 (k=8).
- Outros algoritmos apresentaram desempenho inferior ou não conseguiram formar agrupamentos úteis (como o DBSCAN).

**Conclusão**: A presença de muitos dados gerou ruído, dificultando a formação de grupos bem definidos.

### Notebook 2 – Redução de variáveis com PCA

- Aplicação de PCA para reduzir a dimensionalidade dos dados.
- Testes com 2 e 5 componentes principais.
- Com apenas 2 componentes e o algoritmo KMeans, o silhouette score atingiu 0.52, o melhor resultado do projeto.
- Hierárquico e GMM também tiveram desempenho próximo.

**Conclusão**: A redução de dimensionalidade via PCA permitiu a formação de agrupamentos mais claros e interpretáveis, mesmo com menos variáveis.

### Notebook 3 – Redução do número de registros

- Agrupamento dos dados previamente por Customer_ID, utilizando a média de variáveis numéricas.
- Aplicação de PCA com 2 e 5 componentes.
- O melhor resultado foi um silhouette score de 0.38 (KMeans com 2 componentes).
- Embora o número de registros tenha sido reduzido, os agrupamentos não superaram os obtidos no notebook anterior com dados completos.

**Conclusão**: A perda de granularidade dos dados pode prejudicar a performance do clustering, mesmo com redução dimensional.

### Notebook 4 – Análise dos clusters

- Análise descritiva dos clusters gerados com base em médias de variáveis.
- Os grupos se mostraram muito semelhantes em idade, lucro e valor investido.
- Percebi que, sem um escopo claro, os padrões identificados não traziam insights relevantes ou acionáveis.

**Conclusão**: A ausência de uma pergunta de negócio bem definida compromete a utilidade do modelo.

## Lições Aprendidas

- **Importância de Definir o Escopo**: A ausência de uma definição clara do escopo de negócio antes do agrupamento dificultou a interpretação e a utilidade dos clusters.
- **Avaliação de Resultados**: A avaliação dos resultados de clustering pode ser afetada pela escolha de variáveis e pela quantidade de dados. A combinação de reduções de dimensionalidade e seleção cuidadosa de features são cruciais para a obtenção de agrupamentos significativos.
- **Validade dos Agrupamentos**: A redução de dimensionalidade e a simplificação dos dados podem tornar os agrupamentos mais claros, mas é importante garantir que as variáveis que sustentam os agrupamentos estejam bem alinhadas com os objetivos de negócio.

## Reflexões Finais

🔹 1. Agrupamento com poucas variáveis após PCA
Embora o uso de apenas duas componentes principais tenha gerado o melhor resultado em termos de Silhouette Score (0.52), reconheço que essa abordagem pode ser arriscada do ponto de vista estatístico. A redução extrema da dimensionalidade pode comprometer a fidelidade das informações originais, e, por consequência, a utilidade dos clusters. Em aplicações reais, esse trade-off entre interpretabilidade e preservação da variância dos dados deve ser analisado com mais profundidade.

🔹 2. Comparação de algoritmos sem ajuste fino de hiperparâmetros
A comparação entre KMeans, GMM, Hierárquico e DBSCAN foi feita com configurações padrão, o que não necessariamente reflete o potencial máximo de cada algoritmo. No futuro, pretendo realizar ajustes mais cuidadosos (por exemplo, tuning de eps e min_samples para DBSCAN) e adotar validações mais robustas.

🔹 3. Ausência de escopo claro no início
Inicialmente, não defini uma pergunta de negócio específica nem um objetivo claro para o agrupamento. Isso prejudicou a análise final dos clusters e dificultou a geração de insights acionáveis. Essa experiência reforçou uma das lições mais valiosas do projeto: definir o escopo e entender o contexto do problema são etapas fundamentais antes da modelagem.

🔹 4. Uso isolado do Silhouette Score como métrica de avaliação
O Silhouette Score foi utilizado como principal critério de qualidade, mas sei que ele não é universalmente aplicável. Em próximos projetos, pretendo explorar outras métricas, como Davies-Bouldin Index, Calinski-Harabasz, e até abordagens qualitativas baseadas em validação externa ou feedback de stakeholders.

🔹 5. Potencial para melhorias em Feature Engineering
Apesar das transformações aplicadas (imputações, criação de variáveis temporais, encoding e scaling), vejo oportunidades para expandir o feature engineering. Novas variáveis derivadas — como proporções, variações mensais ou segmentações personalizadas — podem ajudar a revelar padrões mais interessantes nos dados.
