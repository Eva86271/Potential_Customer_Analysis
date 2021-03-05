```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```


```python
data=pd.read_excel("C:/Users/subha/OneDrive/Desktop/KPMG_VI_New_raw_data_update_final.xlsx",header=[1],sheet_name="Transactions")
data.head()
data.set_index("transaction_id")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>product_id</th>
      <th>customer_id</th>
      <th>transaction_date</th>
      <th>online_order</th>
      <th>order_status</th>
      <th>brand</th>
      <th>product_line</th>
      <th>product_class</th>
      <th>product_size</th>
      <th>list_price</th>
      <th>standard_cost</th>
      <th>product_first_sold_date</th>
    </tr>
    <tr>
      <th>transaction_id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>2950</td>
      <td>2017-02-25</td>
      <td>0.0</td>
      <td>Approved</td>
      <td>Solex</td>
      <td>Standard</td>
      <td>medium</td>
      <td>medium</td>
      <td>71.49</td>
      <td>53.62</td>
      <td>2012-12-02</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>3120</td>
      <td>2017-05-21</td>
      <td>1.0</td>
      <td>Approved</td>
      <td>Trek Bicycles</td>
      <td>Standard</td>
      <td>medium</td>
      <td>large</td>
      <td>2091.47</td>
      <td>388.92</td>
      <td>2014-03-03</td>
    </tr>
    <tr>
      <th>3</th>
      <td>37</td>
      <td>402</td>
      <td>2017-10-16</td>
      <td>0.0</td>
      <td>Approved</td>
      <td>OHM Cycles</td>
      <td>Standard</td>
      <td>low</td>
      <td>medium</td>
      <td>1793.43</td>
      <td>248.82</td>
      <td>1999-07-20</td>
    </tr>
    <tr>
      <th>4</th>
      <td>88</td>
      <td>3135</td>
      <td>2017-08-31</td>
      <td>0.0</td>
      <td>Approved</td>
      <td>Norco Bicycles</td>
      <td>Standard</td>
      <td>medium</td>
      <td>medium</td>
      <td>1198.46</td>
      <td>381.10</td>
      <td>1998-12-16</td>
    </tr>
    <tr>
      <th>5</th>
      <td>78</td>
      <td>787</td>
      <td>2017-10-01</td>
      <td>1.0</td>
      <td>Approved</td>
      <td>Giant Bicycles</td>
      <td>Standard</td>
      <td>medium</td>
      <td>large</td>
      <td>1765.30</td>
      <td>709.48</td>
      <td>2015-08-10</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>19996</th>
      <td>51</td>
      <td>1018</td>
      <td>2017-06-24</td>
      <td>1.0</td>
      <td>Approved</td>
      <td>OHM Cycles</td>
      <td>Standard</td>
      <td>high</td>
      <td>medium</td>
      <td>2005.66</td>
      <td>1203.40</td>
      <td>2003-07-21</td>
    </tr>
    <tr>
      <th>19997</th>
      <td>41</td>
      <td>127</td>
      <td>2017-11-09</td>
      <td>1.0</td>
      <td>Approved</td>
      <td>Solex</td>
      <td>Road</td>
      <td>medium</td>
      <td>medium</td>
      <td>416.98</td>
      <td>312.74</td>
      <td>1997-05-10</td>
    </tr>
    <tr>
      <th>19998</th>
      <td>87</td>
      <td>2284</td>
      <td>2017-04-14</td>
      <td>1.0</td>
      <td>Approved</td>
      <td>OHM Cycles</td>
      <td>Standard</td>
      <td>medium</td>
      <td>medium</td>
      <td>1636.90</td>
      <td>44.71</td>
      <td>2010-08-20</td>
    </tr>
    <tr>
      <th>19999</th>
      <td>6</td>
      <td>2764</td>
      <td>2017-07-03</td>
      <td>0.0</td>
      <td>Approved</td>
      <td>OHM Cycles</td>
      <td>Standard</td>
      <td>high</td>
      <td>medium</td>
      <td>227.88</td>
      <td>136.73</td>
      <td>2004-08-17</td>
    </tr>
    <tr>
      <th>20000</th>
      <td>11</td>
      <td>1144</td>
      <td>2017-09-22</td>
      <td>1.0</td>
      <td>Approved</td>
      <td>Trek Bicycles</td>
      <td>Standard</td>
      <td>medium</td>
      <td>small</td>
      <td>1775.81</td>
      <td>1580.47</td>
      <td>1999-06-23</td>
    </tr>
  </tbody>
</table>
<p>20000 rows × 12 columns</p>
</div>




```python
data.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 20000 entries, 0 to 19999
    Data columns (total 13 columns):
     #   Column                   Non-Null Count  Dtype         
    ---  ------                   --------------  -----         
     0   transaction_id           20000 non-null  int64         
     1   product_id               20000 non-null  int64         
     2   customer_id              20000 non-null  int64         
     3   transaction_date         20000 non-null  datetime64[ns]
     4   online_order             19640 non-null  float64       
     5   order_status             20000 non-null  object        
     6   brand                    19803 non-null  object        
     7   product_line             19803 non-null  object        
     8   product_class            19803 non-null  object        
     9   product_size             19803 non-null  object        
     10  list_price               20000 non-null  float64       
     11  standard_cost            19803 non-null  float64       
     12  product_first_sold_date  19803 non-null  datetime64[ns]
    dtypes: datetime64[ns](2), float64(3), int64(3), object(5)
    memory usage: 2.0+ MB
    


```python
data['online_order'].value_counts()
```




    1.0    9829
    0.0    9811
    Name: online_order, dtype: int64




```python
data.describe()
data['product_id']=data['product_id'].astype(str)
data['transaction_id']=data['transaction_id'].astype(str)
data['customer_id']=data['customer_id'].astype(str)
data['online_order']=data['online_order'].astype(str)
data['product_line']=data['product_line'].astype(str)
data['prodyct_class']=data['product_class'].astype(str)
data['brand']=data['brand'].astype(str)
data['order_status']=data['order_status'].astype(str)

```


```python
for col in ['online_order','product_line','customer_id','product_class','order_status','brand','product_id']:
    data.loc[:,col]=data.loc[:,col].str.strip()
```


```python

print(data['product_id'].value_counts())
print(data['brand'].value_counts())
```

    0      1378
    3       354
    1       311
    35      268
    38      267
           ... 
    71      137
    16      136
    8       136
    100     130
    47      121
    Name: product_id, Length: 101, dtype: int64
    Solex             4253
    Giant Bicycles    3312
    WeareA2B          3295
    OHM Cycles        3043
    Trek Bicycles     2990
    Norco Bicycles    2910
    nan                197
    Name: brand, dtype: int64
    


```python
data['brand'].dropna().value_counts().plot(kind='bar',color='orange')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x19e01545808>




![png](output_7_1.png)



```python
data2=pd.read_excel("C:/Users/subha/OneDrive/Desktop/KPMG_VI_New_raw_data_update_final.xlsx",header=[1],sheet_name="NewCustomerList")
data2.head()


