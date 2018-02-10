# Simulation-under-Independent-Cascades


# Edit: I have shared output. I cannot public this code as its entry level task. But, if you are potential employer, please email me, and I will share my code


The goal of this task is to simulate information cascades from a given node according to the independent cascade model (IC) [1]; and then to discuss differences and shortcomings based on the observed behavior. The description here should be self-contained  even if you are unfamiliar with IC (the reference is included as pdf for completeness). Before we define the actual task we start with some notation and background.

1 Preliminaries
We denote a static directed network as G(V;E; P) with nodes V and edges E ( V X V . The third element P is a function mapping all edges (u, v) to a probability value pn(u, v) specifying the probability of activation of node v given that node u was activated. Note, that the term activation here is used as an umbrella notion for adoption or infection events in a disscusion process on the network, for example, a hashtag spreading in Twitter or a virus spreading in the population of a country. 

We refer to individual instances of such diffusion processes over time through the network G as cascades. Thus, a cascade X = f(ui; ti)g is a set of node-time pairs, each representing the activations of nodes ui at different times ti. We assume a discrete timeline and that each cascade activates a vertex at most once. Among the multiple models for cascade processes, we will focus on the well-studied independent cascade (IC) model initially introduced by Goldenberg et al. [1]. The key intuition behind the model is that, with respect to a given cascade, each node may be in only one of three states: inactive, active, or previously activated. The main assumption in this model is that nodes can only infuence neighbors for a single time period after activation. In other words, a node u that is activated at time t increases the likelihood that its neighbors are activated at time t + 1, but not at t + 2 or any later time.
The IC model has two key parameters: the probability pn(u, v) that a newly activated node u activates a network neighbor v (already defined above for each edge in the graph) and the probability pe(u) that an inactive node spontaneously activates due to external factors. For this task, we will assume that pe(u) = 0;  (every)u (belongs to) V , i.e., no external activations are possible. Then, the probability that an inactive node u gets activated at time t is defined as:
p(u, t) = 1 􀀀 Y  v2N(u;t􀀀1) (1 􀀀 pn(v; u));

where N(u, t-1) is the set of in-neighbors of u which were activated at exactly t-1. Note that if u has been previously activated at time t' <= t, its p(u, t) = 0.
Equipped with the above definitions one can simulate multiple cascades X from a given nodes u in a given network G, which will be the main task in this assignment.


2 Simulation Task
Consider the graph G specified in file: graph.txt. Each row specifies an edge in the graph by three comma separated numbers: (u, v, pn(u, v)) where u is the source node id, v is the destination node id and pn(u; v) is the probability of u activating v. You are also given an observed cascade file cascade.txt which specifies a cascade X in the network starting from node 448 at time 1. Each
row in this file is a pair of numbers (u, t) specifying a node id u and a time t at which u got activated.
The evolution profile of a cascade is a function mapping descrete time steps t tp the total number of activations in the cascade at that time. For example, for the included cascade in cascade.txt, the evolution profile is (1, 1); (2, 3); (3, 6); (4, 24).... and so on, meaning that 1 node was activated at time 1, 3 nodes were activated at time 2, 6 at time 3 and so on.


The goal of this assignment is to evaluate different simulation parametrization (defined below) and how well they approximate the behavior (evolution profile) of the observed cascade from file cascade.txt. For each strategy you will simulate 1000 cascades over the network form graph.txt and plot their average evolution profiles in time and also \envelope" profiles around the average for
+/- one standard deviation. All simulations should start with node 448 being activated at time 1.
Compared parameter settings are specified as follows:

1. Heterogeneous: for this setting you will use the pn(u; v) values for each edge defined in the third column of the graph file graph.txt.
2. Low: for this setting you will assume that pn(u; v) = 0:01 for all edges, thus disregarding the values defined in the graph file.
3. Medium: for this setting you will assume that pn(u; v) = 0:05 for all edges, thus disregarding the values defined in the graph file.
4. High: for this setting you will assume that pn(u; v) = 0:2 for all edges, thus disregarding the values defined in the graph file.


Implement the simulation in a language of your choice and simulate 1000 cascades for each setting, then using the resulting cascades
perform the analysis described next.

3 Analysis
(a) Plot the evolution profile of cascade X from file cascade.txt as well as the average evolution profiles for each of the 4 settings above. This figure should have discrete time on the horizontal axis and number of activation on the vertical axis. Show the one standard deviation envelope around each simulated profile (using error bars or a confidence interval plot: search plot ci for matlab to get
an idea) 
(b) Discuss the observed behavior. Which parameter setting "fits" the observed cascade (from file cascade.txt) best? Why? How can you measure the goodness of fit? What is a possible explanation of the observed behavior of bad fits?
How can you further improve the fit? Discuss all the above.


4 Submission instructions
Submit (1) your code (in a single compressed .gzip le, no executa-
bles) as well as (2) the discussion and plots from the previous section
in a pdf file  no later than 48 hours from
receiving this instructions. 

References
[1] Jacob Goldenberg, Barak Libai, and Eitan Muller. Using complex systems
analysis to advance marketing theory development: Modeling heterogene-
ity effects on new product growth through stochastic cellular automata.
Academy of Marketing Science Review, 2001:1, 2001.
3
 

