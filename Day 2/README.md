

```python
!wget https://raw.githubusercontent.com/ohmreborn/Ai/main/Day%202/Student_Marks.csv
```

```python
import plotly.graph_objs as go
import plotly.express as px
from sklearn.cluster import KMeans
from sklearn.datasets import make_blobs
from sklearn.preprocessing import StandardScaler
import pandas as pd
import numpy as np
```

```python
df = pd.read_csv('Student_Marks.csv')
df.head()
```

```python
df['number_courses'].min()
```

```python
px.scatter(df,x='time_study',y='Marks',color='number_courses')
```

```python
scale = StandardScaler()
feature = scale.fit_transform(df[['time_study',	'Marks']])
```

```python

model = KMeans(
    init="random",
    n_clusters=len(df['number_courses'].unique()),
    n_init=10,
    max_iter=300,
    random_state=42
)
```

```python
model.fit(feature)
```

```python
c = model.cluster_centers_
c
     
```

```python

marker = [{'color': 'LightSkyBlue',
          'size': 20,
                          },

          {'color': 'green',
                          'size': 20,
                          },

          {'color': 'orange',
                          'size': 20,
                          },

          {'color': 'purple',
                          'size': 20,
                          },

          {'color': 'Black',
                          'size': 20,
                          },
                    
          {'color': 'brown',
                          'size': 20,
                }]
```

```python
show = []

for i,mark in enumerate(marker):
  x = df[df['number_courses']==i+3]['x']
  y = df[df['number_courses']==i+3]['y']
  trace_data = go.Scatter(x=x,y=y,mode='markers',name=f'data เรียน{i+3}')
  trace_center = go.Scatter(x=[c[i,0]],y=[c[i,1]],marker=mark,name=f'center เรียน {i+3} ครั้ง')
  show.append(trace_data)
  show.append(trace_center)

```

```python
fig = go.Figure(data=show)
fig.show()
```

```python

```
