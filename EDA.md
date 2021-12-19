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




```python
t, p = stats.ttest_rel(fc_sc_acc, fi_sc_acc)

print('Flanker incongruent vs. congruent (Simon-compatible trials only) t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))

#This code displays T-test for the accuracy rates of specific conditions.
```

    Flanker incongruent vs. congruent (Simon-compatible trials only) t = 1.45  p =  0.1619





