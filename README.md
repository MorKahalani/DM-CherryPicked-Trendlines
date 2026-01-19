# **On Detecting Cherry-picked Trendlines**

Topics in Data Management Project (2025-2026)

# **📌 Project Description**

This project implements the methods proposed in the paper "On Detecting Cherry-picked Trendlines" 

The goal is to identify misleading "cherry-picked" claims by calculating a support score—the fraction of alternative trendlines in the data that support the same claim.
We demonstrate the efficiency of the algorithms on the original weather dataset and apply the detection mechanism to a new domain: Bitcoin Price Trends.

# **🛠 Features & Implementation**

**Algorithms:**

* **Baseline**: A brute-force $O(n^2)$ approach for support calculation.

* **EXACT_u**: An optimized $O(n \log n)$ algorithm using sorted target values and binary search.

**Support Metrics:**  Implementation of the support definition for unconstrained trendlines.

**Visualizations:** Automated generation of efficiency curves and support distribution charts.

# **📊 Experiments**

**1. Weather Dataset (Reproduction)**

We replicated the results from the research paper using the Historical Hourly Weather Data: https://www.kaggle.com/datasets/selfishgene/historical-hourly-weather-data?resource=download

*  **Efficiency (Fig 8):** Compared the runtime of Baseline vs EXACT_u on city-specific temperature data. As expected, EXACT_u scales significantly better as the number of tuples ($n$) increases.  
*  **City Support Analysis (Fig 5):** Calculated the support for the claim "Summer was colder than winter in 2012".

       *  Vancouver: Found to have the minimum support (< 0.0001).
       *  Beersheba: Showed the maximum (yet still low) support (~0.1).
       *  Overall Support: Consistently below 0.018, proving the claim is cherry-picked.

**2. Bitcoin/Financial Dataset Analysis**: https://www.kaggle.com/datasets/mczielinski/bitcoin-historical-data

We applied the EXACT_u algorithm to Bitcoin (BTC) price data to find misleading claims:

* Case A (2018 Crash): We identified a short-term window in April/May 2018 where prices rose, creating a "Fake Bull" narrative.

* Case B (2017 Bull Run): We identified a localized dip in June/July 2017 used to suggest a "Fake Bear" trend during one of Bitcoin's strongest years.

# **💻 Tech Stack**

**Language:** Python

**Libraries:** pandas, numpy, matplotlib, seaborn

**Environment:** Jupyter Notebook
