# News-Headlines-Dataset-For-Sarcasm-Detection

Past studies in Sarcasm Detection mostly make use of Twitter datasets collected using hashtag based supervision but such datasets are noisy in terms of labels and language. Furthermore, many tweets are replies to other tweets and detecting sarcasm in these requires the availability of contextual tweets.

To overcome the limitations related to noise in Twitter datasets, this **Headlines dataset for Sarcasm Detection** is collected from two news website. [*TheOnion*](https://www.theonion.com/) aims at producing sarcastic versions of current events and we collected all the headlines from News in Brief and News in Photos categories (which are sarcastic). We collect real (and non-sarcastic) news headlines from [*HuffPost*](https://www.huffingtonpost.com/).

This new dataset has following advantages over the existing Twitter datasets:
* Since news headlines are written by professionals in a formal manner, there are no spelling mistakes and informal usage. This reduces the sparsity and also increases the chance of finding pre-trained embeddings.
* Furthermore, since the sole purpose of *TheOnion* is to publish sarcastic news, we get high-quality labels with much less noise as compared to Twitter datasets.
* Unlike tweets which are replies to other tweets, the news headlines we obtained are self-contained. This would help us in teasing apart the real sarcastic elements.

## Data
Each record consists of three attributes:

* ```is_sarcastic```: 1 if the record is sarcastic otherwise 0

* ```headline```: the headline of the news article

* ```article_link```: link to the original news article. Useful in collecting supplementary data

### Reading the data
In python, data can be read using the following function:

~~~~
def parseJson(fname):
    for line in open(fname, 'r'):
        yield eval(line)
~~~~

Example usecase: `data = list(parseJson('./Sarcasm_Headlines_Dataset.json'))`

## Statistics
The general statistics of this dataset along with high-quality Twitter dataset (in terms of label only) provided by [Semeval challenge](https://competitions.codalab.org/competitions/17468) are given in the following table. 

| Statistic/Dataset                              | Headlines | Semeval |
|------------------------------------------------|-----------|---------|
| # Records                                      | 28,619    | 3,000   |
| # Sarcastic records                            | 13,635    | 2,396   |
| # Non-sarcastic records                        | 14,984    | 604     |
| % of pre-trained word embeddings not available | 23.35     | 35.53   |

We can notice that for Headlines dataset, where the text is much more formal in language, the percentage of words not available in word2vec vocabulary is much less than Semeval dataset.

## WordClouds
As a basic exploration, following figures visualize the word clouds through which we can see the types of words that occur frequently in each category.

### Sarcastic Headlines
![Wordcloud of Sarcastic Headlines](https://github.com/rishabhmisra/Sarcasm-Headlines-Dataset/blob/master/wordcloud_sarcastic.png)

### Non-sarcastic Headlines
![Wordcloud of Sarcastic Headlines](https://github.com/rishabhmisra/Sarcasm-Headlines-Dataset/blob/master/wordcloud_non_sarcastic.png)

## Acknowledgements
This dataset was collected from [TheOnion](https://theonion.com) and [HuffPost](https://www.huffingtonpost.com/).

## Cite
Please cite the following articles in suitable format if you use the dataset:

**Text Format**:
```
1. Misra, Rishabh and Prahal Arora. "Sarcasm Detection using News Headlines Dataset." AI Open (2023).
2. Misra, Rishabh and Jigyasa Grover. "Sculpting Data for ML: The first act of Machine Learning." ISBN 978-0-578-83125-1 (2021).
```
**BibTex Format**:
```
@article{misra2023Sarcasm,
  title = {Sarcasm Detection using News Headlines Dataset},
  journal = {AI Open},
  volume = {4},
  pages = {13-18},
  year = {2023},
  issn = {2666-6510},
  doi = {https://doi.org/10.1016/j.aiopen.2023.01.001},
  url = {https://www.sciencedirect.com/science/article/pii/S2666651023000013},
  author = {Rishabh Misra and Prahal Arora},
}

@book{misra2021sculpting,
author = {Misra, Rishabh and Grover, Jigyasa},
year = {2021},
month = {01},
pages = {},
title = {Sculpting Data for ML: The first act of Machine Learning},
isbn = {978-0-578-83125-1}
}
```
