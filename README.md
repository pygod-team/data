# Data Repository for PyGOD

The statistics of the available dataset (#Con. means the number of contextual outliers, while #Strct. means the number of structural outliers. The number of outliers is slightly less than the sum of two types of outliers because of the intersection between two types of outliers.):

| Dataset      | Type      | #Nodes | #Edges  | \#Feat | Avg. Degree | #Con. | #Strct. | #Outliers | Outlier Ratio |
| ------------ | --------- | ------ | ------- | ------ | ----------- | ----- | ------- | --------- | ------------- |
| 'weibo'      | organic   | 8,405  | 407,963 | 400    | 48.5        | -     | -       | 868       | 10.3%         |
| 'reddit'     | organic   | 10,984 | 168,016 | 64     | 15.3        | -     | -       | 366       | 3.3%          |
| 'disney'     | organic   | 124    | 335     | 28     | 2.7         | -     | -       | 6         | 4.8%          |
| 'books'      | organic   | 1,418  | 3,695   | 21     | 2.6         | -     | -       | 28        | 2.0%          |
| 'enron'      | organic   | 13,533 | 176,987 | 18     | 13.1        | -     | -       | 5         | 0.04%         |
| 'inj_cora'   | injected  | 2,708  | 11,060  | 1,433  | 4.1         | 70    | 70      | 138       | 5.1%          |
| 'inj_amazon' | injected  | 13,752 | 515,042 | 767    | 37.2        | 350   | 350     | 694       | 5.0%          |
| 'inj_flickr' | injected  | 89,250 | 933,804 | 500    | 10.5        | 2,240 | 2,240   | 4,414     | 4.9%          |
| 'gen_time'   | generated | 1,000  | 5,746   | 64     | 5.7         | 100   | 100     | 189       | 18.9%         |
| 'gen_100'    | generated | 100    | 618     | 64     | 6.2         | 10    | 10      | 18        | 18.0%         |
| 'gen_500'    | generated | 500    | 2,662   | 64     | 5.3         | 10    | 10      | 20        | 4.0%          |
| 'gen_1000'   | generated | 1,000  | 4,936   | 64     | 4.9         | 10    | 10      | 20        | 2.0%          |
| 'gen_5000'   | generated | 5,000  | 24,938  | 64     | 5.0         | 10    | 10      | 20        | 0.4%          |
| 'gen_10000'  | generated | 10,000 | 49,614  | 64     | 5.0         | 10    | 10      | 20        | 0.2%          |

To use the datasets:

```python
from pygod.utils import load_data
data = load_data('weibo') # in PyG format
```
Alternative download source in Baidu Disk (Chinese): https://pan.baidu.com/s/1afEZaygCRUYWJPtVbzuRYw Access Code: bond

For injected/generated datasets, the labels meanings are as follows. 

- 0: inlier
- 1: contextual outlier only
- 2: structural outlier only
- 3: both contextual outlier and structural outlier

Examples to convert the labels are as follows:

```python
y = data.y.bool()    # binary labels (inlier/outlier)
yc = data.y >> 0 & 1 # contextual outliers
ys = data.y >> 1 & 1 # structural outliers
```

