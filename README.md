Projeto Power BI: Criação do Diagrama Estrela
Este projeto consiste na construção de um modelo de dados em formato estrela no Power BI para análise financeira e de vendas. O objetivo é organizar as informações em tabelas de dimensão e de fatos, otimizando a análise e facilitando a criação de visualizações dinâmicas.

Etapas do Projeto
1. Importação e Preparação dos Dados
Fonte dos Dados: Os dados originais foram extraídos da amostra Financial Sample fornecida pelo Power BI.
Ferramentas Utilizadas:
Power Query para transformação e limpeza dos dados.
Editor DAX para criação de colunas calculadas, tabelas e medidas.
2. Modelagem do Diagrama Estrela
O modelo foi projetado para organizar os dados em tabelas de fatos e dimensões. Seguem os detalhes:

Tabelas Criadas
Tabela Principal (Financials_origem):

Backup oculto contendo todos os dados originais, usado como base para as tabelas derivadas.
Tabela de Dimensão: D_Produtos
Contém informações agregadas sobre produtos, como médias e valores estatísticos.
Colunas principais:

ID_Produto (Chave Primária)
Produto
Média de Unidades Vendidas
Média do Valor de Vendas
Mediana do Valor de Vendas
Valor Máximo de Venda
Valor Mínimo de Venda
Tabela de Dimensão: D_Produtos_Detalhes
Detalha atributos adicionais dos produtos.
Colunas principais:

ID_Produto
Discount Band
Sale Price
Units Sold
Manufacturing Price
Tabela de Dimensão: D_Calendário
Criada com DAX para fornecer uma tabela de datas para análises temporais.
Função Utilizada:

DAX
Copiar código
Calendario = CALENDAR(DATE(2019,1,1), DATE(2024,12,31))
Tabela Fato: F_Vendas
Centraliza os dados principais de vendas.
Colunas principais:

SK_ID (Chave Surrogada)
ID_Produto
Produto
Units Sold
Sales Price
Discount Band
Segment
Country
Salers
Profit
Date
3. Criação e Aplicação de Medidas DAX
Medidas personalizadas foram criadas para enriquecer as análises, como:

Média de Unidades Vendidas

DAX
Copiar código
Media_Units_Sold = AVERAGE(F_Vendas[Units Sold])
Média do Valor de Vendas

DAX
Copiar código
Media_Sales_Value = AVERAGE(F_Vendas[Sales])
Mediana do Valor de Vendas

DAX
Copiar código
Mediana_Sales_Value = MEDIAN(F_Vendas[Sales])
Lucro Total

DAX
Copiar código
Total_Profit = SUM(F_Vendas[Profit])
Cálculo Dinâmico de Variação Percentual

DAX
Copiar código
Percentual_Variacao = DIVIDE([Lucro Atual] - [Lucro Anterior], [Lucro Anterior], 0)
Funcionalidades do Projeto
Visualizações: Dashboards interativos com KPIs, tabelas dinâmicas e gráficos baseados no modelo estrela.
Relacionamentos:
As tabelas de dimensão estão relacionadas à tabela de fatos via chaves primárias e estrangeiras.
Filtros Dinâmicos: Uso de tabelas de dimensão para filtrar dados por produto, segmento, país, entre outros.
Conclusão
Este projeto utiliza as funcionalidades do Power BI para demonstrar boas práticas em modelagem de dados, agregação e análises avançadas com DAX. O modelo estrela facilita consultas e melhora a performance das análises em grandes volumes de dados.
