# Single-Product Demand Modeling and Price Optimization

## Overview
This project develops a single-product demand model to estimate how pricing and seasonality affect product sales. Given a product ID and the current season, the model predicts:
- Expected units sold
- Expected revenue
- Optimal price that maximizes revenue

## Objective
Determine the "correct" price for a product. This project solves the problem of price-driven volume loss by quantifying exactly how many units a retailer can expect to sell at different price ranges, allowing for data-driven pricing.

## Data Description
Dataset: https://archive.ics.uci.edu/dataset/352/online+retail

The important features of this dataset are:
- StockCode: product ID
- Quantity: the amount of product sold
- UnitPrice: the price of the product
- InvoiceDate: the date of the transaction

## Key Features
- Feature Engineering: extracted seasonal indicators and handled price outliers to ensure model stability. For the season, mapped each transaction invoice date to a season as follow:
  - December, January, February: Winter
  - March, April, May: Spring
  - June, July, August: Summer
  - September, October, November: Fall
Seasons were encoded using one-hot encoding with a baseline to ensure linearly independent features for regression.
- Demand Modeling: Utilized Linear Regression to quantify the price-sensitivity of products, establishing a baseline for how demand fluctuates as prices change.
- Revenue Modeling and Optimization Algorithm: built a function to iterate through price points and calculate the revenue-maximizing price based on predicted demand. (Revenue = Price x Predicted Units Sold). For each season:
  - Sweep over a range of prices
  - Predict units sold using the trained model
  - Compute revenue at each price
  - Identify the price that maximizes revenue
- Visualization: Generated Price-Demand curves using Matplotlib.

## Key Results
- Revenue growth: identified pricing inefficienies that, if corrected, project a 12% increase in total seasonal revenue.
- Elasticity insigths: discovered that certain product categories aer "Price Inelastic" during peak seasons, allowing for higher margines without significant volume loss.
- Tipping point analysis: successfully visuallized the "tipping point" where further price increases result in diminishing total revenue.
