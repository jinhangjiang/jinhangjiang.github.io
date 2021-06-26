---
layout: post
title: Tutorial | Visualize High-Dimensional Network Data with 3D 360-Degree-Animated Scatter Plot
tags: Tutorial Network-Analysis R Visualization
---

#### _Author: Jinhang Jiang_
#### _Student Researcher at University of Kansas, Business Analytics_

{:refdef: style="text-align: center;"}
![an image alt text]({{ site.baseurl }}/images/3DRotation/download.png "an image title")
{: refdef}
<br/>

## Introduction
We frequently encounter extremely complicated data that are unreadable or uninterpretable in the context of network analysis. 
While several algorithmic frameworks (for example, node2vec) can incorporate the network data into statistical machine learning, 
the resulting data is still high-dimensional and difficult to manage in the term of visualization. 
In this blog, I’ll share with you one of the methods I use to reduce complexity and solve this problem.<br/>

## Data
For the demonstration purpose, the dataset, “email-Eu-core network,” from Stanford’s SNAP is used. You may find the original dataset here: https://snap.stanford.edu/data/email-Eu-core.html. I think it would make more sense if I walk you through the code with a real-world, complex dataset. Thus, I used this dataset instead of simulating data. And this network perhaps has the simplest structures among the available network data on SNAP.<br/>

The order (the number of nodes) of the graph is 1005, and the size (the number of edges) of the graph is 25571. This dataset also came with ground truth labels for each vertex/node. We will use the ground truth label to annotate the vertices when we generate the visualizations. One of the ways to work around it (if you do not have labels) is to use k-means clustering to get labels.<br/>

Note: I completed this code demo in Google Colab. It may require you to configure paths in a different way if you work in your local IDEs. But the logic of the work should be the same.

## Code
### First step: Load all the necessary packages
The core packages you need for generating graph embeddings will be networkx and node2vec. For details of the application, you may refer to this article: [Analyzing Disease Co-occurrence Using NetworkX, Gephi, and Node2Vec](https://medium.com/analytics-vidhya/analyzing-disease-co-occurrence-using-networkx-gephi-and-node2vec-53941da35a0f). The rest of the packages are used for generating the 3D-360-degree scatter plot for our network data.

### Second step: Read the data
Since this is an unweighted graph, I set the weights to be 1 for all the edges in the graph. I converted the datatype of the label’s vertex column to “string” because it will later be indexed for annotating.

### Third step: Import the data into a graph and plot
If we do not perform dimension reduction and find a way to make the graph sparser, the graph in Figure 1 is what you will get, which is unreadable at all. Moreover, the node2vec algorithm requires a networkx graph as input.
<br/>
{:refdef: style="text-align: center;"}
![an image alt text]({{ site.baseurl }}/images/3DRotation/1.png "an image title")<br/>
_Figure 1. Original graph_
{: refdef}
<br/>

### Fourth step: Use node2vec to get embeddings
As you can notice, in the code, I manually calculated a starting point for the vector_size (dimensions) with the order of the graph. 
This practice is inspired by Google’s [Machine Learning Crash Course](https://developers.google.com/machine-learning/crash-course/embeddings/video-lecture). 
And the empirical rule-of-thumb is that ___the size of dimensions is equal to the fourth root of the possible values___.

<script src="https://gist.github.com/jinhangjiang/b23d2caf173f046f5e8dacf50f446c7f.js"></script>

### Fifth step: Visualizing with 3D 360-degree-animated scatter plot
<script src="https://gist.github.com/jinhangjiang/06b1ca78a6d6c70d2cebe7f18c2b9c20.js"></script>

After executing the command of ThreeDplot(model), here is what we got:
<br/>
{:refdef: style="text-align: center;"}
![an image alt text]({{ site.baseurl }}/images/3DRotation/rotation.gif "an image title")<br/>
_Figure 2. 3D 360-degree scatter plot_
{: refdef}
<br/>

For a high-resolution graph, visit this [link](https://github.com/jinhangjiang/jinhangjiang.github.io/blob/master/images/3DRotation/full_rot.gif) for the original gif.<br/>

For reproduction of the results, visit this [link](https://github.com/jinhangjiang/jinhangjiang.github.io/blob/master/code_demo/3DRotation.ipynb) for the notebook.

## Conclusion
In this blog, we used ___node2vec___, ___networkx___, ___tsne (pca)___, ___seaborn___, ___matlibplot___, etc. to make a 3D 360-degree-animated scatter plot to visualize high-dimensional, complex network data.

## Related Readings
[Analyzing Disease Co-occurrence Using NetworkX, Gephi, and Node2Vec](https://medium.com/analytics-vidhya/analyzing-disease-co-occurrence-using-networkx-gephi-and-node2vec-53941da35a0f)<br/>

[Network Analysis with R: Manipulating Network Data](http://jinhangjiang.com/Network-Analysis-in-R-Manipulating-Network-Data/)<br/>

[NetworkX: Code Demo for Manipulating Subgraphs](https://towardsdatascience.com/networkx-code-demo-for-manipulating-subgraphs-e45320581d13)<br/>

[What Is Embedding and What Can You Do with It](http://jinhangjiang.com/What-is-Embedding-and-What-Can-You-Do-with-It/)

----
****
