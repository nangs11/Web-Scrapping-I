```markdown
# Assignment - Scraping with BeautifulSoup (Bs4) Python

This assignment involves creating a Python Jupyter Notebook for web scraping from the following URL: [A Guide to Worldwide Pet Ownership](https://www.petsecure.com.au/pet-care/a-guide-to-worldwide-pet-ownership/). You are required to select one table (Dog/Cat/Bird/Fish) from the webpage and scrape data from it.

## Section Jupyter Notebook:

### Import Module yang Dibutuhkan
```python
import pandas as pd
from bs4 import BeautifulSoup
import requests
```

### Response HTML yang diakses
```python
url = 'https://www.petsecure.com.au/pet-care/a-guide-to-worldwide-pet-ownership/'
response = requests.get(url)
print(response)
```

### Parse & Print HTML dengan Bs4
```python
soup = BeautifulSoup(response.content, 'html.parser')
print(soup.prettify())
```

### Dapatkan Data Table dari Bs4 dan jelaskan bagaimana proses pengambilan datanya
```python
x = table.find_all('th')
for i, y in enumerate(x):
    print(i, "text : ", y.text)
```

### Dapatkan Data Table Headers dan Table Rows kemudian jadikan satu DataFrame dan print menjadi .csv file
```python
headers = []
for th in table.find('th'):
    headers.append(th.text.strip())
headers = [header for header in headers if header]
print(headers)

data = []
for tr in table.find_all('tr'):
    row_data = []
    for td in tr.find_all('td'):
        row_data.append(td.text.strip())
    if len(row_data) > 0:
        data.append(row_data)

df = pd.DataFrame(data, columns=headers)
df.to_csv('result.csv', index=False)
```

The completed assignment should be uploaded to your personal public GitHub repository. Share the link to your GitHub repository containing the Jupyter Notebook and the resulting .csv file.
