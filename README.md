# Copula-Structure-Analysis
Implementation of paper [Copula Structure Analysis](https://rss.onlinelibrary.wiley.com/doi/full/10.1111/j.1467-9868.2009.00707.x) by Claudia Klüppelberg and  Gabriel Kuhn. 

When we analyse high dimensional data, in the process of understanding dependence structure, we aim at dimension reduction. In the framework of correlation representing linear dependence, correlation structure analysis is a classic tool. Correlation structure analysis is based on the assumption that the correlation matrix of the data satisfies the equation R = R(θ), where θ is a parametric vector. The whole decomposing of correlation structure is justified only when the data is normally distributed. For a normal distribution the dependence is uniquely determined by its correlation matrix. For real multivariate data like financial data where it is not normally distributed, some margins are heavy tailed following occurrence of non-linear dependence, we try to avoid the problems created by non-existing moments or different marginal distributions by using copulas. 

In this paper, the authors introduced a new method of elliptical copulas being copulas of elliptical distributions as they are very flexible and easy to handle in higher dimensions .The correlation structure analysis is there- fore called as copula structure analysis. The main advantage of this method is that we need only IID data to ensure consis- tency and asymptotic normality of the estimated factor loading’s as well as asymptotic χ2 distribution.


## Simulated Data
Consider a Copula Factor model and estimators CX = C(L,V )ξ where L ∈ Rd and V ∈ Rd and ξ ∼ ξq(0,I,G) . We do two studies, one by simulating data and comparing the test statistic with χ2 distribution. The other is comparing it with Classical factor model.
### Simulation Study 
Compare the empirical distribution of T with the limiting Chi- Square distribution with Kendall’s based correlation estimators rT : = vec(RT), Tτ :=nmin[D{r,r(i)(θ)|Γτ}].
### Classical Factor model 
X = (L, V )ξ here ξ ∼ εm+d(0, I, G), where vector of em- pirical correlations is remp = vec(Remp), Tρ := nmin[D{r,r(i)(θ)|Γρ}]. Disadvantage of classical correlation estimator remp is that Γe depends on distribution of X.


We simulated 100 IID samples of length d=10 of t3 Copula. For Copula correlation ma- trix, We calculated corresponding Kandall’s τ matrix and corresponding Kendall’s τ based correlation estimator. For model selection we started with one factor model. For i=1, and 95% confidence test, the null hypothesis of having 1 factor model got rejected. Where as for i=2, the test statistics are less than the corresponding χ2 distribution value. Hence, We continued with the 2-factor model. For sanity check we plotted both 1-Factor and 2-Factor models.
* For 1-Factor model, the empirical values are way off with respect to Chi-Square dis- tribution since the null hypothesis was rejected.
* For 2-Factor model, we plotted for two sets of samples. The qq-plot is more alighed with 2 distribution for larger n values. The following are the QQ-plots for 2 factor model n=10, n=100



## Stock Data
We considered a five-dimensional set of data (oil, S& P 500, usd/eur, usd/yuan),i.e. to know the dependence structure between oil price, the S& P 500 index and some currency exchange rates w.r.t USD. The time series data consists of 1000 daily log-returns from May 2016 to April 2020. 
We tried to fit both normal and t-copula for the whole data set and tested goodness of fit. Goodness of fit is done using Parametric bootstrap goodness-of-fit test with Kendall KS test and normal copula and t copula.

### Test Statistic Calculations
In order to calculate the optimal min value of test statistic, we used python SciPy optimize and fmin() function. It uses a Nelder-Mead simplex algorithm to find the minimum of function of one or more variables.
* For the initial value, we used Factor Analysis from sklearn. decomposition Factor Analysis which is a simple linear generative model with Gaussian Latent Variables.
* For number of factors selection we started with one factor model. For n=1 and 2, and 95% confidence test, the null hypothesis of having 1 factor model got rejected. Where as for n=3, the test statistics are less than the corresponding χ2 distribution value. Hence, We continued with the 3-factor model.
* For 3rd factor there wasn’t any significance as the factor was clear indication of oil price i.e factor value for oil was 1 and rest were zero. Hence the factor was dropped from analysis.

### Conclusions
* For Factor 1 : We can observe that both exchange currency rates are near zero. But oil, gold are negative. S& P500 which is a benchmark index is positive. We can interpret this as a commodity factor
* For Factor 2: We see that both exchange rates are negative , near to -1. Whereas the oil, SnP500 and gold are near zero. This is a factor which is not even tracked by benchmark. We can call this as currency factor.
* These factors aren’t common factors which are indicated by market or any sector. These factors if analysed more can give a greater insight to the dependence structure between the given securities.
