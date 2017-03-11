# Feature-aware Matrix Factorization Model

This is the implementation based on the following paper:

Tao Chen, Xiangnan He and Min-Yen Kan (2016). [Context-aware Image Tweet Modelling and Recommendation.](https://www.comp.nus.edu.sg/~kanmy/papers/mm16.pdf) In Proceedings of the 24th ACM International Conference on Multimedia (MM'16), Amsterdam, The Netherlands.

We have additionally released two datasets used in our paper. See [data/README.MD] (data/README.MD) for details.


**Please cite our MM'16 paper if you use our code or dataset. Thanks!** 

Author: Tao Chen (http://www.cs.jhu.edu/~taochen)

## Usage

We implemented three feature-aware matrix factorization (FAMF) models that use different features.

  Model | Configuration File | Features
    ------------ | ------------- | -------------
    [Text](https://github.com/kite1988/famf/blob/master/src/main/TextMain.java) | [text.conf] (https://github.com/kite1988/famf/blob/master/conf/text.conf) | Post's contextual words.
    [Visual](https://github.com/kite1988/famf/blob/master/src/main/VisualMain.java) | [visual.conf] (https://github.com/kite1988/famf/blob/master/conf/visual.conf) | Image's visual tags
    [TextVisual](https://github.com/kite1988/famf/blob/master/src/main/TextVisualMain.java) | [text_visual.conf] (https://github.com/kite1988/famf/blob/master/conf/text_visual.conf) | The combination of contextual words and visual tags.
   

### Dataset Preparation

If you are using our [dataset](https://github.com/kite1988/famf/blob/master/data/README.MD#1-dataset-image-tweets-for-recommendation-123mb), please:
* Crawl the tweets from Twitter
* 

crawl the actual posts and images from Twitter, extract necessary features, and 

* Rating file

Each line contains one positive tweet and its paired N negative tweets for a particular user. Each rating consists of four elements: user, post ID, publisher (the author of the post), and the rating (1 denotes the user has retweeted the tweet, 0 not retweeted). The negative tweets could be sampled by our time-aware negative sampling algorithem (details in the paper).

```user_1 486447896191959040 pub_65893 1,user_1 486619477933838336 pub_18 0,user_1 486596611431477248 pub_22 0,user_1 486602569419333632 pub_21 0,user_1 486532028570275840 pub_45 0...```

* Feature file

Each line contains the post ID followed by the word ID (either contextual or visual tags). ID should be integer [0, W), where W is the number of words for that feature.

```544555137272791040,2275 3474 36361 9123 23694 57 714 3112 1212 19505 7409 8011 18770 5878 256 3314 2039```



###How to run

* Change the configuration in [text_visual.conf](https://github.com/kite1988/famf/blob/master/conf/text_visual.conf)
* Run java command:

  ``` java main.TextVisualMain.java conf/text_visual.conf```
 
  If you are training with a large dataset, please allocate more memory to JVM, e.g.,
  
   ``` java -Xmx2g main.TextVisualMain.java conf/text_visual.conf```
ddd
  This code invokes the pipeline of training, testing and evaluation. The evaluation is conducted for a personalized image tweet recommendation task. Please see the paper for detailed description.


   
