# Spatiotemporal-Forecasting-Autoencoder-DMD
Spatiotemporal Forecasting Using Neural Networks and Hybrid Methods

The primary goal of this project is to develop and refine forecasting techniques for spatiotemporal data using neural networks, complemented by statistical tools when applicable, to create more pragmatic and parsimonious hybrid methods. These methods have potential applications in various domains, including climate and hydrology.
In this initial exploration, I utilized an autoencoder to process precipitation time series data. Specifically, a set of time series representing precipitation records from \(m\) stations across a defined territory (where \(n\_features = m\)) were fed into the encoder of an autoencoder, which is constructed from a pair of LSTM networks and two dense layers. The dataset used for this test comprises five years of daily records—this is a proof of concept, but it could be easily extended to include more years. The data is treated as a multivariate time series with \(m\) features and 1,826 records (days) in length. It's crucial that the records are clean, with no missing values.
The encoder transforms this multivariate series into latent vectors of dimension `latent_dim` (for this test, `latent_dim = 100`). Each day in the multivariate series is mapped to a latent vector of size `latent_dim`. The decoder of the autoencoder then reconstructs the multivariate series from these latent vectors.
These latent vectors can be interpreted as representing "latent states" of the time series. Unlike in a Hidden Markov Model (HMM), where the latent state is categorical, here, the latent state is a continuous vector. Furthermore, there is no fixed number of latent states; instead, they form a sequence within the latent space of the autoencoder. As a generative model, the autoencoder aims to generate time series data that serves as a forecast for a future horizon of \(k\) days.
To model transitions between these latent vectors, I employed Dynamic Mode Decomposition (DMD), analogous to finding the transition matrix in an HMM. Once DMD is trained, it allows for predictions in the latent space, which can then be decoded by the autoencoder to reconstruct the time series, extending it for \(k\) days into the future. For this task, I utilized the PyDMD package, and I have included a preprint that explains the package's functionality.

In this preliminary implementation, the method has shown promise in capturing patterns accurately, even though the system is not yet fully optimized. The results are encouraging, and there are still additional refinements to be made. 
I've included sample figures, the Python code in a Jupyter notebook, and a portion of the data to keep the file size manageable.



