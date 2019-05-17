
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

**[`Download the file`](https://drive.google.com/open?id=1zUfKUkhRJxQwrRB_VI6WUURwY1kTsS7q)**

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

**[`Download more experiment results`](https://drive.google.com/open?id=1BM9o5wtju2v6-DuuhGHL8YFKJleCFq5c)**


## GUIsearch_results



## GUI_Style_Consistency_Detection


