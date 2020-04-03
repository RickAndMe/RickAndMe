from urllib.request import urlopen
import json
import csv
from openpyxl import Workbook
import pandas as pd
def get_jsonparsed_data(url):
    """
    Receive the content of ``url``, parse it as JSON and return the object.
    Parameters -> url : str
    Returns ->    dictionary
    """
    response = urlopen(url)
    data = response.read().decode("utf-8")
    return json.loads(data)
Company='AAPL'
ruta=Company+'_.xlsx'

#1- CompanyData
url = ("https://financialmodelingprep.com/api/v3/company/profile/"+Company)
CompanyData=get_jsonparsed_data(url)
df1=pd.DataFrame.from_dict(CompanyData['profile'],orient='index')
print('1 done')

#2- income statement
url='https://financialmodelingprep.com/api/v3/financials/income-statement/'+Company
IncomeStatement=get_jsonparsed_data(url)
df2=pd.DataFrame.from_dict(IncomeStatement['financials'])
print('2 done')

#3- Balance sheet
url='https://financialmodelingprep.com/api/v3/financials/balance-sheet-statement/'+Company
BalanceSheet=get_jsonparsed_data(url)
df3=pd.DataFrame.from_dict(BalanceSheet['financials'])
print('3 done')

#4- Cash flow
url='https://financialmodelingprep.com/api/v3/financials/cash-flow-statement/'+Company
CashFlow=get_jsonparsed_data(url)
df4=pd.DataFrame.from_dict(CashFlow['financials'])
print('4 done')

#5- Financial Ratios (MAL)
url='https://financialmodelingprep.com/api/v3/financial-ratios/'+Company
FinancialRatios=get_jsonparsed_data(url)
df5=pd.DataFrame.from_dict(FinancialRatios['ratios'])
print('5 done')

#6- Enterprise Values
url='https://financialmodelingprep.com/api/v3/enterprise-value/'+Company
EnterpriseValue=get_jsonparsed_data(url)
df6=pd.DataFrame.from_dict(EnterpriseValue['enterpriseValues'])
print('6 done')

#7- Key Metrics
url='https://financialmodelingprep.com/api/v3/company-key-metrics/'+Company
KeyMetrics=get_jsonparsed_data(url)
df7=pd.DataFrame.from_dict(KeyMetrics['metrics'])
print('7 done')

#8- Company Financial Growth
url='https://financialmodelingprep.com/api/v3/financial-statement-growth/'+Company
FinancialGrowth=get_jsonparsed_data(url)
df8=pd.DataFrame.from_dict(FinancialGrowth['growth'])
print('8 done')

#9- Company Rating (MAL)
url='https://financialmodelingprep.com/api/v3/company/rating/'+Company
Rating=get_jsonparsed_data(url)
df9=pd.DataFrame.from_dict(Rating['ratingDetails'])
print('9 done')

#10- Company Discounted Cash Flow Value
url='https://financialmodelingprep.com/api/v3/company/discounted-cash-flow/'+Company
DiscountedCashFlow=get_jsonparsed_data(url)
df10=pd.DataFrame.from_dict(DiscountedCashFlow,orient='index')
print('10 done')

# Pasarlo a EXCEL
with pd.ExcelWriter(ruta) as writer:
    df1.to_excel(writer,sheet_name='Company Data',index=False)
    df2.to_excel(writer,sheet_name='Income Statement',index=False)
    df3.to_excel(writer,sheet_name='Balance Sheet',index=False)
    df4.to_excel(writer,sheet_name='Cash-flow')
    df5.to_excel(writer,sheet_name='Financial Ratios',index=False)
    df6.to_excel(writer,sheet_name='Enterprise Values',index=False)
    df7.to_excel(writer,sheet_name='Key Metrics',index=False)
    df8.to_excel(writer,sheet_name='Financial Growth',index=False)
    df9.T.to_excel(writer,sheet_name='Rating',index=False)
    df10.to_excel(writer,sheet_name='Discounted CashFlowValue',index=False)

