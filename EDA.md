```python
ztransforms = [np.array(stats.zscore(df[df.id == subject]['rt_ms'])) for subject in df['id'].unique()]
df['zscore'] = np.concatenate(ztransforms)

#This shows the z transformation of the data, which standardizes it to allow for easier statistical analysis.
```


```python
t, p = stats.ttest_rel(fc_sc, fi_sc)

print('Flanker incongruent vs. congruent (Simon-compatible trials only) t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))

#This code displays T-test for specific conditions.
```

    Flanker incongruent vs. congruent (Simon-compatible trials only) t = -1.14  p =  0.2659



```python
t, p = stats.ttest_rel(fc_si, fc_sc)

print('Simon-compatible vs incompatible (Flanker congruent trials only) t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))

#This code displays T-test for specific conditions.
```

    Simon-compatible vs incompatible (Flanker congruent trials only) t = 2.44  p =  0.0232



```python
t, p = stats.ttest_rel(fi_si, fc_si)

print('Incongruent-Incompatible vs. Congruent-Compatible t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))

#This code displays T-test for specific conditions.
```

    Incongruent-Incompatible vs. Congruent-Compatible t = 3.64  p =  0.0014



```python
t, p = stats.ttest_rel(fi_si, fi_sc)

print('Incongruent-Incompatible vs. Incongruent-Compatible t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))

#This code displays T-test for specific conditions.
```

    Incongruent-Incompatible vs. Incongruent-Compatible t = 2.66  p =  0.0142



```python
t, p = stats.ttest_rel(fc_sc_acc, fi_sc_acc)

print('Flanker incongruent vs. congruent (Simon-compatible trials only) t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))

#This code displays T-test for the accuracy rates of specific conditions.
```

    Flanker incongruent vs. congruent (Simon-compatible trials only) t = 1.45  p =  0.1619



```python
t, p = stats.ttest_rel(fc_sc_acc, fc_si_acc)

print('Simon-compatible vs incompatible (Flanker congruent trials only) t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))

#This code displays T-test for the accuracy rates of specific conditions.
```

    Simon-compatible vs incompatible (Flanker congruent trials only) t = 2.91  p =  0.0081



```python
t, p = stats.ttest_rel(fi_si_acc, fc_si_acc)

print('Incongruent-Incompatible vs. Congruent-Compatible t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))

#This code displays T-test for the accuracy rates of specific conditions.
```

    Incongruent-Incompatible vs. Congruent-Compatible t = -1.86  p =  0.0763



```python
t, p = stats.ttest_rel(fi_si_acc, fi_sc_acc)

print('Incongruent-Incompatible vs. Incongruent-Compatible t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))

#This code displays T-test for the accuracy rates of specific conditions.
```

    Incongruent-Incompatible vs. Incongruent-Compatible t = -2.91  p =  0.0081

