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

## Bar Plot using `bar`

### Common Parameters of 'bar'

- `color`: Sets the color of bars.
- `edgecolor`: Sets the color of the border line of bars.
- `width`: Sets the width of bars
- `align`: Aligns the bars w.r.t x-coordinates
- `label`: Sets label to a bar, appearing in legend.

```py
fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)
ax.set(title='Avg. Quarterly Sales',
      xlabel='Quarter', ylabel='Sales (in millions)')
quarters = [1, 2, 3]
sales_2017 = [25782, 35783, 36133]
ax.bar(quarters, sales_2017)
ax.set_xticks(quarters)
ax.set_xticklabels(['Q1-2017', 'Q2-2017', 'Q3-2017'])
plt.show()
```

- Draw `Red color bars` with `black edges`

```py
ax.bar(quarters, sales_2017, color='red', width=0.6, edgecolor='black')
```

```py
fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)
ax.set(title='Avg. Quarterly Sales',
      xlabel='Quarter', ylabel='Sales (in millions)')
quarters = [1, 2, 3]
sales_2017 = [25782, 35783, 36133]
ax.bar(quarters, sales_2017, color='red', width=0.6, edgecolor='black')
ax.set_xticks(quarters)
ax.set_xticklabels(['Q1-2017', 'Q2-2017', 'Q3-2017'])
plt.show()
```

### Plotting Multiple Groups

```py
fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)
ax.set(title='Avg. Quarterly Sales',
      xlabel='Quarter', ylabel='Sales (in millions)')
quarters = [1, 2, 3]
x1_index = [0.8, 1.8, 2.8]; x2_index = [1.2, 2.2, 3.2]
sales_2016 = [28831, 30762, 32178]; sales_2017 = [25782, 35783, 36133]
ax.bar(x1_index, sales_2016, color='yellow', width=0.4, edgecolor='black', label='2016')
ax.bar(x2_index, sales_2017, color='red', width=0.4, edgecolor='black', label='2017')
ax.set_xticks(quarters)
ax.set_xticklabels(['Q1', 'Q2', 'Q3'])
ax.legend()
plt.show()
```

### Barplot Using 'barh'

- `barh` draws the bars horizontally as shown in above image.
- `height` parameter is used to adjust the height of each bar.
- `Horizontal` bar plots are used while comparing values of one category at a time.

```py
fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)
ax.set(title='Avg. Quarterly Sales',
      xlabel='Sales (in millions)', ylabel='Quarter')
quarters = [1, 2, 3]
sales_2017 = [25782, 35783, 36133]
ax.barh(quarters, sales_2017, height=0.6, color='red')
ax.set_yticks(quarters)
ax.set_yticklabels(['Q1-2017', 'Q2-2017', 'Q3-2017'])
plt.show()
```

## Pie Plot

```py
fig = plt.figure(figsize=(6,6))
ax = fig.add_subplot(111)
ax.set(title='Avg. Quarterly Sales')
sales_2017 = [25782, 35783, 36133]
ax.pie(sales_2017)
plt.show()
```

### Common Parameters of 'pie'

- `colors`: Sets the colors of portions.
- `labels`: Sets the labels of portions.
- `startangle`: Sets the start angle at which portion drawing starts.
- `autopct`: Sets the percentage display format of an area, covering portions.

```py
fig = plt.figure(figsize=(6,6))
ax = fig.add_subplot(111)
ax.set(title='Avg. Quarterly Sales')
sales_2017 = [25782, 35783, 36133]
ax.pie(sales_2017)
plt.show()
```

## Create Bar Plot iris sepal length

```py
import numpy as np
import matplotlib.pyplot as plt

fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)

species = ['setosa', 'versicolor', 'viriginica']
index = [0.2, 1.2, 2.2]
sepal_len = [5.01, 5.94, 6.59]

ax.bar(index, sepal_len, color='red', width=0.5, edgecolor='black')

ax.set(title='Mean Sepal Length of Iris Species',
      xlabel='Species', ylabel='Sepal Length (cm)')

ax.set_xlim([0,3])
ax.set_ylim([0,7])

ax.set_xticks([ 0.45, 1.45, 2.45])
ax.set_xticklabels(['setosa', 'versicolor', 'viriginica'])

plt.show()
```

