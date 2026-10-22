```python

import pandas as pd
import numpy as np

```

```python
import pandas as pd

base = r"C:\Users\USER\OneDrive\Desktop\RetailPulse_Synthetic_Dataset" 
customers = pd.read_csv(r"C:\Users\USER\OneDrive\Desktop\RetailPulse_Synthetic_Dataset\customers.csv")
daily_demand = pd.read_csv(r"C:\Users\USER\OneDrive\Desktop\RetailPulse_Synthetic_Dataset\daily_demand.csv")
products = pd.read_csv(r"C:\Users\USER\OneDrive\Desktop\RetailPulse_Synthetic_Dataset\products.csv")
sales_transactions = pd.read_csv(r"C:\Users\USER\OneDrive\Desktop\RetailPulse_Synthetic_Dataset\sales_transactions.csv")
```

```python
customers = pd.read_csv(base + r"\customers.csv")
print("customers ok", customers.shape)
```

```text
customers ok (500, 7)
```

```python
products = pd.read_csv(base + r"\products.csv")
print("products ok", products.shape)
```

```text
products ok (25, 6)
```

```python
daily_demand = pd.read_csv(base + r"\daily_demand.csv")
print("daily_demand ok", daily_demand.shape)
```

```text
daily_demand ok (9125, 7)
```

```python
sales = pd.read_csv(base + r"\sales_transactions.csv")
print("sales ok", sales.shape)
```

```text
sales ok (8000, 11)
```

```python
tables = {"customers": customers, "products": products,
          "sales": sales, "daily_demand": daily_demand}

for name, d in tables.items():
    print("=====", name, d.shape)
    print(d.columns.tolist(), "\n")
```

```text
===== customers (500, 7)
['customer_id', 'age', 'city', 'signup_date', 'preferred_channel', 'loyalty_points', 'customer_segment'] 

===== products (25, 6)
['product_id', 'product_name', 'category', 'unit_price_inr', 'unit_cost_inr', 'reorder_level'] 

===== sales (8000, 11)
['transaction_id', 'date', 'customer_id', 'product_id', 'store_id', 'quantity', 'unit_price_inr', 'discount_pct', 'sales_amount_inr', 'payment_method', 'sales_channel'] 

===== daily_demand (9125, 7)
['date', 'product_id', 'store_id', 'units_sold', 'promotion_active', 'price_inr', 'holiday_or_festival_period'] 
```

```python
#Shape, Information, 1st 3 rows

tables = {"customers": customers, "products": products,
          "sales": sales, "daily_demand": daily_demand}

for name, d in tables.items():
    print("=====", name, d.shape)
    d.info()
    print(d.head(3), "\n")
```

