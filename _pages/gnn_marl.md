---
title: "GNN-MARL"
layout: blog
excerpt: "GNN-MARL"
sitemap: false
permalink: /gnn_marl
---
<style>
    img.img-responsive {
        display: block;
        margin: 0 auto;
    }
</style>    

# GNN-MARL

<b><a href="https://github.com/hex-plex/GNN-MARL">Code and Details</a></b>

<img src="{{ site.url }}{{ site.baseurl }}/images/pubpic/gnn-marl.jpg" class="img-responsive" width="120%" />

<h4>This is an implementation of Communication in MARL using Graph Neural Network. This is been trained and tested on <a href="https://github.com/deepmind/pysc2">StarCraft II</a>, And this has shown improved training and performance metrics throughout all the maps. I have implemented this on top of <a herf = "https://github.com/oxwhirl/pymarl">PyMARL</a> for easier comparative study with respect to other algorithms or implementations like <a href="https://github.com/uoe-agents/epymarl">ePyMARL</a>.</h4>

<h4>Currently we have the following algorithms for training.</h4>

<ul>
    <h4><li> <a href = "https://arxiv.org/abs/1803.11485">QMIX: QMIX: Monotonic Value Function Factorisation for Deep Multi-Agent Reinforcement Learning</a></li></h4>
    <h4><li><a href = "https://arxiv.org/abs/1705.08926">COMA: Counterfactual Multi-Agent Policy Gradients</a></li></h4>
    <h4><li><a href = "https://arxiv.org/abs/1706.05296">VDN: Value-Decomposition Networks For Cooperative Multi-Agent Learning</a></li></h4>
    <h4><li><a href = "https://arxiv.org/abs/1511.08779">IQL: Independent Q-Learning</a></li></h4>
    <h4><li><a href = "https://arxiv.org/abs/1905.05408">QTRAN: QTRAN: Learning to Factorize with Transformation for Cooperative Multi-Agent Reinforcement Learning</a></li></h4>
</ul>

<h4>For communication we have used to different Architecures</h4>

<ul>
    <h4><li><a href = "https://arxiv.org/abs/1609.02907">GConv: Graph Convolutional Network</a></li></h4>
    <h4><li><a href = "https://arxiv.org/abs/1710.10903">GAT: Graph Attention Network</a></li></h4>
</ul>

## Graph Neural Network.

<h4>More Information about the architecture and the execution can be found at <a href="https://hex-plex.github.io/project/gnn-marl/">MultiAgent GNN</a> A brief outline would be as follows</h4>

<img src="{{ site.url }}{{ site.baseurl }}/images/pubpic/gnn.png" class="img-responsive" />

<p style="text-align:center">Pipeline for communication using Graph Neural Network</p>

<h4>The implementation is written in PyTorch and uses a modified version of <a href = "https://github.com/oxwhirl/smac">SMAC</a> which could be found in <a href = "https://hex-plex.github.io/smac-py/">smac-py</a> to include the adjacency matrix as the observation more detail on it can be found <a href = "https://hex-plex.github.io/project/gnn-marl/#adjacency-matrix">here</a>.</h4>

<h4>For a glimpse of the algorithm in action checkout the Output section.</h4>

<h3> Adjacency Matrix </h3>
<h4>An adjacency matrix simply represents the vertices of the graph. For the current problem we have used a few heuristics for joining two nodes with a vertex. They are as below</h4>

<ul>
    <h4><li><b>Communication distance</b> : - Even though their is no restriction in communication having local communication improves cooperation in shared tasks</li></h4>
    <h4><li><b>Unit Type</b> : - Many task benefit from similar units perfoming certain part of the task than other other units cooperating with each other.</li></h4>
</ul>

<h3>Output</h3>
<h4>This is a demo output from the policy whose stats are given above</h4>
<img src="{{ site.url }}{{ site.baseurl }}/images/pubpic/output.gif" width="80%" class="img-responsive" />

<h3>Results</h3>
<h4>Below are the training and test metric of the presented algorithm with <b>QMIX</b> on map 2s3z. The study is limited to the number of experiments due to limitation in computation at the disposal. The presented algorithm does support parallel envs and boosting the process of training. This would be tested soon</h4>

<br>

<table>
    <tr>
        <th>Train</th>
    </tr>
    <tr>
        <td><img src= "{{ site.url }}{{ site.baseurl }}/images/pubpic/train_battle_win_percentage.png"/></td>
        <td><img src= "{{ site.url }}{{ site.baseurl }}/images/pubpic/train_return_mean.png"/></td>
    </tr>
</table>

<br>

<table>
    <tr>
        <th>Test</th>
    </tr>
    <tr>
        <td><img src= "{{ site.url }}{{ site.baseurl }}/images/pubpic/test_battle_win_percentage.png"/></td>
        <td><img src= "{{ site.url }}{{ site.baseurl }}/images/pubpic/test_return_mean.png"/></td>
    </tr>
</table>
