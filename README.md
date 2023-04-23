# social_network_optimization

## Introduction and Objectives
There is a growing interest in influence maximization in social networks, considering that recent social events ranging from political (Jan 6 US Capital attack) to financial (GameStop short squeeze) have been built through virality on social network channels like Twitter, Facebook and Reddit. Consequently, many political and commercial institutions should aim to strategically target the right people to spread their messages through social networks. 
Many studies  focus on developing and exploring the most influential initial nodes (or seeds), to maximize the spread of an intended message over the social network using greedy heuristics and numerical algorithmic methods. However, the solutions from an integer programming formulation can achieve a theoretical optimal point, which is often not achieved by greedy algorithms. Hence, in this project, we aim to develop an MIO approach to identify the optimal initial seeds in a social network.
The primary objective of this proposed work is to: 
•	Develop a mixed integer program to identify the optimal initial seeds in a directed weighted social network 
•	Compare the solution and performance with a greedy heuristic baseline 
•	Perform sensitivity analysis with extensive numerical instances
•	Extend it to a use case which also considers negative opinion and harms the spread of the intended message

## Methodology
Through our MIO approach, we will identify the individuals to be targeted in a network at the beginning of the campaign in order to maximize the adoption of a product or an opinion. Selecting the optimal set of influential nodes at the beginning will yield a high expected number of activated nodes at the end of the propagation. Each influenced node in the current time period will be likely to influence its follower node in the next time period. We will assume a threshold associated with each node and if the weighted sum of its “influenced following” in the previous time period exceeds the node threshold, the node will get influenced in the current time period. We will also assume some costs associated with each node so that we are constrained by our budget while selecting the initial nodes. The duration of the propagation plays a vital role in understanding and strategizing the impact we desire.  
The decision is whether a given node i will be influenced at time t. Since we are optimizing interventions for each node at each time period, we have exponential number of outcomes and hence, this problem is fit to be an MIO problem

## Formulation
Please refer to the final report for the formulation

## Dataset and Preliminary EDA
We will use the Bitcoin OTC Stanford SNAP Dataset . This is who-trusts-whom network of people who trade using Bitcoin OTC Platform. The network has directed weighted edges where weight represents the amount of trust one node has on another. 
The dataset is used to create a network where every node is considered to be a user and each edge highlights the effect it has on other user (both negative and positive) based on their edge weights obtained from the data. We then create the synthetic data for the influence threshold of every node and the cost of selecting that node for the initial seed. Intuitively, it should be designed such that the following conditions are satisfied: 
1.	Influence Thresholds: Should be directly proportional to the number of “following” nodes and inversely proportional to the number of “follower” nodes
2.	Node Budgets: Should be based on the reach of the node in a network after certain levels (level 1 is their direct followers, level 2 is followers of their followers and so on)
