<div>
      <h1>Exploratory Data Analysis</h1>
</div>
<br /><br />
<div>
      <h2>Z Transformation of Data</h2>
      <p>This code demonstrates how to z transform data to standarize the data to make it easier to preform statistical analysis on it.</p>
</div>
```python
ztransforms = [np.array(stats.zscore(df[df.id == subject]['rt_ms'])) for subject in df['id'].unique()]
df['zscore'] = np.concatenate(ztransforms)
```
<br /><br />
<div>
      <h2>T-tests</h2>
      <p>The following code demonstrate how to conduct T-tests on different variables within the dataset.</p>
</div>
<br /><br />
```python
t, p = stats.ttest_rel(fc_sc, fi_sc)

print('Flanker incongruent vs. congruent (Simon-compatible trials only) t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))
```

    Flanker incongruent vs. congruent (Simon-compatible trials only) t = -1.14  p =  0.2659

<br /><br />

```python
t, p = stats.ttest_rel(fc_si, fc_sc)

print('Simon-compatible vs incompatible (Flanker congruent trials only) t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))
```

    Simon-compatible vs incompatible (Flanker congruent trials only) t = 2.44  p =  0.0232

<br /><br />

```python
t, p = stats.ttest_rel(fi_si, fc_si)

print('Incongruent-Incompatible vs. Congruent-Compatible t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))
```

    Incongruent-Incompatible vs. Congruent-Compatible t = 3.64  p =  0.0014

<br /><br />

```python
t, p = stats.ttest_rel(fi_si, fi_sc)

print('Incongruent-Incompatible vs. Incongruent-Compatible t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))
```

    Incongruent-Incompatible vs. Incongruent-Compatible t = 2.66  p =  0.0142

<br /><br />

```python
t, p = stats.ttest_rel(fc_sc_acc, fi_sc_acc)

print('Flanker incongruent vs. congruent (Simon-compatible trials only) t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))
```

    Flanker incongruent vs. congruent (Simon-compatible trials only) t = 1.45  p =  0.1619

<br /><br />

```python
t, p = stats.ttest_rel(fc_sc_acc, fc_si_acc)

print('Simon-compatible vs incompatible (Flanker congruent trials only) t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))
```

    Simon-compatible vs incompatible (Flanker congruent trials only) t = 2.91  p =  0.0081

<br /><br />
<div>
      <p>The following code demonstrates further T-tests for accuracy of the dofferent conditions in the dataset.</p>
</div>

```python
t, p = stats.ttest_rel(fi_si_acc, fc_si_acc)

print('Incongruent-Incompatible vs. Congruent-Compatible t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))
```

    Incongruent-Incompatible vs. Congruent-Compatible t = -1.86  p =  0.0763

<br /><br />

```python
t, p = stats.ttest_rel(fi_si_acc, fi_sc_acc)

print('Incongruent-Incompatible vs. Incongruent-Compatible t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))

#This code displays T-test for the accuracy rates of specific conditions.
```

    Incongruent-Incompatible vs. Incongruent-Compatible t = -2.91  p =  0.0081