```text
===== customers (500, 7)
<class 'pandas.DataFrame'>
RangeIndex: 500 entries, 0 to 499
Data columns (total 7 columns):
 #   Column             Non-Null Count  Dtype
---  ------             --------------  -----
 0   customer_id        500 non-null    str  
 1   age                500 non-null    int64
 2   city               500 non-null    str  
 3   signup_date        500 non-null    str  
 4   preferred_channel  500 non-null    str  
 5   loyalty_points     500 non-null    int64
 6   customer_segment   500 non-null    str  
dtypes: int64(2), str(5)
memory usage: 27.5 KB
  customer_id  age         city signup_date preferred_channel  loyalty_points  \
0       C0001   52       Nashik  2024-01-27        Mobile App             500   
1       C0002   45   Aurangabad  2023-02-10        Mobile App             200   
2       C0003   40  Navi Mumbai  2023-02-17             Store             100   

  customer_segment  
0          At Risk  
1          Regular  
2          Regular   

===== products (25, 6)
<class 'pandas.DataFrame'>
RangeIndex: 25 entries, 0 to 24
Data columns (total 6 columns):
 #   Column          Non-Null Count  Dtype  
---  ------          --------------  -----  
 0   product_id      25 non-null     str    
 1   product_name    25 non-null     str    
 2   category        25 non-null     str    
 3   unit_price_inr  25 non-null     float64
 4   unit_cost_inr   25 non-null     float64
 5   reorder_level   25 non-null     int64  
dtypes: float64(2), int64(1), str(3)
memory usage: 1.3 KB
  product_id    product_name category  unit_price_inr  unit_cost_inr  \
0      P1001        Rice 5kg  Grocery          268.47         205.97   
1      P1002  Cooking Oil 1L  Grocery          405.18         227.13   
2      P1003         Milk 1L  Grocery          100.98          64.57   

   reorder_level  
0             17  
1             28  
2             45   

===== sales (8000, 11)
<class 'pandas.DataFrame'>
RangeIndex: 8000 entries, 0 to 7999
Data columns (total 11 columns):
 #   Column            Non-Null Count  Dtype  
---  ------            --------------  -----  
 0   transaction_id    8000 non-null   str    
 1   date              8000 non-null   str    
 2   customer_id       8000 non-null   str    
 3   product_id        8000 non-null   str    
 4   store_id          8000 non-null   str    
 5   quantity          8000 non-null   int64  
 6   unit_price_inr    8000 non-null   float64
 7   discount_pct      8000 non-null   float64
 8   sales_amount_inr  8000 non-null   float64
 9   payment_method    8000 non-null   str    
 10  sales_channel     8000 non-null   str    
dtypes: float64(3), int64(1), str(7)
memory usage: 687.6 KB
  transaction_id        date customer_id product_id store_id  quantity  \
0        T000001  2025-07-10       C0303      P1003     ST02         2   
1        T000002  2025-11-09       C0142      P1021     ST04         1   
2        T000003  2025-12-21       C0225      P1013     ST02         3   

   unit_price_inr  discount_pct  sales_amount_inr payment_method sales_channel  
0          100.98           0.0            201.96            UPI         Store  
1         1873.52           5.0           1779.84           Cash    Mobile App  
2          846.34           0.0           2539.02     Debit Card       Website   

===== daily_demand (9125, 7)
<class 'pandas.DataFrame'>
RangeIndex: 9125 entries, 0 to 9124
Data columns (total 7 columns):
 #   Column                      Non-Null Count  Dtype  
---  ------                      --------------  -----  
 0   date                        9125 non-null   str    
 1   product_id                  9125 non-null   str    
 2   store_id                    9125 non-null   str    
 3   units_sold                  9125 non-null   int64  
 4   promotion_active            9125 non-null   int64  
 5   price_inr                   9125 non-null   float64
 6   holiday_or_festival_period  9125 non-null   int64  
dtypes: float64(1), int64(3), str(3)
memory usage: 499.2 KB
         date product_id store_id  units_sold  promotion_active  price_inr  \
0  2025-01-01      P1001     ST03           8                 0     268.47   
1  2025-01-02      P1001     ST02           5                 0     268.47   
2  2025-01-03      P1001     ST04          10                 0     268.47   

   holiday_or_festival_period  
0                           0  
1                           0  
2                           0   
```

```python
customers.info()
customers.head()
```

```text
<class 'pandas.DataFrame'>
RangeIndex: 500 entries, 0 to 499
Data columns (total 7 columns):
 #   Column             Non-Null Count  Dtype
---  ------             --------------  -----
 0   customer_id        500 non-null    str  
 1   age                500 non-null    int64
 2   city               500 non-null    str  
 3   signup_date        500 non-null    str  
 4   preferred_channel  500 non-null    str  
 5   loyalty_points     500 non-null    int64
 6   customer_segment   500 non-null    str  
dtypes: int64(2), str(5)
memory usage: 27.5 KB
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }
&#10;    .dataframe tbody tr th {
        vertical-align: top;
    }
&#10;    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>customer_id</th>
      <th>age</th>
      <th>city</th>
      <th>signup_date</th>
      <th>preferred_channel</th>
      <th>loyalty_points</th>
      <th>customer_segment</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>C0001</td>
      <td>52</td>
      <td>Nashik</td>
      <td>2024-01-27</td>
      <td>Mobile App</td>
      <td>500</td>
      <td>At Risk</td>
    </tr>
    <tr>
      <th>1</th>
      <td>C0002</td>
      <td>45</td>
      <td>Aurangabad</td>
      <td>2023-02-10</td>
      <td>Mobile App</td>
      <td>200</td>
      <td>Regular</td>
    </tr>
    <tr>
      <th>2</th>
      <td>C0003</td>
      <td>40</td>
      <td>Navi Mumbai</td>
      <td>2023-02-17</td>
      <td>Store</td>
      <td>100</td>
      <td>Regular</td>
    </tr>
    <tr>
      <th>3</th>
      <td>C0004</td>
      <td>44</td>
      <td>Nashik</td>
      <td>2024-12-26</td>
      <td>Store</td>
      <td>500</td>
      <td>At Risk</td>
    </tr>
    <tr>
      <th>4</th>
      <td>C0005</td>
      <td>18</td>
      <td>Thane</td>
      <td>2024-10-04</td>
      <td>Website</td>
      <td>1500</td>
      <td>Regular</td>
    </tr>
  </tbody>
</table>
</div>

```text
  customer_id  age         city signup_date preferred_channel  loyalty_points  \
