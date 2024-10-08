## Objective: The notebook aims to model and simulate the Euribor 12-month rate using the Cox-Ingersoll-Ross (CIR) model.


![image](https://github.com/user-attachments/assets/9fd587ef-5ca3-46e4-b755-e952406b77ef)


## Steps:

Data and Term Structure:

It starts by importing market data for Euribor rates at different maturities.
It calculates zero rates from the market data.
It then uses cubic spline interpolation to generate a smooth term structure of zero rates.
CIR Model Calibration:

The CIR model has three parameters: kappa_r, theta_r, and sigma_r.
The notebook defines a function CIR_forward_rate to calculate forward rates based on the CIR model.
An error function, CIR_error_function, is defined to measure the difference between model-implied forward rates and market forward rates.
The fmin function is used to find the optimal parameters that minimize the error function, effectively calibrating the CIR model to the market data.
Monte Carlo Simulation:

The calibrated CIR model is then used to simulate future Euribor 12-month rates using Monte Carlo simulation.
The simulation generates many paths of the interest rate over one year.
The results of the simulation are then used to calculate a confidence interval for the rate at the end of the year and the expected value of the rate.
Resolving NaN Value Issues:

The notebook addresses potential issues with NaN (Not a Number) values in the simulation by incrementally increasing the number of simulations and adjusting rates as needed.
A modified CIR_simulation function is introduced to ensure the simulated rates do not fall below a certain threshold, preventing NaN values.


# Conclusion:

The notebook provides a framework for calibrating the CIR model to market data and using it for interest rate simulation.
![image](https://github.com/user-attachments/assets/a17ab2e7-698a-4ac6-b258-6c794eb1cb58)

The Monte Carlo simulation allows for the estimation of future interest rate distributions, confidence intervals, and expected values.
![image](https://github.com/user-attachments/assets/3b081cc2-a4d3-4aff-b0f5-fe40454beafe)

The steps taken to resolve potential NaN value issues ensure the robustness of the simulation results.

![image](https://github.com/user-attachments/assets/9adae346-7910-4074-9e50-74a6fe9e71bc)

![image](https://github.com/user-attachments/assets/d9a88a95-117e-4e13-b722-aa01590bf392)


Colab File : [CIR MODEL](https://github.com/ParthDave111/Quant-and-Finance-File/blob/main/CIR(1995)_.ipynb)
