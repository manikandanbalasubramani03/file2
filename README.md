Neighborhood Explosion:

Increased Receptive Field: 

The receptive field of a node, which represents the region of the graph that influences the node's representation, grows larger with each layer in a deep GNN.

Computational Complexity: 

Processing information from a larger neighborhood requires more computation and memory. Deeper GNNs may become computationally expensive due to the increased size of the effective neighborhood.

Over-Smoothing: 

The risk of over-smoothing increases as the neighborhood size expands. Over-smoothing occurs when node representations become too similar, potentially limiting the ability of the model to distinguish between nodes


In deeper GNNs lead to the well-known neighborhood explosion problem since the
number of neighbors grows exponentially with the number of feature propagation layers (Hamilton et This causes tremendous scalability challenges for data sampling, computation, memory, parallelism, and end-to-end training when employing GNNs on large-scale graphs. 



Stack Layer:


They get transformed into the embedding at a level 3 of, node v. 
That is actually an important issue in,

graph neural networks that prevents us from stacking too many layers, uh, together and the important point here that I want to make is introduce you the notion of over-smoothing.


Over Smoothing Problem:

The over-smoothing problem is that kind of node embeddings,you know, converge to the same or very similar value.


First Figure:

So for example, what I'm trying to show here is for a single node, uh,

the receptive field at one layer, one hop away and let's do a two-layer neural network.It's all neighbors and all the neighbors of neighbors.
It's like one-hop neighborhood and two-hop neighborhood.

And if I go to a three-layer neural network

this means that this yellow node is going to collect information from

every other node in the network to combi- to determine its own, uh, embedding.


The embedding of a node is determined by its receptive field,And if two nodes have highly overlapping receptive fields,

there- there- then their embeddings are also going to be most likely, uh, similar.

So this means that if I stack many GNN layers together,then it means nodes will have highly overlapping receptive fields, uh,

which means they will collect information from the same part of the network and they will aggregate it in the same way.So node embeddings will be highly similar.

So it means it can be very hard for us to distinguish between different nodes and this is what we call an over-smoothing problem.


Over Come of Over smoothing:

adding more layers to our graph neural network does not always skip.


Shallow GNN:

each transformation or aggregation function was only one linear transformation.

But we can make aggregation and transformation become deep neural networks by themselves.


for example, we could make the aggregation operator and the transformation operator,

let's say a three-layer- multilayer perceptron network, uh,and not just a simplelayer in the network.



Solution 2

The input features,transform them through the preprocessing step of multilayer perceptron, apply the graph neural network layers,and then again have a couple multilayer,

perceptron layers that do the post-processing of embeddings.

So we can think of these as pre-processing layers that are important when encoding node features.

 it means we are combining classical neural network layers with graph,


SKIP CONNECTIONS:

The message now gets duplicated.

One message goes into the transformation layer and weight update and while the same message also gets dup- duplicated and just kind of forward and then the two branches are summed up.



LAZY GNN
• We reveal a novel perspective to solve the neighborhood explosion problem by exploiting the computation redundancy in training GNNs; 
• A novel shallow model, LazyGNN, is proposed to capture long-distance dependency in graphs for end-to-end graph representation learning through lazy forward and backward propagations; 
• We demonstrate that existing scalable approaches can be compatible with LazyGNN by introducing a highly efficient and scalable mini-batch LazyGNN to handle large-scale graphs based on sampling methods. 
• Comprehensive experiments and studies demonstrate that LazyGNN achieves superior prediction performance and efficiency on large-scale graph datasets.


Remark 1 (Long-distance dependency). 
 LazyGNN is able to capture long-distance dependency in graphs with a small number of feature aggregation layers because LazyGNN accumulatively propagates information to distant nodes in the graphs over many training iterations. In contrast, existing works try to capture long-distance dependency in graphs by increasing the number of feature propagation layers, which is less efficient.

Remark 2 (Over-smoothing). In contrast to many GNN
LazyGNN will not cause the over-smoothing issue because the residual connection point and prevents the over-smoothed solution, as will be

Remark 3 (Computation and memory efficiency). 
LazyGNN uses very few aggregation layers, it significantly reduces the computation and memory cost.

LazyGNN does not need to store intermediate hidden activation values in the aggregation layers because the computation of implicit gradient is agnostic to the forward propagation trajectory, which further reduces memory cost.

Remark 4 (Communication efficiency).

LazyGNN provides a fundamental algorithmic improvement to significantly reduce the communication cost in cross-device feature aggregations for distributed GNN training because it
uses fewer propagations and communication rounds.
