## DEEP LEARNING WORK 






## Project 1  Comparision of Multilevel percepton vs CNN for time series analysis prediction 

![image](https://github.com/user-attachments/assets/cddbee59-a1aa-4c10-ac9e-deb1f03229a8)

image is only for reference 

Code : 

Project Report 

In this report, we document our process of developing and evaluating deep learning models for
predicting financial time series, focusing on optimizing parameter configurations for trading
models. We began by analyzing the properties of a chosen security’s (NVIDIA stock) price data
in its original form, a stationary transformation, and a fractionally differenced version. We fetched
data from Yahoo Finance for the period 01-01-20217 to 01-01-2025.
Next, we implemented Multi-Layer Perceptron (MLP) models to predict each version of the time
series and assess their performance. To further enhance prediction accuracy, we transformed the
data into image representations using Gramian Angular Field (GAF) and trained Convolutional
Neural Networks (CNNs) on these representations. We then compared the predictive capabilities
of MLPs and CNNs, evaluating their effectiveness based on model performance metrics.
Our findings provide insights into how different data transformations impact predictive accuracy
and how model architecture influences performance in time series forecasting.
Finally, we have summarized result of step 2 and step 3 in final page of the report with our
recommendation.

## Step 1: Analysing the Properties of NVIDIA Stock Price
After thorough brainstorming, we decided to do a time series analysis on equity (NVIDIA). During
the discussion, it was emphasized to research and analyze NVDA stock as it has high liquidity and
volatility within the data.

## Data collection:
To get 2000 observation points, data from 20th Jan 2017 to 1st Jan 2025 was considered
Statistical Analysis:
For 2000 observations, when the price was analyzed, the mean was around 25.90 as the losing
price. There was a standard deviation of 34.44 and the minimum price point of the observation
was 2.35, while the maximum price point of the observed data was 148.86. 

![image](https://github.com/user-attachments/assets/b9aed75a-38e9-43e9-ac49-8f576607bedb)

The skewness (a measure of the asymmetry of distribution) of the data was around 2.126, which
means it was positively skewed and the distribution was longer on the right side. Also, Kurtosis
(tailedness) was around 3.58 for all the observations.
From skewness and kurtosis, we were able to come to conclusion that data is not normally
distributed and might require transformation for non-parametric statistical analysis in the future
part of the GWP.
Persistence is the tendency of a time series to retain its current state. Mainly for persistence
analysis, the autocorrelation function is leveraged. The autocorrelation function (ACF) can help in
identifying seasonality, hidden patterns, and dependencies in time series data. 

![image](https://github.com/user-attachments/assets/b3c507e8-aa98-469a-812c-d6ad823d6b48

While analyzing ACF, we discovered the following interpretation from our observation in the time
series :
● There was strong initial autocorrelation as the chart started with high autocorrelation as it
was close to 1.0 at lag 0. This suggested that time series might be perfectly correlated with
itself
● Discovery of short-term memory as autocorrelation drops sharply within the range of 0-
250, and it was interpreted that past values quickly lose their predictive power for future
values. This can also be related to the fundamental growth of stock within the period of
2017-2018.
● A short-term cycle or seasonality was also discovered while looking at data at 1500, but
seasonality is not very strong
● For the lags beyond 1000, auto correlation dips into negative territory, and it can be
interpreted that there is negative correlation from past data.
● ACF decays faster as it was visible in the chart, and it doesn't show any persistent and longterm pattern, which concludes that the time series is most likely stationary.
● We would now confirm our claim of stationarity with advanced tests like ADF.

## Augmented Dickey-Fuller Test (ADF)
Augmented Dickey-Fuller test, also known as ADF test, is a statistical test used to determine
whether a series is stationary or not. Mostly with the ADF test we can prove that the statistical
properties of the time series, which are mean, variance and autocorrelation, does not change over
time. When we did the Augmented Dickey-Fuller Test (ADF) on our actual observed point, we
discovered the value of the ADF test as 2.27 and the p-value to be around 0.99

Our interpretation for the Augmented Dickey-Fuller Test (ADF) was that as the ADF value is
positive, the time series of the actual data point is non-stationary. Also, p-value which is higher
than >0.05 helps in rejecting the null hypothesis. Hence our previous claim of stationarity is
rejected with the Augmented Dickey-Fuller Test (ADF).
For further analysis, if we need to make sure the series is stationary. For this we can either do
differencing or advanced methods like detrending, where we remove trends like nonlinear trends.

![image](https://github.com/user-attachments/assets/d630c1b1-4539-489b-be9b-b20b6ff2ff3e)

we will go with a differencing methodology. We consider first
differencing for the transformed Augmented Dickey-Fuller Test (ADF). With the first differencing
we received a new ADF test value to be around -8.772, which is a large negative value. While
comparing critical values, the ADF statistics also suggested that it has more negative values than
the critical value, which can help in rejecting the null hypothesis. Other values at 1%, 5% and 10%
also recommend rejection of the null hypothesis at all significance levels. While comparing pvalue, it was discovered to be around 2.49e-14
As the series is stationary now, we can proceed with further modeling. 

## Fractional differencing:
Fractional differencing is a method to transform a nonstationary time series into a stationary one
while preserving information. This is useful to deal with long memory processes of time series that
exhibit persistent dependence over long time horizons. For fractional differencing we tried to
incorporate the code from the kaggle source.

![image](https://github.com/user-attachments/assets/3386b3fb-faeb-4ff0-8d3e-3a6a75039297

Fractional differencing indeed allows a smooth transition in the weight when applied to past
values.
Comparing the result of fractional differencing vs traditional differencing 

![image](https://github.com/user-attachments/assets/48742a8e-b7b7-4f91-859b-5e8f58a25dff)

Fractional differencing can be utilized when there are case of long memory in data. 

## MLP for Time Series Prediction

we discuss a predictive model we developed that forecasts NVIDIA's future stock
prices based on various historical data points. Our model used past stock prices, their logarithmic
transformations, and fractionally differenced returns to predict future price movements.
Specifically, we built a Multi-Layer Perceptron (MLP) model, a type of artificial neural network
known for capturing complex relationships in data.
We developed three models, each trained on different transformations of the time series data.
We developed three MLP models based on different transformations of the time series data. The
first model used past closing prices in their original form to predict future prices, capturing trends
but struggling with non-stationary behavior. The second model was trained on the stationary
version of the time series, where the mean and variance remain stable over time, allowing it to
focus on short-term fluctuations. The third model applied fractional differencing, a technique that
balances trend preservation with stationarity, providing an adjusted dataset for training.
The model consists of three layers:
1. The first hidden layer with 64 neurons,
2. The second with 32 neurons, and
3. An output layer with a single neuron that predicts the future stock price.
We leveraged the ReLU activation function in the hidden layers to introduce non-linearity and the
Adam optimizer for training, minimizing errors with the mean squared error (MSE) loss function,
Goodfellow et al. (2016). This setup allows the model to learn from the past behavior of the stock
and predict future movements based on those patterns.

![image](https://github.com/user-attachments/assets/cfee1d8e-672d-4b92-b7ac-2630c047dc3e)

As expected, the Fractionally Differenced Model had a higher training R² of 90% and a test R² of
84%, performing exceptionally better than all the models. This suggests that while fractionally
differenced data can improve predictions to a greater extent, Guo et al. (2022).

## Time Series Prediction under Convolutional Neural Network (CNN)
Convolutional Neural Networks (CNNs) are used for image data, but they can also be applied to
time series data by transforming the time series into a suitable format (e.g., images or 2D
representations). The Gramian Angular Field (GAF) is a technique to transform a 1D time series
into a 2D image representation. This allows CNNs to process time series data as if it were image
data.
The GAF below is a representation of lagged time series when we build and train a CNN that is
designed to predict the level of the time series.

![image](https://github.com/user-attachments/assets/fbfbbda2-042a-4369-819e-36285844c4fe)

Given the level of time series under CNN for Nvidia, the chart below shows actual and predicted
prices for different time steps. The chart below shows that the predicted prices and actual prices
vary for the different time steps for the level of time series. A stationary time series may show
otherwise.

![image](https://github.com/user-attachments/assets/6353eff0-2e92-41fb-89fc-11ee55a1d489)

For stationary time series, the GAF below is a representation when we build and train a CNN that
is designed to predict the stationary version of time series. 


![image](https://github.com/user-attachments/assets/92924fae-fe0c-4afb-a92a-25f338f27f76)

From interpretation perspective, diagonal pattern did show strong autocorrelation for all the 3 lags
value. For all the lags it exhibit similarity and can be concluded to some extent it has consistent
pattern. From this pattern we can summarize that the model (GAF+ CNN) from training data it
seems to have utility in prediction.
Given the stationary time series under CNN for Nvidia, the chart below shows actual and predicted
prices for different time steps. Comparing a stationary time series to the level of time series, this
model shows that the actual and predicted prices are very close, albeit the model prediction is less
volatile compared with reality.

![image](https://github.com/user-attachments/assets/d4d38082-e23d-4066-ba2a-f4d696a8369f)

However, for MLP using stationary time series, the actual and predicted prices are not really close
for most of the time steps as demonstrated in the chart below.

![image](https://github.com/user-attachments/assets/f839e1cb-5f8b-4170-b2a7-d6b140787def)

For fractionally differenced time series, the GAF below is a representation when we build and train
a CNN that is designed to predict the fractionally differenced of the time series.

![image](https://github.com/user-attachments/assets/b084dce5-196b-4d27-984d-14c97c571fd4)

Given the fractionally differenced time series under CNN for Nvidia, the chart below shows actual
and predicted prices for different time steps

![image](https://github.com/user-attachments/assets/a5ec42ac-d710-41d1-9149-0ab27f27b558)


We adopted Mean Square Error (MSE) and Mean Absolute Error (MAE) to evaluate the prediction
performance of the three models.
This MSE calculates the average squared difference between the predicted and true values. Also,
the lower MSE indicates better model performance, indicating that the model predictions are closer
to the true values. However, the MAE is less sensitive to outliers than MSE because it considers
the absolute difference rather than squaring it. Additionally, Train R² measures how well the model
explains the variance in the training data while Test R² measures how well the model generalizes
to unseen data. 

![image](https://github.com/user-attachments/assets/68b144b3-8311-4c9d-a445-4d688412c817)

Time series Level for CNN showed a very low train loss and very low train MAE, indicating good
fit and high accuracy to the training data set respectively. In conclusion, the model performs
exceptionally well on the training data (92%) but fails to generalize to the test data due to the very
poor Test R².

For stationary time series for MLP, the result showed a low train loss and low train MAE,
indicating a reasonable fit and good accuracy on the training data respectively. This model also
performs well on the training data (89%) but struggles to generalize the test data. The negative
Test R² indicates overfitting, similar to the Level-CNN model.
Fractionally differenced CNN also showed a very low train loss and very low train MAE,
indicating good fit and high accuracy to the training data set respectively. The model performs
well on the training data (89%) but still fails to generalize to the test data. The negative Test R²
indicates overfitting, although less severe to the other models.
The three models are deemed overfitted as they fail to generalize the test data. To improve model
performance, we should consider regularization and simplifying the models.

![image](https://github.com/user-attachments/assets/1454e75d-43c3-4635-b5e6-ac8f2b992451)

In summary, the Fractionally Differenced-CNN has the lowest MSE and MAE values, indicating
the best performance on the test set. This aligns with the fact that this model generalizes slightly
better than the others (Test R² = -2.75). This is because it retains more information about the time
series, which likely helps the model make better predictions


## Comparing Results under MLP and CNN Architectures 

Considering the historical time series data for NVIDIA, and stock prediction based on different
models. We expect varied model outcomes in terms of model accuracy, training and
interpretability.
MLPs generally treat data as a one-dimensional vector, that is, each input feature is independent
of others, and the model processes them as such. In time series forecasting, MLPs deploy features
like lagging to make predictions. The shortcoming of MLP is that it does not inherently account
for spatial dependencies in data which may limit their ability to model time series with long term
trends or seasonality. However, CNN due to its convolutional layers performs well at spatial
patterns and local dependencies. Using GAF, we are able to process data as a 2D grid, where it
can learn features between nearest data points. Thisis the reason why CNN is suitable for capturing
trends and seasonality as well as capturing intricate patterns which would not be the case in MLPs.
MLPs are effective for capturing short term trends if lagging features are well selected. However,
where patterns often repeat themselves overtime, CNNs work best to handle such patterns over
small temporal windows.
MLPs also require less computational resources compared to CNN because CNN by design takes
time in determining the appropriate number of layers and neurons, as well as the fact that it can
involve GAF transformation.
MLPs lack interpretability because it treats time series as a flat vector and relies on dense layers
which makes it difficult to understand how model predictions are derived. CNN, which looks like
a black box model, through its structure of convolutional layer makes it easier to interpret spatial
features at different layers. 

****![image](https://github.com/user-attachments/assets/622a60dc-ee71-4aef-814e-eef4757fac6e)

Given our R² result on training and test data under the two different approaches, The MLP models
outperform the CNN models across all three-time series (Level, Stationary, and Fractionally
Differenced). The Fractionally Differenced MLP is the best-performing model, with high Train R²
and Test R² values. However, the level MLP performs well but may be less robust to Fractionally
Differenced MLP. In order to improve performance, we would focus on optimizing the MLP
models and addressing overfitting in the CNN models.

![image](https://github.com/user-attachments/assets/f8fc596f-d67b-4f50-b18f-6282abd3ad1f)
Comparing all the results from step 2 and step 3 above created table act as a summary table. When
we compare level time series for MLP model the performance is excellent and shows good fit with
good generalization but when we compare with GAF model with CNN it was overfitted. Model
fits well with training data but fails with test data. When we compared stationary time series, MLP
model developed was poor fitted and poorly generalized while GAF with CNN and GAF with
MLP were good fit model in training but very poor while generalization is considered.
Performance wise GAF models were overfitted models. Finally, fractionally differenced time
series with MLP model works well with good fitting and good generalization while GAF with
CNN has better results in train but poor result in testing. Overall, we can conclude GAF model
works well with training data set but fails miserably with testing data or predicted data.
Finally, if we have to select a model for prediction that would be Fractionally differenced
time series model with MLP modeling.

References for Project 1

1. Goodfellow, I., Bengio, Y., & Courville, A. (2016). Deep Learning. MIT Press
https://www.deeplearningbook.org/
2. Guo, Y., Chen, Y., Wang, C., & Li, Y. (2022). "Gramian Angular Field-Based
Convolutional Neural Network for Multivariate Time Series Classification." Sensors,
22(4), 1617.
3. Aslanidis, Theodoros. "Time Series Forecasting with ANNs." Kaggle,
https://www.kaggle.com/code/theodorosaslanidis/time-series-forecasting-with-anns.
4. Fischer, Thomas, and Christopher Krauss. "Deep Learning with Long Short-Term Memory
Networks for Financial Market Predictions." European Journal of Operational Research,
vol. 270, no. 2, 2018, pp. 654-69. ScienceDirect, doi:10.1016/j.ejor.2017.11.005.
5. Sezer, Omer Gökçe, and A. Murat Özbayoglu. "Algorithmic Financial Trading with Deep
Convolutional Neural Networks: Time Series to Image Conversion Approach." Applied
Soft Computing, vol. 70, 2018, pp. 531-48. ScienceDirect, doi:10.1016/j.asoc.2018.05.025
6. Zhang, G. Peter, et al. "Time Series Forecasting Using a Hybrid ARIMA and Neural
Network Model." Neurocomputing, vol. 50, 2003, pp. 159-75. ScienceDirect,
doi:10.1016/S0925-2312(01)00702-0.
7. TOTH, Daniel J. "Neural Network (MLP) for Time Series Forecasting in Practice."
Towards Data Science, https://towardsdatascience.com/neural-network-mlp-for-timeseries-forecasting-in-practice-04c47c1e3711.

-----------------------------
-----------------------------

## Project 2 : LSTM single output vs Multioutput model  

![image](https://github.com/user-attachments/assets/e1753d61-6424-49da-b99a-c938954464f5)

Image generated from IMAGEN MODEL (Gemini)



Using Yahoo finance library, all required data set of different asset classes were downloaded from the period of Jan 01, 2018 to Dec 30th 2022. 

![image](https://github.com/user-attachments/assets/8687a864-81c3-476d-bf89-fded426af1c8)

In terms of validation and training, throughout the report, we will be considering 20% of dataset for validation for all models, including single LSTM and multi-output model.


![image](https://github.com/user-attachments/assets/3982981e-b71b-4d7c-8287-fdd5dd315be5)


SPY shows a significant up trend and it did indicate strong growth looking at time series. There is a clear display of volatility and drop in 2020, which can be interpreted by Global event like those covered and there is also a strong recovery. 
For gold data there is some moderate up Trend with some minor fluctuation. Comparing SPY  with Gold (GLD)  it seems gold is a stable asset as it is  less volatile in comparison to SPY
Fixed income (TLT) demonstrated up trend till 2021. May be interest rates might have impacted after 2021. Further investigation might be required to make this claim.
SHY  : asset with least volatility among all the five and there is minimal price change within the time frame
Interestingly DBO also suggest flat trend , DBO was impacted by covid  but trend was not visible as the range of graph was between 0-400

![image](https://github.com/user-attachments/assets/1a6831d1-062e-4ec2-ab7d-8f64bf3f6892)

The returns of DBO exhibit significant negative skew and high kurtosis, indicating more frequent large negative returns and extreme movements, while GLD shows slight negative skew and normal kurtosis, suggesting more balanced returns with fewer extreme events. SHY has a slight positive skew and high kurtosis, indicating a tendency for small positive returns with a higher probability of extreme movements. SPY and TLT show similar behavior, with SPY having negative skew and very high kurtosis, while TLT has positive skew and high kurtosis, indicating relatively stable but with potential for larger extreme returns.Oliveira and de M. (2014)


![image](https://github.com/user-attachments/assets/7d0269f3-d9b9-4956-a8f4-c1ee0bfbe42a)

The histograms of returns for all ETFs show a bell-shaped curve, suggesting that the distributions of returns approximate normality. Additionally, the Augmented Dickey-Fuller (ADF) test on the returns confirms their stationarity (p-values far below 0.05), indicating that the time series are mean-reverting and do not contain a unit root (Shumway & Stoffer, 2017).

![image](https://github.com/user-attachments/assets/18bd3b6a-3af7-4a7b-a23c-13084080cb49)

## Model Exploration 
 tried to navigate to various LSTM models to verify and validate the best model. Final decision was made on the basis of a model which was computationally efficient
Experimenting with LSTM

![image](https://github.com/user-attachments/assets/d1484e3d-55d5-4e4f-8a95-171e31a636da)

![image](https://github.com/user-attachments/assets/ae7be664-82b0-44df-8252-cff64b958759)

Additionally, bidirectional LSTM and LSTM with convolutional took extended time period to complete epoch and it seems they are computationally inefficient with respect to data we have.
After considering RMSE and MAE it was decided to leverage ECONDER -DECODER LSTM based model for future training of all the 5 equities. 

In this step, we develop and evaluate a deep learning framework to forecast short-term market trends across five major asset classes. The goal is to predict the 25-day ahead return for each ETF using past information from its own return time series.

We employ Long Short-Term Memory (LSTM) neural networks due to their effectiveness in modeling temporal dependencies in financial time series data. For each asset class, we construct a dedicated LSTM model that takes in lagged returns (1 day,return,5 & 10 days rolling mean and 5 & 10 day standard deviation) as inputs and outputs the expected return 25 days into the future. These are chosen as a sample for the demonstration purposes. The model architecture includes a combination of LSTM and dense layers, with dropout regularization to prevent overfitting.

After training, we evaluate both in-sample and out-of-sample predictive performance across asset classes using standard metrics such as Mean Squared Error (MSE) and R-squared (R²).

Subsequently, we use the model predictions to implement a dynamic trading strategy. The strategy involves rebalancing the portfolio every 25 days by going long on the two assets with the highest predicted returns and short on the two with the lowest predicted returns. The performance of this strategy is backtested and compared to a passive buy-and-hold strategy of an equally weighted portfolio of the five ETFs.

![image](https://github.com/user-attachments/assets/c9bcde61-311c-4050-95fa-0b934b4218d5)
![image](https://github.com/user-attachments/assets/6420a4f2-60e3-4426-bca0-2c278b75614a)


The results suggest overall model performance varies across different asset classes, with GLD showing
the best predictive capability with both the lowest MSE and highest R² values across in-sample and
out-of-sample data. This could be due to the fact that Gold is considered a 'safe have' asset particularly
during the peridos of high volatility, as it tends to have more stable returns compared to ther asset
classes (Baur & Lucey, 2010).
SHY had the weakest performance, with negative R² in both in-sample and out-of-sample evaluations,
indicating poor model fit. Other tickers such as DBO, SPY, and TLT performed moderately, with
reasonably low MSE values and positive R² in the out-of-sample evaluation. Cash-Like assets such as SHY
which are typically low-volaity and low-return instruments might not show clear predictable trneds over
shorter time periods as they tend to relfeclt macro factors like interest rate exhanges which a re a bit
complex to capture in the model mainly using past returns (Campbell & Shiller, 1991).



##  Trading Strategy and Back test result

For trading we are considering top 2 asset as long and bottom 2 as short. We have analyzed buy and hold
strategy with our considered strategy to long top 2 asset and short 2 asset

![image](https://github.com/user-attachments/assets/d5081847-1f2c-42a1-b9f8-aa0db877b527)

The results suggest that the LSTM strategy performed much better than the buy-and-hold strategy over
the long term. LSTM models are particularly effective in capturing complex, non-linear relationships in
financial data, which gives them an edge over traditional strategies like buy-and-hold in the long run
(Fischer & Krauss, 2018). Unlike traditional models, which fail to account for long-term dependencies and
temporal dynamics, LSTM networks are designed to capture these dependencies, leading to improved
predictive performance (Hochreiter & Schmidhuber, 1997).

## Multi Output Model
we are implementing a multi-output deep learning model that integrates the inputs from the
5 individual models in the previous section to predict the 25-day ahead returns for each of the 5 ETFs,
then using these predictions to create and backtest a new trading strategy, comparing its performance
against both a Buy-and-Hold strategy and the LSTM strategy.
Multi output Model Architecture
To analyse time series in a sequence , sequential model is utlized with LSTM layer with a dropout layer to
prevent overfitting which is followed by a hidden desne layer with 64 neurons and RELU activation
function. Output of this hidden dense layer is consider input for another drop out layer to regularize and
then with a dense layer which adds the output layer with 5 neurons. The role of dense layer is to
produce 5 different output value for each if the 5 asset class. In terms of model compilation it is
configured with an ADAM optimizer which is considered as an effective for neural network and to
minimize loss function. Model was trained with 50 epochs and 20% of initial data was considered for
validation.


![image](https://github.com/user-attachments/assets/a7f35435-cb4c-45d3-bef2-7d50b7a7180c)

The backtesting results indicate that the LSMT architectural model outperformed both the Multi-Output
Strategy and the Equal-Weighted Buy & Hold strategy, with the highest final cumulative return of
1.189196. This suggests that the LSMT model, involved a more focused asset allocation based on
predictions, was successful in leveraging the forecasted market trends to generate better returns. On the
other hand, the Multi-Output Strategy had a final cumulative return of 1.040997, which, while positive,
lagged behind LMST model strategy, indicating that the integration of predictions from all asset classes
might have introduced some complexity or diversification that slightly reduced its efficiency (Fischer &
Krauss, 2018).
The Equal-Weighted Buy & Hold strategy had the lowest final cumulative return of 0.994105, which is
expected, as buy-and-hold strategies are typically less responsive to market conditions and do not take
into account predictive models or market signals (Zhang & Xie, 2019). It shows the traditional method of
holding assets equally weighted over the long term without any active rebalancing based on predictions,
which is often less effective in volatile or dynamic markets (Hassan & Ranjan, 2018) compared to
strategies that adjust based on predicted trends.
Backtesting Performance and Predictability Discussion: Multi-Output vs Single-Output Models

![image](https://github.com/user-attachments/assets/a94037ee-dc2b-4312-b8b2-8cf38bc0db8c)
![image](https://github.com/user-attachments/assets/39927c82-4714-471b-9989-f30af6393ef8)

## Conclusion

To conclude, our analysis has provided valuable insights into the effectiveness of two distinct
trading strategies using Long Short-Term Memory (LSTM) models.
Firstly, the LSTM (single-output) model has proven to be a more effective choice for active
trading strategies, showcasing its ability to capture temporal patterns and making it well-suited
for dynamic decision-making. This model aligns with the nature of active trading, where
short-term market movements and timely responses are critical.
On the other hand, the Multi-output model excels in passive screening and relative scoring.
While it offers valuable insights for asset ranking and comparative evaluation, its performance in
backtesting has shown to be less alpha-rich. This model is more suited for strategic portfolio
diversification and long-term decision-making, where rankings and relative performance are
prioritized over immediate market signals.
Ultimately, both models provide complementary predictive insights. However, our findings
suggest that performance is significantly enhanced when ranking-based allocation is integrated
with temporal predictability. This combination allows for more informed decision-making, making
it the more robust model for real-world trading strategies.

References for Project 2 

1. Oliveira, N. A. C. P. P., & de M., M. G. F. P. (2014). Fat tails and extreme risk. Physica A:
Statistical Mechanics and its Applications, 413, 1-12.
https://doi.org/10.1016/j.physa.2014.06.039
2. Black, F., & Litterman, R. (1992). Global portfolio optimization. Financial Analysts
Journal, 48(5), 28-43. https://doi.org/10.2469/faj.v48.n5.28
3. Shumway, R. H., & Stoffer, D. S. (2017). Time Series Analysis and Its Applications: With
R Examples (4th ed.). Springer.
4. Baur, D. G., & Lucey, B. M. (2010). Is Gold a Hedge or a Safe Haven? An Analysis of
Stocks, Bonds and Gold. Financial Review, 45(2), 217–229.
5. Campbell, J. Y., & Shiller, R. J. (1991). Yield Spreads and Interest Rates: A Broad
Historical Perspective. The Journal of Economic Perspectives, 5(2), 129–152.
6. Fischer, T., & Krauss, C. (2018). Deep learning with long short-term memory networks
for financial prediction. European Journal of Operational Research, 270(2), 654-669.
7. "Simple Vanilla RNN and LSTM Implementation." Kaggle, 2023,
www.kaggle.com/code/manan5598/simple-vanilla-rnn-and-lstm-implementation.
8. Brownlee, Jason. "How to Use Dropout on LSTM Networks for Time Series Forecasting."
Machine Learning Mastery, 28 Sept. 2020,
machinelearningmastery.com/use-dropout-lstm-networks-time-series-forecasting/.
9. S. Siami-Namini, N. Tavakoli and A. S. Namin, "The Performance of LSTM and BiLSTM
in Forecasting Time Series," 2019 IEEE International Conference on Big Data (Big
Data), Los Angeles, CA, USA, 2019, pp. 3285-3292, doi:
10.1109/BigData47090.2019.9005997
10. Bhardwaj, Rahul. "Five Practical Applications of the LSTM Model for Time Series with
Code." Towards Data Science, 18 Oct. 2020,
towardsdatascience.com/five-practical-applications-of-the-lstm-model-for-time-series-wit
h-code-a7aac0aa85c0/.

## Project 3 Time series with variation of walk forward and alleviating leakage of information 

![image](https://github.com/user-attachments/assets/8a179872-c4e5-4ee6-9527-935300596e3f)

Code: 






















