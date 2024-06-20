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
5. 
6. Compressible Non-Newtonian Fluid Based Road Traffic Flow Equation Solved by Physical-Informed Rational Neural Network
   1. 