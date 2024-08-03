#C++ Monte Carlo VaR Engine

This C++ Monte Carlo Value-at-Risk (VaR) engine assesses financial portfolio risk at both the portfolio and individual instrument levels. Leveraging design patterns from Mark Joshi's C++ Design Patterns and Derivatives Pricing, it offers reusable, extensible code that supports various instrument types and stochastic processes, including jump diffusion and stochastic volatility.

##Key Components

MCEngine: Orchestrates Monte Carlo simulations, using SimulationEngine and ValuationFunction classes to evaluate risk factors and portfolio positions.

SimulationEngine: Handles path simulations for underlying risk factors, employing smart pointers to manage multiple instruments.

ValuationFunction: Provides tools to value complex derivatives, such as rainbow and Asian options, through numerical methods.

MCStatistics: Aggregates simulation results to generate statistics like VaR, with support for multiple simultaneous outputs via StatisticsCompiler.

##Features

Modular Design: The codebase is designed to be easily extended for new functionality, instrument types, and stochastic processes.

Historical Backtesting: The engine includes backtesting capabilities to verify the accuracy of the VaR model against historical data.

Numerical Methods: Supports complex option valuation through methods such as binomial trees and Monte Carlo simulations for path-dependent derivatives.

Covariance Calculations: Utilizes helper classes for tasks like producing covariance matrices and correlated normal variates.

##Simulation Process

To run a simulation, you must first calculate the covariance matrix and obtain spot rates. These are managed by the TimeSeriesHandler and CSVReader classes. After defining portfolio positions and creating necessary engines and statistics objects, the DoSimulation function executes the risk assessment, providing detailed outputs of the results.

##Backtesting

The engine includes a comprehensive backtesting module. The Backtest class uses historical data to simulate risk factors, updating instrument values to verify the model's accuracy. This process includes calculating exceedances and assessing the statistical significance using binomial tests, ensuring that the VaR predictions align with actual historical outcomes.