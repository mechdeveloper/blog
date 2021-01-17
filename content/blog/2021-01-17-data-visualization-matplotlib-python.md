---
title: Data Visualization | Matplotlib | Python
date: 2021-01-17T19:05:56.413Z
description: Data Visualization with Matplotlib Python
---
# Matplotlib Data Visualization | Code Snippets

## Installing `matplotlib`

- `matplotlib` is a third party library and is not part of standard Python library
- It can be installed with `pip` utility

    ```py
    pip install matplotlib
    ```

- `matplotlib` is available directly in distributions such as `Anaconda`, and `WinPython`


## upgrading `matplotlib`

```py
pip install --upgrade matplotlib
```

## loading `matplotlib` using `import`

```py
import matplotlib
```

## `matplotlib` version

```py
print(matplotlib.__version__)
```

## Parts of a Matplotlib Figure

- `Figure` : Whole area chosen for plotting
- `Axes` : Area where data is plotted
- `Axis` : Number-like objects, which define graph limits
- `Artist` : Every element on the figure is an artist

## Creating a Figure

```py
import matplotlib.pyplot as plt
fig = plt.figure()
```

- Executing the above code doesn't display any figure.
- You should explicitly tell pyplot to display it.

```py
import matplotlib.pyplot as plt
fig = plt.figure()
plt.show()
```

Output:

```console
<Figure size 432x288 with 0 Axes>
```

- The output simply shows the figure object.
- You will be able to view a picture only when a figure contains at least one `Axes` element.

## Creating Axes

- An `Axes` is the region of the figure, available for plotting data.
- An `Axes` object is associated with only one `Figure`.
- A `Figure` can contain one or more number of `Axes` elements.
- An `Axes` contains two `Axis` objects in case of 2D plots and three `Axis` objects in case of 3D plots.
- An `Axes` can be added to a figure using `add_subplot` methods.

```py
add_subplot(nrows, ncols, index)
```

- When these argument values are less than 10, they all can be clubbed and passed as a single three-digit number.
- `add_subplot(1, 1, 1)` and `add_subplot(111)` are same

## generate a figure with one `axes`

```py
fig = plt.figure()
ax = fig.add_subplot(111)
plt.show()
```

- The default `width` and `height` of a figure are `6` and `4` inches respectively.
- You can change the size of a figure using `figsize` argument.
- the expression `fig = plt.figure(figsize=(8,6))` generates a figure having `8 inches` width and `6 inches` height.

```py
fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)
plt.show()
```

## Setting Title and Axis Labels

```py
fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)
ax.set(title='My First Plot',
      xlabel='X-Axis', ylabel='Y-Axis',
      xlim=(0, 5), ylim=(0,10))
plt.show()
```

## Setting an attribute (`set_<paramter_name>`)

```py
fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)
ax.set_title("My First Plot")
ax.set_xlabel("X-Axis"); ax.set_ylabel('Y-Axis')
ax.set_xlim([0,5]); ax.set_ylim([0,10])
plt.show()
```

## Plotting Data (`plot` function)

```py
fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)
ax.set(title='My First Plot',
      xlabel='X-Axis', ylabel='Y-Axis',
      xlim=(0, 5), ylim=(0,10))
x = [1, 2, 3, 4]; y = [2, 4, 6, 8]
plt.plot(x, y)
plt.show()
```

## implicit vs explicit

- Plotting data or setting attributes can also be done by calling functions like plot, and title directly on plt.
- This would plot the data on axes, which is active currently.
- However, `Explicit is better than implicit`. Hence prefer former style of plotting.

```py
fig = plt.figure(figsize=(8,6))

x = [1, 2, 3, 4]; y = [2, 4, 6, 8]
plt.plot(x, y)
plt.title('My First Plot')
plt.xlabel('X-Axis'); plt.ylabel('Y-Axis')
plt.xlim(0,5); plt.ylim(0,10)
plt.plot(x, y)
plt.show()

# Note this is implicit plotting example. 
# Explicit is better than implicit. Hence prefer the formet styple of plotting.
```

## Adding a Legend

```py
fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)
ax.set(title='My First Plot',
      xlabel='X-Axis', ylabel='Y-Axis',
      xlim=(0, 5), ylim=(0,10))
x = [1, 2, 3, 4]; y = [2, 4, 6, 8]
plt.plot(x, y, label='linear-growth')
plt.legend()
plt.show()
```

## Line Plot

```py
fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)
ax.set(title='Avg. Daily Temperature in Jan 2018',
      xlabel='Day', ylabel='Temperature (in deg)',
      xlim=(0, 30), ylim=(25, 35))
days = [1, 5, 8, 12, 15, 19, 22, 26, 29]
temp = [29.3, 30.1, 30.4, 31.5, 32.3, 32.6, 31.8, 32.4, 32.7]
ax.plot(days, temp)
plt.show()
```

## Common Parameters of 'plot' Function

- `color`: Sets the color of the line.
- `linestyle`: Sets the line style, e.g., solid, dashed, etc.
- `linewidth`: Sets the thickness of a line.
- `marker`: Chooses a marker for data points, e.g., circle, triangle, etc.
- `markersize`: Sets the size of the chosen marker.
- `label`: Names the line, which will come in legend.

### Setting 'plot' Parameters

- A `green dashed line`, having width `3`

```py
ax.plot(days, temp, color='green', linestyle='--', linewidth=3)
```

### Marking Data Points (`marker` argument)

- Data points are made visible using `marker` argument.
- plot a green colored line with data points marked in `circles`

```py
ax.plot(days, temp, color='green', marker='o')
```

## Plotting multiple lines in Line plot

