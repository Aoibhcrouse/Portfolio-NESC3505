<style>
  h1{color:Purple !important;}
  h2{color:Grey !important;}
</style>
<div>
      <h1>Exploratory Data Analysis</h1>
</div>
<br />

<div>
      <p>This shows the z transformation of the data, which standardizes it to allow for easier statistical analysis.</p>
</div>
```python
ztransforms = [np.array(stats.zscore(df[df.id == subject]['rt_ms'])) for subject in df['id'].unique()]
df['zscore'] = np.concatenate(ztransforms)


```
<div>
      <p>This code displays T-test for specific conditions.</p>
</div>
```python
t, p = stats.ttest_rel(fc_sc, fi_sc)

print('Flanker incongruent vs. congruent (Simon-compatible trials only) t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))


```

    Flanker incongruent vs. congruent (Simon-compatible trials only) t = -1.14  p =  0.2659

<div>
      <p>This code displays T-test for the accuracy rates of specific conditions.</p>
</div>

```python
t, p = stats.ttest_rel(fc_sc_acc, fi_sc_acc)

print('Flanker incongruent vs. congruent (Simon-compatible trials only) t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))
```

    Flanker incongruent vs. congruent (Simon-compatible trials only) t = 1.45  p =  0.1619

<div>
      <p>This shows how to get a dataframe without an undesired condition.</p>
