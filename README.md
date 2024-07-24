# MIE1622_Assignment_4
 
Pricing of European and Barrier Options

European Option: The value of a European call or put option for a non-dividend-paying underlying stock is given by
the solution of the Black-Scholes equation.

Alternatively, the price of an underlying stock can be modeled by Monte Carlo simulations using
Geometric Brownian Motion (GBM) with constant drift and volatility. The discretized version
of GBM is known as the Geometric Random Walk equation.

We obtain prices of the European option from Monte Carlo simulations by computing call and put
payoffs and discounting those back to the current time with the riskless short rate r.

One may choose different number of time steps when computing the price of an option. For example,
if the maturity of an option on a stock is 1 year from today, we can compute the price of an underlying
stock once at the end of the year. In this case, the computation involves only one step and we will
denote this method as one-step MC going forward. Alternatively, we may compute the price of
an underlying every week, every month, every day of the year, in other words, we chop the time
interval into as many units as we need. Since we perform calculations multiple times throughout
the life of an option, we will refer to this method as a multiple-step MC.

In this assignment, you need to compare prices of a European call and put options computed from
Black-Scholes formula and from Monte Carlo simulations.

Barrier Option: 

A barrier option is a type of option whose payoff depends on whether or not the underlying asset
has reached or exceeded a predetermined price - barrier.

There are two general types of barrier options, in and out options. A knock-out option only pays
o if the stock does not hit the barrier level throughout the life of the option. If the stock hits a
specifed barrier, then it is knocked out and expires as worthless. A knock-in option on the other
hand only pays out if the barrier is crossed during the life of the option.

If the barrier price is above the spot price, then the option is an up option; if the barrier is below
the spot price then it is a down option. Therefore, we can categorize barrier options (put/call) as
follows: down-and-out, down-and-in, up-and-out, and up-and-in.

Monte Carlo simulations can be used to price barrier options in a similar manner as European
options. Once multiple asset paths for GBM have been simulated, the next step is to determine
the payoff for each asset path. This is done by evaluating each path to see whether it has hit the
barrier. The payoff is then dependent on the type of barrier option and the knowledge of whether
or not the barrier level has been hit during the life of the option. Some options will expire worthless
if the barrier is reached, and others will be worthless unless the barrier is reached.

In this assignment, we will only focus on the knock-in option: the option becomes a standard European
option if the barrier is crossed sometime before expiration. It will then pay if it ends up in the-
money. The barrier is $110 for this assignment and all other variables (initial stock price, strike at
expiry, years to expiry, risk-free rate, drift, volatility) remain the same as in the first part of the
assignment. Note that you may use different number of scenarios for barrier option valuation.

Three Pricing Functions:

1. Black Scholes for European Option
2. Monte Carlo for European Options
3. Monte Carlo for Barrier Knock-In

The number of paths chosen for each Monte Carlo simulation is 100,000. The number of paths need to be large enough for accurate price estimation (according to the law of large numbers the average of the results obtained from a large number of trials should be close to the expected value). The number of time steps chosen (used to calculate the number of calculations of the stock price) for the multi-step was 12, 52, and 252 (Representing months, weeks, and years). The number of steps is selected to represent the time-based periods of common trading strategies. As the number of paths and time steps increase, it will provide a more accurate result but will increase the computation time. The results of the one-step MC simulation and multi-step MC simulation are compared below in Part 2.

**Results:**

Multi steps: Monthly (12)

Black-Scholes price of a European call option is 8.021352235143176
Black-Scholes price of an European put option is 7.9004418077181455
One-step MC price of an European call option is 8.060450530055613
One-step MC price of an European put option is 7.840920573848786
Multi-step MC price of an European call option is 7.990448517773648
Multi-step MC price of an European put option is 7.873521968183865
One-step MC price of an Barrier call option is 7.849650504998772
One-step MC price of an Barrier put option is 0.0
Multi-step MC price of an Barrier call option is 7.93214621191454
Multi-step MC price of an Barrier put option is 1.2744923902658907

Multi steps: Weekly (52)

Black-Scholes price of an European call option is 8.021352235143176
Black-Scholes price of an European put option is 7.9004418077181455
One-step MC price of an European call option is 8.015161880747636
One-step MC price of an European put option is 7.9274454869754445
Multi-step MC price of an European call option is 7.94785269469662
Multi-step MC price of an European put option is 7.886176659380042
One-step MC price of an Barrier call option is 7.829684272035303
One-step MC price of an Barrier put option is 0.0
Multi-step MC price of an Barrier call option is 8.010029597902415
Multi-step MC price of an Barrier put option is 1.7173863545054249

