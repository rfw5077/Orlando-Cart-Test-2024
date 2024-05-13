# Orlando-Cart-Test-2024
The Orlando DSD branch is piloting the use of carts versus pallets as a delivery mechanism. This dashboard was built in order to track pertinent KPI's, both CS&amp;L &amp; Retail metrics relevant to the test.

## Installation
This project was built in PowerBI with the help of Python scripts & Alteryx workflows purposed to wrangle and transform the relevant data important to the cart test.

**PowerBI Version:** 2.128.751.0 64-bit (April 2024)

**Editor Used:** VS Code  
**Python Version:** 3.11.4

### Python Packages Used

**Data Manipulation:**  
* Pandas 1.5.3  
* Numpy 1.24.3
* Datetime 

**File Operations**
* Glob
* OS


## Data
Below is a comprehensive list of data sources used in the project

### Retail Data
**Labor Data** - "\\mznapwapalt002\alteryx\NA_BIS\Orlando Cart Test\Data\Labor Data"
* These files include manually adjusted retail in store service hours split out by employee type
* This data must be manually moved from Rob Miglino into the appropriate alteryx drive folder due to accuracy issues with GCP

**Orlando Store List** - "\\mznapwapalt002\alteryx\NA_BIS\Orlando Cart Test\Data\Store List_M4_2024.xlsx"
* Contains up to date, active store list for the Orlando branch

**Spark Cases** - "\\mznapwapalt002\alteryx\NA_BIS\Orlando Cart Test\Data\orlando_spark_cases.csv"
* This file contains YTD spark cases by store for the Orlando branch by day

### CS&L Data
**Driver Service Data** - "\\kftusoktulfnp15\CL&S\Public\BPA\ERWTransition\DSD Service & Productivity\2024 Service Files"
* These files detail store level service time for drivers, sourced from Descartes data provided by the routing team
* These weekly files are concatenated in a python script and output to a sigle source file used by the dashboard - "\\mznapwapalt002\alteryx\NA_BIS\Orlando Cart Test\Data\orlando_driver_service_ytd.csv"

**Waste Data** - "\\mznapwapalt002\alteryx\NA_BIS\Orlando Cart Test\Data\orlando_waste_ytd.csv"
* This files provides daily waste dollars for the Olrando branch down to the store/sku level
* Reason codes for waste dollars are restricted to:
  * 17 - Damaged in Delivery
  * 40 - DSD Pallet Damage
  * 42 - DSD Handling Damage
  * 43 - DSD Shrink Wrap Damage
  * 45 - DSD Unknown Damage
  * 46 - DSD All Other MFG Damage

**Gross Revenue Data** - "\\mznapwapalt002\alteryx\NA_BIS\Orlando Cart Test\Data\orlando_gr_ytd.csv"
* This file provides daily gross revenue for the Orlando Branch

**Paper & Shrink Wrap Data** - "\\mznapwapalt002\alteryx\NA_BIS\Orlando Cart Test\Data\Paper and Shrink wrap 2023.xlsx"
* Manually provided file from the branch leads in Orlando that tracks paper & shrink wrap spend for the branch

**WUPH & DUPH** - "\\kftusoktulfnp15\CL&S\Public\DSD Dashboard\DSD Dashboard Data.xlsx"
* This is the file that currently populates the iDSD DMS Dashboard and provides branch level WUPH & DUPH values
* **Potential to swap to GCP data once validated**

**Operational Week Map** - "\\mznapwapalt002\alteryx\NA_BIS\Orlando Cart Test\Data\operational_week_map.csv"
* File for mapping dates to operational weeks within the dashboard


## Data Aquisition
Below is the detailed process flow for obtaining all data used in the Orlando Cart Test dashboard.

### Retail Data

**Labor Data**
* Rob Miglino pulls and stores these manual files in a shared drive listed below
  *https://mydrive.mdlz.com/:f:/r/personal/robert_miglino_mdlz_com/Documents/CSL%20all%20EE?csf=1&web=1&e=XnKgvc
* These files are then concatented and transformed by the below python script which outputs a single file for dashboard use
  * "\\mznapwapalt002\alteryx\NA_BIS\Orlando Cart Test\Code\orlando_labor_analysis.ipynb"

**Orlando Store List**
* This is a manually pulled file that can be retrieved from branch management

**Spark Cases**
* This data is pulled from the below BW Query
  * ZORQSC_ZSCNNM56_4145_01A - Wide Open GR (Ad Hoc)
* Using the below Alteryx workflow, scheduled to run daily at 12pm EST
  * "\\mznapwapalt002\alteryx\NA_BIS\Orlando Cart Test\Workflows\orlando_cart_test_automation.yxmd"

### CS&L Data

**Driver Service Data**
* BPA drive is updated weekly on Mondays with previous week's driver service file
* These weekly files are then concatenated and transformed by the below python script which outputs a single file for dashboard use
  * "\\mznapwapalt002\alteryx\NA_BIS\Orlando Cart Test\Code\orlando_driver_service.ipynb"

**Waste Data**
* This data is pulled from the below BW Query
  * ZORQSC_ZSCNNM56_4145_01A - Wide Open GR (Ad Hoc)
* Using the below Alteryx workflow, scheduled to run daily at 12pm EST
  * "\\mznapwapalt002\alteryx\NA_BIS\Orlando Cart Test\Workflows\orlando_cart_test_automation.yxmd"

**Gross Revenue Data** 
* This data is pulled from the below BW Query
  * ZORQSC_ZSCNNM56_4145_01A - Wide Open GR (Ad Hoc)
* Using the below Alteryx workflow, scheduled to run daily at 12pm EST
  * "\\mznapwapalt002\alteryx\NA_BIS\Orlando Cart Test\Workflows\orlando_cart_test_automation.yxmd"

**Paper & Shrink Wrap Data**
* This is a manually pulled file that can be retrieved from branch management

**WUPH & DUPH**
* This file is updated daily by the iDSD DMS Automation workflow. It is simply a reference file that is part of another process.
* **Use of GCP Data under investigation**

**Operational Week Map**
* This data is pulled from the below BW Query
  * ZORQSC_ZSCNNM56_4145_01A - Wide Open GR (Ad Hoc)
* Using the below Alteryx workflow, scheduled to run daily at 12pm EST
  * "\\mznapwapalt002\alteryx\NA_BIS\Orlando Cart Test\Workflows\orlando_cart_test_automation.yxmd"
