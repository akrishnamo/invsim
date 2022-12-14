invsim
================

<!-- WARNING: THIS FILE WAS AUTOGENERATED! DO NOT EDIT! -->

This is the repository for inventory simulation module for Safe Decor.
It includes simulation and order recommendation functionality

## Install

``` sh
pip install invsim
```

## How to use

Clip_date returns first non zero date if there are at least 30 elements,
if not just returns the first date

Case1: there are more than 30 elements

``` python
ndays=40
leading_zero_days=5
dates=pd.date_range(start='2022-01-01', periods=ndays, freq='D')
values=[0]*leading_zero_days+[10]*(ndays-leading_zero_days)

df=pd.DataFrame({'date':dates, 'qty': values})
df['date']=df.date.apply(lambda x: x.date())
display(df.T)

print("clip date =", clip_date(df))
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
      <th>5</th>
      <th>6</th>
      <th>7</th>
      <th>8</th>
      <th>9</th>
      <th>...</th>
      <th>30</th>
      <th>31</th>
      <th>32</th>
      <th>33</th>
      <th>34</th>
      <th>35</th>
      <th>36</th>
      <th>37</th>
      <th>38</th>
      <th>39</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>date</th>
      <td>2022-01-01</td>
      <td>2022-01-02</td>
      <td>2022-01-03</td>
      <td>2022-01-04</td>
      <td>2022-01-05</td>
      <td>2022-01-06</td>
      <td>2022-01-07</td>
      <td>2022-01-08</td>
      <td>2022-01-09</td>
      <td>2022-01-10</td>
      <td>...</td>
      <td>2022-01-31</td>
      <td>2022-02-01</td>
      <td>2022-02-02</td>
      <td>2022-02-03</td>
      <td>2022-02-04</td>
      <td>2022-02-05</td>
      <td>2022-02-06</td>
      <td>2022-02-07</td>
      <td>2022-02-08</td>
      <td>2022-02-09</td>
    </tr>
    <tr>
      <th>qty</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>...</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
<p>2 rows ?? 40 columns</p>
</div>

    clip date = 2022-01-06

Case2: There are less than 30 elements

``` python
ndays=29
leading_zero_days=5
dates=pd.date_range(start='2022-01-01', periods=ndays, freq='D')
values=[0]*leading_zero_days+[10]*(ndays-leading_zero_days)

df=pd.DataFrame({'date':dates, 'qty': values})
df['date']=df.date.apply(lambda x: x.date())
display(df.T)

print("clip date =", clip_date(df))
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
      <th>5</th>
      <th>6</th>
      <th>7</th>
      <th>8</th>
      <th>9</th>
      <th>...</th>
      <th>19</th>
      <th>20</th>
      <th>21</th>
      <th>22</th>
      <th>23</th>
      <th>24</th>
      <th>25</th>
      <th>26</th>
      <th>27</th>
      <th>28</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>date</th>
      <td>2022-01-01</td>
      <td>2022-01-02</td>
      <td>2022-01-03</td>
      <td>2022-01-04</td>
      <td>2022-01-05</td>
      <td>2022-01-06</td>
      <td>2022-01-07</td>
      <td>2022-01-08</td>
      <td>2022-01-09</td>
      <td>2022-01-10</td>
      <td>...</td>
      <td>2022-01-20</td>
      <td>2022-01-21</td>
      <td>2022-01-22</td>
      <td>2022-01-23</td>
      <td>2022-01-24</td>
      <td>2022-01-25</td>
      <td>2022-01-26</td>
      <td>2022-01-27</td>
      <td>2022-01-28</td>
      <td>2022-01-29</td>
    </tr>
    <tr>
      <th>qty</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>...</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
<p>2 rows ?? 29 columns</p>
</div>

    clip date = 2022-01-01
