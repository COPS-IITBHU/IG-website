---
title: Graph Attention based communication in Multi Agent RL
layout: blog
excerpt: "MAMI Sem Eval"
sitemap: false
permalink: /mami-sem
---

<style>
    img.img-responsive {
        display: block;
        margin: 0 auto;
    }
</style>

<h2 align="center">MAMI (Multimedia Automatic Misogyny Identification) Sem Eval</h2>
<br>
<h6 align="center"><a align="center" href="https://github.com/utkarsh-iitbhu/">Utkarsh Kumar Sahu</a></h6>
<br>

### Abstract:
In the past few years, there has been a surge of interest 29 Dec 2020 in multi-modal problems, from image captioning to visual question answering and beyond. In this paper, we focus on hate speech detection in multi-modal memes wherein memes pose an interesting multi-modal fusion problem. We try to solve the Facebook Meme Challenge which aims to solve a binary classification problem of predicting whether a meme is hateful or not. A crucial characteristic of the challenge is that it includes ”benign confounders” to counter the possibility of models exploiting unimodal priors. The challenge states that the state-of-theart models perform poorly compared to humans. During the analysis of the dataset, we realized that majority of the data points which are originally hateful are turned into benign just be describing the image of the meme. Also, majority of the multi-modal baselines give more preference to the hate speech (language modality). To tackle these problems, we explore the visual modality using object detection and image captioning models to fetch the “actual caption” and then combine it with the multi-modal representation to perform binary classification. This approach tackles the benign text confounders present in the dataset to improve the performance. Another approach we experiment with is to improve the prediction with sentiment analysis. Instead of only using multi-modal representations obtained from pre-trained neural networks, we also include the unimodal sentiment to enrich the features. We perform a detailed analysis of the above two approaches, providing compelling reasons in favor of the methodologies used.
<br><br>
<img src ="https://user-images.githubusercontent.com/84759422/149627386-61b7605e-c7b7-4fb5-bfa9-b391b9809e3d.png" class="img-responsive" />
<br>
<p style="text-align: center;">This image is classified as harmful, it has misogynist and violent interpretation.</p> 
<br>

