Logistics Data Analysis --- Strategic Planning

📦 Last-Mile E-Commerce Delivery Performance, Demand Prediction & Route Optimization

A data-driven logistics analytics project focused on improving
last-mile delivery reliability, controlling freight costs,
forecasting demand, segmenting operational zones, and optimizing
delivery routes.

This project is based on the Olist Brazilian E-Commerce Public
Dataset, which contains approximately 100,000 orders from
2016--2018. The project combines descriptive analytics, predictive
modeling, clustering, and vehicle-routing optimization into an
end-to-end logistics decision-support framework.

Project status: Planning / implementation framework
Important: The accompanying strategic report intentionally does
not present fabricated model results. Actual model scores and
optimization savings should be calculated after the dataset is
downloaded, cleaned, validated, and tested.

🎯 Objectives

The project aims to:

Build a reliable analytical dataset by integrating relevant Olist
tables.

Measure delivery performance across time, geography, products,
sellers, and customers.

Predict delivery duration and/or late-delivery risk.

Forecast demand to support capacity and workforce planning.

Segment geographic/customer behavior into operational zones.

Formulate a Vehicle Routing Problem (VRP) using geographic and
operational constraints.

Translate analytical findings into practical logistics
recommendations.

🗂️ Dataset

Olist Brazilian E-Commerce Public Dataset

The primary dataset contains approximately 100,000 Brazilian e-commerce
orders from 2016--2018.

Key tables used in the proposed workflow include:

Dataset                              Main Use

olist_orders_dataset.csv           Delivery timestamps, order status,
delay and lead-time analysis

olist_order_items_dataset.csv      Product value, freight cost and
shipment characteristics

olist_customers_dataset.csv        Customer geography and segmentation

olist_sellers_dataset.csv          Seller/origin geography

olist_products_dataset.csv         Product category, weight and
dimensions

olist_geolocation_dataset.csv      Latitude/longitude for distance
analysis

Dataset source: Olist Brazilian E-Commerce Public Dataset.

🔬 Analytical Approach

1. Data Integration & Cleaning

Relevant Olist tables are integrated at the order level.

Planned preprocessing includes:

Converting timestamps to datetime format

Checking duplicates and primary keys

Handling missing values

Separating delivered, cancelled and unavailable orders

Detecting outliers

Aggregating item-level information to order level

Joining customer and seller geographic information

Calculating approximate origin-to-destination distance

2. Exploratory Data Analysis

The analysis focuses on:

Monthly order volume

Delivery lead time

Delivery delays

Freight costs

Geographic performance

Seller and customer segments

Product/category effects

Relationships between distance, weight, freight and delivery time

High-cost or high-delay regions

3. Key Logistics KPIs

KPI                     Purpose                 Desired Direction

On-Time Delivery Rate   Measure service         ↑ Higher
(OTD)                   reliability

Average Delivery Delay  Measure delay severity  ↓ Lower

Freight Cost per Order  Monitor logistics cost  ↓ Lower

Average Delivery Lead   Measure end-to-end      ↓ Lower
Time                    speed

Route Distance per      Measure last-mile       ↓ Lower
Delivery                efficiency

Vehicle Capacity        Improve fleet           ↑ Higher within safe
Utilization             allocation              limits

Vehicle capacity utilization and route-distance KPIs require
additional fleet/routing data for a production implementation.

🤖 Predictive Modeling

Two main prediction problems are proposed:

Delivery Duration Prediction

Predict the number of days/hours required to deliver an order.

Candidate models:

Baseline mean/median predictor

Linear/Ridge Regression

Random Forest Regressor

Evaluation metrics:

MAE

RMSE

R²

Late-Delivery Risk

Predict whether an order is likely to be delivered late.

Possible models:

Logistic Regression

Tree-based classifiers

Evaluation metrics:

Precision

Recall

F1-score

ROC-AUC

For future prediction, a chronological train/test split is
recommended instead of randomly mixing historical and future
observations.

📈 Demand Forecasting

Historical order volume can be aggregated by:

Month

Week

Geography

Operational zone

Time-based features and lag variables can be used to estimate future
demand.

The forecast can support:

Vehicle allocation

Workforce planning

Delivery capacity planning

Peak-period preparation

🧩 Customer & Zone Segmentation

K-means clustering can group geographic/customer areas using variables
such as:

Latitude

Longitude

Order frequency

Average freight cost

Average delivery delay

Average order weight/value

The number of clusters can be evaluated using silhouette score and
operational interpretability.

The purpose is to create practical delivery zones and differentiated
service strategies.

🚚 Route Optimization

The project formulates a Vehicle Routing Problem (VRP) using Google
OR-Tools.

