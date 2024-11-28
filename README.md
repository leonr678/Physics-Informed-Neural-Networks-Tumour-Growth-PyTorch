# Physics-Informed-Neural-Networks-Tumour-Growth
Here we construct a PINN, using the PyTorch framework, to predict tumour growth and then run simulated treatment interventions (in this case, immunotherapy).

# Background on PINNs

Originally proposed by Raissi et al [1], PINNs can embed physical information (usually in the form in PDEs) into the loss function. We can then calculate the total loss as a linear combination of the physics loss and data loss. This helps the network make predictions with the guidance of the patterns of the physical system at hand.

We will be considering an inverse problem, where instead of passing the PINN known parameters of the physical information (e.g. PDE), we instead give the PINN the task to infer the best parameters, from the properties of the data.

# Usefulness in tumour growth prediction

Clinical tumour growth data is often very noisy and small. This causes networks to struggle to find the underlying pattern in the growth. PINNs allow us to incorporate the governing physical information of the growth process (e.g. though a PDE that measures the rate of change of volume), guiding the network to make predictions according to the dynamics of tumour growth. 


# Mathematical modelling

The PINN will embed the Gompertz PDE, which is a particular case of the Generalised Logistic equation:

dV/dt = $\alpha$ ln(K/V)V

where $\alpha$ and K represent the growth rate and maximum size of the tumour, respectively.

To simulate the effect of immunotherapy, as a ***basic model***, we add a term to the above equation, obtaining:

dV/dt = $\alpha$ ln(k/V)V - $\beta$ IV

where $\beta$ > 0 represents the effect of immune cells on the tumour and the negative sign is due to immunotherapy decreasing the volume. $I(t)$ is a time dependent function that represents the activity of the immune cells. We define $I$ to be sigmoidal (but reflected since the term in the above equation is negative). This represents that the immune response will be slow initially, then will be very effective before eventually not having much of an effect:

$I(t) = \frac{\gamma}{1+\kappa e^{-(t-I_0 ) - \mu}}$

where $\gamma , \kappa$, $I_0$ (starting day of immunotherapy), and $\mu$ are non-negative constants. The constant $\mu$ represents how much delay the treatment has before the process has an effect. We choose $\kappa$ to be high to make the model more realistic - a high $\kappa$ value helps $I(t)$ to start precisely at $t=I_0 + \mu$. Geometrically, we won't see the curve change until day $I_0$ + $\mu$. This sigmoidal nature displays the effect that the volume will start to stop growing (the growth rate will decrease and the curve will flatten) then the volume will drop but will eventually stop dropping due to the cancer cells becoming more resistant and hence the immunotherapy becoming less impactful over time. A more aggressive and effective immunotherapy simulation can be obtained by decreasing $\mu$ and increasing $\gamma$. This model is fairly simplistic, but the main idea to take away is that our PINN is capable of incorporating such models to run simulations of treatment. To make the model more realistic, for example, we can make $\beta$ a time-dependent, decreasing function as tumours can become resistant to immune responses causing the volume to rise again.

# Synthetic data

We will generate data that will follow a modified Gompertz function with Gaussian noise. Adding noise is essential to determine robustness and ensure it resembles realistic clinical tumour growth data.

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