## Bar plot iris measurements

```py
import numpy as np
import matplotlib.pyplot as plt

fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)

sepal_len = [5.01, 5.94, 6.59]
sepal_wd = [3.42, 2.77, 2.97]
petal_len = [1.46, 4.26, 5.55]
petal_wd = [0.24, 1.33, 2.03]
species = ['setosa', 'versicolor', 'viriginica']
species_index1 = [0.7, 1.7, 2.7]
species_index2 = [0.9, 1.9, 2.9]
species_index3 = [1.1, 2.1, 3.1]
species_index4 = [1.3, 2.3, 3.3]

ax.bar(species_index1, sepal_len, color='c', width=0.2, edgecolor='black', label='Sepal Length')
ax.bar(species_index2, sepal_wd, color='m', width=0.2, edgecolor='black', label='Sepal Width')
ax.bar(species_index3, petal_len, color='y', width=0.2, edgecolor='black', label='Petal Length')
ax.bar(species_index4, petal_wd, color='orange', width=0.2, edgecolor='black', label='Petal Width')

ax.set(title='Mean Measurements of Iris Species',
      xlabel='Species', ylabel='Iris Measurements (cm)')

ax.set_xlim([0.5,3.7])
ax.set_ylim([0,10])

ax.set_xticks([1.1, 2.1, 3.1])
ax.set_xticklabels(['setosa', 'versicolor', 'viriginica'])

ax.legend()

plt.show()
```

## hbar plot of iris petal length

```py
import numpy as np
import matplotlib.pyplot as plt

fig = plt.figure(figsize=(12,5))
ax = fig.add_subplot(111)

species = ['setosa', 'versicolor', 'viriginica']
index = [0.2, 1.2, 2.2]
petal_len = [1.46, 4.26, 5.55]

ax.barh(index, petal_len, height=0.5, color='c', edgecolor='black')

ax.set(title='Mean Petal Length of Iris Species',
      xlabel='Petal Length (cm)', ylabel='Species')

ax.set_yticks([0.45, 1.45, 2.45])
ax.set_yticklabels(['setosa', 'versicolor', 'viriginica'])

plt.show()
```

## Histogram Using 'hist'

```py
import numpy as np
np.random.seed(100)
x = 60 + 10*np.random.randn(1000)
fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)
ax.set(title="Distribution of Student's Percentage",
      ylabel='Count', xlabel='Percentage')
ax.hist(x)
plt.show()
```

### Common Parameters of 'hist'

- `color`: Sets the color of bars.
- `bins`: Sets the number of bins to be used.
- `normed`: Sets to `True` where bins display fraction and not the count.

```py
import numpy as np
np.random.seed(100)
x = 60 + 10*np.random.randn(1000)
fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)
ax.set(title="Distribution of Student's Percentage",
      ylabel='Proportion', xlabel='Percentage')
ax.hist(x, color='blue', bins=30, normed=True)
plt.show()
```

## Boxplot Using 'boxplot'

```py
import numpy as np
np.random.seed(100)
x = 50 + 10*np.random.randn(1000)
fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)
ax.set(title="Box plot of Student's Percentage",
      xlabel='Class', ylabel='Percentage')
ax.boxplot(x)
plt.show()
```

### Common Parameters of 'boxplot'

- `labels`: Sets the labels for box plots.
- `notch`: Sets to `True` if notches need to be created around the median.
- `bootstrap`: Number set to indicate that notches around the median are bootstrapped.
- `vert`: Sets to `False` for plotting Box plots horizontally.

- Box plot of Student Percentages can be redrawn by setting `notch`, `bootstrap` and `labels` using the below-shown expression.

