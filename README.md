# Physics-Informed-Neural-Networks-Tumour-Growth
Here we construct a PINN, using the PyTorch framework, to predict tumour growth.

# Background on PINNs

Originally proposed by Raissi et al [1], PINNs can embed physical information (usually in the form in PDEs) into the loss function. We can then calculate the total loss as a linear combination of the physics loss and data loss. This helps the network make predictions with the guidance of the patterns of the physical system at hand.

We will be considering an inverse problem, where instead of passing the PINN known parameters of the physical information (e.g. PDE), we instead give the PINN the task to infer the best parameters, from the properties of the data.

# Usefulness in tumour growth prediction

Clinical tumour growth data is often very noisy and small. This causes networks to struggle to find the underlying pattern in the growth. PINNs allow us to incorporate the governing physical information of the growth process (e.g. though a PDE that measures the rate of change of volume), guiding the network to make predictions according to the dynamics of tumour growth. 


# Mathematical modelling

The PINN will embed the Gompertz PDE, which is a particular case of the Generalised Logistic equation:

dV/dt = $\alpha$ ln(K/V)V

where $\alpha$ and K represent the growth rate and maximum size of the tumour, respectively.

# Synthetic data

We will generate data that will follow a modified Gompertz function with Gaussian noise. Adding noise is essential to determine robustness and ensure it resembles realistic clinical tumour growth data.

# Dependencies

- ***PyTorch (Framework for deep learning)***
- ***NumPy (for data generation)***
- ***Matplotlib (for data visualisation)***  
- ***Jupiter Notebook (software/environment)***

# Usage

Open the code in Jupiter Notebook. After making sure all of the necessary libraries are installed, run the file. Adjust noise and model as needed.

# Future improvements

- ***Use stochastic modeling for more realistic growth***
- ***Test multiple models on PINN, such as exponential growth***
- ***Simulated treatment intervention*** 

# References

Original PINN work: https://github.com/maziarraissi/PINNs