</div>
```python
df = df[df.flankers != 'neutral']
df
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
      <th>id</th>
      <th>year</th>
      <th>month</th>
      <th>day</th>
      <th>hour</th>
      <th>minute</th>
      <th>gender</th>
      <th>age</th>
      <th>handedness</th>
      <th>wait</th>
      <th>block</th>
      <th>trial</th>
      <th>target_location</th>
      <th>target</th>
      <th>flankers</th>
      <th>rt</th>
      <th>response</th>
      <th>error</th>
      <th>pre_target_response</th>
      <th>ITI_response</th>
      <th>target_on_error</th>
      <th>rt_ms</th>
      <th>log_rt</th>
      <th>rt_inv</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>32</th>
      <td>3</td>
      <td>2015</td>
      <td>5</td>
      <td>28</td>
      <td>14</td>
      <td>9</td>
      <td>f</td>
      <td>50</td>
      <td>r</td>
      <td>2.684</td>
      <td>1</td>
      <td>1</td>
      <td>down</td>
      <td>white</td>
      <td>incongruent</td>
      <td>0.480</td>
      <td>white</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>0.023</td>
      <td>480.0</td>
      <td>6.173786</td>
      <td>2.083333</td>
    </tr>
    <tr>
      <th>33</th>
      <td>3</td>
      <td>2015</td>
      <td>5</td>
      <td>28</td>
      <td>14</td>
      <td>9</td>
      <td>f</td>
      <td>50</td>
      <td>r</td>
      <td>2.684</td>
      <td>1</td>
      <td>2</td>
      <td>left</td>
      <td>black</td>
      <td>incongruent</td>
      <td>0.481</td>
      <td>white</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>0.024</td>
      <td>481.0</td>
      <td>6.175867</td>
      <td>2.079002</td>
    </tr>
    <tr>
      <th>37</th>
      <td>3</td>
      <td>2015</td>
      <td>5</td>
      <td>28</td>
      <td>14</td>
      <td>9</td>
      <td>f</td>
      <td>50</td>
      <td>r</td>
      <td>2.684</td>
      <td>1</td>
      <td>6</td>
      <td>up</td>
      <td>black</td>
      <td>incongruent</td>
      <td>0.483</td>
      <td>black</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>0.022</td>
      <td>483.0</td>
      <td>6.180017</td>
      <td>2.070393</td>
    </tr>
    <tr>
      <th>38</th>
      <td>3</td>
      <td>2015</td>
      <td>5</td>
      <td>28</td>
      <td>14</td>
      <td>9</td>
      <td>f</td>
      <td>50</td>
      <td>r</td>
      <td>2.684</td>
      <td>1</td>
      <td>7</td>
      <td>right</td>
      <td>white</td>
      <td>congruent</td>
      <td>0.390</td>
      <td>white</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>0.023</td>
      <td>390.0</td>
      <td>5.966147</td>
      <td>2.564103</td>
    </tr>
    <tr>
      <th>43</th>
      <td>3</td>
      <td>2015</td>
      <td>5</td>
      <td>28</td>
      <td>14</td>
      <td>9</td>
      <td>f</td>
      <td>50</td>
      <td>r</td>
      <td>2.684</td>
      <td>1</td>
      <td>12</td>
      <td>left</td>
      <td>white</td>
      <td>incongruent</td>
      <td>0.538</td>
      <td>white</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>0.023</td>
      <td>538.0</td>
      <td>6.287859</td>
      <td>1.858736</td>
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
      <th>180</th>
      <td>2</td>
      <td>2015</td>
      <td>5</td>
      <td>25</td>
      <td>14</td>
      <td>36</td>
      <td>f</td>
      <td>21</td>
      <td>r</td>
      <td>3.096</td>
      <td>5</td>
      <td>21</td>
      <td>down</td>
      <td>white</td>
      <td>incongruent</td>
      <td>0.836</td>
      <td>white</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>0.024</td>
      <td>836.0</td>
      <td>6.728629</td>
      <td>1.196172</td>
    </tr>
    <tr>
      <th>186</th>
      <td>2</td>
      <td>2015</td>
      <td>5</td>
      <td>25</td>
      <td>14</td>
      <td>36</td>
      <td>f</td>
      <td>21</td>
      <td>r</td>
      <td>3.096</td>
      <td>5</td>
      <td>27</td>
      <td>down</td>
      <td>white</td>
      <td>congruent</td>
      <td>0.416</td>
      <td>white</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>0.024</td>
      <td>416.0</td>
      <td>6.030685</td>
      <td>2.403846</td>
    </tr>
    <tr>
      <th>187</th>
      <td>2</td>
      <td>2015</td>
      <td>5</td>
      <td>25</td>
      <td>14</td>
      <td>36</td>
      <td>f</td>
      <td>21</td>
      <td>r</td>
      <td>3.096</td>
      <td>5</td>
      <td>28</td>
      <td>left</td>
      <td>white</td>
      <td>congruent</td>
      <td>0.416</td>
      <td>white</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>0.024</td>
      <td>416.0</td>
      <td>6.030685</td>
      <td>2.403846</td>
    </tr>
    <tr>
      <th>188</th>
      <td>2</td>
      <td>2015</td>
      <td>5</td>
      <td>25</td>
      <td>14</td>
      <td>36</td>
      <td>f</td>
      <td>21</td>
      <td>r</td>
      <td>3.096</td>
      <td>5</td>
      <td>29</td>
      <td>right</td>
      <td>white</td>
      <td>congruent</td>
      <td>0.408</td>
      <td>white</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>0.024</td>
      <td>408.0</td>
      <td>6.011267</td>
      <td>2.450980</td>
    </tr>
    <tr>
      <th>189</th>
      <td>2</td>
      <td>2015</td>
      <td>5</td>
      <td>25</td>
      <td>14</td>
      <td>36</td>
      <td>f</td>
      <td>21</td>
      <td>r</td>
      <td>3.096</td>
      <td>5</td>
      <td>30</td>
      <td>up</td>
      <td>black</td>
      <td>incongruent</td>
      <td>0.644</td>
      <td>black</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>0.024</td>
      <td>644.0</td>
      <td>6.467699</td>
      <td>1.552795</td>
    </tr>
  </tbody>
</table>
<p>240 rows ?? 24 columns</p>
</div>


<div>
      <p>This uses the .groupby() function to get a much smaller data frame with the average of each condition within the 'flankers' group.</p>
</div>
```python
df.loc[:, ['flankers', 'rt_ms']].groupby('flankers').mean('rt_ms')
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
      <th>rt_ms</th>
    </tr>
    <tr>
      <th>flankers</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>congruent</th>
      <td>431.183333</td>
    </tr>
    <tr>
      <th>incongruent</th>
      <td>491.066667</td>
    </tr>
  </tbody>
</table>
</div>


<div>
      <p>This uses the same .groupby() function to view the error rate within the trials.</p>
</div>
```python
df.loc[:, ['error', 'trial']].groupby('error').count()
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
      <th>trial</th>
    </tr>
    <tr>
      <th>error</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>False</th>
      <td>24</td>
    </tr>
    <tr>
      <th>True</th>
      <td>216</td>
    </tr>
  </tbody>
</table>
</div>


<div>
      <p>This shows how to obtain the mean error rate across the trials.</p>
</div>
```python
df.loc[:, ['error', 'trial']].groupby('error').mean(True)
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
      <th>trial</th>
    </tr>
    <tr>
      <th>error</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>False</th>
      <td>21.041667</td>
    </tr>
    <tr>
      <th>True</th>
      <td>17.009259</td>
    </tr>
  </tbody>
</table>
</div>