```py
ax.boxplot(x, labels=['A'], notch=True, bootstrap=10000)
```

```py
import numpy as np
np.random.seed(100)
x = 50 + 10*np.random.randn(1000)
fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)
ax.set(title="Box plot of Student's Percentage",
      xlabel='Class', ylabel='Percentage')
ax.boxplot(x, labels=['A'], notch=True, bootstrap=10000)
plt.show()
```

## Multiple boxplots

```py
import numpy as np
np.random.seed(100)
x = 50 + 10*np.random.randn(1000)
y = 70 + 25*np.random.randn(1000)
z = 30 + 5*np.random.randn(1000)
fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)
ax.set(title="Box plot of Student's Percentage",
      xlabel='Class', ylabel='Percentage')
ax.boxplot([x, y, z], labels=['A', 'B', 'C'], notch=True, bootstrap=10000)
plt.show()
```

## Horizontal boxplots

```py
import numpy as np
np.random.seed(100)
x = 50 + 10*np.random.randn(1000)
y = 70 + 25*np.random.randn(1000)
z = 30 + 5*np.random.randn(1000)
fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)
ax.set(title="Box plot of Student's Percentage",
      xlabel='Percentage', ylabel='Class')
ax.boxplot([x, y, z], labels=['A', 'B', 'C'], vert=False, notch=True, bootstrap=10000)
plt.show()
```

## Histogram normal distribution

```py
import numpy as np


fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)

np.random.seed(100)
x1 = 25 + 3.0*np.random.randn(1000)

# x, color='blue', bins=30, normed=True
ax.hist(x1, bins=30)
ax.set(title="Histogram of a Single Dataset",
      ylabel='Bin Count', xlabel='X1')

plt.show()
```

## Box Plot of 4 normal distributions

```py
import numpy as np

fig = plt.figure(figsize=(8,6))
ax = fig.add_subplot(111)

np.random.seed(100)
x1 = 25 + 3.0*np.random.randn(1000)
x2 = 35 + 5.0*np.random.randn(1000)
x3 = 55 + 10.0*np.random.randn(1000)
x4 = 45 + 3.0*np.random.randn(1000)

labels = ['X1', 'X2', 'X3', 'X4']
ax.boxplot([x1, x2, x3, x4], labels=labels, notch=True, patch_artist=True, sym='+')

ax.set(title="Box plot of Multiple Datasets",
      xlabel='Dataset', ylabel='Value')
          
plt.show()
```

## Matplotlib Styles

- `matplotlib.pyplot` comes with a lot of styles. Based on the chosen style, the display of figure changes.
- You can view various styles available in `pyplot` by running the following commands.

```py
import matplotlib.pyplot as plt
print(plt.style.available)
```

Output:

```console
['bmh', 'classic', 'dark_background', 'fast', 'fivethirtyeight', 'ggplot', 'grayscale', 'seaborn-bright', 'seaborn-colorblind', 'seaborn-dark-palette', 'seaborn-dark', 'seaborn-darkgrid', 'seaborn-deep', 'seaborn-muted', 'seaborn-notebook', 'seaborn-paper', 'seaborn-pastel', 'seaborn-poster', 'seaborn-talk', 'seaborn-ticks', 'seaborn-white', 'seaborn-whitegrid', 'seaborn', 'Solarize_Light2', 'tableau-colorblind10', '_classic_test']
```

### Using a Style

- A specific style can be invoked with either of the two expressions shown below.

    ```plt.style.use('ggplot')```

    or

    ```plt.style.context('ggplot')```

- Using the later expression with a keyword, `with` is recommended.

### Matplotlib `ggplot` style

```py
with plt.style.context('ggplot'):
    fig = plt.figure(figsize=(8,6))
    ax = fig.add_subplot(111)
    ax.set(title='Avg. Daily Temperature of Jan 2018',
      xlabel='Day', ylabel='Temperature (in deg)',
      xlim=(0, 30), ylim=(25, 35))
    days = [1, 5, 8, 12, 15, 19, 22, 26, 29]
    temp = [29.3, 30.1, 30.4, 31.5, 32.3, 32.6, 31.8, 32.4, 32.7]
    ax.plot(days, temp, color='green', linestyle='--', linewidth=3)
    plt.show()
```

