
# GUI2Vec

Learning GUI Design Vector Space for Assisting Developers with GUI Development

## Dataset construction

The apps(from Rico dataset: http://interactionmining.org/rico) with less than 10 GUI screenshots are filtered out, as it may mean that those apps are not fully explored. There are 2618 apps left. And we take about 84.6% of apps (2,214) for training, 5.4% (142) for validation i.e., tuning the hyperparameters of our model, and the rest 10% (262) for testing. In detail, we have 17,879 intra/inter pairs for training, 1,132 intra/inter pairs for validation, and 2,178 intra/inter pairs for testing. 

Download: https://drive.google.com/drive/folders/1pNXUYAVOBiRDeix2x2Pc_dMhXfr-frC5?usp=sharing()

## Assumption for the GUI Design Style

A pilot study to manually check the assumption for the GUI design style:

We randomly sample 384 pairs of GUIs for manual evaluation, and half of them are from the inter apps, while the other half come from intra apps. Two Master students P1 and P2 are asked to individually check if each pair of GUI is sharing the very similar design style or not and they are not told if the pair of GUIs comes from the same app or not. The results show that 89.32% GUI pairs from the same app are regarded as sharing the similar design format, and 92.71% GUI pairs from different apps are regarded as possessing different design styles. The Cohen’s Kappa metric among annotator’s decisions is 82.03% 

:--------: | :------: | App      |App   |:---:|
---------- | :------: | :------: |:----:|:---:|
P1         | :------: | same     |differ|total|
selection  | same     | 181      |12    |193  |
selection  | differ   | 11       |180   |191  |
:--------: | total    | 192      |192   |384  |

## GUI2Vec Search_TSNE



## Clustering Overall Performance

## GUIsearch_results

## GUI_Style_Consistency_Detection



SQuAD v1.1 Leaderboard (Oct 8th 2018) | Test EM  | Test F1
------------------------------------- | :------: | :------:
1st Place Ensemble - BERT             | **87.4** | **93.2**
2nd Place Ensemble - nlnet            | 86.0     | 91.7
1st Place Single Model - BERT         | **85.1** | **91.8**
2nd Place Single Model - nlnet        | 83.5     | 90.1