0       C0001   52       Nashik  2024-01-27        Mobile App             500   
1       C0002   45   Aurangabad  2023-02-10        Mobile App             200   
2       C0003   40  Navi Mumbai  2023-02-17             Store             100   
3       C0004   44       Nashik  2024-12-26             Store             500   
4       C0005   18        Thane  2024-10-04           Website            1500   

  customer_segment  
0          At Risk  
1          Regular  
2          Regular  
3          At Risk  
4          Regular  
```

```python
products.info()
products.head()
```

```text
<class 'pandas.DataFrame'>
RangeIndex: 25 entries, 0 to 24
Data columns (total 6 columns):
 #   Column          Non-Null Count  Dtype  
---  ------          --------------  -----  
 0   product_id      25 non-null     str    
 1   product_name    25 non-null     str    
 2   category        25 non-null     str    
 3   unit_price_inr  25 non-null     float64
 4   unit_cost_inr   25 non-null     float64
 5   reorder_level   25 non-null     int64  
dtypes: float64(2), int64(1), str(3)
memory usage: 1.3 KB
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }
&#10;    .dataframe tbody tr th {
        vertical-align: top;
    }
&#10;    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>product_id</th>
      <th>product_name</th>
      <th>category</th>
      <th>unit_price_inr</th>
      <th>unit_cost_inr</th>
      <th>reorder_level</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>P1001</td>
      <td>Rice 5kg</td>
      <td>Grocery</td>
      <td>268.47</td>
      <td>205.97</td>
      <td>17</td>
    </tr>
    <tr>
      <th>1</th>
      <td>P1002</td>
      <td>Cooking Oil 1L</td>
      <td>Grocery</td>
      <td>405.18</td>
      <td>227.13</td>
      <td>28</td>
    </tr>
    <tr>
      <th>2</th>
      <td>P1003</td>
      <td>Milk 1L</td>
      <td>Grocery</td>
      <td>100.98</td>
      <td>64.57</td>
      <td>45</td>
    </tr>
    <tr>
      <th>3</th>
      <td>P1004</td>
      <td>Coffee 200g</td>
      <td>Grocery</td>
      <td>127.15</td>
      <td>87.64</td>
      <td>11</td>
    </tr>
    <tr>
      <th>4</th>
      <td>P1005</td>
      <td>Breakfast Cereal</td>
      <td>Grocery</td>
      <td>480.42</td>
      <td>367.05</td>
      <td>11</td>
    </tr>
  </tbody>
</table>
</div>

```text
  product_id      product_name category  unit_price_inr  unit_cost_inr  \
0      P1001          Rice 5kg  Grocery          268.47         205.97   
1      P1002    Cooking Oil 1L  Grocery          405.18         227.13   
2      P1003           Milk 1L  Grocery          100.98          64.57   
3      P1004       Coffee 200g  Grocery          127.15          87.64   
4      P1005  Breakfast Cereal  Grocery          480.42         367.05   

   reorder_level  
0             17  
1             28  
2             45  
3             11  
4             11  
```

```python
sales.info()
sales.head()
```