### Composing Styles

- Multiple style sheets can be used together in `matplotlib`.

```py
with plt.style.context(['dark_background', 'seaborn-poster']):
    fig = plt.figure(figsize=(8,6))
    ax = fig.add_subplot(111)
    ax.set(title='Avg. Daily Temperature of Jan 2018',
      xlabel='Day', ylabel='Temperature (in deg)',
      xlim=(0, 30), ylim=(25, 35))
    days = [1, 5, 8, 12, 15, 19, 22, 26, 29]
    temp = [29.3, 30.1, 30.4, 31.5, 32.3, 32.6, 31.8, 32.4, 32.7]
    ax.plot(days, temp, color='green', linestyle='--', linewidth=3)
    plt.show()
```

### Creating a Custom Style

- A style sheet is a text file having extension `.mplstyle`.
- All custom style sheets are placed in a folder, `stylelib`, present in the config directory of `matplotlib`.
- Use the below expression for knowing the Config folder.

```py
import matplotlib
print(matplotlib.get_configdir())
```

- Now, create a file `mystyle.mplstyle` with the below-shown contents and save it in the folder `<matplotlib_configdir/stylelib/`.

```mplstyle
axes.titlesize : 24
axes.labelsize : 20
lines.linewidth : 8
lines.markersize : 10
xtick.labelsize : 16
ytick.labelsize : 16
```

- Reload the matplotlib library with the subsequent expression.

```py
matplotlib.style.reload_library()
```

- A custom style can also be used similar to builtin styles, after reloading the style library.
- use `mystyle` along with `dark_background`.

```py
with plt.style.context(['dark_background', 'mystyle']):
    fig = plt.figure(figsize=(8,6))
    ax = fig.add_subplot(111)
    ax.set(title='Avg. Daily Temperature of Jan 2018',
      xlabel='Day', ylabel='Temperature (in deg)',
      xlim=(0, 30), ylim=(25, 35))
    days = [1, 5, 8, 12, 15, 19, 22, 26, 29]
    temp = [29.3, 30.1, 30.4, 31.5, 32.3, 32.6, 31.8, 32.4, 32.7]
    ax.plot(days, temp, color='green', linestyle='--', linewidth=3)
    plt.show()
```

### `matplotlibrc` file

- `matplotlib` uses all the settings specified in `matplotlibrc` file.
- These settings are known as `rc settings` or `rc parameters`.
- For customization, `rc settings` can be altered in the file or interactively.
- The location of active `matplotlibrc` file used by `matplotlib` can be found with below expression.

```py
import matplotlib
matplotlib.matplotlib_fname()
```

### Matplotlib rcParams

- All `rc settings`, present in `matplotlibrc` file are stored in a dictionary named `matplotlib.rcParams`.
- Any settings can be changed by editing values of this dictionary.
- For example, if you want to change `linewidth` and `color`, the following expressions can be used.

```py
import matplotlib as mpl
mpl.rcParams['lines.linewidth'] = 2
mpl.rcParams['lines.color'] = 'r'
```

### Generate plot with style

