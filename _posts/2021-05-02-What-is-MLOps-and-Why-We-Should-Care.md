---
layout: post
title: Blog | What is MLOps and Why We Should Care
tags: Blog Data-Science Machine-Learning Review
---

#### _Author: Jinhang Jiang
#### _Student Researcher at ASU Actionable Analytics Lab_

<br/>

{:refdef: style="text-align: center;"}
![an image alt text]({{ site.baseurl }}/images/MLOps/Feature Image.png "an image title")<br/>
_Image by Author_
{: refdef}
<br/>

I came across one of Dr. Ng’s LinkedIn posts two weeks ago. 
He was calling for people to watch one of his latest presentation videos on the topic of MLOps and asking for opinions and spreadings. 
I was busy with the finals, capstone projects, and miscellaneous stuff about the graduation, so I didn’t watch it until today.<br/>

When I was only halfway into the video, I realized that this topic is not one of the six thousand boring topics we saw online in our daily life. 
It is something worth sharing with friends, and it should be discussed in the community and schools much more than it is currently.<br/>

## The bottleneck we all encountered
AI was introduced in the 1950s, and Big Data was introduced in the 1990s, but they did not get so popular until the past decade. 
And until today, there are still so many businesses having a hard time integrating those technologies into their operations.<br/>

For individuals, I will bet 100 bucks that in your past machine learning practice, or in the projects of someone you know, you have encountered the problem: 
no matter how hard you try or how many iterations you trained your model, the accuracy of your model would stop increasing at a certain place where the performance was far away from human work.<br/>

We’d probably all agree that those dilemmas happened highly likely because businesses or individuals could not capture enough data to feed their needs, or the available algorithms are not advanced enough.<br/>
<br/>

{:refdef: style="text-align: center;"}
![an image alt text]({{ site.baseurl }}/images/MLOps/accuracy.png "an image title")<br/>
_Bottleneck of Model Training_
{: refdef}
<br/>

However, today, Andrew Ng has pointed out that there is another solution to the issue: shifting from big data to clean data. 
Below is an example he gave to illustrate his idea. In the graph, we can perceive that if we currently have 500 training examples and want to achieve a 0.6 accuracy score, 
we can either clean the data (improve label consistency) or triple the data size.<br/>

<br/>

{:refdef: style="text-align: center;"}
![an image alt text]({{ site.baseurl }}/images/MLOps/accuracy2.png "an image title")<br/>
_Clean data vs. noisy data_
{: refdef}
<br/>

He also claimed that for certain types of analyses, merely increasing the size of the dataset will not help much, such as voice recognition. 
You have to identify which factor has prevented the model from better performance, like the car sound in the background.<br/>

And we have to note that, for small datasets, label consistency is more important, 
because powerful algorithms will have the ability to average out the loss given a large enough dataset. 
If we look at this statement from a different point of view, we can also expect that the business with a small amount of data will have the chance to leverage AI 
in their operations if they can achieve label consistency and find proper algorithms.<br/>

Andrew also stated that big data problems where there’s a long tail of rare events in the input (web search, self-driving cars, recommender systems) are also small data problems.<br/>

## MLOps
In the presentation, Andrew mentioned that how people usually joke that we tend to spend 80% of the time in a machine learning project on soucing and preparing data, however people only pay most attention to the 20% of the time of training and modeling. 
In other words, suppose we have got the most out of the training process, we still have plenty of room (80%) to work on and improve.<br/>

Yet, when he went through the latest academic papers in the AI community, 99% of them were research for modeling and only 1% were for data. 
He clarified that doing research on boosting modeling technologies is a great thing, but we should recognize and make contributions to the importance of data quality as well.<br/>

> Data is Food for AI

Hence, he promotes the idea of MLOps which helps ensure consistently high-quality data. 
He illustrated the idea in a graph of the lifecycle of an ML project. 
I transformed the original graph a little bit to make it more readable.<br/>
<br/>

{:refdef: style="text-align: center;"}
![an image alt text]({{ site.baseurl }}/images/MLOps/Lifecycle of an ML Project.jpeg "an image title")<br/>
_Clean data vs. noisy data_
{: refdef}
<br/>

Basically, the MLOps team will keep inspecting the process and analyze the possibilities of improving the label/data consistency and quality during the training and deploying phases. 
Its most important task is to ensure consistently high-quality data in all phases of the ML project lifecycle.<br/>

And here is an example of how he would have his team do to make data quality systematic (repeatable and reliable):<br/>
  * _Aske two independent labelers to label a sample of images_ <br/>
  * _Measure consistency between labelers to discover where they disagree_ <br/>
  * _For classes where the labelers disagree, revise the labeling instructions until they become consistent_<br/>

## Takeaways
First, from model-centric to data-centric:<br/>
  * _Model-centric view:_
    * Collect the data you can, and develop a model good enough to deal with the noise in the data
    * Hold the data fixed and iteratively improve the code/model
  <br/>
  * _Data-centric view:_
    * The consistency of the data is paramount. Use tools to improve the data quality; this will allow multiple models to do well
    * Hold the code fixed and iteratively improve the data


Second, current neural network models could be biased. It is easy to achieve a perfect training score on small datasets, but the variance will increase, which means overfitting occurred. 
And that is why we need clean data over noisy data.<br/>

Third, important frontier: MLOps tools to make data-centric AI an efficient and systematic process.<br/>

Fourth, what good data is:
  * Defined consistently (definition of labels y is unambiguous)
  * Cover of important cases (good coverage of inputs x)
  * Has timely feedback from production data (distribution covers data drift and concept drift)
  * Sized appropriately

He also made a live survey at the end of the presentation: who do you think would be on the MLOps team? 
And the attendees seemed to prefer the ML engineers and domain experts for this job. 
And I strongly agree on the necessity of bringing in the domain experts for particular projects. It would be nice if one can handle all, but it is not realistic. 
The domain experts may lack ML knowledge, but they would be the people who know the data best.<br/>

Here is the (video)[https://www.youtube.com/watch?v=06-AZXmwHjo&t=10s] from DeepLearning.AI on youtube, which will take you one hour to watch.

----
****
