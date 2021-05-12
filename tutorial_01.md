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

# Tutorial 1: Getting Oriented

In this tutorial, we're going to learn the following:

1. Learn how to use the base Pybats classes to open files.
2. Learn how to discover what is in a file.
3. Learn how to navigate Pybats and Pybats objects to find the right classes & methods.


```python
from spacepy import pybats
```

```python
data = pybats.IdlFile('data/GM/y=0_mhd_1_e20121008-010000-014_20121009-120000-000.outs')
```

## Start with some imports
Import the things we'll need now

```python
from spacepy.pybats import bats
mhd = bats.Bats2d('data/GM/y=0_mhd_1_e20121008-010000-014_20121009-120000-000.outs')
```

```python
print(data)
data.keys()
```

```python
data['Rho']
data['x']
data['z']
```

```python
import numpy as np
rad = np.sqrt(data['x']**2 + data['z']**2)
print(rad)
data['rad'] = np.sqrt(data['x']**2 + data['z']**2)
```

```python
import matplotlib.pyplot as plt
```

```python
plt.plot(data['x'], data['z'], 'k.')
```

```python
data.attrs
```

```python
data['Rho'].attrs
```

```python
data['x'].attrs
```

```python
from spacepy.pybats import bats
mhd = bats.Bats2d('data/GM/y=0_mhd_1_e20121008-010000-014_20121009-120000-000.outs')

```

```python
rim = 10
print(rim)
from spacepy.pybats import rim
print(rim)
```

```python
# Tab complete to see cool things!!!
mhd.add_contour?
```

```python
fig, ax, cont, cbar = mhd.add_contour('x', 'z', 'p', 101, add_cbar=True, dolog=True)
```

```python
ax.set_title('What a great plot') #not great in jupyter
```

```python
iono = rim.Iono('data/IE/it121008_010000_000.idl.gz')
print(iono)
```

```python
fig = plt.figure()
mhd.add_contour('x','z','rho', dolog=True, target=fig, loc=221, cmap='jet')
mhd.add_contour('x','z','p', dolog=True, target=fig, loc=222)
iono.add_cont('n_jr', target=fig, loc=223)
iono.add_cont('n_phi', target=fig, loc=224)
```

```python
mhd?
```

```python
mhd['rad'] = np.sqrt(mhd['x']**2 + mhd['z']**2)
mhd.add_contour('x','z','rad')
```

```python
mhd.calc_alfven()
print(mhd.keys())
```

```python
mhd.add_pcolor('x','z','bx_hat')
```

```python
ls data/GM
```

```python
fig, ax, cont, cbar = mhd.add_contour('x','z', 'p', dolog=True, add_cbar=True)
mhd.add_b_magsphere(target=ax)
```

```python
fig, ax, cont, cbar = mhd.add_contour('x','z', 'p', dolog=True, add_cbar=True, xlim=[-32,16], ylim=[-24, 24])
mhd.add_stream_scatter('ux', 'uz', target=ax)
```

```python
mhd.get_stream?
```

```python
mhd.keys()

```

```python
stream = mhd.get_stream(15, 10, 'ux','uz', extract=True)
```

```python
stream.attrs
print(stream)
```

```python
plt.plot(stream['x'], stream['p'])
```

```python
plt.plot(stream['x'], stream['z'])
```

```python
mhd.extract?
```

```python

```
