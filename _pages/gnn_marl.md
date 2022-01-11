---
title: Graph Attention based communication in Multi Agent RL
summary: Enabling communication in MultiAgent Reinforcement Learning using Graph.
tags:
- MultiAgent
- Graph Neural Network
- Reinforcement Learning
- StarCraft II
date: "2021-12-05T00:00:00Z"

layout: blog
excerpt: "GNN-MARL"
sitemap: false
permalink: /gnn_marl

# Optional external URL for project (replaces project detail page).
external_link: ""

image:
caption: StarCraft
focal_point: Smart

links:
- icon: github
icon_pack: fab
name: Code and Details
url: https://www.github.com/hex-plex/GNN-MARL
url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
# Associate this project with Markdown slides.
# Simply enter your slide deck's filename without extension.
# E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
# Otherwise, set `slides = ""`.
#slides: example
---


<style>
    img.img-responsive {
        display: block;
        margin: 0 auto;
    }
</style>

<h3 align="center">Graph Attention based communication in Multi Agent RL</h3>
<h6 align="center"><a align="center" href="http://hex-plex.github.io/">Somnath Kumar</a></h6>

[Code and Details](https://github.com/hex-plex/GNN-MARL)

This is an implementation of Communication in MARL using Graph Neural Network. This is been trained and tested on
[StarCraft II](https://github.com/deepmind/pysc2), And this has shown improved training and performance metrics
throughout all the maps. I have implemented this on top of [PyMARL](https://github.com/oxwhirl/pymarl) for easier
comparative study with respect to other algorithms or implementations like
[ePyMARL](https://github.com/uoe-agents/epymarl).

Currently we have the following algorithms for training.
- [**QMIX**: QMIX: Monotonic Value Function Factorisation for Deep Multi-Agent Reinforcement
Learning](https://arxiv.org/abs/1803.11485)
- [**COMA**: Counterfactual Multi-Agent Policy Gradients](https://arxiv.org/abs/1705.08926)
- [**VDN**: Value-Decomposition Networks For Cooperative Multi-Agent Learning](https://arxiv.org/abs/1706.05296)
- [**IQL**: Independent Q-Learning](https://arxiv.org/abs/1511.08779)
- [**QTRAN**: QTRAN: Learning to Factorize with Transformation for Cooperative Multi-Agent Reinforcement
Learning](https://arxiv.org/abs/1905.05408)

For communication we have used to different Architecures

- [**GConv**: Graph Convolutional Network](https://arxiv.org/abs/1609.02907)
- [**GAT**: Graph Attention Network](https://arxiv.org/abs/1710.10903)

### Graph Neural Network.

More Information about the architecture and the execution can be found at [MultiAgent
GNN](https://hex-plex.github.io/project/gnn-marl/)
A brief outline would be as follows

<img src="https://cops-iitbhu.github.io/IG-website//images/pubpic/gnn-marl.jpg" class="img-responsive" />

<p align="center">Pipeline for communication using Graph Neural Network</p>


The implementation is written in PyTorch and uses a modified version of [SMAC](https://github.com/oxwhirl/smac) which
could be found in [smac-py](/smac-py/) to include the adjacency matrix as the observation more detail on it can be found
[here](#adjacency-matrix).

For a glimpse of the algorithm in action checkout the [**Output**](#output) section


## Adjacency Matrix

An adjacency matrix simply represents the vertices of the graph. For the current problem we have used a few heuristics
for joining two nodes with a vertex. They are as below
- **Communication distance** : - Even though their is no restriction in communication having local communication
improves cooperation in shared tasks
- **Unit Type** : - Many task benefit from similar units perfoming certain part of the task than other other units
cooperating with each other.

## Output
This is a demo output from the policy whose stats are given above
<img align="centre" src="https://raw.githubusercontent.com/hex-plex/GNN-MARL/master/media/output.gif" width="80%"
    class="img-responsive" />

## Results

Below are the training and test metric of the presented algorithm with **QMIX** on map 2s3z. The study is limited to the
number of experiments due to limitation in computation at the disposal. The presented algorithm does support parallel
envs and boosting the process of training. This would be tested soon


|Train||
|--|--|
|Battle win percentage| Average Return|
|![](https://raw.githubusercontent.com/hex-plex/GNN-MARL/master/media/train_battle_win_percentage.png)|![](https://raw.githubusercontent.com/hex-plex/GNN-MARL/master/media/train_return_mean.png)|

|Test||
|--|--|
|Battle win percentage| Average Return|
|![](https://raw.githubusercontent.com/hex-plex/GNN-MARL/master/media/test_battle_win_percentage.png)|![](https://raw.githubusercontent.com/hex-plex/GNN-MARL/master/media/test_return_mean.png)|