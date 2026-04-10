# Macro-Econometrics
# Exchange Rate Forecasting Using Econometric and Machine Learning Models
# 1. Introduction
Exchange rate forecasting has long been a central topic in international macroeconomics, particularly due to the difficulty of outperforming simple benchmarks such as the random walk. Since the seminal work of Meese and Rogoff (1983), it has been widely recognised that many structural models struggle to consistently beat naïve forecasts in out-of-sample settings.
This study investigates whether macroeconomic fundamentals can improve exchange rate forecasts and whether machine learning models provide additional predictive power beyond traditional econometric approaches. Specifically, the analysis compares a Vector Autoregression (VAR) model and a Random Forest model against a random walk benchmark in forecasting the GBP/USD exchange rate.

# 2. Data
The dataset consists of monthly observations from December 2003 to January 2025. The variables used are:
	GBP/USD exchange rate obtained from Yahoo Finance
	United States money supply (M2) sourced from FRED
	United Kingdom money supply (M4) obtained from Bank of England statistics
All variables are transformed into logarithms where appropriate.

# 3. Preliminary Analysis
3.1 Stationarity
To ensure valid time series modelling, Augmented Dickey-Fuller (ADF) tests were conducted on all variables. The results indicate that:
	All variables are non-stationary in levels
	All variables become stationary after first differencing
Thus, the analysis proceeds using: ∆y_t=y_t-y_(t-1)
which ensures that the variables are integrated of order one, I(1), and suitable for VAR modelling in differences.
# 4. Theoretical Framework
# 4.1 Monetary Fundamentals Model
The empirical specification is based on the traditional monetary model of exchange rate determination. The vector: z_t=〖(e〗_t,x_t)'
includes the exchange rate ( et ) and a fundamentals term ( xt ), defined as:
x_t=(m_t- ⏞(m_t ) )- (y_t- ⏞(y_t ) )
where:
	( m_t): domestic money supply
	( ⏞(m_t ) ): foreign money supply
	( y_t ): domestic real income
	((⏞(y_t ) ) ): foreign real income
The cointegrating vector is given by:    β'= (1, -1)
This framework originates from the monetary approach to exchange rates developed by Frenkel (1976) and Mussa (1976, 1979), where exchange rates are determined by relative money supplies and output levels across countries.
Although income data is not explicitly included in this implementation, the framework motivates the use of relative monetary variables as key drivers of exchange rate dynamics.

# 4.2 Vector Autoregression (VAR)
The VAR model captures dynamic interactions between multiple time series variables. A VAR(p) model is defined as:  
where:
	( y_t) is a vector containing exchange rates and fundamentals
	( A_i) are coefficient matrices
	( ε_t ) is a white noise error term
The lag length ( p ) is selected using the Akaike Information Criterion (AIC).
The VAR framework is particularly useful as it allows for:
	feedback effects between variables
	dynamic adjustment processes
	flexible modelling without strong theoretical restrictions
# 4.3 Random Walk Benchmark
The random walk model assumes that exchange rate changes are unpredictable:   
or in first differences:  
This model serves as a benchmark under the Efficient Market Hypothesis, which implies that all available information is already incorporated into current prices.

# 4.4 Random Forest Model
The Random Forest model is a machine learning algorithm that constructs an ensemble of decision trees. The model can be expressed as:    
where ( X_t ) includes lagged values of all variables:
 
Random Forests are capable of capturing:
	nonlinear relationships
	interaction effects
	complex patterns in the data
This makes them a useful complement to linear econometric models.
# 5. Methodology
A rolling window forecasting approach is used to evaluate model performance:
	A fixed window size is used for estimation
	Models are re-estimated at each time step
	Forecasts are generated up to 12 months ahead
Forecast accuracy is measured using Root Mean Squared Error (RMSE):<img width="485" height="66" alt="image" src="https://github.com/user-attachments/assets/aafc4d74-76df-48f2-ae1e-1229a952c5f6" />

 
To compare models, relative performance is calculated as:    <img width="104" height="53" alt="image" src="https://github.com/user-attachments/assets/47c0132a-9df1-48b8-899c-7d7028ed2bed" />


# 6. Results
The results show a clear ranking of model performance across all forecast horizons:
	The VAR model consistently achieves the lowest RMSE
	The Random Forest model improves upon the random walk but does not outperform the VAR
	The random walk remains a strong benchmark
Across horizons, the VAR model reduces RMSE by approximately 20–30% relative to the random walk. The Random Forest achieves smaller improvements, typically in the range of 5–20%.

# 7. Discussion
The findings suggest that macroeconomic fundamentals contain useful information for predicting exchange rates. The strong performance of the VAR model indicates that linear relationships between variables are sufficient to capture most of the predictive structure in the data.

While the Random Forest model is able to outperform the random walk, its inability to outperform the VAR suggests that nonlinearities in the data are either weak or not stable over time. These results are consistent with the broader literature, which finds that exchange rate predictability is limited and that simple models often perform surprisingly well.

# 8. Conclusion
This study provides evidence that:
	Macroeconomic fundamentals improve exchange rate forecasts
	Linear econometric models remain highly effective
	Machine learning models offer limited additional gains
Overall, the results support the view that while exchange rates are difficult to predict, incorporating macroeconomic information can yield improvements over naïve benchmarks.
# 9. References
	Frenkel, J. (1976)
	Mussa, M. (1976, 1979)
	Frenkel, J. & Johnson, H. (1978)
	Meese, R. & Rogoff, K. (1983)
	Breiman, L. (2001)

