---
jupyter:
  jupytext:
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
      jupytext_version: 1.11.2
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

```python
ls data/GM
```

```python
more data/GM/log_e20121008-010000.log
```

```python
from spacepy.pybats import LogFile, ImfInput
```

```python
log = LogFile('data/GM/log_e20121008-010000.log')
```

```python
print(log)
```

```python
import matplotlib.pyplot as plt
plt.plot(log['time'], log['dst'])
```

```python
from spacepy.pybats.bats import BatsLog, GeoIndexFile
```

```python
log = BatsLog('data/GM/log_e20121008-010000.log')
```

```python
log.add_dst_quicklook(plot_sym=True)
```

```python
ls data/GM/

```

```python
geolog = GeoIndexFile('data/GM/geoindex_e20121008-010000.log')
```

```python
geolog.add_kp_quicklook(plot_obs=True)
```

```python
from spacepy import plot
```

```python
plot.style()
```

```python
geolog.add_kp_quicklook(plot_obs=True)
```

```python
from spacepy.pybats.bats import MagFile
mags = MagFile('data/GM/magnetometers_e20121008-010000.mag')
```

```python
mags.attrs
```

```python
mags['HON']
```

```python
m = mags['HON']
```

```python
m.attrs
```

```python
print(m)
```

```python
m.add_comp_plot('n')
```

```python
mags['PBQ'].add_comp_plot('e')
```

```python
imf = ImfInput('data/imf20121001.dat')
```

```python
print(imf)
```

```python
imf.quicklook([('by','bz'),'pram','v'])
```

```python
imf2 = ImfInput('test.blah', load=False)
```

```python
imf['by'] *= -1 # same as imf['by'] = -1 * imf['by']
imf.attrs['file'] = 'imf_flip.dat'
```

```python
imf.write()
```

```python
ls 

```

```python
more imf_flip.dat

```

```python
imf.attrs['header'].append('Darren said this is different.  Dan flipped by\n')
imf.attrs['header']
```

```python

```