```text
<class 'pandas.DataFrame'>
RangeIndex: 8000 entries, 0 to 7999
Data columns (total 11 columns):
 #   Column            Non-Null Count  Dtype  
---  ------            --------------  -----  
 0   transaction_id    8000 non-null   str    
 1   date              8000 non-null   str    
 2   customer_id       8000 non-null   str    
 3   product_id        8000 non-null   str    
 4   store_id          8000 non-null   str    
 5   quantity          8000 non-null   int64  
 6   unit_price_inr    8000 non-null   float64
 7   discount_pct      8000 non-null   float64
 8   sales_amount_inr  8000 non-null   float64
 9   payment_method    8000 non-null   str    
 10  sales_channel     8000 non-null   str    
dtypes: float64(3), int64(1), str(7)
memory usage: 687.6 KB
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }
&#10;    .dataframe tbody tr th {
        vertical-align: top;
    }
&#10;    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>transaction_id</th>
      <th>date</th>
      <th>customer_id</th>
      <th>product_id</th>
      <th>store_id</th>
      <th>quantity</th>
      <th>unit_price_inr</th>
      <th>discount_pct</th>
      <th>sales_amount_inr</th>
      <th>payment_method</th>
      <th>sales_channel</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>T000001</td>
      <td>2025-07-10</td>
      <td>C0303</td>
      <td>P1003</td>
      <td>ST02</td>
      <td>2</td>
      <td>100.98</td>
      <td>0.0</td>
      <td>201.96</td>
      <td>UPI</td>
      <td>Store</td>
    </tr>
    <tr>
      <th>1</th>
      <td>T000002</td>
      <td>2025-11-09</td>
      <td>C0142</td>
      <td>P1021</td>
      <td>ST04</td>
      <td>1</td>
      <td>1873.52</td>
      <td>5.0</td>
      <td>1779.84</td>
      <td>Cash</td>
      <td>Mobile App</td>
    </tr>
    <tr>
      <th>2</th>
      <td>T000003</td>
      <td>2025-12-21</td>
      <td>C0225</td>
      <td>P1013</td>
      <td>ST02</td>
      <td>3</td>
      <td>846.34</td>
      <td>0.0</td>
      <td>2539.02</td>
      <td>Debit Card</td>
      <td>Website</td>
    </tr>
    <tr>
      <th>3</th>
      <td>T000004</td>
      <td>2025-04-01</td>
      <td>C0142</td>
      <td>P1002</td>
      <td>ST04</td>
      <td>1</td>
      <td>405.18</td>
      <td>15.0</td>
      <td>344.40</td>
      <td>UPI</td>
      <td>Store</td>
    </tr>
    <tr>
      <th>4</th>
      <td>T000005</td>
      <td>2025-05-27</td>
      <td>C0281</td>
      <td>P1014</td>
      <td>ST04</td>
      <td>1</td>
      <td>763.20</td>
      <td>0.0</td>
      <td>763.20</td>
      <td>Debit Card</td>
      <td>Mobile App</td>
    </tr>
  </tbody>
</table>
</div>

```text
  transaction_id        date customer_id product_id store_id  quantity  \
0        T000001  2025-07-10       C0303      P1003     ST02         2   
1        T000002  2025-11-09       C0142      P1021     ST04         1   
2        T000003  2025-12-21       C0225      P1013     ST02         3   
3        T000004  2025-04-01       C0142      P1002     ST04         1   
4        T000005  2025-05-27       C0281      P1014     ST04         1   

   unit_price_inr  discount_pct  sales_amount_inr payment_method sales_channel  
0          100.98           0.0            201.96            UPI         Store  
1         1873.52           5.0           1779.84           Cash    Mobile App  
2          846.34           0.0           2539.02     Debit Card       Website  
3          405.18          15.0            344.40            UPI         Store  
4          763.20           0.0            763.20     Debit Card    Mobile App  
```

```python
daily_demand.info()
daily_demand.head()
```

```text
<class 'pandas.DataFrame'>
RangeIndex: 9125 entries, 0 to 9124
Data columns (total 7 columns):
 #   Column                      Non-Null Count  Dtype  
---  ------                      --------------  -----  
 0   date                        9125 non-null   str    
 1   product_id                  9125 non-null   str    
 2   store_id                    9125 non-null   str    
 3   units_sold                  9125 non-null   int64  
 4   promotion_active            9125 non-null   int64  
 5   price_inr                   9125 non-null   float64
 6   holiday_or_festival_period  9125 non-null   int64  
dtypes: float64(1), int64(3), str(3)
memory usage: 499.2 KB
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }
&#10;    .dataframe tbody tr th {
        vertical-align: top;
    }
&#10;    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>date</th>
      <th>product_id</th>
      <th>store_id</th>
      <th>units_sold</th>
      <th>promotion_active</th>
      <th>price_inr</th>
      <th>holiday_or_festival_period</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2025-01-01</td>
      <td>P1001</td>
      <td>ST03</td>
      <td>8</td>
      <td>0</td>
      <td>268.47</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2025-01-02</td>
      <td>P1001</td>
      <td>ST02</td>
      <td>5</td>
      <td>0</td>
      <td>268.47</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2025-01-03</td>
      <td>P1001</td>
      <td>ST04</td>
      <td>10</td>
      <td>0</td>
      <td>268.47</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2025-01-04</td>
      <td>P1001</td>
      <td>ST02</td>
      <td>10</td>
      <td>0</td>
      <td>268.47</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2025-01-05</td>
      <td>P1001</td>
      <td>ST01</td>
      <td>11</td>
      <td>0</td>
      <td>268.47</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>

