# Steps Performed in the Notebook

## Step 1
# <------------------------ Happy Independence Day ------------------------>

## Step 2
# Clustering with K-Means

## Step 3
# import libraries

## Step 4
### Load Dataset

## Step 5

## Step 6
### Loook Dataset

## Step 7
```python
dataset.head(10)
```

## Step 8
### Shape Dataset

## Step 9
```python
dataset.shape
```

## Step 10
### Check null value present in Dataset

## Step 11
```python
dataset.isnull().sum()
```

## Step 12
### Check data type of each column

## Step 13
```python
dataset.info()
```

## Step 14
### Check duplicate value present in dataset

## Step 15
```python
dataset.duplicated().sum()
```

## Step 16
### Remove CustomerID

## Step 17
```python
dataset.drop(columns='CustomerID',inplace=True)
```

## Step 18
# EDA

## Step 19
```python
from matplotlib import pyplot as plt
import seaborn as sns
```

## Step 20
### Pair plot

## Step 21
```python
sns.pairplot(data = dataset)
plt.show()
```

## Step 22
### Encoding Gender Column

## Step 23
```python
from sklearn.preprocessing import LabelEncoder
encoder = LabelEncoder()
dataset['Gender'] = encoder.fit_transform(dataset['Gender'])
```

## Step 24
# Create Cluster

## Step 25
```python
from sklearn.cluster import KMeans
wcss = []
for i in range(2,21):
...
```

## Step 26
### Use the Elbow Method to find optimal K

## Step 27
```python
plt.plot([i for i in range(2,21)],wcss,marker='o')
plt.grid(axis='both')
plt.xlabel('Number of Cluster')
...
```

## Step 28
# Fit model on best k value

## Step 29
```python
km1 = KMeans(n_clusters=6,init='k-means++')
dataset['Predict'] = km1.fit_predict(dataset)
```

## Step 30
### Check Labels

## Step 31
```python
km.labels_
```

## Step 32
### Look Dataset

## Step 33
```python
dataset.sample(10)
```

## Step 34
# Silhoultte Score

## Step 35
```python
from sklearn.metrics import silhouette_score
silhouette_score(dataset,labels=km1.labels_)
```

## Step 36
# Visualize clusters with color-coding.

## Step 37
```python
# Define custom colors for each hue category
custom_palette = {
    0: "#E6194B",  # Bright Red
...
```

## Step 38
```python
sns.pairplot(data = dataset,hue='Predict',palette=custom_palette)
plt.show()
```

## Step 39
# Evaluate clustering using Silhouette Score

## Step 40
```python
silh_sco = []
n_clus = [j for j in range(2,21)]
for i in range(2,21):
...
```

## Step 41
### Graph of no. of clustering Vs Silhouette Score