A routing model can include:

Depot/start location

Customer delivery nodes

Travel distance/time

Vehicle capacities

Maximum route duration

Customer time windows

The objective is to reduce avoidable travel and improve vehicle
utilization while respecting operational constraints.

For scalability, routing can initially be solved for small
daily/zone-level problems before expanding through clustering, batching,
time limits, or heuristic approaches.

🔄 End-to-End Workflow

RAW DATA
   ↓
DATA CLEANING & JOINING
   ↓
EDA + KPI BASELINE
   ↓
PREDICTIVE MODELING + CLUSTERING
   ↓
DEMAND FORECASTING
   ↓
ROUTE OPTIMIZATION
   ↓
DECISION SUPPORT
   ↓
OPERATIONAL ACTIONS

📁 Recommended Project Structure

logistics-data-analysis/
│
├── data/
│   ├── raw/
│   ├── processed/
│   └── external/
│
├── notebooks/
│   ├── 01_data_quality.ipynb
│   ├── 02_eda_kpis.ipynb
│   ├── 03_delivery_prediction.ipynb
│   ├── 04_clustering.ipynb
│   └── 05_route_optimization.ipynb
│
├── src/
│   ├── data_prep.py
│   ├── features.py
│   ├── models.py
│   └── routing.py
│
├── outputs/
│   ├── figures/
│   ├── models/
│   └── reports/
│
├── requirements.txt
├── README.md
└── LICENSE

🛠️ Technology Stack

Python

pandas --- data manipulation

NumPy --- numerical computing

Matplotlib / Seaborn --- visualization

scikit-learn --- machine learning and clustering

Google OR-Tools --- vehicle-routing optimization

Jupyter Notebook --- analysis and experimentation

🚀 Getting Started

1. Clone the repository

git clone https://github.com/<your-username>/logistics-data-analysis.git
cd logistics-data-analysis

2. Create a virtual environment

python -m venv venv

Activate it on Windows:

venv\Scripts\activate

On macOS/Linux:

source venv/bin/activate

3. Install dependencies

pip install -r requirements.txt

4. Add the dataset

Place the Olist CSV files inside:

data/raw/

5. Run the notebooks

Start with:

01_data_quality.ipynb

Then proceed through EDA, prediction, clustering and route optimization.

📊 Expected Business Impact

The completed analytics framework is designed to answer four key
management questions:

Where is performance weak?
Why is it weak?
What is likely to happen next?
What action should be taken?

Potential decisions include:

Identifying underperforming regions

Prioritizing high-risk deliveries

Planning capacity before demand peaks

Creating operational delivery zones

Reducing unnecessary route distance

Improving vehicle/driver allocation

Identifying high-cost freight lanes

Monitoring logistics KPIs over time

⚠️ Limitations

The project has several important limitations:

The Olist dataset represents 2016--2018, so it may not represent
today's delivery environment.

The public dataset does not provide direct fleet telemetry.

ZIP-code geolocation provides approximate coordinates rather than
exact addresses.

Some orders have missing delivery timestamps.

Historical relationships should not automatically be interpreted as
causal relationships.

Large VRP problems can become computationally expensive.

For production deployment, the framework should be retrained and
validated using current operational data, real road-network distances,
GPS/fleet information, vehicle capacity data and route logs.

✅ Validation & Governance

The project recommends:

Chronological train/test separation for future prediction

Comparison against simple baselines

Reporting MAE in business-friendly units

Error analysis by region, month, category and order size

Precision/recall analysis for late-risk classification

Comparison of optimized routes against a baseline route plan

Sensitivity analysis for capacity, time windows, demand and distance
assumptions

Versioning of data, features, code and model outputs

Monitoring data and KPI drift

Avoiding data leakage

Minimizing personally identifying customer information

📚 References

Olist Brazilian E-Commerce Public Dataset

Google OR-Tools Routing Documentation

scikit-learn Regression Documentation

scikit-learn Clustering Documentation

scikit-learn Evaluation Metrics Documentation

scikit-learn Random Forest Documentation

👨‍💻 Project Information

Project: Logistics Data Analysis --- Strategic Planning Report
Focus: Last-Mile E-Commerce Delivery Performance, Demand Prediction
& Route Optimization
Dataset: Olist Brazilian E-Commerce Public Dataset
Prepared: September 2026

⭐ Future Enhancements

Possible extensions include:

Real-time delivery ETA prediction

Current operational/fleet data integration

Road-network based travel-time matrices

GPS-based vehicle tracking

Dynamic route re-optimization

Real-time delivery-risk alerts

Interactive logistics dashboard

Automated KPI/model monitoring

Deployment as a web-based decision-support application