```py
with plt.style.context('ggplot'):
    fig = plt.figure(figsize=(8,6))
    ax = fig.add_subplot(111)
    
    sepal_len = [5.01, 5.94, 6.59]
    sepal_wd = [3.42, 2.77, 2.97]
    petal_len = [1.46, 4.26, 5.55]
    petal_wd = [0.24, 1.33, 2.03]
    species = ['setosa', 'versicolor', 'viriginica']
    species_index1 = [0.7, 1.7, 2.7]
    species_index2 = [0.9, 1.9, 2.9]
    species_index3 = [1.1, 2.1, 3.1]
    species_index4 = [1.3, 2.3, 3.3]
    
    ax.bar(species_index1, sepal_len, width=0.2, label='Sepal Length')
    ax.bar(species_index2, sepal_wd, width=0.2, edgecolor='black', label='Sepal Width')
    ax.bar(species_index3, petal_len, width=0.2, edgecolor='black', label='Petal Length')
    ax.bar(species_index4, petal_wd, width=0.2, edgecolor='black', label='Petal Width')

    ax.set(title='Mean Measurements of Iris Species',
          xlabel='Species', ylabel='Iris Measurements (cm)')

    ax.set_xlim([0.5,3.7])
    ax.set_ylim([0,10])

    ax.set_xticks([1.1, 2.1, 3.1])
    ax.set_xticklabels(['setosa', 'versicolor', 'viriginica'])

    ax.legend()

    plt.show()
```

```py
with plt.style.context('seaborn-colorblind'):
    fig = plt.figure(figsize=(8,6))
    ax = fig.add_subplot(111)
    
    sepal_len = [5.01, 5.94, 6.59]
    sepal_wd = [3.42, 2.77, 2.97]
    petal_len = [1.46, 4.26, 5.55]
    petal_wd = [0.24, 1.33, 2.03]
    species = ['setosa', 'versicolor', 'viriginica']
    species_index1 = [0.7, 1.7, 2.7]
    species_index2 = [0.9, 1.9, 2.9]
    species_index3 = [1.1, 2.1, 3.1]
    species_index4 = [1.3, 2.3, 3.3]
    
    ax.bar(species_index1, sepal_len, width=0.2, label='Sepal Length')
    ax.bar(species_index2, sepal_wd, width=0.2, edgecolor='black', label='Sepal Width')
    ax.bar(species_index3, petal_len, width=0.2, edgecolor='black', label='Petal Length')
    ax.bar(species_index4, petal_wd, width=0.2, edgecolor='black', label='Petal Width')

    ax.set(title='Mean Measurements of Iris Species',
          xlabel='Species', ylabel='Iris Measurements (cm)')

    ax.set_xlim([0.5,3.7])
    ax.set_ylim([0,10])

    ax.set_xticks([1.1, 2.1, 3.1])
    ax.set_xticklabels(['setosa', 'versicolor', 'viriginica'])

    ax.legend()

    plt.show()
```

```py
with plt.style.context('grayscale'):
    fig = plt.figure(figsize=(8,6))
    ax = fig.add_subplot(111)
    
    sepal_len = [5.01, 5.94, 6.59]
    sepal_wd = [3.42, 2.77, 2.97]
    petal_len = [1.46, 4.26, 5.55]
    petal_wd = [0.24, 1.33, 2.03]
    species = ['setosa', 'versicolor', 'viriginica']
    species_index1 = [0.7, 1.7, 2.7]
    species_index2 = [0.9, 1.9, 2.9]
    species_index3 = [1.1, 2.1, 3.1]
    species_index4 = [1.3, 2.3, 3.3]
    
    ax.bar(species_index1, sepal_len, width=0.2, label='Sepal Length')
    ax.bar(species_index2, sepal_wd, width=0.2, edgecolor='black', label='Sepal Width')
    ax.bar(species_index3, petal_len, width=0.2, edgecolor='black', label='Petal Length')
    ax.bar(species_index4, petal_wd, width=0.2, edgecolor='black', label='Petal Width')

    ax.set(title='Mean Measurements of Iris Species',
          xlabel='Species', ylabel='Iris Measurements (cm)')

    ax.set_xlim([0.5,3.7])
    ax.set_ylim([0,10])

    ax.set_xticks([1.1, 2.1, 3.1])
    ax.set_xticklabels(['setosa', 'versicolor', 'viriginica'])

    ax.legend()

    plt.show()
```

## Creating Suplots

```py
subplot(nrows, ncols, index)
# 'index' is the position in a virtual grid with 'nrows' and 'ncols'
# 'index' number varies from 1 to `nrows*ncols`.
```

