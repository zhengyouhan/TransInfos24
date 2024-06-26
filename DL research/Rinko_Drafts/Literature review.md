## Literature review

This part will introduce the development of GNN implementation in traffic forecasting. In this part, I shall list a couple of iconic methods. But since the proposed method is still in consideration, it's better to leave this part as a list for now. In final draft, only several literature in this list will be chosen based on their relevance to the proposed method.

1. “Short-term traffic forecasting: Modeling and learning spatio-temporal relations in transportation networks using graph neural networks" (2015)
   1. As one of the first attempts to utilize GNN in traffic forecasting, Shahsavari proposed a method considering the temporal and spatial correlation between sensors in transportation network.
   2. features captured by sensors are:
      1. flow
      2. density
      3. speed
   3. in the graph, edges represent the spatial interrelations forced by network topology: length, capacity and directions.
   4. And the GNN is trained as a supervised learning model to predict short-term future traffic.
   5. This is an example of naive implementations of GNN in traffic forecasting. Those works' achievement is sketching a graph framework that can interpret the information of transportation science and incorporate machine learning scheme upon it.
2. “Diffusion convolutional recurrent neural network: Data-driven traffic forecasting"(DCRNN) (2017)
   1. DCRNN is established to tackle challenges:
      1. complex spatial dependency on road networks
      2. non-linear temporal dynamics with changing road conditions
      3. inherent difficulty of long-term forecasting
   2. DCRNN incorporates both spatial and temporal dependency in the traffic flow. It captures the spatial dependency using the encoder-decoder architecture with scheduled sampling. Generally speaking, DCRNN models spatial dependency as diffusion process on a directed graph by proposing diffusion convolution.
   3. DCRNN considers temporal dependencies using diffusion convolutional gated recurrent units with diffusion convolution. 
   4. Compared with ARIMA, Vector auto-regression, support vector regression, Feed-forward neural network, and fully connected long-short-term-memory.
3. "Spatial-Temporal Graph Convolutional Network" (STGCN) (2018)
   1. STGCN aims to tackle the time series prediction problem in traffic domain which enables much faster training speed with fewer parameters. 
   2. STGCN consists of two spatial-temporal convolutional blocks, followed by a fully connected layer. Each ST-Conv includes two temporal gated convolution layers that surround one spatial graph convolutional layer for considering spatial dependencies. 
   3. Chebyshev polynomial is used in localizing the filter and therefore do the elimination of parameters. The number of parameter of Cheb poly is restricted by kernel size which determines the maximum radius of the convolution from central nodes.
   4. Compared with ARIMA, FNN, FC-LSTM, DCRNN
4. "T-GCN: A Temporal Graph Convolutional Network for Traffic Prediction" (T-GCN) (2018)
   1. T-GCN manages to capture spatial and temporal dependencies simultaneously by implement a combination of graph convolutional network(GCN) and gated recurrent unit(GRU). 
      1. GCN is used to learn complex topological structure to capture the spatial dependence
      2. GRU is used to learn dynamic changes of traffic data to capture the temporal dependence.
   2. ![image-20240619083719646](C:\Users\hanzh\AppData\Roaming\Typora\typora-user-images\image-20240619083719646.png)This picture illustrate the framework with a much more direct way. 
   3. And this is basically all of this method. Simple and efficient.
5. "Incorporating Dynamicity of Transportation Network with Multi-Weight Traffic Graph Convolutional Network for Traffic Forecasting"(MW-TGC) 2020
   1. This work defines the adjacent matrices to include features such as speed limit, distance and the angle between two road segments. 
   1. In this model. a spatially isolated dimension reduction operation is applied to the combined features to learn their dependencies and reduce the output size to a level that is computationally feasible. 
   1. The framework is formulated as a Seq2Seq model with LSTM units. And it is used to learn temporal relationships from multi-weighted graph convolution. 
   1. MW-TGC is used to compare with TGC-LSTM, STGCN, Seq2Seq
