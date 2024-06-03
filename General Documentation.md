# Orlando Cart Test 2024 - General Documentation

## Overview
The Orlando Cart Test project revolves around the hypothesis that Mondelez DSD locations can be more efficient by using a different mechanism for loading and transporting product. Currently, most DSD facilities load their product on white wood pallets which require electric forklifts or hand jacks to move throughout the warehouse, the back of the truck and throughout the stores. Instead of using white wood pallets, the continuous improvement team has designed warehouse and retail friendly roller carts with the idea that they can be more easily manuevered and thus drive productivity.

The goal of this project is to test whether these roller carts can prove the intial hypothesis that Mondelez can be more efficient when loading and delivering product to DSD customers on carts versus pallets. The team has chosen the Orlando, FL branch as the testing location. The results will be visually represented using a dashboard showcasing differences in productivity metrics for the Orlando branch on pallets versus carts.

## The Test
This hypothesis will be tested using paired statistical tests on specific KPIs related to warehouse and retail productivity. The Orlando branch currently delivers their product on white wood pallets. Beginning mid June, the entire Orlando branch will transition to delivering their product on Mondelez designed carts.

There will be a collection of 10 weeks of pallet data, paired with 10 weeks of cart data to test if there is any significant increase or decrease in the following productivity related metrics:
 * WUPH - warehouse units per hour
 * DUPH - delivery units per hour
 * Driver Service Time - duration of how long it takes a Mondelez driver to complete a delivery
 * Branch Waste - warehouse product that must be donated
 * Branch Shrink Wrap & Paper Spend - any spend related to paper and shrinkwrap, generally an expense related to shipping on pallets
 * Retail CPH - retail cases per hour

## The Data
Data collection for these metrics is conducted either daily or weekly depending on each KPI:
* WUPH/DUPH - Daily, currently updated using the iDSD DMS Tableau backend file
  * IMPORTANT - GCP validation currently underway for these metrics. The data source could be switched midway through the test.
* Driver Service Time - Weekly, using the routing team's weekly service files
* Branch Waste - Daily, using BW queries to pull data from SAP
* Branch Shrink Wrap & Paper Spend - Ad hoc, provided by branch management
* Retail CPH - Weekly, using BW queries to pull spark cases and a weekly labor file provided by Rob Miglino