- subplot creates the Axes object at index position and returns it.

```py
fig = plt.figure(figsize=(10,8))
axes1 = plt.subplot(2, 2, 1, title='Plot1')
axes2 = plt.subplot(2, 2, 2, title='Plot2')
axes3 = plt.subplot(2, 2, 3, title='Plot3')
axes4 = plt.subplot(2, 2, 4, title='Plot4')
plt.show()
```

- The above shown code creates a figure with four subplots, having two rows and two columns.
- The third argument, `index` value varied from `1 to 4`, and respective subplots are drawn in `row-major order`.

- create a figure with `three` subplots, where the first subplot spans all columns of first row

```py
fig = plt.figure(figsize=(10,8))

axes1 = plt.subplot(2, 2, (1,2), title='Plot1')
axes1.set_xticks([]); axes1.set_yticks([])

axes2 = plt.subplot(2, 2, 3, title='Plot2')
axes2.set_xticks([]); axes2.set_yticks([])

axes3 = plt.subplot(2, 2, 4, title='Plot3')
axes3.set_xticks([]); axes3.set_yticks([])

plt.show()
```

## Subplots Using 'GridSpec'

- `GridSpec` class of `matplotlib.gridspec` can also be used to create Subplots.
- Initially, a grid with given number of rows and columns is set up.
- Later while creating a subplot, the number of rows and columns of grid, spanned by the subplot are provided as inputs to `subplot` function.

```py
import matplotlib.gridspec as gridspec
import matplotlib.pyplot as plt

fig = plt.figure(figsize=(10,8))
gd = gridspec.GridSpec(2,2)

axes1 = plt.subplot(gd[0,:],title='Plot1')
axes1.set_xticks([]); axes1.set_yticks([])
axes2 = plt.subplot(gd[1,0])
axes2.set_xticks([]); axes2.set_yticks([])
axes3 = plt.subplot(gd[1,-1])
axes3.set_xticks([]); axes3.set_yticks([])

plt.show()
```

### Creating a Complex Layout

```py
fig = plt.figure(figsize=(12,10))
gd = gridspec.GridSpec(3,3)

axes1 = plt.subplot(gd[0,:],title='Plot1')
axes1.set_xticks([]); axes1.set_yticks([])

axes2 = plt.subplot(gd[1,:-1], title='Plot2')
axes2.set_xticks([]); axes2.set_yticks([])

axes3 = plt.subplot(gd[1:, 2], title='Plot3')
axes3.set_xticks([]); axes3.set_yticks([])

axes4 = plt.subplot(gd[2, :-1], title='Plot4')
axes4.set_xticks([]); axes4.set_yticks([])

plt.show()
```

## Create multiple plots

```py
import numpy as np

t = np.arange(0.0, 5.0, 0.01)
s1 = np.sin(2*np.pi*t)
s2 = np.sin(4*np.pi*t)

fig = plt.figure(figsize=(8,6))
axes1 = plt.subplot(2, 1, 1, title='Sin(2*pi*x)')
axes1.plot(t, s1)

axes2 = plt.subplot(2, 1, 2, title='Sin(4*pi*x)', sharex=axes1, sharey=axes1)
axes2.plot(t, s2)

plt.show()
```

