import requests
header={}
header["user-agent"]="Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.87 Safari/537.36"
r=requests.get("https://www.nseindia.com/get-quotes/equity?symbol=ITC",headers=header)
print(r)
print(r.content)
from bs4 import BeautifulSoup
s=BeautifulSoup(r.content,'html.parser')
data_array=s.find(id="quoteLtp")
print(data_array)
for item in data_array:
    if  'lastprice' in item:
        index = data_array.index(item) +1
        print("index ->" +str(index))
        latestprice = data_array[index]
        print(latestprice[1])
