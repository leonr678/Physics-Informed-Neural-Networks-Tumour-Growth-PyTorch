# Physics-Informed-Neural-Networks-Tumour-Growth
Here we construct a PINN, using the PyTorch framework, to predict tumour growth and then run simulated treatment interventions (in this case, immunotherapy).

# Background on PINNs

Originally proposed by Raissi et al [1], PINNs can embed physical information (usually in the form in PDEs) into the loss function. We can then calculate the total loss as a linear combination of the physics loss and data loss. This helps the network make predictions with the guidance of the patterns of the physical system at hand.

# Usefulness in tumour growth prediction

Clinical tumour growth data is often very noisy and small. This causes networks to struggle to find the underlying pattern in the growth. PINNs allow us to incorporate the governing physical information of the growth process (e.g. though a PDE that measures the rate of change of volume), guiding the network to make predictions according to the dynamics of tumour growth.


# Mathematical modelling

The PINN will embed the Gompertz PDE, which is a particular case of the Generalised Logistic equation:

dV/dt = $\alpha$ ln(K/V)

where $\alpha$ and K represent the growth rate and maximum size of the tumour, respectively.

To simulate the effect of immunotherapy, as a ***basic model***, we add a term to the above equation, obtaining:

dV/dt = $\alpha$ ln(k/V) + $\beta$ IV

where 

Th

# Synthetic data

We will generate data that will follow a modified Gompertz function with Gaussian noise. Adding noise is essential to determine robustness and ensure it resembles realistic clinical data.

# Dependencies

- ***PyTorch (Framework for deep learning)***
- ***NumPy (for data generation)***
- ***Matplotlib (for data visualisation)***  
- ***Jupiter Notebook (software/environment)***

# Future improvements

- ***Use stochastic modeling for more realistic growth***
- ***Test multiple models on PINN, such as exponential growth***
- ***Different types of simulated treatment intervention*** 

# References

Original PINN work: https://github.com/maziarraissi/PINNs
[Gompertz equation]
