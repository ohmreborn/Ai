```python
from sklearn.linear_model import LinearRegression
import matplotlib.pyplot as plt
import numpy as np

x = np.array([2,4,6,8,10,12,14]).reshape(-1, 1)
y = np.array([6,10,11,22,25,30,55])

plt.scatter(x,y)
plt.show()
```

```python
model = LinearRegression()
model.fit(x, y)
```

```python
plt.scatter(x,y)
plt.plot(x,model.predict(x),color='red')
plt.show()
```

# โจทย์โหลด data
https://github.com/ohmreborn/Ai/blob/main/Day%201/data-firearm.csv

1. ให้หาLineargressionของ รัฐ 'Alabama'