### Introduction:
In today’s world, social media platforms play a major role in influencing people’s everyday life. Though having numerous benefits, it also has the capability of shaping public opinion and religious beliefs across the world. It can be used to attack people directly or indirectly based on race, caste, immigration status, religion, ethnicity, nationality, sex, gender identity, sexual orientation, and disability or disease. Hate Speech on online social media can trigger social polarization, hateful crimes. On large platforms such as Facebook and Twitter, it becomes practically impossible for a human to monitor the source and spreading of such malicious activities, thus it is the responsibility of the machine learning and artificial intelligence research community to address and solve this problem of detecting hate speech efficiently.
<br><br>
<img src ="https://user-images.githubusercontent.com/84759422/149627263-e91d94b1-2a6c-4e25-a2fc-359a81f8625d.png" class="img-responsive" />
<br><br>
<img src ="https://user-images.githubusercontent.com/84759422/149631107-82cb0eb2-78c3-4c73-8b05-961eecfc1208.png" class="img-responsive" />
<br><br>
This README.txt file describes the dataset "Don't Patronize Me! An Annotated Dataset with Patronizing and Condescending Language towards Vulnerable Communities", an annotated corpus with PCL (Patronizing and Condescending Language) in the newswire domain. The dataset consists of the following files:
<br><br>
-- README.txt
-- dontpatronizeme_pcl.tsv *
-- dontpatronizeme_categories.tsv *
<br>
* Please note that both files have a Disclaimer at the top. The actual data starts at line 5 for both files.
<br>
where
<br>
-- README.txt is this file.
<br>
-- dontpatronizeme_pcl.tsv contains paragraphs annotated with a label from 0 (not containing PCL) to 4 (being highly patronizing or condescending) towards vulnerable communities.
It contains one instance per line with the following format:
<br>
- &lt;doc-id&gt; &lt;tab&gt; &lt;keyword&gt; &lt;tab&gt; &lt;country-code&gt; &lt;tab&gt; &lt;paragraph&gt; &lt;tab&gt; &lt;label&gt;
<br>
where
<br>
- &lt;doc-id&gt; is the document id in the original NOW corpus (News on Web: https://www.english-corpora.org/now/).
- &lt;keyword&gt; is the search term used to retrieve texts about a target community.
- &lt;country-code&gt; is a two-letter ISO Alpha-2 country code for the source media outlet.
- &lt;paragraph&gt; is the paragraph containing the keyword.
- &lt;label&gt; is an integer between 0 and 4. Each paragraph has been annotated by two annotators as 0 (No PCL), 1 (borderline PCL) and 2 (contains PCL). The combined annotations have been used in the following graded scale:

0 -> Annotator 1 = 0 AND Annotator 2 = 0

1 -> Annotator 1 = 0 AND Annotator 2 = 1 OR Annotator 1 = 1 AND Annotator 2 = 0

2 -> Annotator 1 = 1 AND Annotator 2 = 1

3 -> Annotator 1 = 1 AND Annotator 2 = 2 OR Annotator 1 = 2 AND Annotator 2 = 1

4 -> Annotator 1 = 2 AND Annotator 2 = 2

The experiments reported in the paper consider the following tag grouping: 
- {0,1}   = No PCL
- {2,3,4} = PCL


<img src ="https://user-images.githubusercontent.com/84759422/149627407-a40b994f-e425-4b8d-a539-0bf98a29fd87.png" class="img-responsive" />
<br>
<p style="text-align: center;">Few more examples.</p>
<br>
-- dontpatronizeme_categories.tsv is the *PCL multilabel classification* dataset. It contains one instance per line with the following format:

- &lt;doc-id&gt; &lt;tab&gt; &lt;paragraph&gt; &lt;tab&gt; &lt;keyword&gt; &lt;tab&gt; &lt;country-code&gt; &lt;tab&gt; &lt;span-start&gt; &lt;tab&gt; &lt;span-end&gt; &lt;tab&gt; &lt;span-text&gt; &lt;tab&gt; &lt;pcl-category&gt; &lt;tab&gt; &lt;number-of-annotators&gt;

- &lt;doc-id&gt; is the document id in the original NOW corpus (News on Web: https://www.english-corpora.org/now/).
- &lt;paragraph&gt; is the paragraph containing the keyword.
- &lt;keyword&gt; is the search term used to retrieve texts about a target community.
- &lt;country-code&gt; is a two-letter ISO Alpha-2 country code for the source media outlet.
- &lt;start&gt; is the start character position of the span identified as pcl.
- &lt;end&gt; is the end character position of the span identified as pcl.
- &lt;span&gt; is the span identified as pcl.
- &lt;pcl-category&gt; is the pcl category of the &lt;span&gt; at position &lt;paragraph&gt;[&lt;start&gt;:&lt;end&gt;]
- &lt;number-of-annotators&gt; is the number of annotators agreeing on that label (1 or 2).

<br>
  
<img src ="https://user-images.githubusercontent.com/84759422/149627297-092580b3-78bc-41c5-8c18-90f13dcf316e.png" class="img-responsive" />
 
<p style="text-align: center;">Creating a working model and implementing its pipelines.</p>
<br>
<img src ="https://user-images.githubusercontent.com/84759422/149627600-6bf92262-d506-4cd0-b87e-793c6aa8d48f.png" class="img-responsive" />
 
<p style="text-align: center;">Output which gives a binary classifier as harmful or not.</p>

<br><br>

### Image Captioning:
It tackles the benign text confounders present in the dataset which converts an originally hateful meme into a benign one just by describing what is happening in the image. It shows some of these adversarial samples. They account for 20% of the dataset and thus our hypothesis is that if we can provide our model with this extra knowledge, it will combat these adversarial examples and provide a boost in accuracy. Using object detection and image captioning helps in learning this aspect of the dataset and understanding the behavior of the benign text confounders and thus gives a better performance than the baseline models. Comparing the "actual caption" with the "pre-extracted caption" of the meme will help in understanding whether both are aligned or not. Also, most of the multi-modal baselines tend to focus more on the text modality for the hate speech. Our intuition behind this approach is to find a deeper relationship between the text and the image modalities.

### Sentiment Analysis:
Another approach is to utilize the sentiment information of both modalities to generate richer representations for further prediction. We first obtain the multi-modal contextual representations em from input by using a pre-trained model. In our experiment, we use VisualBERT (Li et al., 2019). However, similar to some other pre-trained models, the VisualBERT focuses more on the correlation between the input modalities, but the text and image in hateful memes are usually connected indirectly. Thus, unimodal sentiments, which are closely related to hate detection, can benefit the prediction. A RoBERTa (Liu et al., 2019) model is then used to obtain the text sentiment embeddings while a VGG (Simonyan & Zisserman, 2014) is applied for visual sentiments. However, due to the limitation of annotated data, we are unable to fine-tune those two models on our dataset. Instead, the RoBERTa is trained on Stanford Sentiment Treebank (Socher et al., 2013) and the visual sentiment model parameters are learned from T4SA dataset (Vadicamo et al., 2017).

