# Experiment 18: Statistical and Specialized Data Visualization Techniques

## Aim:

To study and implement statistical and specialized visualization techniques such as area plots, pie charts, donut charts, boxplots, heatmaps, and bubble plots using Matplotlib and Seaborn libraries in Python.

---

## Theory:

### 1. Importing Libraries

```python
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
import numpy as np
```

- `import matplotlib.pyplot as plt`
  - Imports the `pyplot` module from Matplotlib.
  - Used for creating graphs and visualizations.

- `import seaborn as sns`
  - Imports Seaborn library.
  - Provides advanced statistical visualization tools with attractive themes.

- `import pandas as pd`
  - Imports Pandas library.
  - Used for data handling and manipulation using DataFrames.

- `import numpy as np`
  - Imports NumPy library.
  - Used for numerical operations and random number generation.

---

### 2. Creating Dataset

```python
np.random.seed(0)

df = pd.DataFrame({
    'Category': ['A','B','C','D','E'],
    'Values':[10,70,30,90,60],
    'Sales': np.random.randint(100,500,5),
    'Profit': np.random.randint(10,200,5)
})
```

- `np.random.seed(0)`
  - Sets a fixed seed value.
  - Ensures that randomly generated values remain the same every time the program runs.

- `pd.DataFrame()`
  - Creates a DataFrame from the provided dictionary.

- `'Category'`
  - Stores category labels.

- `'Values'`
  - Stores numerical values for visualization.

- `np.random.randint(100,500,5)`
  - Generates 5 random integers between 100 and 500.

- `np.random.randint(10,200,5)`
  - Generates 5 random profit values between 10 and 200.

---

### 3. Area Plot

```python
plt.fill_between(
    df['Category'],
    df['Values'],
    color='green',
    alpha=0.5
)

plt.show()
```

- `plt.fill_between()`
  - Creates an area plot by filling the area between the X-axis and plotted values.

- `df['Category']`
  - Used as X-axis categories.

- `df['Values']`
  - Used as Y-axis values.

- `color='green'`
  - Sets fill color to green.

- `alpha=0.5`
  - Sets transparency level.

- `plt.show()`
  - Displays the graph.

Area plots are used to visualize cumulative quantities over categories or time.

---

### 4. Multiple Area Plot

```python
sns.set_style("whitegrid")

plt.fill_between(
    df['Category'],
    df['Sales'],
    color='skyblue',
    alpha=0.5,
    label='Sales'
)

plt.fill_between(
    df['Category'],
    df['Profit'],
    color='orange',
    alpha=0.5,
    label='Profit'
)

plt.legend()

plt.show()
```

- `sns.set_style("whitegrid")`
  - Applies a white grid background style.

- `label='Sales'`
  - Assigns label for legend.

- `label='Profit'`
  - Assigns label for second dataset.

- `plt.legend()`
  - Displays legend box.

Multiple area plots compare multiple datasets together.

---

### 5. Pie Chart

```python
plt.pie(
    df['Values'],
    labels=df['Category'],
    autopct='%1.2f%%'
)

plt.show()
```

- `plt.pie()`
  - Creates a pie chart.

- `df['Values']`
  - Defines slice sizes.

- `labels=df['Category']`
  - Assigns labels to pie slices.

- `autopct='%1.2f%%'`
  - Displays percentage values with two decimal places.

Pie charts represent proportional distribution of data.

---

### 6. Donut Chart

```python
fig, ax = plt.subplots()

ax.pie(
    df['Values'],
    labels=df['Category'],
    autopct='%1.1f%%'
)

centre_circle = plt.Circle(
    (0,0),
    0.70,
    fc='white'
)

fig.gca().add_artist(centre_circle)

plt.show()
```

- `plt.subplots()`
  - Creates figure and axis objects.

- `ax.pie()`
  - Creates pie chart on axis.

- `plt.Circle()`
  - Creates a circular shape.

- `(0,0)`
  - Represents center coordinates.

- `0.70`
  - Defines radius of inner white circle.

- `fc='white'`
  - Sets fill color to white.

- `fig.gca().add_artist()`
  - Adds circle object to graph.

Donut charts are modified pie charts with hollow centers.

---

### 7. Boxplot

```python
sns.boxplot(x=df['Values'])

plt.show()
```

- `sns.boxplot()`
  - Creates a boxplot.

- `x=df['Values']`
  - Uses values for statistical distribution.

Boxplots display:

- Median
- Quartiles
- Minimum and maximum values
- Outliers

They are useful for statistical analysis.

---

### 8. Heatmap

```python
corr = df[['Sales','Profit']].corr()

sns.heatmap(
    corr,
    annot=True,
    cmap='coolwarm'
)

plt.show()
```

- `df[['Sales','Profit']]`
  - Selects specific columns.

- `.corr()`
  - Calculates correlation between variables.

- `sns.heatmap()`
  - Creates heatmap visualization.

- `annot=True`
  - Displays numerical values inside cells.

- `cmap='coolwarm'`
  - Applies color theme.

Heatmaps are used to visualize relationships and correlations.

---

### 9. Bubble Plot

```python
plt.scatter(
    df['Sales'],
    df['Profit'],
    s=df['Values'] * 10
)

plt.show()
```

- `plt.scatter()`
  - Creates scatter plot.

- `df['Sales']`
  - Used as X-axis values.

- `df['Profit']`
  - Used as Y-axis values.

- `s=df['Values'] * 10`
  - Controls bubble size.

Bubble plots represent three variables simultaneously.

---

### 10. Advanced Bubble Plot

```python
sns.scatterplot(
    x='Sales',
    y='Profit',
    size='Values',
    hue='Values',
    data=df,
    sizes=(50,300),
    palette='viridis'
)

plt.show()
```

- `sns.scatterplot()`
  - Creates advanced scatter plot.

- `x='Sales'`
  - Defines X-axis data.

- `y='Profit'`
  - Defines Y-axis data.

- `size='Values'`
  - Controls bubble size based on values.

- `hue='Values'`
  - Changes bubble color according to values.

- `data=df`
  - Specifies dataset.

- `sizes=(50,300)`
  - Defines minimum and maximum bubble sizes.

- `palette='viridis'`
  - Applies color palette.

This visualization improves interpretation of multidimensional data.

---

## Conclusion:

Statistical and specialized visualization techniques such as area plots, pie charts, donut charts, boxplots, heatmaps, and bubble plots were successfully implemented using Matplotlib and Seaborn. These visualizations helped in understanding statistical distributions, correlations, and relationships among multiple variables, making data interpretation more effective.
