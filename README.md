# MRT-Map-Graph-Analysis Project

## Introduction
This Python application leverages clustering techniques to analyze a dataset containing Mass Rapid Transit (MRT) information. Whether you're interested in understanding station patterns, passenger behavior, or optimizing MRT services, this tool provides valuable insights through data-driven clustering.

## About the dataset
`mrtJourneys.xlsx` is a dataset with timestamps as its features and station codes (represented by numerical IDs) as the values. Each observation represents one passenger. We can understand each row as representing the journey of a particular passenger, namely the stations traversed (including order of stations), and othee time-related insights. No 2 consecutive timestamps will have the same feature, i.e. each station will only ever take up one timestamp. A snippet of the data can be seen below.

<img width="668" alt="image" src="https://github.com/dljw98/MRT-Map-Graph-Analysis/assets/72072042/f6d9ec2a-f931-41e0-bbcd-4cf29edb0735">

Using this information, a graph of the MRT map can be created, with the stations as nodes and the train routes between stations as edges. The `NetworkX` package by dschult was used for this. Documentation for this package can be found here: [https://networkx.org/](https://github.com/networkx/networkx)


A generated graph of the dataset can be seen below. To add additional dimensionality to the graph, colors were applied to the edges, with green edges representing routes that experience a below average number of passengers and red edges representing routes that experience an above average number of passengers and red edges:
<img width="668" alt="image" src="https://github.com/dljw98/MRT-Map-Graph-Analysis/assets/72072042/733778d1-a609-440b-b401-fe09b7d0123c">

## Objective
The objective is to improve the travel experiences of MRT passengers as well as to identify key areas that can be optimised by the station and train companies

## Analysis
To conduct this analysis, several objectives needed to be established. Graph principles were applied, namely: Laplacian matrices, clustering (such as spectral clustering), centrality measures (such as closeness centrality)

The selected objectives were:
1. Identifying edges with a higher number of passengers
    - Are there stations that would reap higher benefits from having a higher frequency of trains?
    - Which stations have lower foot-fall -> could some manpower be redirected from these stations to "busier" stations?
2. Identifying journies that traverse a high number of stations
    - What are the trends we can detect by performing feature engineering on the dataset and through EDA?
    - Can we use network analysis to shorten these journies or improve the transport experience of these passengers in some way?
    - Can we use the Laplacian matrix to identify the most optimal ways to add links to shorten the journeys of these passengers?
3. Clustering network through Spectral Clustering and linking clusters using nodes with the highest closeness centrality within each cluster
4. Obtaining the shortest path of every passenger based on start/end station
    - Find passengers that are not taking the shortest path -> recommend shortest path to these passengers to improve their travelling experience
5. Find out what time each station is the most crowded, and get the value counts to further understand the most frequently occured time where there are most stations with peak crowd to formulate recommendations for staff and train allocation
6. Find out the footfall at each time period and the culmulative footfall over a range of time. This can be done over the whole network -> make recommendations to increase station capacities at specific stations or increase frequency of specific trains to prevent overcrowding
7. Squaring or cubing the laplacian matrix can be used to analyse the impact of a fault at a particular station on the rest of the network. Specifically, it can be used to identify the stations that are most affected by a fault at the initial station (stations which are one step away).
    - If a fault occurs at a station (with high centrality measure), squaring the laplacian matrix can help identify which stations are directly connected to the affected station, while cubing the laplacian matrix can help identify which stations are indirectly affected by the fault. This information can then be used to develop contingency plans and alternative routes to minimise the impact of the fault on the network as a whole.


## Snippets of Analysis
<img width="898" alt="image" src="https://github.com/dljw98/MRT-Map-Graph-Analysis/assets/72072042/5ce21ec3-f19b-4859-8a75-6f22e9caa9ae">

<img width="410" alt="image" src="https://github.com/dljw98/MRT-Map-Graph-Analysis/assets/72072042/90221747-d441-4c5a-926a-cf64901a9ebd">


