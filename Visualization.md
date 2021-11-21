```python
df.T.loc['rt_ms', :].plot(kind = 'hist')

plt.axvline(df['rt_ms'].describe()['25%'], 0, 1, color='turquoise', linestyle='--')
plt.axvline(df['rt_ms'].median(), 0, 1, color='cyan', linestyle='-')
plt.axvline(df['rt_ms'].describe()['75%'], 0, 1, color='turquoise', linestyle='--')

plt.show()

#This code creates a histogram using matplotlib with the median and the 25th and 75th percentiles shown.
```




    
![png](Visualization_files/Visualization_0_0.png)
    




```python
df.T.loc['rt_ms', :].hist(cumulative=True)

plt.axvline(df['rt_ms'].describe()['25%'], 0, 1, color='turquoise', linestyle='--')
plt.axvline(df['rt_ms'].median(), 0, 1, color='cyan', linestyle='-')
plt.axvline(df['rt_ms'].describe()['75%'], 0, 1, color='turquoise', linestyle='--')

plt.show()

#This code uses the same data to create a cumulative distribution function using matplot lib with the 
#median and 25th and 75th percentiles shown.
```




    
![png](Visualization_files/Visualization_1_0.png)
    




```python
import numpy as np

df['log_rt'] = np.log(df['rt_ms'])

df.T.loc['log_rt', :].plot(kind = 'hist')

plt.axvline(df['log_rt'].describe()['25%'], 0, 1, color='turquoise', linestyle='--')
plt.axvline(df['log_rt'].median(), 0, 1, color='cyan', linestyle='-')
plt.axvline(df['log_rt'].describe()['75%'], 0, 1, color='turquoise', linestyle='--')

plt.show()

#This code uses the same data as before to transform the original histogram, using matplotlib 
#to log form to make the data less skewed and easier to use for statistical analysis.
```




    
![png](Visualization_files/Visualization_2_0.png)
    




```python
df.T.loc['rt_inv', :].plot(kind = 'hist')

plt.axvline(df['rt_inv'].describe()['25%'], 0, 1, color='turquoise', linestyle='--')
plt.axvline(df['rt_inv'].median(), 0, 1, color='cyan', linestyle='-')
plt.axvline(df['rt_inv'].describe()['75%'], 0, 1, color='turquoise', linestyle='--')

plt.show()

#This code continues to use the same data and changes the histogram, using matplotlib, so that 
#it is even easier to use for statistical analysis with the more normal distribution.
```




    
![png](Visualization_files/Visualization_3_0.png)
    




```python
df=df.reset_index()
sns.displot(data=df, x='rt_ms', hue='flankers')
plt.show()

#This code continues to use the same data and uses the seaborn package to create a 
#distribution plot with different colors for each of the conditions within the dataset.
```




    
![png](Visualization_files/Visualization_4_0.png)
    




```python
sns.catplot(kind='box', data=df, x='flankers', y='rt_ms')

plt.show()

#This code continues to use the same data and uses the seaborn package to display
#a boxplot for the same condiditons as the above graph.
```




    
![png](Visualization_files/Visualization_5_0.png)
    




```python
sns.catplot(kind='bar', data=df, x='flankers', y='error')

plt.show()

#This code continues to use the same data and seaborn package to create a boxplot of the same conditions as above.
```




    
![png](Visualization_files/Visualization_6_0.png)
    