```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>first_name</th>
      <th>last_name</th>
      <th>gender</th>
      <th>past_3_years_bike_related_purchases</th>
      <th>DOB</th>
      <th>job_title</th>
      <th>job_industry_category</th>
      <th>wealth_segment</th>
      <th>deceased_indicator</th>
      <th>owns_car</th>
      <th>...</th>
      <th>state</th>
      <th>country</th>
      <th>property_valuation</th>
      <th>Unnamed: 16</th>
      <th>Unnamed: 17</th>
      <th>Unnamed: 18</th>
      <th>Unnamed: 19</th>
      <th>Unnamed: 20</th>
      <th>Rank</th>
      <th>Value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Chickie</td>
      <td>Brister</td>
      <td>Male</td>
      <td>86</td>
      <td>1957-07-12</td>
      <td>General Manager</td>
      <td>Manufacturing</td>
      <td>Mass Customer</td>
      <td>N</td>
      <td>Yes</td>
      <td>...</td>
      <td>QLD</td>
      <td>Australia</td>
      <td>6</td>
      <td>1.05</td>
      <td>1.3125</td>
      <td>1.640625</td>
      <td>1.394531</td>
      <td>1</td>
      <td>1</td>
      <td>1.718750</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Morly</td>
      <td>Genery</td>
      <td>Male</td>
      <td>69</td>
      <td>1970-03-22</td>
      <td>Structural Engineer</td>
      <td>Property</td>
      <td>Mass Customer</td>
      <td>N</td>
      <td>No</td>
      <td>...</td>
      <td>NSW</td>
      <td>Australia</td>
      <td>11</td>
      <td>1.05</td>
      <td>1.0500</td>
      <td>1.312500</td>
      <td>1.115625</td>
      <td>1</td>
      <td>1</td>
      <td>1.718750</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Ardelis</td>
      <td>Forrester</td>
      <td>Female</td>
      <td>10</td>
      <td>1974-08-28</td>
      <td>Senior Cost Accountant</td>
      <td>Financial Services</td>
      <td>Affluent Customer</td>
      <td>N</td>
      <td>No</td>
      <td>...</td>
      <td>VIC</td>
      <td>Australia</td>
      <td>5</td>
      <td>0.80</td>
      <td>0.8000</td>
      <td>0.800000</td>
      <td>0.800000</td>
      <td>1</td>
      <td>1</td>
      <td>1.718750</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Lucine</td>
      <td>Stutt</td>
      <td>Female</td>
      <td>64</td>
      <td>1979-01-28</td>
      <td>Account Representative III</td>
      <td>Manufacturing</td>
      <td>Affluent Customer</td>
      <td>N</td>
      <td>Yes</td>
      <td>...</td>
      <td>QLD</td>
      <td>Australia</td>
      <td>1</td>
      <td>0.44</td>
      <td>0.5500</td>
      <td>0.550000</td>
      <td>0.550000</td>
      <td>4</td>
      <td>4</td>
      <td>1.703125</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Melinda</td>
      <td>Hadlee</td>
      <td>Female</td>
      <td>34</td>
      <td>1965-09-21</td>
      <td>Financial Analyst</td>
      <td>Financial Services</td>
      <td>Affluent Customer</td>
      <td>N</td>
      <td>No</td>
      <td>...</td>
      <td>NSW</td>
      <td>Australia</td>
      <td>9</td>
      <td>1.04</td>
      <td>1.0400</td>
      <td>1.300000</td>
      <td>1.300000</td>
      <td>4</td>
      <td>4</td>
      <td>1.703125</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 23 columns</p>
</div>




```python
data2.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 1000 entries, 0 to 999
    Data columns (total 23 columns):
     #   Column                               Non-Null Count  Dtype         
    ---  ------                               --------------  -----         
     0   first_name                           1000 non-null   object        
     1   last_name                            971 non-null    object        
     2   gender                               1000 non-null   object        
     3   past_3_years_bike_related_purchases  1000 non-null   int64         
     4   DOB                                  983 non-null    datetime64[ns]
     5   job_title                            894 non-null    object        
     6   job_industry_category                835 non-null    object        
     7   wealth_segment                       1000 non-null   object        
     8   deceased_indicator                   1000 non-null   object        
     9   owns_car                             1000 non-null   object        
     10  tenure                               1000 non-null   int64         
     11  address                              1000 non-null   object        
     12  postcode                             1000 non-null   int64         
     13  state                                1000 non-null   object        
     14  country                              1000 non-null   object        
     15  property_valuation                   1000 non-null   int64         
     16  Unnamed: 16                          1000 non-null   float64       
     17  Unnamed: 17                          1000 non-null   float64       
     18  Unnamed: 18                          1000 non-null   float64       
     19  Unnamed: 19                          1000 non-null   float64       
     20  Unnamed: 20                          1000 non-null   int64         
     21  Rank                                 1000 non-null   int64         
     22  Value                                1000 non-null   float64       
    dtypes: datetime64[ns](1), float64(5), int64(6), object(11)
    memory usage: 179.8+ KB
    


```python
len(data2['address'].unique())
```




    1000




