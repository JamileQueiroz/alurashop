# alurashop
Alura Challenge BI: Reporting solutions in marketing on a PBI dashboard

# Case study
An ecommercy company (Alura Shop) invested in digital advertising and now they need to know the effect. Our aim is to support this 
enterprise creating a strategic marketing dashboard. Metrics in marketing was monitored during July 2021 using Power BI Desktop. 

# Database
Two datasets were provided in Json format: 

Devices (in Portuguese: Tabela_dispositivos.json)
Age and Gender (in Portuguese: Tabela_idade_e_genero.json)

# Data Handling

We excluded redudance lines found in Devices column on Power Query. 

On model section on Power BI, the two tables were related to a calendar table.

Creating a calandar table, using the below formule:

Tabela Calendário = 
ADDCOLUMNS(
    CALENDARAUTO(), 
    "Dia num",DAY([Date]), 
    "Dia nome",FORMAT([Date], "dddd"), 
    "Dia semana",WEEKDAY([Date]), 
    "Semana num",WEEKNUM([Date]), 
    "Mês num", MONTH([Date]), 
    "Mês nome",FORMAT([Date],"mmm"), 
    "Trimestre",QUARTER([Date]), 
    "Ano",Year([Date])
    )

# Data Analyses

Total of Purchases, Purchases Conversion Value and Total of Investment in Marketing campaign were calculated using SUM() formule. 

We provided a card showing date and hour  when the dashboard is being updated, using NOW() formule on calendar table.

Marketing Metrics and some POWER BI formulates.

Cost per click (CPC):

Custo por clique = IF([Quantia gasta (BRL)] = IF([Cliques no link] = 0, 0,[Cliques no link]),0,[Quantia gasta (BRL)]) / IF([Cliques no link] > 0, [Cliques no link],1)

Return on ad spend (ROAS):

ROAS = SUM('Tabela_idade_e_genero'[Valor de conversão de compras])/SUM('Tabela_idade_e_genero'[Quantia gasta (BRL)])

Conversion rate:

Taxa de conversão = SUM(Tabela_idade_e_genero[Compras])/SUM(Tabela_idade_e_genero[Visualizações por página])

Average ticket:

Ticket Médio = 
DIVIDE(
    SUM(Tabela_dispositivos[Quantia gasta (BRL)]),
    SUM(Tabela_dispositivos[Compras])
)

# Dashboard

https://app.powerbi.com/view?r=eyJrIjoiNjUwNzI4M2EtMmQyMS00ZjJlLTgyMDEtN2Y2OTk5MDViMTBhIiwidCI6ImY1YTgxMzY2LWVjOWQtNDdhZC05YThmLWI0MWFkZjRlOTRmOCIsImMiOjl9&pageName=ReportSection