```text
         date product_id store_id  units_sold  promotion_active  price_inr  \
0  2025-01-01      P1001     ST03           8                 0     268.47   
1  2025-01-02      P1001     ST02           5                 0     268.47   
2  2025-01-03      P1001     ST04          10                 0     268.47   
3  2025-01-04      P1001     ST02          10                 0     268.47   
4  2025-01-05      P1001     ST01          11                 0     268.47   

   holiday_or_festival_period  
0                           0  
1                           0  
2                           0  
3                           0  
4                           0  
```

```python
#Finding Null values

print(customers.isnull().sum())
```

```text
customer_id          0
age                  0
city                 0
signup_date          0
preferred_channel    0
loyalty_points       0
customer_segment     0
dtype: int64
```

```python
print(products.isnull().sum())
```

```text
product_id        0
product_name      0
category          0
unit_price_inr    0
unit_cost_inr     0
reorder_level     0
dtype: int64
```

```python
print(sales.isnull().sum())
```

```text
transaction_id      0
date                0
customer_id         0
product_id          0
store_id            0
quantity            0
unit_price_inr      0
discount_pct        0
sales_amount_inr    0
payment_method      0
sales_channel       0
dtype: int64
```

```python
print(daily_demand.isnull().sum())
```

```text
date                          0
product_id                    0
store_id                      0
units_sold                    0
promotion_active              0
price_inr                     0
holiday_or_festival_period    0
dtype: int64
```

```python
#Deduplication

print(customers.duplicated().sum(), products.duplicated().sum(),
      sales.duplicated().sum(), daily_demand.duplicated().sum())

print(customers["customer_id"].duplicated().sum())
print(products["product_id"].duplicated().sum())
```

```text
0 0 0 0
0
0
```

```python
#Coloums 

print(sales.columns.tolist())
print(daily_demand.columns.tolist())
```

```text
['transaction_id', 'date', 'customer_id', 'product_id', 'store_id', 'quantity', 'unit_price_inr', 'discount_pct', 'sales_amount_inr', 'payment_method', 'sales_channel']
['date', 'product_id', 'store_id', 'units_sold', 'promotion_active', 'price_inr', 'holiday_or_festival_period']
```

```python


sales["date"] = pd.to_datetime(sales["date"], errors="coerce")
daily_demand["date"] = pd.to_datetime(daily_demand["date"], errors="coerce")

print(sales["date"].isnull().sum())
print(daily_demand["date"].isnull().sum())
print(sales["date"].dtype, daily_demand["date"].dtype)
```

```text
0
0
datetime64[us] datetime64[us]
```

```python
#Duration
print(sales["date"].min(), sales["date"].max())
print(daily_demand["date"].min(), daily_demand["date"].max())
```

```text
2025-01-01 00:00:00 2025-12-31 00:00:00
2025-01-01 00:00:00 2025-12-31 00:00:00
```

```python
#To see a every value in another coloum list.

print((~sales["customer_id"].isin(customers["customer_id"])).sum())
print((~sales["product_id"].isin(products["product_id"])).sum())
print((~daily_demand["product_id"].isin(products["product_id"])).sum())
```

```text
0
0
0
```

```python
print(sales.columns.tolist())
print(products.columns.tolist())
```

```text
['transaction_id', 'date', 'customer_id', 'product_id', 'store_id', 'quantity', 'unit_price_inr', 'discount_pct', 'sales_amount_inr', 'payment_method', 'sales_channel']
['product_id', 'product_name', 'category', 'unit_price_inr', 'unit_cost_inr', 'reorder_level']
```

```python
#Data Frame
df = (sales.merge(customers, on="customer_id", how="left") 
          .merge(products, on="product_id", how="left"))

print(sales.shape, df.shape)
print(df.isnull().sum().sum()) #sum of null value coloumwise and sum of it.
print(df.columns.tolist())
```

