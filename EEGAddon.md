```python
# YOUR CODE HERE
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```


```python
# YOUR CODE HERE
df = pd.read_csv('crowder_data_all.csv')
```


```python
# YOUR CODE HERE
df.sample(20)
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
      <th>neuron</th>
      <th>spiketime</th>
      <th>repetition</th>
      <th>contrast</th>
      <th>condition</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>5872</th>
      <td>m2_9</td>
      <td>1959</td>
      <td>8</td>
      <td>12</td>
      <td>ADAPT</td>
    </tr>
    <tr>
      <th>21517</th>
      <td>m6_3b2</td>
      <td>3165</td>
      <td>8</td>
      <td>84</td>
      <td>ADAPT</td>
    </tr>
    <tr>
      <th>15868</th>
      <td>m3_3</td>
      <td>596</td>
      <td>7</td>
      <td>8</td>
      <td>ADAPT</td>
    </tr>
    <tr>
      <th>31393</th>
      <td>m6_17b</td>
      <td>27</td>
      <td>3</td>
      <td>84</td>
      <td>ADAPT</td>
    </tr>
    <tr>
      <th>1258</th>
      <td>m1_6</td>
      <td>627</td>
      <td>6</td>
      <td>32</td>
      <td>ADAPT</td>
    </tr>
    <tr>
      <th>19849</th>
      <td>m6_3b2</td>
      <td>2337</td>
      <td>2</td>
      <td>48</td>
      <td>CTRL</td>
    </tr>
    <tr>
      <th>15405</th>
      <td>m3_3</td>
      <td>1446</td>
      <td>1</td>
      <td>4</td>
      <td>ADAPT</td>
    </tr>
    <tr>
      <th>16215</th>
      <td>m3_3</td>
      <td>1324</td>
      <td>2</td>
      <td>16</td>
      <td>ADAPT</td>
    </tr>
    <tr>
      <th>29579</th>
      <td>m6_17b</td>
      <td>556</td>
      <td>7</td>
      <td>12</td>
      <td>ADAPT</td>
    </tr>
    <tr>
      <th>2604</th>
      <td>m2_9</td>
      <td>1802</td>
      <td>8</td>
      <td>12</td>
      <td>CTRL</td>
    </tr>
    <tr>
      <th>12958</th>
      <td>m2_13</td>
      <td>1125</td>
      <td>2</td>
      <td>100</td>
      <td>ADAPT</td>
    </tr>
    <tr>
      <th>9206</th>
      <td>m2_13</td>
      <td>3580</td>
      <td>1</td>
      <td>16</td>
      <td>CTRL</td>
    </tr>
    <tr>
      <th>7751</th>
      <td>m2_9</td>
      <td>324</td>
      <td>6</td>
      <td>64</td>
      <td>ADAPT</td>
    </tr>
    <tr>
      <th>14608</th>
      <td>m3_3</td>
      <td>2041</td>
      <td>4</td>
      <td>64</td>
      <td>CTRL</td>
    </tr>
    <tr>
      <th>21934</th>
      <td>m4_17</td>
      <td>2272</td>
      <td>5</td>
      <td>16</td>
      <td>CTRL</td>
    </tr>
    <tr>
      <th>2149</th>
      <td>m2_9</td>
      <td>770</td>
      <td>8</td>
      <td>4</td>
      <td>CTRL</td>
    </tr>
    <tr>
      <th>2626</th>
      <td>m2_9</td>
      <td>2859</td>
      <td>1</td>
      <td>16</td>
      <td>CTRL</td>
    </tr>
    <tr>
      <th>20393</th>
      <td>m6_3b2</td>
      <td>1029</td>
      <td>5</td>
      <td>4</td>
      <td>ADAPT</td>
    </tr>
    <tr>
      <th>10212</th>
      <td>m2_13</td>
      <td>3215</td>
      <td>5</td>
      <td>84</td>
      <td>CTRL</td>
    </tr>
    <tr>
      <th>4171</th>
      <td>m2_9</td>
      <td>203</td>
      <td>7</td>
      <td>84</td>
      <td>CTRL</td>
    </tr>
  </tbody>
</table>
</div>




```python
# YOUR CODE HERE
dat = df[(df['neuron'] == 'm1_6') & (df['condition'] == 'CTRL') & (df['contrast'] == 48)]
dat
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
      <th>neuron</th>
      <th>spiketime</th>
      <th>repetition</th>
      <th>contrast</th>
      <th>condition</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>85</th>
      <td>m1_6</td>
      <td>1504</td>
      <td>1</td>
      <td>48</td>
      <td>CTRL</td>
    </tr>
    <tr>
      <th>86</th>
      <td>m1_6</td>
      <td>2361</td>
      <td>1</td>
      <td>48</td>
      <td>CTRL</td>
    </tr>
    <tr>
      <th>87</th>
      <td>m1_6</td>
      <td>2374</td>
      <td>1</td>
      <td>48</td>
      <td>CTRL</td>
    </tr>
    <tr>
      <th>88</th>
      <td>m1_6</td>
      <td>2508</td>
      <td>1</td>
      <td>48</td>
      <td>CTRL</td>
    </tr>
    <tr>
      <th>89</th>
      <td>m1_6</td>
      <td>2657</td>
      <td>1</td>
      <td>48</td>
      <td>CTRL</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>152</th>
      <td>m1_6</td>
      <td>2602</td>
      <td>8</td>
      <td>48</td>
      <td>CTRL</td>
    </tr>
    <tr>
      <th>153</th>
      <td>m1_6</td>
      <td>2634</td>
      <td>8</td>
      <td>48</td>
      <td>CTRL</td>
    </tr>
    <tr>
      <th>154</th>
      <td>m1_6</td>
      <td>2689</td>
      <td>8</td>
      <td>48</td>
      <td>CTRL</td>
    </tr>
    <tr>
      <th>155</th>
      <td>m1_6</td>
      <td>2717</td>
      <td>8</td>
      <td>48</td>
      <td>CTRL</td>
    </tr>
    <tr>
      <th>156</th>
      <td>m1_6</td>
      <td>2838</td>
      <td>8</td>
      <td>48</td>
      <td>CTRL</td>
    </tr>
  </tbody>
</table>
<p>72 rows × 5 columns</p>
</div>




```python
# YOUR CODE HERE
trial = dat['repetition']
fig, ax = plt.subplots()
ax.vlines(dat['spiketime'], trial - 0.4, trial + 0.4)

ax.set_xlim([0, trial_length])

plt.show()
```




    
![png](grade%26feedback_Assignment_4_Aiobh_files/grade%26feedback_Assignment_4_Aiobh_4_0.png)
    




```python
# YOUR CODE HERE

fig, ax = plt.subplots()

ax.axvspan(stim_on_time, stim_off_time, alpha=0.5, color='grey')

dat['spiketime'].plot(kind='hist', bins=range(0, trial_length, 100))

plt.show()
```




    
![png](grade%26feedback_Assignment_4_Aiobh_files/grade%26feedback_Assignment_4_Aiobh_5_0.png)
    


