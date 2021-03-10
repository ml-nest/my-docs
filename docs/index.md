# Welcome to MkDocs

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

------- 

## Commands

* `mkdocs new [dir-name]` - Create a **new** project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.


```python
def fn():
    pass
```
### asdf
asdasd
asd


```
Fenced code blocks are like Standard #dfdsf
Markdown’s regular code blocks, except that
they’re not indented and instead rely on
start and end fence lines to delimit the
code block.
```

    def fn():
        pass


#Table markdown table

First Header | Second Header | Third Header
------------ | ------------- | ------------
Content Cell | Content Cell  | Content Cell
Content Cell | Content Cell  | Content Cell

<!-- <a href="http://www.youtube.com/watch?feature=player_embedded&v=aNLIWvk2CRY
" target="_blank"><img src="http://img.youtube.com/vi/aNLIWvk2CRY/0.jpg" 
alt="IMAGE ALT TEXT HERE" width="12" height="12" border="10" /></a> -->

#Figure A Matplotlib figure
```python
import matplotlib.pyplot as plt
plt.plot([2, 4])
```
```python
print(1)
```
## Examples


#Fig Markdown link for an image can be numbered. {#cat#}
![jpg](img/temp.jpg =100x20)

```python
from mlxtend.classifier import EnsembleVoteClassifier
```

```python
plt.plot([2, 4])
```

```python
import plotly.express as px
df = px.data.iris() # iris is a pandas DataFrame
fig = px.scatter(df, x="sepal_width", y="sepal_length")
fig.show()
```


```python
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.gridspec as gridspec
import itertools
from sklearn.linear_model import LogisticRegression
from sklearn.svm import SVC
from sklearn.ensemble import RandomForestClassifier
from mlxtend.classifier import EnsembleVoteClassifier
from mlxtend.data import iris_data
from mlxtend.plotting import plot_decision_regions

# Initializing Classifiers
clf1 = LogisticRegression(random_state=0)
clf2 = RandomForestClassifier(random_state=0)
clf3 = SVC(random_state=0, probability=True)
eclf = EnsembleVoteClassifier(clfs=[clf1, clf2, clf3],
                              weights=[2, 1, 1], voting='soft')

# Loading some example data
X, y = iris_data()
X = X[:,[0, 2]]
```

```python
# Plotting Decision Regions

gs = gridspec.GridSpec(2, 2)
fig = plt.figure(figsize=(20, 16))
labels = ['Logistic Regression',
          'Random Forest',
          'RBF kernel SVM',
          'Ensemble']

for clf, lab, grd in zip([clf1, clf2, clf3, eclf],
                         labels,
                         itertools.product([0, 1],
                         repeat=2)):
    clf.fit(X, y)
    ax = plt.subplot(gs[grd[0], grd[1]])
    fig = plot_decision_regions(X=X, y=y,
                                clf=clf, legend=2)
    plt.title(lab)

plt.show()
```

#Fig Markdown link for an image can be numbered. {#cat#}
<img src="img/temp.jpg" alt="drawing" height = "850" width="1000"/>