6. "Attention based spatial-temporal graph convolutional networks for traffic forecasting"(ASTGCN)(2019)
   1. The works before ASTGCN fail to capture dynamic spatial-temporal correlations of traffic data. (i.e. short-term, daily and weekly)
   2. ASTGCN consists of three independent components for hourly daily and weekly time intervals. And each of them has several spatial-temporal blocks consisting of spatial and temporal attention mechanisms to capture dynamic spatial-temporal correlations, followed by graph convolutions for capturing spatial patterns and standard convolutions for describing temporal features.
      1. a spatial attention is applied to model the complex spatial correlations between different locations.
      2. a temporal attention is applied to capture the dynamic temporal correlations between different times.
      3. The S-T Conv consists of graph convolutions capturing spatial features from the topological structure of original network and convolutions in the temporal dimension for describing dependencies from nearby time slices.
   3. compared to ARIMA, STGCN,
7. "Spatio-Temporal Meta Learning for Urban Traffic Prediction" (ST-MetaNet) (2022)
   1. This work is based on previous work on graph attention networks and encoder-decoder. 
   2. ST-MetaNet employs a sequence-to-sequence architecture, consisting of an encoder to learn historical information and a decoder to make predictions step by step. Specifically, the encoder and decoder have the same network structure, consisting of meta graph attention networks and meta recurrent neural networks, to capture diverse spatial and temporal correlations, respectively. Furthermore, the weights (parameters) of meta graph attention networks and meta recurrent neural networks are generated from the embeddings of geo-graph attributes and the traffic context learned from dynamic traffic states.
   3. So, it has four components: A RNN for embedding the historical data sequence; a Meta-knowledge learner learn from nodes and edges attributes; Meta-GAT for capturing diverse spatial correlations from meta-knowledge of all nodes and edges; a Meta-RNN for capturing temporal correlations from meta-knowledge of all nodes.
   4. Compared to ARIMA, Seq2Seq, GAT-Seq2Seq and DCRNN
8. "Traffic Graph Convolutional Recurrent Neural Network: A Deep Learning Framework for Network-Scale Traffic Learning and Forecasting"(TGC-LSTM) (2019)
   1. They added two regularization terms to the model's loss function to enhance the interpretability of their model.
      1. L1-norm on graph convolution weights
      2. an L2-norm on graph convolution features.
   2. Moreover, by introducing the neighborhood matrix and the free flow reachability matrix, they defined the k-order traffic graph convolution (TGC) in order to consider both graph edge properties (e.g., the distance between sensing locations) and high-order neighborhood in the traffic graph.
   3. This model is proposed that it can identify roadway segments in traffic networks which is regarded as an aspect of the interpretability of a deep learning model(?)
   4. This model is compared to DCRNN, Conv+LSTM, SGC+LSTM
9. "Graph WaveNet for Deep Spatial-Temporal Graph Modeling" (Graph WaveNet) (2019)
   1. Two challenges the WaveNet tries to tackle:
      1. explicit graph structure does not necessarily reflect the true dependency and genuine relation may be missing due to incomplete connections in the data.  
      2. RNNs and CNNs employed in previous works are hindering modeling long-range temporal sequences.
      3. So, the Graph WaveNet consists of several spatial - temporal layers. Each of them is comprised of a gated temporal convolution module followed by a graph convolution layer. And Graph WaveNet learns an adaptive dependency(adjacency) matrix and assembles the standard graph convolution with dilated casual convolution to learn the graph structure dynamicslly and handle long sequences.
10.   GMAN
   1. a graph multi-attention network which adopts a spatial-temporal encoder-decoder architecture.

Listed above, DL methods have drawn great attention from both industry and academia, and achieved great success in many real-world applications. However, these methods also have defects. 

First, without the physical knowledge to guarantee generalization ability, the data-driven models are very likely to lose effectiveness in scenarios that are not sampled by the training data. Second, the “black-box” structure of deep learning models introduces unknown risks in the ITS, which may cause potential threats to urban safety

1. Compressible Non-Newtonian Fluid Based Road Traffic Flow Equation Solved by Physical-Informed Rational Neural Network
2. STDEN: Towards Physics-Guided Neural Networks for Traffic Flow Prediction

simulation-based 

finishing this draft 

do  some research in other field