```python
data3=pd.read_excel("C:/Users/subha/OneDrive/Desktop/KPMG_VI_New_raw_data_update_final.xlsx",header=[1],sheet_name="CustomerDemographic")
data3.head()


```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>customer_id</th>
      <th>first_name</th>
      <th>last_name</th>
      <th>gender</th>
      <th>past_3_years_bike_related_purchases</th>
      <th>DOB</th>
      <th>job_title</th>
      <th>job_industry_category</th>
      <th>wealth_segment</th>
      <th>deceased_indicator</th>
      <th>default</th>
      <th>owns_car</th>
      <th>tenure</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Laraine</td>
      <td>Medendorp</td>
      <td>F</td>
      <td>93</td>
      <td>1953-10-12</td>
      <td>Executive Secretary</td>
      <td>Health</td>
      <td>Mass Customer</td>
      <td>N</td>
      <td>"'</td>
      <td>Yes</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Eli</td>
      <td>Bockman</td>
      <td>Male</td>
      <td>81</td>
      <td>1980-12-16</td>
      <td>Administrative Officer</td>
      <td>Financial Services</td>
      <td>Mass Customer</td>
      <td>N</td>
      <td>&lt;script&gt;alert('hi')&lt;/script&gt;</td>
      <td>Yes</td>
      <td>16.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Arlin</td>
      <td>Dearle</td>
      <td>Male</td>
      <td>61</td>
      <td>1954-01-20</td>
      <td>Recruiting Manager</td>
      <td>Property</td>
      <td>Mass Customer</td>
      <td>N</td>
      <td>2018-02-01 00:00:00</td>
      <td>Yes</td>
      <td>15.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Talbot</td>
      <td>NaN</td>
      <td>Male</td>
      <td>33</td>
      <td>1961-10-03</td>
      <td>NaN</td>
      <td>IT</td>
      <td>Mass Customer</td>
      <td>N</td>
      <td>() { _; } &gt;_[$($())] { touch /tmp/blns.shellsh...</td>
      <td>No</td>
      <td>7.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Sheila-kathryn</td>
      <td>Calton</td>
      <td>Female</td>
      <td>56</td>
      <td>1977-05-13</td>
      <td>Senior Editor</td>
      <td>NaN</td>
      <td>Affluent Customer</td>
      <td>N</td>
      <td>NIL</td>
      <td>Yes</td>
      <td>8.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
np.shape(data3)
data3.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 4000 entries, 0 to 3999
    Data columns (total 13 columns):
     #   Column                               Non-Null Count  Dtype         
    ---  ------                               --------------  -----         
     0   customer_id                          4000 non-null   int64         
     1   first_name                           4000 non-null   object        
     2   last_name                            3875 non-null   object        
     3   gender                               4000 non-null   object        
     4   past_3_years_bike_related_purchases  4000 non-null   int64         
     5   DOB                                  3913 non-null   datetime64[ns]
     6   job_title                            3494 non-null   object        
     7   job_industry_category                3344 non-null   object        
     8   wealth_segment                       4000 non-null   object        
     9   deceased_indicator                   4000 non-null   object        
     10  default                              3698 non-null   object        
     11  owns_car                             4000 non-null   object        
     12  tenure                               3913 non-null   float64       
    dtypes: datetime64[ns](1), float64(1), int64(2), object(9)
    memory usage: 406.4+ KB
    


```python
data3.sort_values(by=['past_3_years_bike_related_purchases'],ascending= False)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>customer_id</th>
      <th>first_name</th>
      <th>last_name</th>
      <th>gender</th>
      <th>past_3_years_bike_related_purchases</th>
      <th>DOB</th>
      <th>job_title</th>
      <th>job_industry_category</th>
      <th>wealth_segment</th>
      <th>deceased_indicator</th>
      <th>default</th>
      <th>owns_car</th>
      <th>tenure</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3431</th>
      <td>3432</td>
      <td>Max</td>
      <td>Cloney</td>
      <td>Female</td>
      <td>99</td>
      <td>1988-11-27</td>
      <td>Junior Executive</td>
      <td>Argiculture</td>
      <td>Mass Customer</td>
      <td>N</td>
      <td>ç¤¾æç§å­¸é¢èªå­¸ç ç©¶æ</td>
      <td>Yes</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>1451</th>
      <td>1452</td>
      <td>Zachery</td>
      <td>Hamber</td>
      <td>Male</td>
      <td>99</td>
      <td>1955-12-31</td>
      <td>Safety Technician III</td>
      <td>Retail</td>
      <td>Mass Customer</td>
      <td>N</td>
      <td>,./;'[]\-=</td>
      <td>No</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>2063</th>
      <td>2064</td>
      <td>Reynard</td>
      <td>Jaffrey</td>
      <td>Male</td>
      <td>99</td>
      <td>1969-05-19</td>
      <td>VP Marketing</td>
      <td>Health</td>
      <td>Mass Customer</td>
      <td>N</td>
      <td>â°â´âµâââ</td>
      <td>Yes</td>
      <td>18.0</td>
    </tr>
    <tr>
      <th>3777</th>
      <td>3778</td>
      <td>Ilaire</td>
      <td>Redborn</td>
      <td>Male</td>
      <td>99</td>
      <td>1971-06-09</td>
      <td>Dental Hygienist</td>
      <td>Health</td>
      <td>High Net Worth</td>
      <td>N</td>
      <td>,ãã»:*:ã»ãâ( â» Ï â» )ãã»:*:ã»ãâ</td>
      <td>No</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>560</th>
      <td>561</td>
      <td>Karin</td>
      <td>Burkill</td>
      <td>Female</td>
      <td>99</td>
      <td>1977-08-15</td>
      <td>Tax Accountant</td>
      <td>NaN</td>
      <td>Mass Customer</td>
      <td>N</td>
      <td>Î©âÃ§ââ«ËÂµâ¤â¥Ã·</td>
      <td>No</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>601</th>
      <td>602</td>
      <td>Lebbie</td>
      <td>Bruck</td>
      <td>Female</td>
      <td>0</td>
      <td>1992-03-28</td>
      <td>Office Assistant II</td>
      <td>NaN</td>
      <td>High Net Worth</td>
      <td>N</td>
      <td>åè£½æ¼¢èª</td>
      <td>Yes</td>
      <td>9.0</td>
    </tr>
    <tr>
      <th>1353</th>
      <td>1354</td>
      <td>Karee</td>
      <td>Hyman</td>
      <td>Female</td>
      <td>0</td>
      <td>2000-10-15</td>
      <td>Analyst Programmer</td>
      <td>Financial Services</td>
      <td>Affluent Customer</td>
      <td>N</td>
      <td>ï¼ï¼ï¼</td>
      <td>No</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>3975</th>
      <td>3976</td>
      <td>Gretel</td>
      <td>Chrystal</td>
      <td>Female</td>
      <td>0</td>
      <td>1957-11-20</td>
      <td>Internal Auditor</td>
      <td>NaN</td>
      <td>Affluent Customer</td>
      <td>N</td>
      <td>'"''''"</td>
      <td>Yes</td>
      <td>13.0</td>
    </tr>
    <tr>
      <th>2238</th>
      <td>2239</td>
      <td>Jocelyne</td>
      <td>Pasquale</td>
      <td>Female</td>
      <td>0</td>
      <td>1960-01-11</td>
      <td>Associate Professor</td>
      <td>Property</td>
      <td>High Net Worth</td>
      <td>N</td>
      <td>-1</td>
      <td>Yes</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>1290</th>
      <td>1291</td>
      <td>Warner</td>
      <td>Zuker</td>
      <td>Male</td>
      <td>0</td>
      <td>1980-08-16</td>
      <td>Quality Engineer</td>
      <td>Health</td>
      <td>Mass Customer</td>
      <td>N</td>
      <td>âââ</td>
      <td>No</td>
      <td>12.0</td>
    </tr>
  </tbody>
</table>
<p>4000 rows × 13 columns</p>
</div>




```python
a=list(data3['past_3_years_bike_related_purchases'].unique())
```


```python
data4=pd.read_excel("C:/Users/subha/OneDrive/Desktop/KPMG_VI_New_raw_data_update_final.xlsx",header=[1],sheet_name="CustomerAddress")
data4.head()

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>customer_id</th>
      <th>address</th>
      <th>postcode</th>
      <th>state</th>
      <th>country</th>
      <th>property_valuation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>060 Morning Avenue</td>
      <td>2016</td>
      <td>New South Wales</td>
      <td>Australia</td>
      <td>10</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>6 Meadow Vale Court</td>
      <td>2153</td>
      <td>New South Wales</td>
      <td>Australia</td>
      <td>10</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>0 Holy Cross Court</td>
      <td>4211</td>
      <td>QLD</td>
      <td>Australia</td>
      <td>9</td>
    </tr>
    <tr>
      <th>3</th>
      <td>5</td>
      <td>17979 Del Mar Point</td>
      <td>2448</td>
      <td>New South Wales</td>
      <td>Australia</td>
      <td>4</td>
    </tr>
    <tr>
      <th>4</th>
      <td>6</td>
      <td>9 Oakridge Court</td>
      <td>3216</td>
      <td>VIC</td>
      <td>Australia</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>




```python
data4.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 3999 entries, 0 to 3998
    Data columns (total 6 columns):
     #   Column              Non-Null Count  Dtype 
    ---  ------              --------------  ----- 
     0   customer_id         3999 non-null   int64 
     1   address             3999 non-null   object
     2   postcode            3999 non-null   int64 
     3   state               3999 non-null   object
     4   country             3999 non-null   object
     5   property_valuation  3999 non-null   int64 
    dtypes: int64(3), object(3)
    memory usage: 187.6+ KB
    


```python
data_merge = pd.merge(data3, data4, on=['customer_id'])
data_merge.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>customer_id</th>
      <th>first_name</th>
      <th>last_name</th>
      <th>gender</th>
      <th>past_3_years_bike_related_purchases</th>
      <th>DOB</th>
      <th>job_title</th>
      <th>job_industry_category</th>
      <th>wealth_segment</th>
      <th>deceased_indicator</th>
      <th>default</th>
      <th>owns_car</th>
      <th>tenure</th>
      <th>address</th>
      <th>postcode</th>
      <th>state</th>
      <th>country</th>
      <th>property_valuation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Laraine</td>
      <td>Medendorp</td>
      <td>F</td>
      <td>93</td>
      <td>1953-10-12</td>
      <td>Executive Secretary</td>
      <td>Health</td>
      <td>Mass Customer</td>
      <td>N</td>
      <td>"'</td>
      <td>Yes</td>
      <td>11.0</td>
      <td>060 Morning Avenue</td>
      <td>2016</td>
      <td>New South Wales</td>
      <td>Australia</td>
      <td>10</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Eli</td>
      <td>Bockman</td>
      <td>Male</td>
      <td>81</td>
      <td>1980-12-16</td>
      <td>Administrative Officer</td>
      <td>Financial Services</td>
      <td>Mass Customer</td>
      <td>N</td>
      <td>&lt;script&gt;alert('hi')&lt;/script&gt;</td>
      <td>Yes</td>
      <td>16.0</td>
      <td>6 Meadow Vale Court</td>
      <td>2153</td>
      <td>New South Wales</td>
      <td>Australia</td>
      <td>10</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>Talbot</td>
      <td>NaN</td>
      <td>Male</td>
      <td>33</td>
      <td>1961-10-03</td>
      <td>NaN</td>
      <td>IT</td>
      <td>Mass Customer</td>
      <td>N</td>
      <td>() { _; } &gt;_[$($())] { touch /tmp/blns.shellsh...</td>
      <td>No</td>
      <td>7.0</td>
      <td>0 Holy Cross Court</td>
      <td>4211</td>
      <td>QLD</td>
      <td>Australia</td>
      <td>9</td>
    </tr>
    <tr>
      <th>3</th>
      <td>5</td>
      <td>Sheila-kathryn</td>
      <td>Calton</td>
      <td>Female</td>
      <td>56</td>
      <td>1977-05-13</td>
      <td>Senior Editor</td>
      <td>NaN</td>
      <td>Affluent Customer</td>
      <td>N</td>
      <td>NIL</td>
      <td>Yes</td>
      <td>8.0</td>
      <td>17979 Del Mar Point</td>
      <td>2448</td>
      <td>New South Wales</td>
      <td>Australia</td>
      <td>4</td>
    </tr>
    <tr>
      <th>4</th>
      <td>6</td>
      <td>Curr</td>
      <td>Duckhouse</td>
      <td>Male</td>
      <td>35</td>
      <td>1966-09-16</td>
      <td>NaN</td>
      <td>Retail</td>
      <td>High Net Worth</td>
      <td>N</td>
      <td>ðµ ð ð ð</td>
      <td>Yes</td>
      <td>13.0</td>
      <td>9 Oakridge Court</td>
      <td>3216</td>
      <td>VIC</td>
      <td>Australia</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>




```python
data_merge.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 3996 entries, 0 to 3995
    Data columns (total 18 columns):
     #   Column                               Non-Null Count  Dtype         
    ---  ------                               --------------  -----         
     0   customer_id                          3996 non-null   int64         
     1   first_name                           3996 non-null   object        
     2   last_name                            3871 non-null   object        
     3   gender                               3996 non-null   object        
     4   past_3_years_bike_related_purchases  3996 non-null   int64         
     5   DOB                                  3909 non-null   datetime64[ns]
     6   job_title                            3492 non-null   object        
     7   job_industry_category                3341 non-null   object        
     8   wealth_segment                       3996 non-null   object        
     9   deceased_indicator                   3996 non-null   object        
     10  default                              3694 non-null   object        
     11  owns_car                             3996 non-null   object        
     12  tenure                               3909 non-null   float64       
     13  address                              3996 non-null   object        
     14  postcode                             3996 non-null   int64         
     15  state                                3996 non-null   object        
     16  country                              3996 non-null   object        
     17  property_valuation                   3996 non-null   int64         
    dtypes: datetime64[ns](1), float64(1), int64(4), object(12)
    memory usage: 593.2+ KB
    


```python

```


```python
data_sort=data_merge.sort_values(by='past_3_years_bike_related_purchases',ascending=False)
data_merge.head()
df=data_merge[data_merge.duplicated()].index
print(df)
```

    Int64Index([], dtype='int64')
    


```python
data_sort['property_valuation'].isna().sum()
```




    0




```python
from datetime import date
df=[]
record=[]
for birthDate in data_sort['DOB']:
   today = date.today() 
   age = today.year - birthDate.year - ((today.month, today.day) < (birthDate.month, birthDate.day)) 
   if (age>63):
    record.append(0)
    df.append(age)
   else:
    record.append(1)
    df.append(age)
data_sort=data_sort.assign(Age=df)
print(record)
data_sort=data_sort.assign(Buying_chance=record)
print(data_sort['Buying_chance'])

df1=[]
for birthDate in data2['DOB']:
   today = date.today() 
   age = today.year - birthDate.year - ((today.month, today.day) < (birthDate.month, birthDate.day)) 
   df1.append(age)
data2=data2.assign(Age=df1)
indi=data_sort[data_sort['past_3_years_bike_related_purchases']==0].index
print(indi)
for i in indi:
    data_sort.loc[i,'Buying_chance']=0






```

    [1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 1, 0, 0, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 0, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 0, 0, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 0, 1, 1, 0, 1, 0, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1]
    3773    1
    3342    1
    1093    1
    2059    1
    1447    0
           ..
    423     1
    1286    1
    2772    1
    1209    1
    597     1
    Name: Buying_chance, Length: 3996, dtype: int64
    Int64Index([ 305, 1937, 2065, 2715, 2707,  470, 3544, 3971, 2675,  481,  924,
                3242, 1524, 1349, 2546,  274, 1041, 1037, 2406, 2915, 1011, 2355,
                 976, 3641, 2800,  455, 2234, 2231, 3838, 1295, 1190,  567, 3138,
                 423, 1286, 2772, 1209,  597],
               dtype='int64')
    


```python
data_sort.info()
print(data_sort.head())
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 3996 entries, 3773 to 597
    Data columns (total 20 columns):
     #   Column                               Non-Null Count  Dtype         
    ---  ------                               --------------  -----         
     0   customer_id                          3996 non-null   int64         
     1   first_name                           3996 non-null   object        
     2   last_name                            3871 non-null   object        
     3   gender                               3996 non-null   object        
     4   past_3_years_bike_related_purchases  3996 non-null   int64         
     5   DOB                                  3909 non-null   datetime64[ns]
     6   job_title                            3492 non-null   object        
     7   job_industry_category                3341 non-null   object        
     8   wealth_segment                       3996 non-null   object        
     9   deceased_indicator                   3996 non-null   object        
     10  default                              3694 non-null   object        
     11  owns_car                             3996 non-null   object        
     12  tenure                               3909 non-null   float64       
     13  address                              3996 non-null   object        
     14  postcode                             3996 non-null   int64         
     15  state                                3996 non-null   object        
     16  country                              3996 non-null   object        
     17  property_valuation                   3996 non-null   int64         
     18  Age                                  3909 non-null   float64       
     19  Buying_chance                        3996 non-null   int64         
    dtypes: datetime64[ns](1), float64(2), int64(5), object(12)
    memory usage: 815.6+ KB
          customer_id first_name last_name  gender  \
    3773         3778     Ilaire   Redborn    Male   
    3342         3347    Nichols       NaN    Male   
    1093         1098      Maure      Crow  Female   
    2059         2064    Reynard   Jaffrey    Male   
    1447         1452    Zachery    Hamber    Male   
    
          past_3_years_bike_related_purchases        DOB  \
    3773                                   99 1971-06-09   
    3342                                   99 1985-11-08   
    1093                                   99 1989-02-01   
    2059                                   99 1969-05-19   
    1447                                   99 1955-12-31   
    
                            job_title job_industry_category  wealth_segment  \
    3773             Dental Hygienist                Health  High Net Worth   
    3342  Computer Systems Analyst II         Entertainment  High Net Worth   
    1093  Administrative Assistant IV    Financial Services   Mass Customer   
    2059                 VP Marketing                Health   Mass Customer   
    1447        Safety Technician III                Retail   Mass Customer   
    
         deceased_indicator                           default owns_car  tenure  \
    3773                  N  ,ãã»:*:ã»ãâ( â» Ï â» )ãã»:*:ã»ãâ       No    10.0   
    3342                  N                               NaN      Yes    18.0   
    1093                  N                 ç°ä¸­ããã«ããã¦ä¸ãã      Yes    12.0   
    2059                  N                         â°â´âµâââ      Yes    18.0   
    1447                  N                        ,./;'[]\-=       No    20.0   
    
                        address  postcode state    country  property_valuation  \
    3773    69131 Kipling Alley      3351   VIC  Australia                   4   
    3342         75 Logan Place      3071   VIC  Australia                  10   
    1093      9419 Homewood Way      2160   NSW  Australia                   9   
    2059       4 Sachtjen Drive      4701   QLD  Australia                   3   
    1447  913 Londonderry Trail      2567   NSW  Australia                   8   
    
           Age  Buying_chance  
    3773  48.0              1  
    3342  34.0              1  
    1093  31.0              1  
    2059  50.0              1  
    1447  64.0              0  
    


```python
print(data_sort['state'].unique())
mer=data_sort.loc[data_sort['state']=="New South Wales"].index
for i in mer:
    data_sort.loc[i,'state']="NSW"
mer1=data_sort.loc[data_sort['state']=="Victoria"].index
for i in mer1:
    data_sort.loc[i,'state']="VIC"
print(data_sort['state'].unique())
print(data_sort['state'].value_counts())
print(data_sort['gender'].unique())
mer_f=data_sort.loc[data_sort['gender']=="F"].index
mer_fm=data_sort.loc[data_sort['gender']=="Femal"].index
for i in mer_fm:
    data_sort.loc[i,'gender']="Female"
mer_m=data_sort.loc[data_sort['gender']=="M"].index
for i in mer_m:
    data_sort.loc[i,'gender']="Male"
for i in mer_f:
    data_sort.loc[i,'gender']="Female"
print(data_sort['owns_car'].unique())
print(data_sort['deceased_indicator'].unique())

#data_sort.iloc[:1000,:]
print(data_sort[data_sort['deceased_indicator']=='Y'].index)
data_sort.head()
#for i in (['gender','past_3_years_bike_related_purchases','deceased_indicator','job_title','owns_car','state','Age','wealth_segment']):
#    ind=data_sort[data_sort[i].isna()].index
 #   for j in ind:
 #       data_sort.loc[j,i]="NotSpecified"
zero_buy=data_sort.loc[data_sort['past_3_years_bike_related_purchases']==0].index
print(len(zero_buy))
for i in zero_buy:
    data_sort[i,'Buying_chance']=0
dc=data_sort.loc[data_sort['deceased_indicator']=='Y'].index
for i in dc:
    data_sort[i,'Buying_chance']=0

label=['gender','past_3_years_bike_related_purchases','wealth_segment','job_title','deceased_indicator','owns_car','job_industry_category','state','Age','property_valuation','tenure','Buying_chance']



```

    ['VIC' 'NSW' 'QLD' 'Victoria' 'New South Wales']
    ['VIC' 'NSW' 'QLD']
    NSW    2138
    VIC    1021
    QLD     837
    Name: state, dtype: int64
    ['Male' 'Female' 'U' 'F' 'M' 'Femal']
    ['No' 'Yes']
    ['N' 'Y']
    Int64Index([3785, 748], dtype='int64')
    38
    


```python
for i in data_sort.columns:
    nullind=data_sort.loc[data_sort[i].isna()].index
    if (len(nullind)!=0):
      for j in nullind:
        data_sort.loc[j,i]="Not Specified"
data_sort['job_title'].replace('Budget/Accounting Analyst III','BAIII',inplace=True)
data_sort['job_title'].replace('Budget/Accounting Analyst II','BAII',inplace=True)
data_sort['job_title'].replace('Budget/Accounting Analyst I','BAI',inplace=True)
it=data_sort.loc[data_sort['past_3_years_bike_related_purchases']==0].index
data_explore=data_sort.drop(it,axis=0)
data_explore.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>customer_id</th>
      <th>first_name</th>
      <th>last_name</th>
      <th>gender</th>
      <th>past_3_years_bike_related_purchases</th>
      <th>DOB</th>
      <th>job_title</th>
      <th>job_industry_category</th>
      <th>wealth_segment</th>
      <th>deceased_indicator</th>
      <th>...</th>
      <th>(1190, Buying_chance)</th>
      <th>(567, Buying_chance)</th>
      <th>(3138, Buying_chance)</th>
      <th>(423, Buying_chance)</th>
      <th>(1286, Buying_chance)</th>
      <th>(2772, Buying_chance)</th>
      <th>(1209, Buying_chance)</th>
      <th>(597, Buying_chance)</th>
      <th>(3785, Buying_chance)</th>
      <th>(748, Buying_chance)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3773</th>
      <td>3778</td>
      <td>Ilaire</td>
      <td>Redborn</td>
      <td>Male</td>
      <td>99</td>
      <td>1971-06-09 00:00:00</td>
      <td>Dental Hygienist</td>
      <td>Health</td>
      <td>High Net Worth</td>
      <td>N</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3342</th>
      <td>3347</td>
      <td>Nichols</td>
      <td>Not Specified</td>
      <td>Male</td>
      <td>99</td>
      <td>1985-11-08 00:00:00</td>
      <td>Computer Systems Analyst II</td>
      <td>Entertainment</td>
      <td>High Net Worth</td>
      <td>N</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1093</th>
      <td>1098</td>
      <td>Maure</td>
      <td>Crow</td>
      <td>Female</td>
      <td>99</td>
      <td>1989-02-01 00:00:00</td>
      <td>Administrative Assistant IV</td>
      <td>Financial Services</td>
      <td>Mass Customer</td>
      <td>N</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2059</th>
      <td>2064</td>
      <td>Reynard</td>
      <td>Jaffrey</td>
      <td>Male</td>
      <td>99</td>
      <td>1969-05-19 00:00:00</td>
      <td>VP Marketing</td>
      <td>Health</td>
      <td>Mass Customer</td>
      <td>N</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1447</th>
      <td>1452</td>
      <td>Zachery</td>
      <td>Hamber</td>
      <td>Male</td>
      <td>99</td>
      <td>1955-12-31 00:00:00</td>
      <td>Safety Technician III</td>
      <td>Retail</td>
      <td>Mass Customer</td>
      <td>N</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 60 columns</p>
</div>




```python
data_explore['customer_id'].groupby(data_sort['state']).count().plot(kind='bar')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x19e0d5d1748>




![png](output_26_1.png)



```python
data_explore['customer_id'].groupby(data_explore['job_industry_category']).count().plot(kind='bar',color='orange')
plt.ylabel("Cusomer Count")
```




    Text(0, 0.5, 'Cusomer Count')




![png](output_27_1.png)



```python
data_explore['customer_id'].groupby(data_sort['gender']).count().plot(kind='bar',color='purple')
plt.ylabel("Customer Count ")
```




    Text(0, 0.5, 'Customer Count ')




![png](output_28_1.png)



```python
data_explore['customer_id'].groupby(data_sort['wealth_segment']).count().plot(kind='bar',color='orange')
plt.ylabel("Customer Count")
```




    Text(0, 0.5, 'Customer Count')




![png](output_29_1.png)



```python
data_sort['job_title'].value_counts()
for i in label:
   print(data_sort[i].unique())
```

    ['Male' 'Female' 'U']
    [99 98 97 96 95 94 93 92 91 90 89 88 87 86 85 84 83 82 81 80 79 78 77 76
     75 74 73 72 71 70 69 68 67 66 65 64 63 62 61 60 59 58 57 56 55 54 53 52
     51 50 49 48 47 46 45 44 43 42 41 40 39 38 37 36 35 34 33 32 31 30 29 28
     27 26 25 24 23 22 21 20 19 18 17 16 15 14 13 12 11 10  9  8  7  6  5  4
      3  2  1  0]
    ['High Net Worth' 'Mass Customer' 'Affluent Customer']
    ['Dental Hygienist' 'Computer Systems Analyst II'
     'Administrative Assistant IV' 'VP Marketing' 'Safety Technician III'
     'Programmer III' 'Actuary' 'Product Engineer' 'Accountant I'
     'Internal Auditor' 'Cost Accountant' 'Programmer Analyst III'
     'Accounting Assistant IV' 'Librarian' 'Sales Associate'
     'Account Executive' 'Account Representative I' 'Junior Executive'
     'General Manager' 'Financial Analyst' 'Developer III'
     'Database Administrator I' 'Help Desk Technician' 'Not Specified'
     'Assistant Professor' 'Database Administrator IV'
     'Desktop Support Technician' 'Compensation Analyst'
     'Accounting Assistant II' 'Editor' 'Speech Pathologist'
     'Clinical Specialist' 'Tax Accountant' 'Geologist III' 'Registered Nurse'
     'Paralegal' 'Chief Design Engineer' 'Data Coordiator'
     'Automation Specialist IV' 'Structural Analysis Engineer'
     'Information Systems Manager' 'Recruiting Manager' 'Technical Writer'
     'Geological Engineer' 'Software Consultant' 'Quality Control Specialist'
     'Recruiter' 'Statistician III' 'Computer Systems Analyst I'
     'Senior Sales Associate' 'Marketing Manager' 'Associate Professor'
     'Director of Sales' 'Community Outreach Specialist' 'Senior Editor'
     'Budget/Accounting Analyst IV' 'VP Quality Control' 'Senior Developer'
     'Systems Administrator III' 'Statistician I' 'Electrical Engineer'
     'Chemical Engineer' 'Legal Assistant' 'Structural Engineer'
     'Software Test Engineer III' 'Financial Advisor' 'Nurse' 'Food Chemist'
     'Systems Administrator IV' 'Graphic Designer' 'Help Desk Operator'
     'Research Nurse' 'Database Administrator II' 'Civil Engineer'
     'Nuclear Power Engineer' 'Payment Adjustment Coordinator'
     'Health Coach II' 'VP Accounting' 'Executive Secretary'
     'Research Associate' 'GIS Technical Architect' 'Nurse Practicioner'
     'Systems Administrator II' 'Geologist I'
     'Business Systems Development Analyst' 'Social Worker'
     'Programmer Analyst II' 'Physical Therapy Assistant' 'Operator'
     'Software Test Engineer IV' 'Programmer IV' 'Quality Engineer'
     'Health Coach IV' 'Biostatistician II' 'Accountant IV'
     'Database Administrator III' 'Analyst Programmer' 'Software Engineer II'
     'Staff Accountant II' 'Environmental Tech' 'Automation Specialist I'
     'Account Representative IV' 'Pharmacist' 'Sales Representative'
     'Staff Scientist' 'Human Resources Assistant II'
     'Computer Systems Analyst IV' 'Safety Technician II'
     'Senior Cost Accountant' 'VP Product Management' 'Professor'
     'Web Developer III' 'Assistant Manager' 'Environmental Specialist'
     'Teacher' 'Design Engineer' 'Project Manager' 'VP Sales'
     'Office Assistant III' 'Accounting Assistant III' 'Statistician II'
     'Programmer II' 'Accountant III' 'Web Designer IV' 'Developer IV'
     'Safety Technician I' 'BAI' 'Human Resources Assistant I'
     'Senior Financial Analyst' 'Accountant II' 'Mechanical Systems Engineer'
     'Administrative Officer' 'Office Assistant I' 'Marketing Assistant'
     'Software Test Engineer II' 'Senior Quality Engineer'
     'Research Assistant III' 'Programmer I' 'Geologist IV'
     'Human Resources Manager' 'BAII' 'Analog Circuit Design manager'
     'Account Coordinator' 'Web Developer IV' 'Web Designer III'
     'Assistant Media Planner' 'Software Engineer III'
     'Administrative Assistant II' 'Geologist II' 'Accounting Assistant I'
     'Biostatistician I' 'Automation Specialist III' 'Occupational Therapist'
     'Web Designer I' 'Statistician IV' 'Account Representative III'
     'Engineer II' 'Biostatistician III' 'Staff Accountant IV'
     'Staff Accountant III' 'Administrative Assistant I'
     'Research Assistant II' 'Software Test Engineer I'
     'Account Representative II' 'Research Assistant I' 'Developer II'
     'Administrative Assistant III' 'Safety Technician IV' 'Engineer IV'
     'Programmer Analyst I' 'Programmer Analyst IV' 'Engineer I'
     'Media Manager IV' 'Software Engineer IV' 'Automation Specialist II'
     'Media Manager II' 'Office Assistant IV' 'Biostatistician IV'
     'Office Assistant II' 'Web Developer II' 'Systems Administrator I'
     'Web Developer I' 'Computer Systems Analyst III' 'Software Engineer I'
     'Engineer III' 'Web Designer II' 'Media Manager I' 'Media Manager III'
     'Human Resources Assistant IV' 'Human Resources Assistant III'
     'Staff Accountant I' 'Health Coach I' 'Health Coach III'
     'Research Assistant IV' 'BAIII' 'Developer I']
    ['N' 'Y']
    ['No' 'Yes']
    ['Health' 'Entertainment' 'Financial Services' 'Retail' 'Not Specified'
     'Manufacturing' 'IT' 'Property' 'Argiculture' 'Telecommunications']
    ['VIC' 'NSW' 'QLD']
    [48.0 34.0 31.0 50.0 64.0 42.0 39.0 30.0 46.0 35.0 62.0 60.0 23.0 45.0
     61.0 47.0 21.0 43.0 27.0 58.0 53.0 40.0 22.0 66.0 41.0 18.0 33.0 49.0
     24.0 38.0 28.0 54.0 36.0 59.0 57.0 20.0 44.0 26.0 55.0 65.0 29.0 37.0
     25.0 32.0 56.0 52.0 51.0 63.0 19.0 'Not Specified' 79.0 88.0 176.0 84.0
     76.0]
    [ 4 10  9  3  8  7  6  5 12 11  1  2]
    [10.0 18.0 12.0 20.0 9.0 7.0 16.0 5.0 8.0 14.0 15.0 1.0 17.0 21.0 3.0 22.0
     11.0 19.0 4.0 2.0 13.0 6.0 'Not Specified']
    [1 0]
    


```python
id1=data_sort.loc[data_sort['gender']=="nan"].index
print(id1)
```

    Int64Index([], dtype='int64')
    


```python
id3=data_sort[data_sort['tenure'].isna()==True].index
```


```python
data_sort.drop(id3,axis=0,inplace=True)
p=data_sort[data_sort['gender']=='U'].index
data_sort.drop(p,axis=0,inplace=True)
```


```python
data_sort['job_title'].value_counts()
for i in label:
   print(data_sort[i].unique())
```

    ['Male' 'Female']
    [99 98 97 96 95 94 93 92 91 90 89 88 87 86 85 84 83 82 81 80 79 78 77 76
     75 74 73 72 71 70 69 68 67 66 65 64 63 62 61 60 59 58 57 56 55 54 53 52
     51 50 49 48 47 46 45 44 43 42 41 40 39 38 37 36 35 34 33 32 31 30 29 28
     27 26 25 24 23 22 21 20 19 18 17 16 15 14 13 12 11 10  9  8  7  6  5  4
      3  2  1  0]
    ['High Net Worth' 'Mass Customer' 'Affluent Customer']
    ['Dental Hygienist' 'Computer Systems Analyst II'
     'Administrative Assistant IV' 'VP Marketing' 'Safety Technician III'
     'Programmer III' 'Actuary' 'Product Engineer' 'Accountant I'
     'Internal Auditor' 'Cost Accountant' 'Programmer Analyst III'
     'Accounting Assistant IV' 'Librarian' 'Sales Associate'
     'Account Executive' 'Account Representative I' 'Junior Executive'
     'General Manager' 'Financial Analyst' 'Developer III'
     'Database Administrator I' 'Help Desk Technician' 'Not Specified'
     'Assistant Professor' 'Database Administrator IV'
     'Desktop Support Technician' 'Compensation Analyst'
     'Accounting Assistant II' 'Editor' 'Speech Pathologist'
     'Clinical Specialist' 'Tax Accountant' 'Geologist III' 'Registered Nurse'
     'Paralegal' 'Chief Design Engineer' 'Data Coordiator'
     'Automation Specialist IV' 'Structural Analysis Engineer'
     'Information Systems Manager' 'Recruiting Manager' 'Technical Writer'
     'Geological Engineer' 'Software Consultant' 'Quality Control Specialist'
     'Recruiter' 'Statistician III' 'Computer Systems Analyst I'
     'Senior Sales Associate' 'Marketing Manager' 'Associate Professor'
     'Director of Sales' 'Community Outreach Specialist' 'Senior Editor'
     'Budget/Accounting Analyst IV' 'VP Quality Control' 'Senior Developer'
     'Systems Administrator III' 'Statistician I' 'Electrical Engineer'
     'Chemical Engineer' 'Legal Assistant' 'Structural Engineer'
     'Software Test Engineer III' 'Financial Advisor' 'Nurse' 'Food Chemist'
     'Systems Administrator IV' 'Graphic Designer' 'Help Desk Operator'
     'Research Nurse' 'Database Administrator II' 'Civil Engineer'
     'Nuclear Power Engineer' 'Payment Adjustment Coordinator'
     'Health Coach II' 'VP Accounting' 'Executive Secretary'
     'Research Associate' 'GIS Technical Architect' 'Nurse Practicioner'
     'Systems Administrator II' 'Geologist I'
     'Business Systems Development Analyst' 'Social Worker'
     'Programmer Analyst II' 'Physical Therapy Assistant' 'Operator'
     'Software Test Engineer IV' 'Programmer IV' 'Quality Engineer'
     'Health Coach IV' 'Biostatistician II' 'Accountant IV'
     'Database Administrator III' 'Analyst Programmer' 'Software Engineer II'
     'Staff Accountant II' 'Environmental Tech' 'Automation Specialist I'
     'Account Representative IV' 'Pharmacist' 'Sales Representative'
     'Staff Scientist' 'Human Resources Assistant II'
     'Computer Systems Analyst IV' 'Safety Technician II'
     'Senior Cost Accountant' 'VP Product Management' 'Professor'
     'Web Developer III' 'Assistant Manager' 'Environmental Specialist'
     'Teacher' 'Design Engineer' 'Project Manager' 'VP Sales'
     'Office Assistant III' 'Accounting Assistant III' 'Statistician II'
     'Programmer II' 'Accountant III' 'Web Designer IV' 'Developer IV'
     'Safety Technician I' 'BAI' 'Human Resources Assistant I'
     'Senior Financial Analyst' 'Accountant II' 'Mechanical Systems Engineer'
     'Administrative Officer' 'Office Assistant I' 'Marketing Assistant'
     'Software Test Engineer II' 'Senior Quality Engineer'
     'Research Assistant III' 'Programmer I' 'Geologist IV'
     'Human Resources Manager' 'BAII' 'Analog Circuit Design manager'
     'Account Coordinator' 'Web Developer IV' 'Web Designer III'
     'Assistant Media Planner' 'Software Engineer III'
     'Administrative Assistant II' 'Geologist II' 'Accounting Assistant I'
     'Biostatistician I' 'Automation Specialist III' 'Occupational Therapist'
     'Web Designer I' 'Statistician IV' 'Account Representative III'
     'Engineer II' 'Biostatistician III' 'Staff Accountant IV'
     'Staff Accountant III' 'Administrative Assistant I'
     'Research Assistant II' 'Software Test Engineer I'
     'Account Representative II' 'Research Assistant I' 'Developer II'
     'Administrative Assistant III' 'Safety Technician IV' 'Engineer IV'
     'Programmer Analyst I' 'Programmer Analyst IV' 'Engineer I'
     'Media Manager IV' 'Software Engineer IV' 'Automation Specialist II'
     'Media Manager II' 'Office Assistant IV' 'Biostatistician IV'
     'Office Assistant II' 'Web Developer II' 'Systems Administrator I'
     'Web Developer I' 'Computer Systems Analyst III' 'Software Engineer I'
     'Engineer III' 'Web Designer II' 'Media Manager I' 'Media Manager III'
     'Human Resources Assistant IV' 'Human Resources Assistant III'
     'Staff Accountant I' 'Health Coach I' 'Health Coach III'
     'Research Assistant IV' 'BAIII' 'Developer I']
    ['N' 'Y']
    ['No' 'Yes']
    ['Health' 'Entertainment' 'Financial Services' 'Retail' 'Not Specified'
     'Manufacturing' 'IT' 'Property' 'Argiculture' 'Telecommunications']
    ['VIC' 'NSW' 'QLD']
    [48.0 34.0 31.0 50.0 64.0 42.0 39.0 30.0 46.0 35.0 62.0 60.0 23.0 45.0
     61.0 47.0 21.0 43.0 27.0 58.0 53.0 40.0 22.0 66.0 41.0 18.0 33.0 49.0
     24.0 38.0 28.0 54.0 36.0 59.0 57.0 20.0 44.0 26.0 55.0 65.0 29.0 37.0
     25.0 32.0 56.0 52.0 51.0 63.0 19.0 79.0 88.0 84.0 76.0]
    [ 4 10  9  3  8  7  6  5 12 11  1  2]
    [10.0 18.0 12.0 20.0 9.0 7.0 16.0 5.0 8.0 14.0 15.0 1.0 17.0 21.0 3.0 22.0
     11.0 19.0 4.0 2.0 13.0 6.0]
    [1 0]
    


```python
datasub=data_sort[label]
print(datasub['deceased_indicator'].unique())
datasub.loc[:,'deceased_indicator']=datasub.loc[:,'deceased_indicator'].astype(str)
print(data_sort.columns)
label1=['gender','wealth_segment','deceased_indicator','state','owns_car','job_industry_category','job_title']
from sklearn.preprocessing import LabelEncoder
lc=LabelEncoder()
for i in label1:
   print(i)
   datasub.loc[:,i]=datasub.loc[:,i].str.strip()
   datasub.loc[:,i]=lc.fit_transform(datasub.loc[:,i])


```

    ['N' 'Y']
    Index([                        'customer_id',
                                    'first_name',
                                     'last_name',
                                        'gender',
           'past_3_years_bike_related_purchases',
                                           'DOB',
                                     'job_title',
                         'job_industry_category',
                                'wealth_segment',
                            'deceased_indicator',
                                       'default',
                                      'owns_car',
                                        'tenure',
                                       'address',
                                      'postcode',
                                         'state',
                                       'country',
                            'property_valuation',
                                           'Age',
                                 'Buying_chance',
                          (305, 'Buying_chance'),
                         (1937, 'Buying_chance'),
                         (2065, 'Buying_chance'),
                         (2715, 'Buying_chance'),
                         (2707, 'Buying_chance'),
                          (470, 'Buying_chance'),
                         (3544, 'Buying_chance'),
                         (3971, 'Buying_chance'),
                         (2675, 'Buying_chance'),
                          (481, 'Buying_chance'),
                          (924, 'Buying_chance'),
                         (3242, 'Buying_chance'),
                         (1524, 'Buying_chance'),
                         (1349, 'Buying_chance'),
                         (2546, 'Buying_chance'),
                          (274, 'Buying_chance'),
                         (1041, 'Buying_chance'),
                         (1037, 'Buying_chance'),
                         (2406, 'Buying_chance'),
                         (2915, 'Buying_chance'),
                         (1011, 'Buying_chance'),
                         (2355, 'Buying_chance'),
                          (976, 'Buying_chance'),
                         (3641, 'Buying_chance'),
                         (2800, 'Buying_chance'),
                          (455, 'Buying_chance'),
                         (2234, 'Buying_chance'),
                         (2231, 'Buying_chance'),
                         (3838, 'Buying_chance'),
                         (1295, 'Buying_chance'),
                         (1190, 'Buying_chance'),
                          (567, 'Buying_chance'),
                         (3138, 'Buying_chance'),
                          (423, 'Buying_chance'),
                         (1286, 'Buying_chance'),
                         (2772, 'Buying_chance'),
                         (1209, 'Buying_chance'),
                          (597, 'Buying_chance'),
                         (3785, 'Buying_chance'),
                          (748, 'Buying_chance')],
          dtype='object')
    gender
    wealth_segment
    deceased_indicator
    state
    owns_car
    job_industry_category
    job_title
    

    C:\Users\subha\anaconda3\lib\site-packages\pandas\core\indexing.py:965: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      self.obj[item] = s
    


```python
datasub.head(20)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>gender</th>
      <th>past_3_years_bike_related_purchases</th>
      <th>wealth_segment</th>
      <th>job_title</th>
      <th>deceased_indicator</th>
      <th>owns_car</th>
      <th>job_industry_category</th>
      <th>state</th>
      <th>Age</th>
      <th>property_valuation</th>
      <th>tenure</th>
      <th>Buying_chance</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3773</th>
      <td>1</td>
      <td>99</td>
      <td>1</td>
      <td>55</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
      <td>2</td>
      <td>48</td>
      <td>4</td>
      <td>10</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3342</th>
      <td>1</td>
      <td>99</td>
      <td>1</td>
      <td>46</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>2</td>
      <td>34</td>
      <td>10</td>
      <td>18</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1093</th>
      <td>0</td>
      <td>99</td>
      <td>2</td>
      <td>18</td>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>0</td>
      <td>31</td>
      <td>9</td>
      <td>12</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2059</th>
      <td>1</td>
      <td>99</td>
      <td>2</td>
      <td>184</td>
      <td>0</td>
      <td>1</td>
      <td>3</td>
      <td>1</td>
      <td>50</td>
      <td>3</td>
      <td>18</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1447</th>
      <td>1</td>
      <td>99</td>
      <td>2</td>
      <td>144</td>
      <td>0</td>
      <td>0</td>
      <td>8</td>
      <td>0</td>
      <td>64</td>
      <td>8</td>
      <td>20</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3873</th>
      <td>1</td>
      <td>99</td>
      <td>2</td>
      <td>128</td>
      <td>0</td>
      <td>0</td>
      <td>6</td>
      <td>2</td>
      <td>42</td>
      <td>9</td>
      <td>9</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1127</th>
      <td>0</td>
      <td>99</td>
      <td>0</td>
      <td>14</td>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>2</td>
      <td>34</td>
      <td>7</td>
      <td>9</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3655</th>
      <td>1</td>
      <td>99</td>
      <td>2</td>
      <td>18</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>0</td>
      <td>39</td>
      <td>10</td>
      <td>7</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2467</th>
      <td>1</td>
      <td>99</td>
      <td>1</td>
      <td>120</td>
      <td>0</td>
      <td>1</td>
      <td>3</td>
      <td>2</td>
      <td>30</td>
      <td>7</td>
      <td>16</td>
      <td>1</td>
    </tr>
    <tr>
      <th>222</th>
      <td>1</td>
      <td>99</td>
      <td>2</td>
      <td>6</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>46</td>
      <td>9</td>
      <td>18</td>
      <td>1</td>
    </tr>
    <tr>
      <th>153</th>
      <td>1</td>
      <td>99</td>
      <td>0</td>
      <td>95</td>
      <td>0</td>
      <td>0</td>
      <td>6</td>
      <td>0</td>
      <td>35</td>
      <td>6</td>
      <td>5</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2397</th>
      <td>0</td>
      <td>99</td>
      <td>2</td>
      <td>49</td>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>0</td>
      <td>62</td>
      <td>7</td>
      <td>8</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1277</th>
      <td>1</td>
      <td>99</td>
      <td>0</td>
      <td>124</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>39</td>
      <td>5</td>
      <td>14</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2052</th>
      <td>0</td>
      <td>99</td>
      <td>0</td>
      <td>13</td>
      <td>0</td>
      <td>1</td>
      <td>5</td>
      <td>2</td>
      <td>60</td>
      <td>8</td>
      <td>15</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3810</th>
      <td>1</td>
      <td>99</td>
      <td>2</td>
      <td>98</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>2</td>
      <td>39</td>
      <td>5</td>
      <td>5</td>
      <td>1</td>
    </tr>
    <tr>
      <th>376</th>
      <td>0</td>
      <td>99</td>
      <td>0</td>
      <td>146</td>
      <td>0</td>
      <td>0</td>
      <td>6</td>
      <td>0</td>
      <td>23</td>
      <td>12</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2176</th>
      <td>1</td>
      <td>99</td>
      <td>2</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>4</td>
      <td>0</td>
      <td>45</td>
      <td>11</td>
      <td>8</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2349</th>
      <td>0</td>
      <td>99</td>
      <td>2</td>
      <td>120</td>
      <td>0</td>
      <td>0</td>
      <td>8</td>
      <td>2</td>
      <td>61</td>
      <td>8</td>
      <td>17</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3318</th>
      <td>1</td>
      <td>99</td>
      <td>1</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
      <td>1</td>
      <td>47</td>
      <td>7</td>
      <td>8</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1359</th>
      <td>1</td>
      <td>99</td>
      <td>2</td>
      <td>96</td>
      <td>0</td>
      <td>0</td>
      <td>5</td>
      <td>2</td>
      <td>42</td>
      <td>6</td>
      <td>21</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
from sklearn.feature_selection import chi2
y = datasub['Buying_chance']
x = datasub.drop('Buying_chance',axis=1)
```


```python
chi_score=chi2(x,y)
```


```python
print(chi_score)
```

    (array([2.01976692e-01, 4.60494875e+02, 9.09301032e-02, 4.31079480e+02,
           1.07306552e-01, 2.00084033e-01, 1.30160185e+00, 8.18333051e-01,
           1.70799370e+03, 1.01407121e-01, 1.64528915e+01]), array([6.53130026e-001, 3.75144079e-102, 7.62998035e-001, 9.46106603e-096,
           7.43231675e-001, 6.54653026e-001, 2.53920834e-001, 3.65667994e-001,
           0.00000000e+000, 7.50147524e-001, 4.98740537e-005]))
    


```python

p_values = pd.Series(chi_score[1],index = x.columns)
p_values.sort_values(ascending = False , inplace = True)
p_values.plot.bar()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x19e0fa1c088>




![png](output_40_1.png)



```python
data2.info()
data_feat=datasub.loc[:,['past_3_years_bike_related_purchases','Buying_chance','job_title','tenure','Age']]
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 1000 entries, 0 to 999
    Data columns (total 24 columns):
     #   Column                               Non-Null Count  Dtype         
    ---  ------                               --------------  -----         
     0   first_name                           1000 non-null   object        
     1   last_name                            971 non-null    object        
     2   gender                               1000 non-null   object        
     3   past_3_years_bike_related_purchases  1000 non-null   int64         
     4   DOB                                  983 non-null    datetime64[ns]
     5   job_title                            894 non-null    object        
     6   job_industry_category                835 non-null    object        
     7   wealth_segment                       1000 non-null   object        
     8   deceased_indicator                   1000 non-null   object        
     9   owns_car                             1000 non-null   object        
     10  tenure                               1000 non-null   int64         
     11  address                              1000 non-null   object        
     12  postcode                             1000 non-null   int64         
     13  state                                1000 non-null   object        
     14  country                              1000 non-null   object        
     15  property_valuation                   1000 non-null   int64         
     16  Unnamed: 16                          1000 non-null   float64       
     17  Unnamed: 17                          1000 non-null   float64       
     18  Unnamed: 18                          1000 non-null   float64       
     19  Unnamed: 19                          1000 non-null   float64       
     20  Unnamed: 20                          1000 non-null   int64         
     21  Rank                                 1000 non-null   int64         
     22  Value                                1000 non-null   float64       
     23  Age                                  983 non-null    float64       
    dtypes: datetime64[ns](1), float64(6), int64(6), object(11)
    memory usage: 187.6+ KB
    


```python
label2=['job_title','tenure','Age','past_3_years_bike_related_purchases']
for i in label2:
    nullid=data2[data2[i].isna()].index
    for j in nullid:
      data2.loc[j,i]="Not Specified"
data_newcust=data2.loc[:,['first_name','last_name','job_title','tenure','Age','past_3_years_bike_related_purchases']]

```


```python
data_newcust.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 1000 entries, 0 to 999
    Data columns (total 6 columns):
     #   Column                               Non-Null Count  Dtype 
    ---  ------                               --------------  ----- 
     0   first_name                           1000 non-null   object
     1   last_name                            971 non-null    object
     2   job_title                            1000 non-null   object
     3   tenure                               1000 non-null   int64 
     4   Age                                  1000 non-null   object
     5   past_3_years_bike_related_purchases  1000 non-null   int64 
    dtypes: int64(2), object(4)
    memory usage: 47.0+ KB
    


```python
from sklearn.model_selection import train_test_split
y=data_feat['Buying_chance']
x=data_feat.drop('Buying_chance',axis=1)
X_train,X_valid,Y_train,Y_valid=train_test_split(x,y,test_size=0.25,random_state=0)
from sklearn.tree import DecisionTreeClassifier
dc=DecisionTreeClassifier()
dc.fit(X_train,Y_train)
y_pre=dc.predict(X_valid)

from sklearn.metrics import accuracy_score
print(accuracy_score(Y_valid,y_pre))
```

    1.0
    


```python
from sklearn.preprocessing import LabelEncoder
label3=['job_title']
lc=LabelEncoder()
for i in label3:
   print(i)
   data_newcust.loc[:,i]=data_newcust.loc[:,i].str.strip()
   data_newcust.loc[:,i]=lc.fit_transform(data_newcust.loc[:,i])

```

    job_title
    


```python

ind=data_newcust[data_newcust['Age']=="Not Specified"].index
data_newcust.drop(ind,axis=0,inplace=True)
dp=data_newcust
dr=data_newcust.drop(['first_name','last_name'],axis=1)
y_pred_t=dc.predict(dr)
data_newcust=dr.assign(buy=y_pred_t)
data_newcust.info()
final=data_newcust.loc[data_newcust['buy']==1].index
f_name=[]
l_name=[]
for i in final:
  if ((isinstance(dp.loc[i,'first_name'],str))& (isinstance(dp.loc[i,'last_name'],str))):
    
       fullname=dp.loc[i,'first_name']+" "+dp.loc[i,'last_name']
  f_name.append(fullname)
  
testcsv=pd.DataFrame(f_name)
testcsv.to_csv('Potential_Customers_List.csv',index=False)


```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 983 entries, 0 to 999
    Data columns (total 5 columns):
     #   Column                               Non-Null Count  Dtype 
    ---  ------                               --------------  ----- 
     0   job_title                            983 non-null    int32 
     1   tenure                               983 non-null    int64 
     2   Age                                  983 non-null    object
     3   past_3_years_bike_related_purchases  983 non-null    int64 
     4   buy                                  983 non-null    int64 
    dtypes: int32(1), int64(3), object(1)
    memory usage: 42.2+ KB
    


```python
len(final)
```




    634




```python

```
