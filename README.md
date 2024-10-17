# 常用資料格式讀取

# 資料來源

**政府資料開放平台 - 新竹市重要遊憩據點遊客人次統計**

[新竹市重要遊憩據點遊客人次統計 ｜ 政府資料開放平臺](https://data.gov.tw/dataset/99374)

# json檔案

讀取json檔案

```python
import json
import pandas as pd
#讀取json檔案
with open('新竹市重要遊憩據點遊客人次統計.json', 'r', encoding='utf-8') as file:
    data_array = json.load(file)
df = pd.DataFrame(data_array)
df
```

![image.png](image.png)

在將df寫入新的json檔案

```python
#寫入json檔案
df.to_json('New_新竹市重要遊憩據點遊客人次統計.json', orient='records', force_ascii=False, indent=4)
```

# xml檔案

讀取xml檔案

```python
import xml.etree.ElementTree as ET
import pandas as pd
#讀取xml檔案
tree = ET.parse('新竹市重要遊憩據點遊客人次統計.xml')
root = tree.getroot()

data_list = []
for data in root.findall('Data'):
    entry = {child.tag: child.text for child in data}
    data_list.append(entry)
data_list

df = pd.DataFrame(data_list)
df
```

![image.png](image%201.png)

寫入新的xml檔案

```python
#寫入xml檔案
df.to_xml('New_新竹市重要遊憩據點遊客人次統計', root_name='Datas', row_name='Data', index=False)
```

# csv檔案

讀取csv檔案

```python
import pandas as pd
#讀取csv檔案
df=pd.read_csv('新竹市重要遊憩據點遊客人次統計.csv')
df
```

![image.png](image%202.png)

寫入新的csv檔案

```python
#寫入csv檔案
df.to_csv('New_新竹市重要遊憩據點遊客人次統計.csv', index=False, encoding='utf-8-sig')
```

# excel檔案

讀取xlsx檔案

```python
import pandas as pd
#讀取xlsx檔案
df=pd.read_excel('新竹市重要遊憩據點遊客人次統計.xlsx')
df
```

![image.png](image%203.png)

寫入新的xlsx檔案

```python
#寫入xlsx檔案
df.to_excel('New_新竹市重要遊憩據點遊客人次統計.xlsx', index=False)
```

結果

![image.png](fc82d0af-680c-4e31-8599-f522b2e7e818.png)