```py
fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)
ax.set(title='Avg. Daily Temperature of Jan 2018',
      xlabel='Day', ylabel='Temperature (in deg)',
      xlim=(0, 30), ylim=(25, 35))
days = [1, 5, 8, 12, 15, 19, 22, 26, 29]
location1_temp = [29.3, 30.1, 30.4, 31.5, 32.3, 32.6, 31.8, 32.4, 32.7]
location2_temp = [26.4, 26.8, 26.1, 26.4, 27.5, 27.3, 26.9, 26.8, 27.0]
ax.plot(days, location1_temp, color='green', marker='o', linewidth=3)
ax.plot(days, location2_temp, color='red', marker='o', linewidth=3)
plt.show()
```

## Scatter plot (`scatter` function)

- scatter plot only marks the data points with the chosen marker.

```py
fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)
ax.set(title='Avg. Daily Temperature of Jan 2018',
      xlabel='Day', ylabel='Temperature (in deg)',
      xlim=(0, 30), ylim=(25, 35))
days = [1, 5, 8, 12, 15, 19, 22, 26, 29]
temp = [29.3, 30.1, 30.4, 31.5, 32.3, 32.6, 31.8, 32.4, 32.7]
ax.scatter(days, temp)
plt.show()
```

### Common Parameters of 'scatter'

- `c`: Sets color of markers.
- `s`: Sets size of markers.
- `marker`: Selects a marker. e.g: circle, triangle, etc
- `edgecolor`: Sets the color of lines on edges of markers.

- Parameters `c` and `s` can take a list of values.
- If the number of values is less than the number of data points considered, then the list is repeated.
- plot `green` colored `circles` of size `60`, with `black edges`

```py
ax.scatter(days, temp, marker='o', c=['green'], s=[60], edgecolor='black')
```

Example:

```py
fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)
ax.set(title='Avg. Daily Temperature of Jan 2018',
      xlabel='Day', ylabel='Temperature (in deg)',
      xlim=(0, 30), ylim=(25, 35))
days = [1, 5, 8, 12, 15, 19, 22, 26, 29]
temp = [29.3, 30.1, 30.4, 31.5, 32.3, 32.6, 31.8, 32.4, 32.7]
ax.scatter(days, temp, marker='o', c=['green'], s=[60], edgecolor='black')
plt.show()
```

## Scatter Plot Using 'plot'

- `plot` function can also create a scatter plot when `linestyle` is set to `none`, and a `marker` is chosen

```py
fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)
ax.set(title='Avg. Daily Temperature of Jan 2018',
      xlabel='Day', ylabel='Temperature (in deg)',
      xlim=(0, 30), ylim=(25, 35))
days = [1, 5, 8, 12, 15, 19, 22, 26, 29]
temp = [29.3, 30.1, 30.4, 31.5, 32.3, 32.6, 31.8, 32.4, 32.7]
ax.plot(days, temp, marker='o', linestyle='none')
plt.show()
```

## Sine wave plot

```py
import numpy as np
import matplotlib.pyplot as plt

fig = plt.figure(figsize=(12,3))
ax = fig.add_subplot(111)

t = np.linspace(0.0, 2.0, num=200)
v = np.sin(2.5*np.pi*t)

ax.plot(t,v, color='red', label='sin(t)')
ax.set_xlabel('Time (seconds)')
ax.set_ylabel('Voltage (mV)')
ax.set_title("Sine Wave")
ax.set_xlim([0,2])
ax.set_ylim([-1,1])

# Mark major ticks on X-Axis at 0, 0.2, 0.4, 0.6, 0.8, 1.0, 1.2, 1.4, 1.6, 1.8, and 2.0.
ax.set_xticks([0, 0.2, 0.4, 0.6, 0.8, 1.0, 1.2, 1.4, 1.6, 1.8, 2.0])
# Mark major ticks on Y-Axis at -1, 0, and 1.
ax.set_yticks([-1, 0, 1])

ax.grid(linestyle='--')
ax.legend()

plt.show()
```

## Multi Curve Plot

```py
import numpy as np
import matplotlib.pyplot as plt

fig = plt.figure(figsize=(12,3))
ax = fig.add_subplot(111)

x = np.linspace(0.0, 5.0, num=20)
y1 = x
y2 = x**2
y3 = x**3

ax.plot(x, y1, color='red', marker='o', label='y = x')
ax.plot(x, y2, color='green', marker='s', label='y = x**2')
ax.plot(x, y3, color='blue', marker='^', label='y = x**3')


ax.set_xlabel('X')
ax.set_ylabel('f(X)')

ax.set_title("Linear, Quadratic, & Cubic Equations")
ax.legend()

plt.show()
```

## Scatter Plot (Cars sold by a company)

```py
import numpy as np
import matplotlib.pyplot as plt

fig = plt.figure(figsize=(12,3))
ax = fig.add_subplot(111)

s = [50, 60, 55, 50, 70, 65, 75, 65, 80, 90, 93, 95]
# print(s)
months = list(range(1, 13))
# print(months)

ax.scatter(months, s, c=['green'])

ax.set_xlim([0,13])
ax.set_ylim([20,100])

ax.set_xticks([1, 3, 5, 7, 9, 11])
ax.set_xticklabels(['Jan', 'Mar', 'May', 'Jul', 'Sep', 'Nov'])

ax.set_xlabel('Months')
ax.set_ylabel('No. of Cars Sold')

ax.set_title("Cars Sold by Company 'X' in 2017")

plt.show()
```




# References
- matplotib website: <https://matplotlib.org/>
- matplotlib documentation: <https://matplotlib.org/contents.html>
- matplotlib examples: <https://matplotlib.org/gallery/index.html>
- matplotlib tutorials: <https://matplotlib.org/tutorials/index.html>