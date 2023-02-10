```python
from sklearn.linear_model import LinearRegression
import plotly.express as px
import plotly.graph_objs as go
import pandas as pd
import numpy as np
```

```python
!wget https://raw.githubusercontent.com/ohmreborn/Basic-for-Datasci/main/pandas-02/data-firearm.csv
```

```python
df = pd.read_csv('data-firearm.csv')
Alabama = df[df['state']=='Alabama']

```

```python
model = LinearRegression()
x,y = np.arange(len(Alabama['totals'])).reshape(-1,1),Alabama['totals']
model.fit(x,y)
```

```python
fig = go.Figure(data=[go.Scatter(x=Alabama['month'],y=Alabama['totals'],mode='markers',name='data'),
go.Scatter(x=Alabama['month'],y=model.predict(x).flatten(),mode='lines',name='data')])


```

```python
fig.show()
```

```python

```
