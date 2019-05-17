
# GUI2Vec

Learning GUI Design Vector Space for Assisting Developers with GUI Development

## Dataset construction

The apps (from **[`Rico dataset`](http://interactionmining.org/rico)**) with less than 10 GUI screenshots are filtered out, as it may mean that those apps are not fully explored. There are 2618 apps left. And we take about 84.6% of apps (2,214) for training, 5.4% (142) for validation i.e., tuning the hyperparameters of our model, and the rest 10% (262) for testing. In detail, we have 17,879 intra/inter pairs for training, 1,132 intra/inter pairs for validation, and 2,178 intra/inter pairs for testing. 

*   **[`Download the data`](https://drive.google.com/open?id=1sBUPegjqehcaqFCXT0vgRnjD-Keg4bdm)**:
    2618 apps, split apps (2214 for training, 142 for validation, and 262 for testing), train_pairs, valid_pairs, test_pairs.


## Assumption for the GUI Design Style

A pilot study to manually check the assumption for the GUI design style:

We randomly sample 384 pairs of GUIs for manual evaluation, and half of them are from the inter apps, while the other half come from intra apps. Two Master students P1 and P2 are asked to individually check if each pair of GUI is sharing the very similar design style or not and they are not told if the pair of GUIs comes from the same app or not. The results show that 89.32% GUI pairs from the same app are regarded as sharing the similar design format, and 92.71% GUI pairs from different apps are regarded as possessing different design styles. The Cohen’s Kappa metric among annotator’s decisions is 82.03%.

**[`Download the style_pair_samples`](https://drive.google.com/open?id=1jKI62P1INAqhx3gX3qNcdrivqfWtCNeK)**


P1           | --       | App    |App   |--
----------   | :------: | :----: |:----:|:---:
--           | --       | same   |differ|total
**Selection**| same     | 181    |12    |193  
**Selection**| differ   | 11     |180   |191  
--           | total    | 192    |192   |384  

P1_o = 0.94, P1_e = 0.5, Kappa rate1 = 0.88
**[`P1 file`](https://drive.google.com/open?id=1ljyvKYqZjoykpnru2fDMORg-ldB3Lhfl)**


P2           | --       | App    |App   |--
----------   | :------: | :----: |:----:|:---:
--           | --       | same   |differ|total
**Selection**| same     | 162    |16    |178  
**Selection**| differ   | 30     |176   |206  
--           | total    | 192    |192   |384  

P2_o = 0.88, P2_e = 0.5, Kappa rate2 = 0.76
**[`P2 file`](https://drive.google.com/open?id=1P3BghWyHmqw4sVDqoE8Kan2XyUMXcyMW)**

*   **[`Download the file`](https://drive.google.com/open?id=1zUfKUkhRJxQwrRB_VI6WUURwY1kTsS7q)**

## GUI2Vec Search_TSNE

T-SNE is used to project the high-dimension embedding to 2-dimension vector for visualization. We visualize the embedding of random design images which are from 20, 30, 50, 100, 150, and 200 apps.


**20 apps**
![Alt text](https://github.com/GUIDesignResearch/GUIDesignResearch/blob/master/III.B.2.GUI_Search_TSNE/20apps.png)

**30 apps**
![Alt text](https://github.com/GUIDesignResearch/GUIDesignResearch/blob/master/III.B.2.GUI_Search_TSNE/30apps.png)
    
**50 apps**
![Alt text](https://github.com/GUIDesignResearch/GUIDesignResearch/blob/master/III.B.2.GUI_Search_TSNE/50apps.png)
    
**100 apps**
![Alt text](https://github.com/GUIDesignResearch/GUIDesignResearch/blob/master/III.B.2.GUI_Search_TSNE/100apps.png)
    
**150 apps**
![Alt text](https://github.com/GUIDesignResearch/GUIDesignResearch/blob/master/III.B.2.GUI_Search_TSNE/150apps.png)
    
**200 apps**
![Alt text](https://github.com/GUIDesignResearch/GUIDesignResearch/blob/master/III.B.2.GUI_Search_TSNE/200apps.png)



## Clustering Overall Performance

To check the quality of GUI embedding with 5 metrics(Homogeneity, Completeness, V-measure, Adjusted Rand Index, and Adjusted Mutual Information), we randomly select apps with the number ranging from 10 to 100. 

10apps  |    HOM   |    COM   |   V-M    |    ARI    |    AMI  
------- | :------: | :------: | :------: | :------:  | :------:
Sift    | 0.196    | 0.376    | 0.257    | 0.096     | 0.129
Hog     | 0.237    | 0.302    | 0.266    | 0.099     | 0.147
Gabor   | 0.229    | 0.331    | 0.27     | 0.099     | 0.158
AE      | 0.263    | 0.319    | 0.288    | 0.149     | 0.174
GUI2Vec | **0.397**| **0.474**| **0.432**| **0.264** | **0.315**

*   **[`Download more experiment results of clustering`](https://drive.google.com/open?id=1BM9o5wtju2v6-DuuhGHL8YFKJleCFq5c)**


## GUIsearch_results

We build a vector space of GUI designs by converting all GUI in the training set into the vectors. Then We randomly select 10 GUIs from 10 apps from our testing dataset, and convert them into vector by our trained model as the queries. For each query, we retrieve the top 10 GUIs whose vectors are most closed to that of query GUI.

*   **[`Download the GUI images of GUI searching`](https://drive.google.com/open?id=1MQSWLb5UhAvP6woD-pL9xZr32VYnW8Ut)**


|P1     | pre(k1)| pre(k2)| pre(k3)| pre(k4)| pre(k5)| pre(k6)| pre(k7)| pre(k8)| pre(k9)| pre(k10)| map     |
|-------| -------| -------| -------| -------| -------| -------| -------| -------| -------| --------| ------  |
|Hog    | 0.8    | 0.75   | 0.67   | 63     | 0.58   | 0.55   | 0.53   | 0.51   | 0.49   | 0.49    | 0.556   |
|Gabor  | 0.3    | 0.4    | 0.4    | 0.35   | 0.32   | 0.28   | 0.27   | 0.25   | 0.24   | 0.24    | 0.364   |
|AE     | 0.8    | 0.85   | 0.7    | 0.7    | 0.68   | 0.68   | 0.63   | 0.61   | 0.59   | 0.59    | 0.35    |
|GUI2Vec|**0.9** |**0.9** |**0.87**|**0.85**|**0.76**|**0.77**|**0.8** |**0.78**|**0.77**|**0.76** |**0.588**|
*   **[`P1 GUI searching result`](https://drive.google.com/open?id=1b4nHoHqwRzkylHM0OzBvZlCOUJ9m9ayb)**

| P2      | pre(k1) | pre(k2) | pre(k3) | pre(k4) | pre(k5) | pre(k6) | pre(k7) | pre(k8) | pre(k9) | pre(k10) | map     |
| ------- | ------- | ------- | ------- | ------- | ------- | ------- | ------- | ------- | ------- | -------- | ------  |
| Hog     | 0.3     | 0.25    | 0.23    | 0.2     | 0.18    | 0.15    | 0.17    | 0.19    | 0.19    | 0.19     | 0.162   |
| Gabor   | 0.1     | 0.1     | 0.13    | 0.13    | 0.1     | 0.1     | 0.09    | 0.8     | 0.07    | 0.06     | 0.093   |
| AE      | 0.2     | 0.3     | 0.27    | 0.28    | 0.22    | 0.23    | 0.23    | 0.24    | 0.22    | 0.22     | 0.158   |
| GUI2Vec |**0.8**  |**0.9**  |**0.83** |**0.85** |**0.86** |**0.85** |**0.83** |**0.83** |**0.79** |**0.8**   |**0.234**|

*   **[`P2 GUI searching result`](https://drive.google.com/open?id=1M_4kLkrOeJw1UViAANwQ2E4gHmtTAKNF)**

| mean    | pre(k1) | pre(k2) | pre(k3) | pre(k4) | pre(k5) | pre(k6) | pre(k7) | pre(k8) | pre(k9) | pre(k10) | map     |
| ------- | ------- | ------- | ------- | ------- | ------- | ------- | ------- | ------- | ------- | -------- | ------  |
| Hog     | 0.55    | 0.5     | 0.45    | 31.6    | 0.38    | 0.35    | 0.35    | 0.35    | 0.34    | 0.34     | 0.359   |
| Gabor   | 0.2     | 0.25    | 0.265   | 0.24    | 0.21    | 0.19    | 0.18    | 0.525   | 0.155   | 0.15     | 0.2285  |
| AE      | 0.5     | 0.575   | 0.485   | 0.49    | 0.45    | 0.455   | 0.43    | 0.425   | 0.405   | 0.405    | 0.254   |
| GUI2Vec |**0.85** |**0.9**  |**0.85** |**0.85** |**0.81** |**0.81** |**0.815**|**0.805**|**0.78** |**0.78**  |**0.411**|

*   **[`Download more experiment results of GUI searching`](https://drive.google.com/open?id=19sKgojM3KTAxZSq0YJMS6YxzO7arUquy)**

## GUI_Style_Consistency_Detection

We randomly select 10 apps from 8 categories. For each of the app, we individually check which GUIs are outliers with different design style from the whole app. Thus, we construct a ground truth dataset of GUI style inconsistency, and we evaluate the performance of different methods with this ground truth. 

| Algorithm | Precision   | Recall      |
| --------- | ----------- | ----------- |
| Hog       | 0.288135593 | 0.708333333 |
| Gabor     | 0.575757576 | 0.791666667 |
| AE        | 0.642857143 | 0.75        |
| GUI2Vec   | 0.913043478 | 0.875       |

*   **[`Download more experiment results of GUI Style Consistency Detection`](https://drive.google.com/open?id=1CB5-al7ox12Nh0DSCgQLtATRN3LtiiO4)**