Multi Steps: Daily (252)

Black-Scholes price of an European call option is 8.021352235143176
Black-Scholes price of an European put option is 7.9004418077181455
One-step MC price of an European call option is 8.149968778804695
One-step MC price of an European put option is 7.8257668716518305
Multi-step MC price of an European call option is 7.972309141645514
Multi-step MC price of an European put option is 7.918148549202533
One-step MC price of an Barrier call option is 7.787853705917305
One-step MC price of an Barrier put option is 0.0
Multi-step MC price of an Barrier call option is 7.991006857456702
Multi-step MC price of an Barrier put option is 2.018322737248009

![image](https://github.com/user-attachments/assets/9f9350f1-498b-44ba-8b75-5b0572084ab8)

Each line represents a path for the stock price, since this is a 1-time step model, all of the paths start at initial stock price S0, and predicts the value at the end of 1 year.

![image](https://github.com/user-attachments/assets/b254f629-efcd-45c4-bd79-d54f97864c83)

The histogram shows the frequency of the asset price distribution for the 100,000 paths for the 1 step model. The mean stock price at time T is hovering around $100.

![image](https://github.com/user-attachments/assets/169c8865-6c5c-4fed-a74c-43c325a00d60)

Each line represents a path for the stock price, since this is a 52-time step model, all of the paths start at initial stock price S0, and predicts the future value at 52 different equally spaced time steps to ultimately predict the stock price at the end of 1 year.

![image](https://github.com/user-attachments/assets/135767c7-ca7d-4ff0-8110-118eee516c95)

This shows the asset price distribution for the 100,000 paths for the 52-step model. The mean stock price at time T is similarly also hovering around $100. The number of bins can be chosen to make the histogram look smooth since there are 100,000 paths/samples.

![image](https://github.com/user-attachments/assets/318b539f-22ce-48cb-8738-c3e4f23e07fb)

The number of bins can be chosen to make the histogram look smooth since there are 100,000 paths/samples. 150 bins were used instead of 10 bins, from here it looks more like a normal distribution curve.

The three strategies have very similar results when estimating the price of a European option. The one-step and multi-step MC simulations give similar results to the Black-Scholes equation in which is used as the true value. I can observe that as I increase the number of time steps, the value approaches the value given by the Black Scholes equation. However, one may use fewer time steps or even the one-step MC simulation to save computing power. This may be required when there are many more stock prices to be predicted.

A knock-in option becomes a standard European option if the barrier was crossed by the stock price and worthless if the stock price does not reach the barrier before expiration. This means the knock-in option has a higher chance to become worthless ($0) compared to a standard European option, thus will have a lower expected value and thus lower price. The difference between call option prices for European and Barrier options are very similar. However, the put option prices for European and Barrier options are drastically different. The barrier option is much more stringent and tighter since the barrier ($110) is higher than the strike at expiry ($105). The only way in which the put value makes a profit is for the underlying stock price to go beyond $110 before expiration (pass the barrier) and fall below $105 at expiration (asset price less than strike price). Since the probability of making a profit is quite low, the put option price is also very low. The barrier put option may be worth more if the time to expiry increase, allowing the asset more time to reach the barrier.

Increasing the volatility by 10%:

One-step MC price of an Barrier call option with volatility increased by 10% is 8.658251329622082
One-step MC price of an Barrier put option with volatility increased by 10% is 0.0
Multi-step MC price of an Barrier call option with volatility increased by 10% is 8.657093178136849
Multi-step MC price of an Barrier put option with volatility increased by 10% is 1.5856543858665149

Decreasing the volatility by 10%:

One-step MC price of an Barrier call option with volatility decreased by 10% is 6.9518301941217135
One-step MC price of an Barrier put option with volatility decreased by 10% is 0.0
Multi-step MC price of an Barrier call option with volatility decreased by 10% is 7.103190938498456
Multi-step MC price of an Barrier put option with volatility decreased by 10% is 0.9781872790602056


Discuss possible strategies to obtain the same prices from two procedures:

To be able to obtain the same prices from the Monte Carlo Simulations as the Black-Scholes equation, I can update the number of paths and number of steps. The possible numbers of steps are 1, 12, 52, and 252 which correspond to the number of years, months, weeks, and trading days in 1 year. The possible numbers of paths are 10000, 100000, 500000, and 1000000. I want to check which number of steps could achieve the same up-to-cent price with a smaller number of paths. Black Scholes Equation tells us that the value of the European call option is $8.0213, and the value of the put option is $7.9004. We can see that the 252 time step period with 500,000 paths provides us the call and put option values that is similar to the Black Scholes equation within a cent.