```text
(8000, 11) (8000, 22)
0
['transaction_id', 'date', 'customer_id', 'product_id', 'store_id', 'quantity', 'unit_price_inr_x', 'discount_pct', 'sales_amount_inr', 'payment_method', 'sales_channel', 'age', 'city', 'signup_date', 'preferred_channel', 'loyalty_points', 'customer_segment', 'product_name', 'category', 'unit_price_inr_y', 'unit_cost_inr', 'reorder_level']
```

```python
print((df["unit_price_inr_x"] != df["unit_price_inr_y"]).sum())
         #Price during sale time    #current price
print(df[["quantity", "unit_price_inr_x", "discount_pct", "sales_amount_inr"]].head())
```

```text
0
   quantity  unit_price_inr_x  discount_pct  sales_amount_inr
0         2            100.98           0.0            201.96
1         1           1873.52           5.0           1779.84
2         3            846.34           0.0           2539.02
3         1            405.18          15.0            344.40
4         1            763.20           0.0            763.20
```

```python
df = df.drop(columns=["unit_price_inr_y"]).rename(columns={"unit_price_inr_x": "unit_price_inr"})

df["profit_inr"] = df["sales_amount_inr"] - (df["quantity"] * df["unit_cost_inr"])

print(df["profit_inr"].describe())
print((df["profit_inr"] < 0).sum())
df[["quantity", "unit_cost_inr", "sales_amount_inr", "profit_inr"]].head()
```

```text
count    8000.000000
mean      415.449617
std       519.415285
min         5.090000
25%        86.790000
50%       226.740000
75%       535.260000
max      4951.600000
Name: profit_inr, dtype: float64
0
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }
&#10;    .dataframe tbody tr th {
        vertical-align: top;
    }
&#10;    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>quantity</th>
      <th>unit_cost_inr</th>
      <th>sales_amount_inr</th>
      <th>profit_inr</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2</td>
      <td>64.57</td>
      <td>201.96</td>
      <td>72.82</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1338.26</td>
      <td>1779.84</td>
      <td>441.58</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>536.95</td>
      <td>2539.02</td>
      <td>928.17</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>227.13</td>
      <td>344.40</td>
      <td>117.27</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>562.20</td>
      <td>763.20</td>
      <td>201.00</td>
    </tr>
  </tbody>
</table>
</div>

```text
   quantity  unit_cost_inr  sales_amount_inr  profit_inr
0         2          64.57            201.96       72.82
1         1        1338.26           1779.84      441.58
2         3         536.95           2539.02      928.17
3         1         227.13            344.40      117.27
4         1         562.20            763.20      201.00
```

```python
df.to_csv("retailpulse_merged.csv", index=False)
daily_demand.to_csv("daily_demand_clean.csv", index=False)
```

```python
print(df.shape, "profit_inr" in df.columns)
```

```text
(8000, 22) True
```

```python
import os              #built in module which work for folders and files, here to check file 
print(os.path.exists("retailpulse_merged.csv"))
print(os.path.getsize("retailpulse_merged.csv"))
print(os.path.getsize("retailpulse_merged.csv") / 1024, "KB")

check = pd.read_csv("retailpulse_merged.csv")
print(check.shape)
print("profit_inr" in check.columns, "month" in check.columns)
```

```text
True
1277950
1247.998046875 KB
(8000, 22)
True False
```

```python
df.to_csv("retailpulse_merged.csv", index=False)

check = pd.read_csv("retailpulse_merged.csv")
print(check.shape, "month" in check.columns)
```

```text
(8000, 22) False
```

```python
check = pd.read_csv("retailpulse_merged.csv")
print(check.shape)
print("profit_inr" in check.columns, "country" in check.columns)
```

```text
(8000, 22)
True False
```

```python
region_map = {
    "Mumbai": "Konkan", "Navi Mumbai": "Konkan", "Thane": "Konkan",
    "Pune": "Western Maharashtra", "Kolhapur": "Western Maharashtra", "Nashik": "Western Maharashtra",
    "Nagpur": "Vidarbha", "Aurangabad": "Marathwada"
}
df["country"] = "India"
df["region"] = df["city"].map(region_map)

print(df["region"].isnull().sum())   # 0 aana chahiye
df.to_csv("retailpulse_merged.csv", index=False)
```

```text
0
```

```python
df.to_csv("retailpulse_merged.csv", index=False)
import os
print(os.getcwd())
```

```text
C:\Users\USER\Installation\Retail Pulse
```
