---
layout: post
title: Tutorial | Network Analysis in R: Manipulating Network Data
tags: Network-Analysis Tutorial R
	
---

#### _Author: Jinhang Jiang_
#### _Student Researcher at University of Kansas, Business Analytics_

{:refdef: style="text-align: center;"}
![an image alt text]({{ site.baseurl }}/images/NA_in_R_1/0.png "an image title")
{: refdef}
<br/>

## Introduction
Network analysis is a technique that uses graph theory to study complex real-world problems, 
such as computational biology, engineering, finance, marketing, neuroscience, political science, and public health (Kolaczyk et al., 2014). 
In my previous works, I have done quite a lot of network analysis in the python environment with NetworkX and node2vec. 
However, recently I came across the book - “[_Statistical Analysis of Network Data with R_](https://link.springer.com/book/10.1007/978-1-4939-0983-4)” 
(this is the 1st version, and the 2nd version was published in 2020)- 
written by Eric D. Kolaczyk and Gábor Csárdi, which showed me many cool packages (e.g., igraph) in R 
which provides high-quality network analysis in terms of manipulating graphs, descriptive analysis, mathematical modeling, statistical modeling, etc.<br/>

The book came with a list of code demos, which can be found here: https://github.com/kolaczyk/sand.<br/>

This blog is built upon Chapter 2 of the book: Manipulating Network Data, assuming that you already understood the basic concepts of network analysis, 
such as nodes, edges, etc. However, if you need a comprehensive explanation, I encourage you to read the book.<br/>

## What you need:
RStudio (or similar IDEs) and “igraph” (an R package, available in CRAN)<br/>

In case you do not have “igraph” installed:

	{% raw %}
	  ## Download and install the package 
    install.packages("igraph") 
    
    ## Load package 
    library(igraph)
	{% endraw %}
  
## Code
### Create Undirected and Directed Graphs
To manually create a graph, the function “graph.formula” can be used.
<script src="https://gist.github.com/jinhangjiang/236b656ccd0870bfcfe87e6cdb0010d9.js"></script>

To make it more understandable for creating directed graphs, I proposed an airport network consisting of three airports: 
JFK (New York City airport), PEK (Beijing airport), and CDG (Paris airport). 
Thus, the directed graph that I created can be read: we only have one-way flights from JFK to PEK and CDG (assume some travel restrictions applied); 
PEK and CDG are mutually connected, and you can fly both ways.  <br/>

### Get Basic Info of the Graphs
To make the blog concise, the rest of the demo will only focus on undirected graphs. For more reference, please visit the book’s GitHub repository.<br/>

A graph, represented by G = (V, E), is a mathematical structure consisting of a set V of vertices and a set E of edges. 
The number of vertices and the number of edges in the graph are sometimes called the order and size of graph G (Kolaczyk et al., 2014).<br/>

You may use ___V(graph)___ and ___E(graph)___ to check the vertices and edges; use ___vcount(graph)___ and ___ecount(graph)___ to check the order and size of the graph; 
use ___print_all(graph)___ to show the summary of the graph.
<script src="https://gist.github.com/jinhangjiang/d1118eec7407eddfcb7a773df5904361.js"></script>

## Visualize the graph
You may use the command of ___plot(graph)___ to visualize the graph:<br/>
{:refdef: style="text-align: center;"}
![an image alt text]({{ site.baseurl }}/images/NA_in_R_1/1.png "an image title")<br/>
_Figure 1. plot(g)_
{: refdef}
<br/>

## Label the vertices
I made the graph whose vertices were labeled with numbers 1 through N. In practice, you might already have natural labels, such as names. 
So here is how you could label your vertices and how it would look like:

	{% raw %}
    V(g)$name <- c("Adam","Judy","Bobby","Sam","Frank","Jay","Tom","Jerry")
    plot(g) 
	{% endraw %}

{:refdef: style="text-align: center;"}
![an image alt text]({{ site.baseurl }}/images/NA_in_R_1/2.png "an image title")<br/>
_Figure 2: Labeled graph_
{: refdef}
<br/>

## Representations for Graphs
Normally, the graph will be stored in three basic formats: adjacency lists, edge lists, and adjacency matrix (Kolaczyk et al., 2014). <br/>

An adjacency list is a collection of unordered lists. Each unordered list describes the set of neighbors of a specific vertex in the graph within an adjacency list. 
This format is what igraph uses in the graph summary function.<br/>

An edge list is a two-column table to list all the node pairs in the graph. This format is preferred by NetworkX (in python).<br/>

The adjacency matrix’s entries show whether two vertices in the graph are connected or not. If there is a link between two nodes, “i and j,” the row-column indices (i, j) will be marked as 1, otherwise 0. Therefore, the adjacency matrix will be symmetric for undirected graphs. 
Statistical models normally prefer to encode graphs with this format, such as node2vec which requires the adjacency matrix as inputs.<br/>

You can use the functions of ___get.adjlist(graph)___, ___get.edgelist(graph)___, and ___get.adjacency(graph)___ to get the three different formats, respectively.
<script src="https://gist.github.com/jinhangjiang/8e198d7d7b58182441afc945c9874b41.js"></script>

## Operations on Graphs
In practice, we might want to remove certain edges or join graphs to get subgraphs. In this case, the math operators can help you achieve the goal.
<script src="https://gist.github.com/jinhangjiang/c69e88888ac80b4bbbfa6164a696a914.js"></script>

{:refdef: style="text-align: center;"}
![an image alt text]({{ site.baseurl }}/images/NA_in_R_1/3.png "an image title")<br/>
_Figure 3. Operations on graphs_
{: refdef}
<br/>

The graph in (1, 1) is the original graph. The graph in (1, 1) removed two vertices from the original graph. 
The graph in (2, 1) is made of certain edges (the edges were removed from the original graph due to the removal of vertices). 
The graph in (2, 2) is the joined graph of (1, 1) and (2, 1), and it has the same structure as (1, 1).<br/>

## Using Data Frames
In real-world problems, we rarely make graphs manually. Instead, we have to import data. 
For the best practice to manipulate graphs, we normally need to prepare two data files/data frames. 
One of the files needs to contain all the attributes for each vertex in the graph. 
The other file needs to contain the edges in the network (typically an edge list).<br/>

In the book, the author gave an example of a lawyer dataset of Lazega. The information is stored in two different files: ___elist.lazega___ and ___v.attr.lazega___. 
The original data is available in the sand (Statistical Analysis of Network Data) library. Therefore, here is how you would read your own data:<br/>
<script src="https://gist.github.com/jinhangjiang/ef67cede3fc66d32011859e92c3e01de.js"></script>

{:refdef: style="text-align: center;"}
![an image alt text]({{ site.baseurl }}/images/NA_in_R_1/4.png "an image title")<br/>
_Figure 4. Read your own data_
{: refdef}
<br/>

## Conclusion
In this blog, I covered the code for creating directed and undirected graphs, visualizing graphs, 
getting statistics from graphs, labeling vertices, generating different formats of representations, subsetting and joining graphs, 
and reading your own network data with igraph.

## Relevant Readings
[NetworkX: Code Demo for Manipulating Subgraphs](https://towardsdatascience.com/networkx-code-demo-for-manipulating-subgraphs-e45320581d13)<br/>

[Analyzing Disease Co-occurrence Using NetworkX, Gephi, and Node2Vec](https://medium.com/analytics-vidhya/analyzing-disease-co-occurrence-using-networkx-gephi-and-node2vec-53941da35a0f)

## Reference
Statistical Analysis of Network Data with R, by Eric D. Kolaczyk and Csárdi Gábor, Springer, 2014, pp. 13–28.

----
****
