# Physics-Informed-Neural-Networks-Tumour-Growth
Here we use PINNs to predict tumour growth and then run simulated treatment interventions (in this case, immunotherapy)

# Background on PINNs

Originally proposed by Raissi et al [1], PINNs can embed physical information (usually in the form in PDEs) into the loss function 

# Usefulness in tumour growth prediction






# Mathematical modelling

The PINN will embed the Gompertz PDE, which is a particular case of the Generalised Logistic equation:



# Synthetic data visualisation

We will generate data that will follow a modified Gompertz function with Gaussian noise. Adding noise is essential to determine robustness and ensure it resembles
realistic clinical data.

# Dependencies

- ***PyTorch (Framework for deep learning)***
- ***NumPy (for data generation)***
- ***Matplotlib (for data visualisation)***  
- ***Jupiter Notebook (software/environment)***

# References

Original PINN work: https://github.com/maziarraissi/PINNs
[Gompertz equation]