```py
import numpy as np


np.random.seed(1000)
x = np.random.rand(10)
y = np.random.rand(10)
z = np.sqrt(x**2 + y**2)

fig = plt.figure(figsize=(8,6))
axes1 = plt.subplot(2, 2, 1, title='Scatter plot with Upper Traingle Markers')
axes1.scatter(x,y, s=80, c=z, marker='^')
axes1.set_xticks([0.0, 0.4, 0.8, 1.2])
axes1.set_yticks([-0.2, 0.2, 0.6, 1.0])

axes2 = plt.subplot(2, 2, 2, title='Scatter plot with Plus Markers')
axes2.scatter(x, y, s=80, c=z, marker='+')
axes2.set_xticks([0.0, 0.4, 0.8, 1.2])
axes2.set_yticks([-0.2, 0.2, 0.6, 1.0])

axes3 = plt.subplot(2, 2, 3, title='Scatter plot with Circle Markers')
axes3.scatter(x, y, s=80, c=z, marker='o')
axes3.set_xticks([0.0, 0.4, 0.8, 1.2])
axes3.set_yticks([-0.2, 0.2, 0.6, 1.0])

axes4 = plt.subplot(2, 2, 4, title='Scatter plot with Diamond Markers')
axes4.scatter(x, y, s=80, c=z, marker='d')
axes4.set_xticks([0.0, 0.4, 0.8, 1.2])
axes4.set_yticks([-0.2, 0.2, 0.6, 1.0])

plt.tight_layout()


plt.show()
```

```py
import numpy as np
import matplotlib.gridspec as gridspec
import matplotlib.pyplot as plt

x = np.arange(1, 101)
y1 = x
y2 = x**2
y3 = x**3

fig = plt.figure(figsize=(8,6))
g = gridspec.GridSpec(2,2)

axes1 = plt.subplot(g[0,0], title='y = x')
axes1.plot(x, y1)

axes2 = plt.subplot(g[1,0], title='y = x**2')
axes2.plot(x, y2)

axes3 = plt.subplot(g[:,1], title='y = x**3')
axes3.plot(x, y3)

plt.tight_layout()

plt.show()
```

### Adding text

- Text can be added to any part of the figure using `text` function.

#### Syntax

```py
text(x, y, s)
# 'x', 'y' represent x and y coordinates of a position.
# 's' is the text or string to be written
```

- Example of adding text

```py

fig = plt.figure(figsize=(8,6))

ax = fig.add_subplot(111)

ax.set(title='Writing Text',
      xlabel='X-Axis', ylabel='Y-Axis',
      xlim=(0, 5), ylim=(0, 9))

x = [1, 2, 3, 4]
y = [2, 4, 6, 8]

ax.scatter(x, y, c=['green'], s=[60], edgecolor='black')

for i in range(len(x)):
    str_temp = '({}, {})'.format(x[i] - 0.2, y[i] + 0.4)
    ax.text(x[i] - 0.4, y[i] + 0.4, str_temp, fontsize=16)

plt.show()

```

## Matplotlib Backend

- `matplotlib` can generate plots in different outputs.
- In general, `backend` refers to everything that occurs from the time of executing a plotting code to generating the figure.
- Backends are of two types.
  - `interactive backends`: Graphical user interfaces like PyGTK, wxPython, Tkinter, qt4, etc.
  - `non-interactive backends`: Image files such as PNG, JPEG, etc.

### Choosing a Backend

- The default backend chosen by matplotlib is available as `backend` setting in `matplotlibrc` file.
- If you want to alter the backend of many figures, change the value of `backend` setting.
- The below expression chooses `WXAgg` backend.

    ```py
    backend : WXAgg
    ```

- You can also use `use` method if you want to go with a specific backend.

    ```py
    import matplotlib
    matplotlib.use('WXAgg') 
    # Above expression must be used before importing pylot
    ```

### Saving Figures

- Once a backend is chosen, a matplotlib figure can be saved in any format supported by it.
- The below shown example saves the plot in png format.

```py
fig = plt.figure(figsize(8,6))
ax = fig.add_subplot(111)
ax.set(title='My First Plot',
      xlabel='X-Axis', ylabel='Y-Axis',
      xlim=(0, 5), ylim=(0,10))
x = [1, 2, 3, 4]; y = [2, 4, 6, 8]
plt.plot(x, y)
plt.figsave('myplot.png')
```

# References
- matplotib website: <https://matplotlib.org/>
- matplotlib documentation: <https://matplotlib.org/contents.html>
- matplotlib examples: <https://matplotlib.org/gallery/index.html>
- matplotlib tutorials: <https://matplotlib.org/tutorials/index.html>