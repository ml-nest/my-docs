# Introduction
- compares local density of the outliers to the local density of its K neighbours
- if a points local density is significantly lower than its K nearest neighbours, it can be called as an anomaly
- this density is calculated by the inverse of the reachability distance


## Selection criteria
- used when the anomaly is very close to the actual points but less densely packed
- will flag high density and sparse clusters as normal, but a loose point near a dense cluster as an anomaly

## How it works?
- Considering a dataset which has already formed clusters

```python
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

# Generate normal (not abnormal) training observations
X = 0.3 * np.random.randn(100, 2) # create a normal distribution between 0 and 1 of the required shape
X_train = np.r_[X + 2, X - 2] # concat multiple array's of the same shape together

# Generate new normal (not abnormal) observations
X = 0.3 * np.random.randn(20, 2)
X_test = np.r_[X + 2, X - 2]
# Generate some abnormal novel observations
X_outliers = np.random.uniform(low=-4, high=4, size=(20, 2))

df = pd.DataFrame(np.r_[X_train, X_test, X_outliers], columns = ['x', 'y'])
df.head()
```
```python
plt.scatter(df['x'], df['y'])
plt.show()
```
- **Step 1:** Find K nearest datapoints using eucleidian distance from the point under consideration, we are assuming K to be 3 in this case

```python
# Getting indices for each of the point
temp = df[['x', 'y']].reset_index()

# Applying cross join to calculate Euclidean distance
# Adding 0 column for cross join
temp[0] = 0
temp = pd.merge(temp, temp, how = 'outer', on = 0)
# Dropping 0 column
del temp[0]

# Calculating Euclidean distance
temp['eu_dist'] = ((temp['x_x'] - temp['x_y'])**2 + (temp['y_x'] - temp['y_y'])**2)**0.5

# Dropping zero values because they will be same point
temp = temp[temp['eu_dist'] != 0]

# Adding a rank by distance to each datapoint to get the closest K datapoint
temp["rank"] = temp.groupby("index_x")["eu_dist"].rank("min", ascending=True)

#let k = 10
k = 10
temp = temp[temp['rank'] <=k]

temp.head()
```
- **Step 2:** Calculate reachability distance from the considered point to its neighbours (which also equals the maximum distance between Kth distance of the other point or the euclidian distance of that point)

```python
# Sorting values to get the kth distance for each point
temp_2 = temp.sort_values(['index_x', 'eu_dist'], ascending = [True,False]).reset_index(drop = True)[['index_x', 'index_y','eu_dist']]

# Getting the kth value
min_indices = []

for i in np.unique(np.array(temp_2['index_x'])):
    min_indices.append(min(temp_2[temp_2['index_x'] == i].index))

kth_distance = temp_2[temp_2.index.isin(min_indices)]


kth_distance = kth_distance.rename(columns={"eu_dist": "kth_dist", "index_x": "point_label"})
del kth_distance['index_y']

kth_distance.head()
```


```python
# Calculating reachability distance
reach_dist = pd.merge(temp_2, kth_distance, left_on = 'index_y', right_on= 'point_label', how = 'left')
del reach_dist['point_label']

reach_dist['rd'] = reach_dist[['eu_dist','kth_dist']].max(axis = 1)
del reach_dist['eu_dist']
del reach_dist['kth_dist']

reach_dist.head()
```


```python
mean_rd = pd.DataFrame(reach_dist.groupby(['index_x'])['rd'].mean()).reset_index()

mean_rd = mean_rd.rename(columns={"index_x": "point_label"})
mean_rd.head()
```
- **Step 3:** Calculate local reachability density

```python
# Getting LRD(local reachability density) for individual points
lrd_all_pts = mean_rd.copy()
lrd_all_pts['lrd'] = 1/lrd_all_pts['rd']
del lrd_all_pts['rd']

lrd_all_pts.head()
```


```python
# Getting average LRD from all the neighbours
avg_lrd = pd.merge(temp_2[['index_x', 'index_y']], lrd_all_pts, left_on = 'index_y', right_on = 'point_label', how = 'left')
avg_lrd = pd.DataFrame(avg_lrd.groupby(['index_x'])['lrd'].mean()).reset_index()
avg_lrd = avg_lrd.rename({"index_x":"point_label", "lrd":"avg_lrd_neigh"}, axis = 1)

avg_lrd.head()
```


- **Step 4:** Calculate lof
```python
# Calculating LOF by dividing average LRD of neighbours to the actual LRD of the point
lof = pd.merge(avg_lrd, lrd_all_pts, on = 'point_label', how = 'left')
lof['lof'] = lof['avg_lrd_neigh']/ lof['lrd']
del lof['lrd']
del lof['avg_lrd_neigh']

lof.sort_values('lof', ascending = False)[:10]
```
- More the value of this LOF is higher, more the probablity of this point becoming an anomaly

```python
# Getting x and y coordinates for the given points
lof_df = pd.merge(df[['x', 'y']].reset_index(), lof, left_on = 'index', right_on = 'point_label', how = 'left')
del lof_df['index']
del lof_df['point_label']

lof_df.head()
```

```python
thresh = 1.8
plt.scatter(lof_df[lof_df['lof'] > thresh]['x'], lof_df[lof_df['lof'] > thresh]['y'])
plt.scatter(lof_df[lof_df['lof'] <= thresh]['x'], lof_df[lof_df['lof'] <= thresh]['y'])

plt.show()
```


## Hyperparameter Selection
- How to select the correct K-value?
    - Minimum K should be considered as the number of points which can be considered as a cluster, so that other clusters with less points can be considered outliers. When K < 10, LOF is highly volatile
    - Max K should be selected as the points to be considered as outliers if clustered together

## Alternatives

How to select the correct value for LOF

User dependendent

## Disadvantages

- LOF < 1 is definitely an inlier but the inverse statement may not be as true
- strong local fluctuations may increase the number of false positives

## Alternatives

- can use feature bagging instead to reduce FP
- can use local outlier probability to reduce the chance of choosing the wrong K

Why reachability distance is considered instead of euclidean distance?