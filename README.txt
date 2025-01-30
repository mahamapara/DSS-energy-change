DATA

Part 1-Citation Impact Data:
- The academic research data is named 'metadata_team.pkl'. 
- It can be loaded by using pandas read_pickle function:
  pd.read_pickle('metadata_team.pkl')
- This data is used to calculate the citation impact metrics. 

- There are a total of 191 columns:
1. The 121 year columns range from 1900 to 2021. 
   The value in the column is the number of citations of the publication in that year.
2. There are 68 non-year columns containing the metadata on the publication + 
   2 columns on the nationalities of each author and unique nationalities of the team.
   The definition for the 68 metadata columns can be found here: https://images.webofknowledge.com/images/help/WOS/hs_wos_fieldtags.html

- The total number of rows in the data is 87792. This means the data contains 87792 academic sustainable research publications.
- The publications range from 1981 - 2021, are only academic publications and only publications available in the english language.

-This data was collected from the Web of Science and compiled by the Sunter Lab at Tufts University.

Part 2 - WDI and World Bank data: 

WDI data 
(downloaded from: 1. https://datahelpdesk.worldbank.org/knowledgebase/articles/378834-how-does-the-world-bank-classify-countries
2. https://databank.worldbank.org/source/world-development-indicators/preview/on ):

WDI_onlydata.csv
-- Has data for all SDG indicators for all countries from 1960 till 2021.

WDI_series.csv
-- Data on indicator code, indicator name.

Wdi_incomelevels.csv
-- Report of countries categorized by income levels based on a variety of factors determined by the World Bank.
-- Income level as defined by Gross National Income (GNI) per capita
-- World Development Indicators database: Low income is $1 045 or less, middle income is $1 046 to $12 745, high income is $12 745 or more.
-- There are 4 income levels: high-income, upper-middle income, lower-middle income, lower-income

Part 3 - data sets we generated using SDG7 Indicators VS Citations DataFrame-Bulk Knowledge.ipynb and SDG7 Indicators VS Citations DataFrame-Country Author.ipynb:

pc_change_citations_bulk_df.csv
-- Percent Change of all 27 SDG 7 indicators calculated on a yearly basis for all countries

log_diff_citations_bulk_df.csv
-- Log Difference Change of all 27 SDG 7 indicators calculated on a yearly basis for all countries

dist_calc_citations_bulk_df.csv
-- Distance from Target of 12 (indicators chosen because targets were available in literature) SDG 7 indicators calculated on a yearly basis for all countries

dist_calc_oecd_citations_bulk_df.csv
-- Distance from Target of 12 (indicators chosen because targets were available in literature) SDG 7 indicators calculated on a yearly basis for OECD countries

pc_change_citations_ca_df.csv
-- Percent Change of all 27 SDG 7 indicators calculated country-wise and on a yearly basis for all countries

log_diff_citations_ca_df.csv
-- Log Difference Change of all 27 SDG 7 indicators calculated country-wise and on a yearly basis for all countries

dist_calc_citations_ca_df.csv
-- Distance from Target of 12 (indicators chosen because targets were available in literature) SDG 7 indicators calculated country-wise and on a yearly basis for all countries

dist_calc_oecd_citations_ca_df.csv
-- Distance from Target of 12 (indicators chosen because targets were available in literature) SDG 7 indicators calculated country-wise and on a yearly basis for OECD countries

----------------------------------------------------------------------------------------------------------------------------------------------
NOTEBOOKS

SDG7 Indicators VS Citations DataFrame-Bulk Knowledge.ipynb
- Extracts all articles related to SDG 7 research [looks for articles that mention 'energy' or 'electricity' in their abstract (AB), title (TI), and keywords (DE)]
- Range of years it takes into account: 1991-2020
- Generates the log(2 Year Citations) and AR Index, aggregating these scales on a yearly [Publication Year (PY)] basis.
- Linearly interpolates missing WDI data for every SDG 7 indicator
- Creates various CSV files depending on how relative change on SDG7 is calculated (pc_change_citations_bulk_df, log_diff_citations_bulk_df, dist_calc_citations_bulk_df, dist_calc_oecd_citations_bulk_df)

SDG7 Indicators VS Citations DataFrame-Country Author.ipynb
- Extracts all articles related to SDG 7 research [looks for articles that mention 'energy' or 'electricity' in their abstract (AB), title (TI), and keywords (DE)]
- Range of years it takes into account: 1991-2020
- Generates the log(2 Year Citations) and AR Index, aggregating these scales on a country-wise [Country Name/Unique Nationalities] and yearly [Publication Year (PY)] basis.
- Linearly interpolates missing WDI data for every SDG 7 indicator
- Creates various CSV files depending on how relative change on SDG7 is calculated (pc_change_citations_ca_df, log_diff_citations_ca_df, dist_calc_citations_ca_df, dist_calc_oecd_citations_ca_df)

SDG7 Indicator VS Citation -Regression_bulk_knowledge.ipynb
- Plots linear and quantile regressions for all bulk-knowledge related CSV files mentioned in part 3
- Sets hue color based on income level category of each country (Sourced from Wdi_incomelevels)
- Uses AR Index and log(2 Year Citations) as the predictor (x) variable and Indicator values for each country as the response (y) value
- Checks for normality on all linear regression plots
- Creates Confidence Intervals for quantile regression plots
- Tabulates and documents all regression results

SDG7 Indicator VS Citation -Regression_bulk_knowledge.ipynb
- Plots linear and quantile regressions for all country-specific CSV files mentioned in part 3
- Sets hue color based on income level category of each country (Sourced from Wdi_incomelevels)
- Uses AR Index and log(2 Year Citations) as the predictor (x) variable and Indicator values for each country as the response (y) value
- Checks for normality on all linear regression plots
- Creates Confidence Intervals for quantile regression plots
- Tabulates and documents all regression results